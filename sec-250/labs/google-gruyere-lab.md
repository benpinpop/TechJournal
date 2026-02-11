# Google Gruyere Lab

## Challenge 1 (File Upload XSS)

![](../../.gitbook/assets/unknown.png)

Create an HTML file and save it as a .html. Ensure that you have a script in there.

![](<../../.gitbook/assets/unknown (1).png>)

Upload it to Gruyere, and navigate to the link.

![](<../../.gitbook/assets/unknown (2).png>)

You are now being attacked through an XSS attack.&#x20;

### Reflection

#### Look at the [OWASP Top 10](https://owasp.org/Top10/2025/) site; what categories would the vulnerabilities you found fit into, if any?

A05 Injection, Security Logging, and Alerting Failures. Particularly, this is CWE-79 Improper Neutralization of Input During Web Page Generation.&#x20;

#### What kind of impact could this vulnerability have?

This vulnerability could have a large impact on confidentiality and availability. If a user clicks on the file, account passwords could be stolen, or even malware could be downloaded if a CVE is exploited. Typically, a script like this usually runs an HTTP request to steal the account cookie and hijack the session. &#x20;

#### How would you fix this vulnerability?

Sanitize input files by scanning for XSS attacks and blocking any invalid input.

## Challenge 2 (Reflected XSS)

![](<../../.gitbook/assets/unknown (3).png>)

Navigate to the Gruyere website and input \<script>alert(“ay yo”)\</script> as the path.

![](<../../.gitbook/assets/unknown (4).png>)

This is the final page that shows up after the Reflected XSS is complete.

### Reflection

#### Look at the [OWASP Top 10](https://owasp.org/Top10/2025/) site; what categories would the vulnerabilities you found fit into, if any?

A05 Injection and A06 Insecure Design. At a minimum, you should not be able to run an XSS attack in the path. If any user clicks on the link, their account will be instantly stolen.&#x20;

#### What kind of impact could this vulnerability have?

This is the same as challenge number 1. An individual could steal your session cookies, make a post on your behalf, etc, etc. Violate integrity and confidentiality.&#x20;

#### How would you fix this vulnerability?

Filter URL paths to sanitize all HTML and script objects to stop reflected XSS attacks.

## Challenge 3 (Stored XSS)

![](<../../.gitbook/assets/unknown (5).png>)

Start by creating a snippet. We can circumvent the current sanitization by just adding the alert to an HTML event. Let’s create this new snippet.

![](<../../.gitbook/assets/unknown (6).png>)

When we hover over our “read this!” snippet, we get our alert, which proves that we can likely execute any JavaScript code that we want.&#x20;

### Reflection

#### Look at the [OWASP Top 10](https://owasp.org/Top10/2025/) site; what categories would the vulnerabilities you found fit into, if any?

A05 Injection. This is a classic cross-site stored XSS attack.&#x20;

#### What kind of impact could this vulnerability have?

This would theoretically have a worse impact than the reflected XSS attacks because they would require a link to be clicked. In this instance, they just require the site to be loaded for the attack to take place. If anyone hovers over this, which is very easy for any user potentially scrolling the site, their cookies could be stolen, or malware could theoretically be downloaded. Not good.&#x20;

#### How would you fix this vulnerability?

Same as above, sanitize HTML attributes&#x20;

## Challenge 4 (Stored XSS via HTML)

![](<../../.gitbook/assets/unknown (7).png>)

Now, we want to try doing a Stored XSS via an HTML attribute. (I don’t know why this challenge is different from Challenge number 3, but I may be doing it wrong)

![](<../../.gitbook/assets/unknown (8).png>)

We also get alert(2) on mouse over.&#x20;

### Reflection

#### Look at the [OWASP Top 10](https://owasp.org/Top10/2025/) site; what categories would the vulnerabilities you found fit into, if any?

This would fall under A05 Injection and Insecure Design. We shouldn’t be trusting the users with their own HTML tags; that’s just asking for an XSS vulnerability.

#### What kind of impact could this vulnerability have?

Again, same as before in all of these challenges. When you have an XSS attack, the JavaScript has access to pretty much everything on the browser, including cookies.

#### How would you fix this vulnerability?

Sanitize input and restrict the usage of HTML events through regex. <br>

## Challenge 5 (Stored XSS via AJAX)![](<../../.gitbook/assets/unknown (9).png>)

First, submit a snippet with the following code: all `<span style=display:none>"+ (alert(1),"")+ "</span>your base`

Then curl feed.gtl. You can also go to the website itself and see the vulnerability in action. The code doesn’t even show up, which means it can be hidden behind the website.&#x20;

