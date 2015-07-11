moinmoin-bootswatch
===================

bootswatch is a simple theme for [MoinMoin][https://moinmo.in/] 1.9 based on [memodump][https://github.com/dossist/moinmoin-memodump].

Comes with responsive navbar and sidebar.

You can create your own sidebar by creating a page called `SideBar`.

Tested with MoinMoin 1.9.7 on Python 2.7.5.

For details, please refer to [the project wiki][Wiki Home].


Screenshot
----------

![Main](https://github.com/fzipi/moinmoin-bootswatch/wiki/Cerulean.png)

[More][Wiki Screenshots]


Install
-------

1. Get files by cloning the repository or download a zip and unpack it.  
   To clone:

    ```console
    $ git clone https://github.com/fzipi/moinmoin-bootswatch.git
    ```

2. Copy `bootswatch.py` into plugin directory `data/plugin/theme/`.
   Location of the directory varies according to how you installed MoinMoin.

3. Copy directory `memodump` into static files directory `MoinMoin/web/static/htdocs/`.
   Again location of that directory will vary. It could be:
    * `/usr/share/moin/htdocs` if you installed MoinMoin from Ubuntu package
    * `/usr/local/lib/python2.7/dist-packages/MoinMoin/web/static/htdocs` if you installed MoinMoin from zip
    * and so on

4. Done!
   If you run MoinMoin on a server, you might have to terminate running MoinMoin processes to reflect changes.  
   e.g. on Ubuntu:

    ```console
    $ pkill moin
    ```


How to use
----------

There are two ways to apply the theme.

### As your personal theme, keeping default theme unchanged ###

* Log into your wiki and go to user preferences page.
  (**Settings** near the upper left corner, then **Preferences**)
* Choose **memodump** from Preferred theme dropdown box.
* Hit *save* button at the bottom of the page.

### As the default theme ###

Edit `wikiconfig.py` to change `theme_default`.

```python
    theme_default = 'bootswatch'
```

Please note that indentations are important in python codes, and here you must
indent the line by exactly 4 spaces.

### Theme variants ###

Edit `wikiconfig.py` and select some of the bootswatch posible variantsi. For example, to select `cerulean`:

```python
    bootswatch_variant = 'cerulean'
```

Customization
-------------
For details, please refer to [the project wiki][Wiki Home].


### SideBar ###

Create a page named `SideBar` to create your own site-wide sidebar.
In sidebar, list items receive special menu-like styles.  


### Site logo ###

If you go with the default wikiconfig, the default logo picture will run off the navbar height.
This theme is not optimized for the default logo picture (although it won't break page design).
By disabling the logo, MoinMoin will use your site name as a text logo with a link to the FrontPage.
To do it, just comment out `logo_string` in `wikiconfig.py`:

```python
    logo_string = ...
```
↓
```python
#   logo_string = ...
```


### Location area ###

On top of page contents, we have an area which shows where in the wiki you are now, and when it was updated last time.  
However, showing the info on every page feels a bit redundant.
You can define a list of pages which comes without the info.  
Define a list `memodump_hidelocation` in `wikiconfig.py`. The list has page names as its entries.  
Example:

        bootswatch_hidelocation = [page_front_page, u'SideBar', ]

By default, `page_front_page` is the only page in the list.


### Menu items ###

Basic knowledge of python language is required!

By defining `bootswatch_menuoverride` in `wikiconfig.py`, you can override menu entries.  
Example:

        bootswatch_menuoverride = [
            'raw',
            'print',
        ]

For details, please refer to [the project wiki][Wiki EditMenu].


Limitations
-----------

* Some words in the theme are not translated. (Can be translated via [WikiDictionary][Wiki Translation] pages, though)
* Sidebar area is reserved even if `SideBar` page does not exist nor is accessible.
* editbar and actionsMenu are replaced with the theme's own menu functionality, and settings
  on the replaced will not affect the new menu.
* Original actionsMenu were listing all additional actions automatically, but the menu of this theme
  won't do so automatically.


License and copyrights
----------------------

Copyright 2014 dossist.  
Copyright 2015 fzipi.  
This theme is licensed under [GNU GPL][].  
[Twitter Bootstrap][] is copyrighted by Twitter, Inc and licensed under [the MIT license][MIT].  
[MoinMoin][] is copyrighted by [The MoinMoin development team](https://moinmo.in/MoinCoreTeamGroup) and licensed under [GNU GPL][].  
Icons and some part of CSS were taken from the default modernized theme.  



[MoinMoin]: https://moinmo.in/
[Twitter Bootstrap]: http://getbootstrap.com/
[Bootswatch]: http://bootswatch.com/
[Wiki Home]: https://github.com/fzipi/moinmoin-bootswatch/wiki
[Wiki EditMenu]: https://github.com/fzipi/moinmoin-bootswatch/wiki/EditMenu
[Wiki Translation]: https://github.com/fzipi/moinmoin-bootswatch/wiki/Translation
[Wiki Screenshots]: https://github.com/fzipi/moinmoin-bootswatch/wiki/Screenshots
[GNU GPL]: http://www.gnu.org/licenses/gpl
[MIT]: https://github.com/twbs/bootstrap/blob/master/LICENSE
