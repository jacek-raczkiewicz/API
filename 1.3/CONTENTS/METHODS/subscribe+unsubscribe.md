<a href="/1.3/README.md">Back to the Table of Contents</a>&nbsp;&nbsp;|&nbsp;&nbsp;<a href="API_METHODS.md">Back to API Methods</a>
<h2>subscribe + unsubscribe</h2>
<p><strong>Synopsis:</strong><br />
This API will subscribe or unsubscribe users to a particular campaign. Once a user is subscribed to a campaign they will receive all auto responders and scheduled messages for that campaign until they are unsubscribed through the API or through normal STOP or STOP ALL SMS request. You may not re-subscribe someone who has unsubscribed themselves from a campaign. You may re-subscribe someone who you have unsubscribed through the API.</p>
<div><strong>Request: subscribe</strong></div>
<pre>&lt;REQUEST&gt;
  &lt;ACTION&gt;subscribe&lt;/ACTION&gt;
	&lt;API_KEY&gt;API KEY&lt;/API_KEY&gt;
	&lt;CAMPAIGNID&gt;Campaign ID&lt;/CAMPAIGNID&gt;
	&lt;MOBILE&gt;Number to subscribe&lt;/MOBILE&gt;
	&lt;DATA&gt;
		&lt;FIRST_NAME&gt;First Name&lt;/FIRST_NAME&gt;
		&lt;LAST_NAME&gt;Last Name&lt;/LAST_NAME&gt;
		&lt;GENDER&gt;Gender&lt;/GENDER&gt;
		...
	&lt;/DATA&gt;	
	&lt;NOTIFY&gt;'yes/no' on whether to notify user on successful opt in&lt;/NOTIFY&gt;
	&lt;SPID&gt; the carrier ID &lt;/SPID&gt;
	&lt;CTA&gt;'yes/no' to request double opt in from the user to opt-in&lt;/CTA&gt;
        &lt;TIMEZONE&gt;Timezone abbreviation: EST, CST, MST, PST, etc.&lt;/TIMEZONE&gt;
&lt;/REQUEST&gt;</pre>
<div><strong>Request: unsubscribe</strong></div>
<pre>&lt;REQUEST&gt;
    &lt;ACTION&gt;unsubscribe&lt;/ACTION&gt;
    &lt;API_KEY&gt;API KEY&lt;/API_KEY&gt;
    &lt;CAMPAIGNID&gt;Campaign ID&lt;/CAMPAIGNID&gt;
    &lt;MOBILE&gt;Number to unsubscribe&lt;/MOBILE&gt;
	&lt;NOTIFY&gt;'yes/no' on whether to notify user on opt-out&lt;/NOTIFY&gt;
&lt;/REQUEST&gt;</pre>
<div><strong>Request Parameters:</strong></div>
<pre><strong>Mandatory:</strong> Action, API_KEY, CAMPAIGNID, Mobile
<strong>Optional:</strong> CTA, Notify, SPID, TZ</pre>
<strong>Response Parameters:</strong><br />
CAMPAIGNID, Errorcode, Errorinfo, mobile, Status

<strong>Related Errorcodes: </strong><br />
E901, E902, E903, E904, E905

<div><strong>Request Examples</strong></div>
XML:
<pre>&lt;REQUEST&gt;
	&lt;ACTION&gt;subscribe&lt;/ACTION&gt;
	&lt;API_KEY&gt;qTFkykO9JTfahCOqJ0V2Wf5Cg1t8iWlZ&lt;/API_KEY&gt;
	&lt;CAMPAIGNID&gt;1116&lt;/CAMPAIGNID&gt;
	&lt;MOBILE&gt;16502426055&lt;/MOBILE&gt;
	&lt;DATA&gt;
		&lt;FIRST_NAME&gt;John&lt;/FIRST_NAME&gt;
		&lt;LAST_NAME&gt;Smith&lt;/LAST_NAME&gt;
		&lt;AGE&gt;29&lt;/AGE&gt;
		&lt;PET&gt;Dog&lt;/PET&gt;
	&lt;/DATA&gt;	
	&lt;NOTIFY&gt;no&lt;/NOTIFY&gt;
	&lt;CTA&gt;no&lt;/ CTA&gt;
&lt;/REQUEST&gt;</pre>
GET:
<pre>https://secure.skycore.com/API/wxml/1.3/index.php?action=subscribe&api_key=qTFkykO9JTfahCOqJ0V2Wf5Cg1t8iWlZ
&mobile=16502426055&campaignid=1116&notify=no&cta=no&data_first_name=John&data_last_name=Smith&data_age=29&
data_pet=Dog</pre>
<div><strong>Response Example: Success</strong></div>
<pre>&lt;RESPONSE&gt;
    &lt;STATUS&gt;Success&lt;/STATUS&gt;
    &lt;CAMPAIGNID&gt;1116&lt;/CAMPAIGNID&gt;
    &lt;MOBILE&gt;16502426055&lt;/MOBILE&gt;
&lt;/RESPONSE&gt;</pre>
<div><strong>Response Example: Failure</strong></div>
<pre>&lt;RESPONSE&gt;
    &lt;STATUS&gt;Failure&lt;/STATUS&gt;
    &lt;ERRORCODE&gt;E903&lt;/ERRORCODE&gt;
    &lt;ERRORINFO&gt; Invalid CAMPAIGNID &lt;/ERRORINFO&gt;
&lt;/RESPONSE&gt;</pre>
<p><strong>Postback Notifications</strong><br />
Upon subscribing/unsubscribing a number the system will generate a notification.</p>
<div><strong>On subscribe:</strong></div>
<pre>&lt;NOTIFICATION id="325" created="2011-01-01 20:09:12.975911-04 "&gt;
    &lt;ORIGIN&gt;SUB&lt;/ORIGIN&gt;
    &lt;CODE&gt;N301&lt;/CODE&gt;
    &lt;BODY&gt;
        &lt;MOBILE&gt;16502426055&lt;/MOBILE&gt;
        &lt;CAMPAIGNID&gt;1116&lt;/CAMPAIGNID&gt;
    &lt;/BODY&gt;
&lt;/NOTIFICATION&gt;</pre>
<div><strong>On unsubscribe:</strong></div>
<pre>&lt;NOTIFICATION id="325" created="2011-01-01 20:09:12.975911-04" &gt;
    &lt;ORIGIN&gt;SUB&lt;/ORIGIN&gt;
    &lt;CODE&gt;N302&lt;/CODE&gt;
    &lt;BODY&gt;
        &lt;MOBILE&gt;16502426055&lt;/MOBILE&gt;
        &lt;CAMPAIGNID&gt;1116&lt;/CAMPAIGNID&gt;
    &lt;/BODY&gt;
&lt;/NOTIFICATION&gt;</pre>
