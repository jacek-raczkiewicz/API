<a href="/1.3/README.md">Back to the Table of Contents</a>&nbsp;&nbsp;|&nbsp;&nbsp;<a href="API_METHODS.md">Back to API Methods</a>
<h2>createUser</h2>
<p><strong>Synopsis:</strong><br />
Creates new user with given username and password. The rest of the parameters required for account creation are inherited from creator’s account. 
<div><strong>Request:</strong></div>
<pre>&lt;REQUEST&gt;
  &lt;ACTION&gt;createUser&lt;/ACTION&gt;
	&lt;API_KEY&gt;API KEY&lt;/API_KEY&gt;
	&lt;NEWUSER&gt;New Username&lt;/NEWUSER&gt;
	&lt;NEWPASS&gt;New Password&lt;/NEWPASS&gt;
&lt;/REQUEST&gt;</pre>
<div><strong>Request Parameters:</strong></div>
<pre><strong>Mandatory:</strong> Action, API_KEY, NewUser, NewPass</pre>
<strong>Response Parameters:</strong><br />
    Status, Username, Password, API_KEY, Errorcode, Errorinfo<br>
<strong>Related Error codes: </strong><br />
    E150, E151, E152, E153, E154
<div><strong>Request Examples</strong></div>
XML:
<pre>&lt;REQUEST&gt;
    &lt;ACTION&gt;createUser&lt;/ACTION&gt;
    &lt;API_KEY&gt;qTFkykO9JTfahCOqJ0V2Wf5Cg1t8iWlZ&lt;/API_KEY&gt;
    &lt;NewUser&gt;john&lt;/NewUser&gt;
    &lt;NewPass&gt;john_pass&lt;/NewPass&gt;
&lt;/REQUEST&gt;</pre>
GET:
<pre>https://secure.skycore.com/API/wxml/1.3/index.php?action=createuser&api_key=qTFkykO9JTfahCOqJ0V2Wf5Cg1t8iWlZ
&newuser=john&newpass=john_pass</pre>
<div><strong>Response Example: Success</strong></div>
<pre>&lt;RESPONSE&gt;
    &lt;STATUS&gt;Success&lt;/STATUS&gt;
    &lt;USERNAME&gt;john&lt;/USERNAME&gt;
    &lt;PASSWORD&gt;42363deef6129efa1dc0a54b26cf1426&lt;/PASSWORD&gt;
    &lt;API_KEY&gt;umfKkSLCDKI9yJ5b7fDBk5I8EQaoq88l&lt;/API_KEY&gt;
&lt;/RESPONSE&gt;</pre>
<div><strong>Response Example: Failure</strong></div>
<pre>&lt;RESPONSE&gt;
    &lt;STATUS&gt;Failure&lt;/STATUS&gt;
    &lt;ERRORCODE&gt;E151&lt;/ERRORCODE&gt;
    &lt;ERRORINFO&gt;'username' already exists. Duplicate username&lt;/ERRORINFO&gt;
&lt;/RESPONSE&gt;</pre>
