# Cross site scripting

## Content
- Foreword
- Research question:
   - What is cross site scripting?
   - What counter measures can be taken against cross site scripting?
   - Which default prevention techniques does react have built in?
- Conclusion
- References


## Foreword

The reason why I researched this topic is to secure my application better due to my app being
a content management system which includes a load of user data which can make it very
unsafe. This research was done using the DOT framework with the following strategies:
**Literature study**.


## Research question:

Main question:
How can cross site scripting be prevented in my application?
- What is cross site scripting?
- What counter measures can be taken against cross site scripting?
- Which default prevention techniques does react have built in and?


## What is cross site scripting?

Cross site scripting is a kind of attack where the attacker injects malicious script into
websites. These kinds of attacks usually happen by the attacker sending a malicious script
to another user when using a web application. The attacks usually take place when input
from a user is used in the output to a user and is not being properly validated or encoded.
The main problem of cross site scripting is the inability of the browser to know if the content
is trustable due to it being sent from a trusted source. Due to the browser thinking it’s
trustable to execute the script the attacker gains access to sensitive information like
sessions and cookies and rewrite HTML content.

These attacks can be carried out in 3 ways:
- Reflected XSS: Reflected XSS happens when an injected script is reflected off a web server and sent to the client when requesting data from a server depending on user input.
   <br/>
  <img src="https://github.com/DB-S3/Documentation/blob/main/Images/xss-reflected.gif?raw=true" alt="drawing" width="350"/>

- Stored XSS: Stored XSS are attacks where the script is stored on the server. For instance a database, forum or visitor. After which the user will unknowingly execute the script and give control to the attacker.
   <br/>
  <img src="https://github.com/DB-S3/Documentation/blob/main/Images/xss-stored.gif?raw=true" alt="drawing" width="350"/>
- DOM-Based XSS DOM-Based XSS when the attacker is allowed to change the DOM and let a user execute code through it.
   <br/>
  <img src="https://github.com/DB-S3/Documentation/blob/main/Images/Dom-based-XSS.jpg?raw=true" alt="drawing" width="350"/>

## What counter measures can be taken against cross site scripting?

There are many ways to prevent cross site scripting attacks
- Sanitise and validate input forms: Input forms are the most common form of XSS attack due to the user input data, checking the data is especially important when the users data is used in html content. This usually means that script tags need to be extracted from user data.


- Implement a content security policy: A content security policy defines the sources of content that can be used by the website this greatly reduces the risk of inline scripting. Think of where images, scripts, css are allowed to come from. This makes it harder to inject malicious elements into a website.

- Web application firewall: web application can detect bots and malicious activity and can block the attacker before he’s able to do any damage.

- Up to Date: Keep the software used up to date to prevent the attacker using vulnerabilities and remove all unused software to further decrease the risk of vulnerabilities.

- Scan code: To decrease the risk of XSS attack tools like acunetix can be used to scan whether there are any vulnerabilities in the application. This will let you know where to pay extra attention to secure the application.

## Which default prevention techniques does react have built in?

The react front-end framework has built in protection against XSS under the hood
- Auto escaping: This means when user input is passed onto a component the input will be categorised as a string making it impossible for an attacker to input a script.
- Inline react won’t allow inline script tags making it harder to store html in the database and injecting into the browser.


## Conclusion
To prevent the cross site scripting in the application measures need to be taken on the front-end and the back-end to ensure safety.

Front-end: To prevent it on the front-end the most important countermeasure is sanitizing the input from the user and filter out dangerous inputs, uninstall the unused packages and scan with a tool like acunetix to find vunerabilities in the application more easily. And finally add a content security policy so only the react script can be ran in the browser.

Back-end: To prevent cross site scripting on the back-end all user input needs to be sanitised for safety.

These measures will greatly decrease the risk of cross site scripting. 


## References

```
A7:2017-Cross-Site Scripting (XSS) | OWASP. (2017).Owasp.Org. Retrieved

December 1, 2021, from

https://owasp.org/www-project-top-ten/2017/A7_2017-Cross-Site_Scripting_(XSS).html
```
```
DOM Based XSS Software Attack | OWASP Foundation .(z.d.). Owasp.Org.

Geraadpleegd op 2 december 2021, van

https://owasp.org/www-community/attacks/DOM_Based_XSS
```
```
Guercio, K. (2021, 19 mei). How to Prevent Cross-SiteScripting (XSS)

Attacks. ESecurityPlanet. Geraadpleegd op 2 december2021, van

https://www.esecurityplanet.com/endpoint/prevent-xss-attacks/
```
```
React XSS Guide: Examples and Prevention. (2021, 18juli). StackHawk.

Geraadpleegd op 2 december 2021, van

https://www.stackhawk.com/blog/react-xss-guide-examples-and-prevention/#is-react-xss-foolproof
```

