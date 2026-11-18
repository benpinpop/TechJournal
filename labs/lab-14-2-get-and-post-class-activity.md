# Lab 14-2: GET and POST Class Activity

Use the following server for this activity: http://192.168.4.135/

&#x20;

1\. Open up Wireshark to get ready to capture packets

2\. Start the capture

3\. Go to the website on http://192.168.4.135/get.html&#x20;

4\. **Fill** it out and submit

5\. Stop the capture

Review the capture and answer the following:

* Can you find the Form in the HTML from the server? **Post Screenshot of the Form in the packet (1 POINT)**
*

    <figure><img src="../.gitbook/assets/image (172).png" alt=""><figcaption><p>Screenshot of the Wireshark Packet with Form Details</p></figcaption></figure>
* Can you find the GET Request that is created **when you submit the form**? **Post Screenshot (1 POINT)**
  *

      <figure><img src="../.gitbook/assets/image (173).png" alt=""><figcaption></figcaption></figure>
* Where can you find the submitted values in the packet that was sent to the server? **Post Screenshot (1 POINT)**
  *

      <figure><img src="../.gitbook/assets/image (174).png" alt=""><figcaption><p>Screenshot of submitted values via query parameters</p></figcaption></figure>

&#x20;

POST:

Repeat steps 2 -5 but this time use the POST (<a href="http://192.168.4.135/post.html" target="_blank">http://192.168.4.135/post.htmlLinks to an external site.</a>)

* Can you find the Form in the HTML from the server? **Post Screenshot of the Form in the packet (1 POINT)**
  *

      <figure><img src="../.gitbook/assets/image (175).png" alt=""><figcaption><p>Screenshot of form in the HTML in Wireshark</p></figcaption></figure>
* Do you see the "method" that is used by the form?
  * method="post"
* Can you find the POST Request that is created when you submit the form? **Post Screenshot (1 POINT)**
  *

      <figure><img src="../.gitbook/assets/image (176).png" alt=""><figcaption><p>Screenshot of the created POST request upon submission</p></figcaption></figure>
* What is the big difference from the GET file in the packet that was sent to the server? **Post Screenshot (1 POINT)**
  * **The POST request includes data in the body, whereas the GET request sends the request via URL parameters.**&#x20;
