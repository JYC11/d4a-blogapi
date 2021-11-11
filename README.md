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
### Cookies
-- to fill in

### Sessions
-- to fill in

### Tokens
-- to fill in

Authentication is implemented with two packages in Django:
* django-allauth
* django-rest-auth

I'll look into the details of the packages at a later date but the fact that I could just install some packages and write at max 1~2 lines of code to implement this is really mindblowing. I would have had to write a lot of lines with node.js to do the same thing. I guess there is passport.js in node but I haven't used it yet and have only written code normally to achieve this sorta thing.

## Chapter 8 - Viewsets and Routers
Viewsets are absractions for a (as the name suggests) a set(bundle) of views. A router can auto generate routes according to the views/models. 
-- to fill in

## Chapter 9 - Schemas and Documentation
-- to fill in

Was on a roll today and finished the whole book. Will go over it more thoroughly again to summarise what I learnt