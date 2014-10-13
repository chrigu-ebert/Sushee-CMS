Sushee CMS
==========

A JSON based content management system. **Work in progress!**

> This whole thing is just a first prototype. Don't use it, things might change a lot and there will be a heavy
> cleanup iteration soon! There will be a roadmap soon.

![alt text](https://raw.githubusercontent.com/chrigu-ebert/Sushee-CMS/master/web/admin/facebook.png "Logo")

About
-----
Sushee CMS has a few key features and principles to make my life easier.

It is **simple** to setup and maintain. It has almost no dependencies. It doesn't need all those time-consuming updates and you can backup your data easily by just copying the `data` folder. Check the [system requirements](#system-requirements) section for details.

You can **customize** it easily to fit your client needs. You can add & remove data attributes on the fly. You can extend existing modules or build your own.

It is really **fast** and performing effectively. All the usual vendor scripts bloat your application and make it slow but often you just need a fraction of all the things that are loaded. Sushee directly writes data to the filesystem. No database necessary. Everything is loaded asynchronously with Javascript.

It has a small footprint and is open source :)


### Tools
- [Gumby Framework](http://gumbyframework.com/) - CSS framework
- [JQuery](http://jquery.com/) - Javascript library


Setup
-----

### System requirements
- PHP 5.2.17 or higher
- Write permissions in `/data/modules` folder

### Getting started
0. Clone/copy repository
0. Create a user
0. Create a module
0. Access admin panel `/web/admin`


Configuration
-------------

### User management

Managing users is quite easy. Edit the file `data/config/users.json` and provide a user-object for each account
that contains the following fields:

    {
        "name": "chrigu",
        "role": "user",
        "display_name": "Chrigu",
        "salt": "YOUR SALT",
        "hash": "YOUR HASH"
    }


Key | Value
--- | ---
name | The user id which must be unique for each user
role | The user role which is either `user` or `admin`. The admin role has some more options in the admin panel.
display_name | The name that is displayed in the admin panel
salt | The salt is random data used to decrypt your password hash. Create a different, long-enough (64 characters) salt for each user [here](http://www.sethcardoza.com/tools/random-password-generator/).
hash | The hash is a derivation of data used to authenticate. It represents your password in a way, nobody can read it. To create the hash you can use [this service](http://www.xorbin.com/tools/sha256-hash-calculator). Enter your hash + password and save the generated hash value.


### Module management

#### Basic Module

    {
        "id": "contact",
        "name": "Contact",
        "single": true,
        "fields": [
            {
                "name": "Name",
                "id": "name",
                "placeholder": "",
                "type": "text"
            },
            {
                "name": "Message",
                "id": "message",
                "placeholder": "",
                "type": "textarea"
            }
        ]
    }


#### Custom icons

You can change the icon displayed in the sidemenu of each module. Just specify an `icon` property for the module. You can use the famous [Entypo Icons](http://gumbyframework.com/docs/ui-kit/#!/icons).

    {
        "icon": "icon-cloud",
        ...
    }

### Field types

#### Text

    {
        "name": "Name",
        "id": "name",
        "placeholder": "",
        "type": "text"
    }

#### E-Mail

    {
        "name": "E-Mail",
        "id": "email",
        "placeholder": "",
        "type": "email"
    }

#### Textarea

    {
        "name": "Message",
        "id": "message",
        "placeholder": "",
        "type": "textarea"
    }

#### Select

    {
        "name": "Rating",
        "id": "rating",
        "placeholder": "- Choose -",
        "type": "select",
        "values": [
            {
                "label": "Ok",
                "value": 1
            },
            {
                "label": "Good",
                "value": 2
            },
            {
                "label": "Perfect",
                "value": 3
            }
        ]
    }


#### Image

    {
        "name": "Image",
        "id": "image",
        "placeholder": "",
        "type": "image"
    }

#### Youtube video

    {
        "name": "Video",
        "id": "video",
        "placeholder": "http://www.youtube.com/watch?v=xxx",
        "type": "youtube"
    }

Roadmap
-------
TBD
