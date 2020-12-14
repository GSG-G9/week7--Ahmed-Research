# Ahmed-Research

# How does HTTPS work? What are TLS/SSL certificates?

- #### definition of HTTPS :

  is a request response protocol to communicate asynchronously between client and server.

- #### definition of HTTPS :

  is hypertext transfer protocol secure and is the encrypted version of HTTP,use for secure connection via internet and encrypt by SSl\TLS.

- #### secure Sockets Layer(SSL) :

  prevent any attack read data when sending data between sys by using encryption algorithms to scramble data in transit (protect internet connection during transfer data).

- #### Transport Layer Security(TLS) :

  update and more secure of SSl.

  #### How HTTPS Work ?

  - HTTPS requires a TLS certificate to be installed on your server.
  - TSl storage key (public & privet) created randomly generated in your server The public key is verified with the client and the private key used in the decryption process

- # Why is this important to implement in your projects?
  - Protect Your Users Privacy.
  - Protect your revenue : the HTTPS client over a website using HTTP. This could become a stronger signal in the future(as google say in 2014 ).
  - in 2017 chrome also gave users a “Not Secure” warning for any HTTP websites'
  - in HTTPS users will faster browse speeds.

#### Demo how to generate certificates and use them in a node project

- #### connection-sequence-diagram
  ![connection-sequence-diagram](https://user-images.githubusercontent.com/60399953/102102582-aa38c200-3e34-11eb-95fa-5b8ba1a4ff6e.png)

---

# Stateless vs stateful authentication

- Stateful D.F: You can revoke the authentication session on the IdP anytime.

- Stateless D.F: The session expiration time is set when the authentication token is released. You cannot revoke the session on the IdP.

- #### What is session based authentication (stateful) vs token based authentication (stateless)?

- A stateless app is one that does not save client data generated in one session for use in the next session – instead session data is stored on the client and passed to the server as needed. Each session is carried out as if it was the first time and responses are not dependent upon data from a previous session. In contrast, a stateful application saves data about each client session and uses that data the next time the client makes a request.

- #### Draw flow diagrams to show the steps involved in each process
- #### Stateless session

![Stateless session](https://user-images.githubusercontent.com/60399953/102102853-f08e2100-3e34-11eb-8d8c-f14510babea1.png)

- #### StateFul session

  ![Stateful session ](https://user-images.githubusercontent.com/60399953/102102992-17e4ee00-3e35-11eb-916e-090aec849b9e.png)

  - #### What are the advantages and disadvantages of each?

  - #### Stateful session
  - #### Advantages
    - Revoke the session anytime
    - Easy to implement and manage for one-session-sever scenario
    - Session data can be changed later (assume that for a one-session-sever, no inconsistent problem)

- #### Disadvantages
  - Increasing server overhead: As the number of logged-in users increases, the more server resources are occupied.
  - Difficult for mobile device e applications to use your credentials

#### Stateless session

- #### Advantages

  - Lower server overhead
  - Easy to scale
  - Good to integrate with 3rd party application

- #### Disadvantages
  - Cannot revoke the session anytime
  - Relatively complex to implement for one-session-server scenario
  - Session data cannot be changed until its expiration time

---

#### Session-management in Express

- #### What are sessions?

  a Session is a storage that consists of information on server-side. JavaScript Session will be in active state till the user interacts with a website or web application.

- #### What are the different ways of managing sessions in express?

  by using one of these packages :

  - express-session.
  - client-sessions.
  - cookie session.

- #### Create a minimal example of how to set up a session (FYI: pseudo code is fine)
  - install express-session.
    //npm install express-session
  - require express-session package.
    const session = require('express-session')
    const app = express()
    app.set('trust proxy', 1) // trust first proxy
    app.use(session({
    secret: 'keyboard cat',
    resave: false,
    saveUninitialized: true,
    cookie: { secure: true }
    }))

---

# Attacks

- #### What are the following types of attack?

  - Man In The Middle (MITM):
    A man-in-the-middle (MitM) attack is when an attacker intercepts communications between two parties either to secretly eavesdrop or modify traffic traveling between the two.

  - Cross Site Scripting (XSS):
    Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites. XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser side script, to a different end user
  - Cross Site Request Forgery (CSRF)
    Cross-Site Request Forgery (CSRF) is an attack that forces authenticated users to submit a request to a Web application against which they are currently authenticated.

- #### How can you defend against each of them?

  #### how to avoid MIMT:

  - Be wary of links that you click to avoid phishing attempts that lead to MiTM attacks.
  - Keep your operating system and your browser always up to date. This way, the attackers will not be able to use exploits to install malware on your computer.

  - Use a secure WiFi protocol on your router (WPA2, WPA3 if available), use a secure WiFi key, change default login credentials for your router and update your router firmware. This way, attackers won’t be able to compromise your local area network.

  - Limit your sensitive activity on public networks or use a VPN connection on public networks. A VPN will add an extra layer of security.

  - Make sure that the DNS servers (DNS caches) that you use are secure. Check the configuration on your router (DNS cache addresses are usually provided via DHCP). If in doubt, use Google public DNS caches: 8.8.8.8 and 8.8.4.4.

#### how to avoid Cross Site Scripting (XSS) :

- Enabling inline code
  As a first option, you could enable the execution of inline scripts. You can do this by adding the 'unsafe-inline' source to the allowed source list
- Using hash codes
  Alternatively, CSP allows you to enable specific trusted code blocks by identifying them through their hash code.
- Using nonce
  If you have noticed, the error message provided by Chrome Dev Tools suggests another possible solution to enable script blocks.

#### how to avoid Cross Site Request Forgery (CSRF) :

- Using a secret cookie
  Remember that all cookies, even the secret ones, will be submitted with every request.
- Only accepting POST requests
  Applications can be developed to only accept POST requests for the execution of business logic
- Multi-Step Transactions
  Multi-Step transactions are not an adequate prevention of CSRF.
- URL Rewriting
  This might be seen as a useful CSRF prevention technique as the attacker cannot guess the victim’s session ID.
