# Week 11: Web Fundamentals

Lecture Slides: [Presentation](https://docs.google.com/presentation/d/1g9xyq9E5xS0ISw13vWvGKCwz74t4PhzakOg49mVFIXA/edit?slide=id.ge546415ea0_2_84#slide=id.ge546415ea0_2_84)

### Vocabulary & Key Terms

#### Client Server Model

* The model used to serve webpages. Webpages come from the server to a client.&#x20;

#### Dynamic vs. Static

* Static webpages do not move, whereas dynamic webpages have moving elements

#### HyperText Markup Language (HTML)

* Language used to make a website. Made up of tags:
  * \<a>, \<b>, \<img>.

#### CSS (Cascading Style Sheets)

* Used to describe the design of a website

#### JavaScript

* Client-side scripting language to make dynamic web pages.

#### HTML Forms

* Web pages that accept input, either by forms, buttons, or other types of input.

#### DNS (Domain Name System)

* A system or server used for converting domain names into IP addresses

#### IP (Internet Protocol) Addresses

* Unique numbers (dynamic) used to identify devices on the internet

#### URL (Uniform Resource Locator))

* A URL is a string used to access a resource on the internet, like:&#x20;
  *

      <figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>
* When accessing a website, the website conducts a request and response cycle.

#### HTTP (Hypertext Transfer Protocol)

* Used for communicating on layer 7 with websites.
  * Response Codes/Headers
    * 100: Continue      \
      The client should continue the request, or if it’s already complete, it should ignore the response
    * 101: Switching Protocols      \
      Sent in response to an Upgrade request header and tells the client what protocol the server is switching to. (Not sure exactly what it means by switching protocol
    * 102: Processing      \
      The request has been received by the server, but there is no status available yet.
    * 200: OK      &#x20;The request was good and has succeeded.
    * 202: Accepted      \
      The request was received by the server, but nothing has been done by the server yet. Used for batch processing.
    * 203: Non-Authoritative Information      \
      Returned metadata is not the same as the origin server. Used for mirrors or backups.
    * 226: IM Used      \
      Practically a 200 OK, but the response has some data about the instance changed      \
      Redirection Messages:      \
      (There needs to be further action to complete the request.)
    * 300: Multiple Choice      \
      There are more than one response, and the client needs to choose one. Rarely used because there’s no real way for clients to automatically choose a response.
    * 301: Moved Permanently      \
      The URL that you are requesting has moved to a different endpoint, and this endpoint will not work.
    *   307: Temporary Redirect        \
        Much like Moved Permanently, the temporary redirect tells the client to go to another URI with the same method


    * 400: Bad Request      \
      The server cannot process the request because you messed something up with the request, like syntax, etc.
    * 401: Unauthorized      \
      You do not have the credentials to make this HTTP request. You need to authenticate yourself to get a response.
    * 403: Forbidden      \
      Much like unauthorized, you are being denied a resource, but 403 indicates that the server knows who you are. You have authenticated, but you still don’t have access.
    *   404: Not Found

        The server cannot find the resource/endpoint you are looking for.
    * 408: Request Timeout      \
      The connection has lasted for too long, and it is idle, so the connection has ended.
    * 418: I’m a teapot      \
      “The server refuses the attempt to brew coffee with a teapot” - What….      \

    * 500: Internal Server Error      \
      The server encountered an error and it doesn’t know what to do.
    * 503: Service Unavailable      \
      The server may be down for maintenance or overloaded.
    * 506: Variant Also Negotiates      \
      Internal Configuration Error: Circular references. (wtf is this error code)
    * 510: Not Extended      \
      The client asks for an HTTP extensions, but the extension is not supported.
  * Request methods
    * Request methods indicate what type of operation you are performing.
    * GET requests get data, whereas POST requests send data.

#### PHP (Hypertext Preprocessor)

* Server-side scripting language used to make dynamic web pages like input forms, etc. Where HTML defines structure, PHP defines the logic and function.

### Diagrams and Visuals

![](<../../.gitbook/assets/unknown (70).png>)

![](<../../.gitbook/assets/unknown (71).png>)

![](<../../.gitbook/assets/unknown (68).png>)

![](<../../.gitbook/assets/unknown (69).png>)

### Commands, Tools, or Techniques

* apache2 - Webserver
  * Directory: /var/www/html
  * Default display file: index.html
  * systemctl start apache2

\
\
<br>
