﻿ - LAB ( BWAPP)
 - Vulnerable as `HTTP_HOST` 
 - User Action is required
 - Example: reset code link (MITM)

  Reference

```
https://www.skeletonscribe.net/2013/05/practical-http-host-header-attacks.html

```
 Vulnerable Code

```
<b>Password Reset Form</b>
<form action="" method="POST">
	<input type="text" name="email">
	<input type="submit" name="submit" value="reset">
</form>
<?php
	if (isset($_POST['submit'])) {
		$to      = $_POST['email'];
		$subject = "Password Reset Code for Vulnerable Lab";
		$headers = "From: sender@gmail.com\r\n";
		$headers .= "MIME-Version: 1.0\r\n";
		$headers .= "Content-Type: text/html; charset=ISO-8859-1\r\n";
		$body    = "Dear Mrs. LOL,<br>You can reset your password <a href=http://".$_SERVER['HTTP_HOST']."?resetcode=CODE_".rand()." target=\"_blank\">here.</a><br><br>Regard, Vulnerable Inc.";

		$sender  = "sender@gmail.com";

		if(mail($to, $subject, $body, $headers, "-f $sender"))
		{
			print "Success";
		}
		else
		{
			print "Failed";
		}
	}
?>

```
