An HTTP request is used to retrieve a specific resource from a web server. This resource can be an HTML file, a video, JSON data, etc. The web server’s job is to process the response received and present it to the user.

![](https://miro.medium.com/v2/resize:fit:1050/0*nbKun6Ll1ZelLYD1.png)

HTTP Request

1. The GET method indicates that the resource `/` is being requested from the server. Because there is no name, a symbol like `/` means that the main page of the web server is being requested.
2. HTTP/1.1 indicates that the client wants to use HTTP/1.1.
3. Nowadays, there are web applications that belong to more than one domain found on a single web server, so browsers use the Host header to identify which domain the requested resource belongs to.
4. When a web application wants to store information on the client’s device, it stores it in a Cookie header. Cookies are typically used to store session information. This saves you from having to re-enter your username and password when you visit a web application that requires you to log in.
5. The Upgrade-Insecure-Requests HTTP header is a client-side request header used by browsers to signal to servers that the client prefers to upgrade insecure (HTTP) requests to secure (HTTPS) ones when possible. It is a boolean-like flag where:  
    1 = true / enabled (upgrade is preferred)  
    0 = false / not used (though 0 is rarely sent)
6. The User-Agent header contains information about the client’s browser and operating system.
7. The type of data requested is in the Accept header.
8. The Accept-Encoding header tells the server which compression (encoding) algorithms the client (usually a browser) supports. This helps reduce the size of HTTP responses to improve load time and bandwidth efficiency.
9. The Accept-Language header contains the client’s language information. The web server uses this information to display the prepared content in the client’s language.
10. The Connection header shows how the HTTP connection is made.  
    If there is data such as “close”, it means that the TCP connection will be closed after receiving the HTTP response.  
    If you see “keep-alive”, this means that the connection will be maintained.
11. An empty line is inserted between the HTTP request header and the HTTP request message body to create a partition.
12. Any other data to be sent to the web application is in the Request Message Body. If the HTTP POST method is used, then the POST parameters can be found here.

# HTTP Responses

When the web server receives an HTTP request, it performs the necessary checks and processes and then sends the requested resource to the client.

![](https://miro.medium.com/v2/resize:fit:872/0*HBzNbXQIy7BYsGrD.png)

**Status Line**

The Status Line contains information about the HTTP version and the HTTP Response Status Code. The HTTP Response Status Code is used to describe the status of the request. There are many HTTP response status codes, but they can be summarized as follows:

● **100–199**: Informational responses

● **200–299**: Successful responses

● **300–399**: Redirection messages

● **400–499**: Client error responses

● **500–599**: Server error responses

**Response Headers**

Here are some HTTP Response Headers that you may encounter frequently:

● **Date**: The exact time the server sent the HTTP Response to the client.

● **Connection**: This indicates how the connection is handled, just like the HTTP Request header.

● **Server**: It informs about the operating system of the server and the version of the web server.

● **Last-Modified**: The `Last-Modified` header in an HTTP **response** tells the client **when the resource was last changed** on the server.

● **Content-Type**: The type of data being sent.

● **Content-Length**: The size of the data sent.

**Response Body**

The HTTP response body contains the resource sent by the server and requested by the client.

![](https://miro.medium.com/v2/resize:fit:792/0*tWF3zvbPaDhd8EMb.png)

