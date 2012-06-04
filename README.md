About
-----

This is the source code that powers [xcolors.net](http://xcolors.net). Xcolors.net is a color theme
directory for terminals that support color configuration through
[X resources](http://en.wikipedia.org/wiki/X_resources). It provides a visual presentation of the themes
and will hopefully [grow over time](https://github.com/tlatsas/xcolors#Contribute) with help from
the community :).


How to use these themes
-----------------------

Download and use the `#include` directive in your `.Xdefaults` or `.Xresources` files. Then load/reload
using the `xrdb` utility. Some information is provided [here](http://kb.mit.edu/confluence/pages/viewpage.action?pageId=3907291).

E.g.:

    #include "<path/to/theme>/rezza"


Contribute
----------

1.  Fork the [xcolors repository](https://github.com/tlatsas/xcolors).

2.  Add your theme file(s) in the `themes` folder found in the project's root directory.

3.  Commit the newly added files.

4.  Make a pull request.

5.  Changes will show at the [xcolors site](http://xcolors.net) as soon as I push
    the chages back at the heroku deployment.


Supported formats
-----------------

Both files using rgb `*color0: rgb:19/19/19` and hash `*color0: #2e3436` notation are supported.


Supported keyworks
------------------

Keywords: `*color` (from 0 to 15), `*background`, and `*foreground` are supported.
Everything else is ignored.


How this works
--------------

Xcolors.net is powered by [Flask](http://flask.pocoo.org/), the Python micro-framework and is
hosted at [Heroku](http://www.heroku.com). Only the master branch of this repository is deployed at heroku,
so this branch should reflect the website contents/state.

With each push to heroku and before the Flask framework fires-up, a bit of python magic happens.
The files (themes) that reside in the `themes` folder of the root directory are parsed. Then, for each
theme file, a corresponding html file is generated using the [Jinja2](http://jinja.pocoo.org/) engine in
the `templates/xcolors` folder. These files are imported later by the `templates/index.html` template,
when the main page is requested.