# The Web Application Hackers Handbook: Finding and Exploiting Security Flaws
By Dafydd Stuttard and Marcus Pinto

## 2 | Core Defense Mechanisms

1. Handling User Access
  - *Authentication* is the most basic dependency for a user to access an application and a very common attack vector
  - *Session management* is only as secure as the tokens used for it
  - *Access Control* decides who can get where and do what, often laborious to test but an important attack vector
2. Handling User Input
  - There is a huge *variety of input* that you must watch out for when doing validation. Certain input may need to follow stricter requirements than others.
  - There are several techniques to mitigate risks with user input:
    - Although not very effective we can create an explicit blacklist
    - Slightly better is building a white list (often with regexp) to denote what is allowed.
    - *Sanitization* is a very common approach where we clean the input for malicious content
    - We can handle user data safely, such as using *parameterized queries* for SQL
    - Lastly an attack vector could just be due to semantics such as ensuring the queried account is associated with the current user
  - *Boundary validation* is a model where each functional unit of an application treats its input as potentially malicious
    - Thus validation occurs at each of these trust boundaries
  - Wherever you have multi-step validation the world is opened up to a whole other string of possible attacks
3. Handling Attackers
  - Effective *error handling* should be in place. Show appropriate information for the appropriate user.
  - Extension *audit logs* should be kept so that you can respond to attacks appropriately. Make sure to protect those logs though as they could be very useful in the wrong hands.
  - Effective *alerting* of attacks can guarantee that most attacks are handled quickly
  - It is also often very useful to have automated reaction in the application to any attacks that are detected.
4. Managing the Application
  - Often times in an application that's a management interface that gives certain users special privileges. This interface must be just as, if not more, secure than the actual application

## 3 | Web Application Technologies

*Cookies* are a vehicle for the server to send items of data to the client, which the client then stores and resubmits to the server on each subsequent request.

An *HTTP Proxy* is a server that mediates between the client and web server. It's important to note that when HTTPS is used the client must do the SSL handshake with the destination web server, not the proxy. The browser will make a CONNECT request to the proxy via HTTP and then the proxy will just act as a TCP-level relay to the destination server.

The *same-origin policy* is a mechanism in a browsers that specifies that a site can only read and modify content that came from that same site. This prevents malicious websites from messing with the users confidential information or from making requests to other sites on behalf of the user.

## 4 | Mapping the Application

The first step in attacking an application is enumerating it's content and functionality in order to understand its attack surface.

A basic manual walk through the application and look at the site map is great but there are more advanced tools that can be used such as:
- *web spidering* (web crawling) tools search through the whole site, automatically recursively following links
  - There are great existing spidering tools such as Burp Suite, WebScarab, Zed Attack Proxy, etc
  - Important to note that there are limitation such as programmatically generated navigation, complicated input validation, volatile URLs that cause infinite recursion, etc.
  - Also be careful of sites that have obvious functionality exposed that could be damaging such as an exposed CMS that could delete content from the site.
- *user directed spidering* is where a user clicks through an application manually but extra tools intercept requests and responses to create a map
  - Some of the key advantages: users can follow complex navigation, user can navigate complicated validation, user can log in and ensure authenticated session, user can avoid dangerous functionality.

There may also be sections of the application that are hidden to normal navigation techniques. These hidden areas may only be discoverable with a combination of various techniques and a certain degree of luck.
- tools can be used to run through possible hidden directories in an automated manner.
- it's also useful to try and infer other resources from existing resources based on naming schema, trends, etc.
- there may also be content that was linked to in the past that can be found through search engines or web archives.
- it's useful to look for hidden parameters.
