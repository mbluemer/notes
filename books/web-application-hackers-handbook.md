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