![](<../../.gitbook/assets/unknown (10).png>)

View the website, and there is no “alert(1)” shown.&#x20;

### Reflection

#### Look at the [OWASP Top 10](https://owasp.org/Top10/2025/) site; what categories would the vulnerabilities you found fit into, if any?

Injection and Insecure Design.

#### What kind of impact could this vulnerability have?

See Challenges 1-4.

#### How would you fix this vulnerability?

SANITIZE INPUT PROPERLY!!!! RAHHHHH

## Challenge 6 (Reflected XSS)

![](<../../.gitbook/assets/unknown (11).png>)

A reflected XSS also exists in the user paths, when looking up individual users. If we look for a UID but instead insert a script, we can get an alert.&#x20;

![](<../../.gitbook/assets/unknown (12).png>)

This is what the alert looks like.&#x20;

### Reflection

#### Look at the [OWASP Top 10](https://owasp.org/Top10/2025/) site; what categories would the vulnerabilities you found fit into, if any?

This fits into A05 Injection and Insecure Design.

#### What kind of impact could this vulnerability have?

See Challenge 2.&#x20;

#### How would you fix this vulnerability?

See Challenge 2.&#x20;

## Challenge 7 (Client Side Manipulation)

![](<../../.gitbook/assets/unknown (13).png>)

Google Gruyere seems to support allowing unauthorized users to make admin updates. I first tried creating a cookie called is\_admin and setting it to true, but that didn’t work.

![](<../../.gitbook/assets/unknown (14).png>)

Then, we need to log out so our admin cookie can be reissued.

![](<../../.gitbook/assets/unknown (15).png>)\
When we log in, we have server management access.

### Reflection

#### Look at the [OWASP Top 10](https://owasp.org/Top10/2025/) site; what categories would the vulnerabilities you found fit into, if any?

Well, for one, broken access control. Any user can update their admin status. In addition, Insecure Design applies to this as well.&#x20;

#### What kind of impact could this vulnerability have?

Well, any user can just give themselves admin access, so that’s a little ridiculous. They can manage accounts, possibly shut down the server, or, if they’re given the permission, modify snippets and attack other users.&#x20;

#### How would you fix this vulnerability?

Implement authentication for these endpoints, or disable them entirely. Only admin users should be able to grant admin access. It’s as simple as that. Do a database check at a minimum.

## Challenge 8 (Cookie Manipulation)

![](<../../.gitbook/assets/unknown (16).png>)

At first, I tried to create an is\_admin cookie and set it to true, but that didn’t seem to work. So I wanted to examine the cookies and see if I could find a pattern. Each cookie seems to come with a user id, username, and permission levels.&#x20;

![](<../../.gitbook/assets/unknown (17).png>)

![](<../../.gitbook/assets/unknown (18).png>)

Looking at our Gruyere guide, we can fake an account by just copying the Gruyere cookie separator. When we sign up for this username, we get our admin access.

![](<../../.gitbook/assets/unknown (19).png>)

As can be seen here.&#x20;

### Reflection

#### Look at the [OWASP Top 10](https://owasp.org/Top10/2025/) site; what categories would the vulnerabilities you found fit into, if any?

I would say this falls under Insecure Design, possibly Injection, and Cryptographic failures. If the application did a better job at storing the user data, maybe instead with a JWT or doing some hashing, it wouldn’t save multiple properties into a cookie. Just make each property separate, and store them into a database.&#x20;

#### What kind of impact could this vulnerability have?

See Challenge 7.&#x20;

#### How would you fix this vulnerability?

Users should be restricted from inputting special characters into the user field, and this should be filtered at the endpoint, not the client side.&#x20;

## Challenge 9 (XSRF)

![](<../../.gitbook/assets/unknown (20).png>)

The snippet code used to delete another user's snippet via XSRF <br>

![](<../../.gitbook/assets/unknown (21).png>)

Snippets before upload.

![](<../../.gitbook/assets/unknown (22).png>)

Snippets after upload.

![](<../../.gitbook/assets/unknown (23).png>)

After the site refreshes, a snippet has been deleted by the first snippet of index 0.&#x20;

### Reflection

#### Look at the [OWASP Top 10](https://owasp.org/Top10/2025/) site; what categories would the vulnerabilities you found fit into, if any?

#### What kind of impact could this vulnerability have?

#### How would you fix this vulnerability?

## Challenge 10 (XSSI)

### Reflection

#### Look at the [OWASP Top 10](https://owasp.org/Top10/2025/) site; what categories would the vulnerabilities you found fit into, if any?

#### What kind of impact could this vulnerability have?

#### How would you fix this vulnerability?

<br>
