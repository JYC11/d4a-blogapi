# Django For Apis Chapter 5 ~ 9: Blog API

## Chapter 5 - Blog API set up
Nothing new compared to the last chapters. Just setting up serializers, views, urls and such. A fast review.

## Chapter 6 - Permissions/Authorization
New(not really) concept. This is something I learned while studying node.js and it is implemented just so simply in Django it's kinda nuts.

You can set a project level permissions in the settings.py file when using django-rest-framework and then customise permissions by creating a custom permissions.py file, inheriting the base permissions class and overriding necessary methods. Adding permissions to views is as simple as importing the class and adding it to the view.

Permissions -> gating content behind certain arbitrary conditions(user role, login, etc).

## Chapter 7 - Authentication
Authentication is, from what I understand, a way for the client side to "remember" state as it communicates with a server. This state is usually login status as many things in a website can be locked behind login.
The book describes 3 main ways this happens and it settles on Tokens.

There are many ways to authenticate:
### Basic
1. Client sends request
2. Server sends anauthorized response and on how to authorize
3. Client sends credentials 
4. Sever decodes the credentials and responds

Pros - simple

Cons - has to authorize on every request, credentials can be intercepted

### Sessions
1. User inputs login credentials
2. Server verifies credentials and generates session object stored in the database
3. Server sends session ID (not the object itself) and all future requests contain the session ID
4. Future requests contain session ID which is used to verify the user 
5. Once user logs out, the session ID is destroyed by both client and server
6. New logins create new session ID to be used

Pros - more secure, more efficient

Cons - only works where login is performed, will not work across multiple domains, session object must be kept up to date, cookie is sent out for every single request(inefficient) when none may be needed
### Tokens
Stateless way to authenticate.
1. Client sends initial user credentials to server
2. A unique token is generated and stored by client as either cookie or local storage
3. This token is then passed in the header of each incoming HTTP request
4. Server only keeps record of whether the token is valid or not and authenticates user based on that

Pro - token is stored on frontend so backend doesn't need to maintain up-to-date session objects, tokens can be shared across multiple front-ends

Cons - token can become very large, managing its size can become a performance issue

Authentication is implemented with two packages in Django:
* django-allauth
* django-rest-auth

I'll look into the details of the packages at a later date but the fact that I could just install some packages and write at max 1~2 lines of code to implement this is really mindblowing. I would have had to write a lot of lines with node.js to do the same thing. I guess there is passport.js in node but I haven't used it yet and have only written code normally to achieve this sorta thing.

The book literally just says to add a couple of lines in the settings.py file and adds an extra two routes. Idk how to go into more detail on those.

## Chapter 8 - Viewsets and Routers
Viewsets are absractions for a (as the name suggests) a set(bundle) of views. A router can auto generate routes according to the views/models. 

So this is another QOL thing that Django has that probably allows devs to manage routes and views as the application grows large. It prevents repeating code which can happen because views are kinda written the same way over and over again.

To use viewsets, you import viewsets and SimpleRouter from rest_framework and re-write the views and router code(currently implemented in my code, the repetitive standard way is commented out). Then

I think I'm just barely scratching the surface of the Django stuff so I can't comment any more on this besides what I already said before(WOW this is so simple and easy)

## Chapter 9 - Schemas and Documentation
So there is apparently a way to quickly and easily make documentation for your APIs and someone already automated it. Kinda expected since writing docs can be tedious. The example in the book is outdated so I had to look for alternatives. I couldn't figure out the new one but on the next book(Django For Professionals) I'll figure it out.