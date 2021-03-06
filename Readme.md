Heroku buildpack: Python + Gulp
===============================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for Python apps with Gulp tasks, powered by [pip](http://www.pip-installer.org/) and [Gulp](http://gulpjs.com/).


Usage
-----

Example usage:

    $ ls
    Procfile  requirements.txt  web.py gulpfile.js

    $ heroku create --buildpack git://github.com/nadirizr/heroku-buildpack-python-gulp.git

    $ git push heroku master
    ...
    -----> Python app detected
    -----> Installing runtime (python-2.7.9)
    -----> Installing dependencies using pip
           Downloading/unpacking requests (from -r requirements.txt (line 1))
           Installing collected packages: requests
           Successfully installed requests
           Cleaning up...
    -----> Discovering process types
           Procfile declares types -> (none)

You can also add it to upcoming builds of an existing application:

    $ heroku config:add BUILDPACK_URL=git://github.com/nadirizr/heroku-buildpack-python-gulp.git

The buildpack will detect your app as Python if it has the file `requirements.txt` in the root.

It will use Pip to install your dependencies, vendoring a copy of the Python runtime into your slug.

If a gulpfile.js file is present, it will run the task named `production` (gulp production).

Specify a Runtime
-----------------

You can also provide arbitrary releases Python with a `runtime.txt` file.

    $ cat runtime.txt
    python-3.4.3

Runtime options include:

- python-2.7.9
- python-3.4.3
- pypy-2.4.0 (unsupported, experimental)
- pypy3-2.4.0 (unsupported, experimental)

Other [unsupported runtimes](https://github.com/heroku/heroku-buildpack-python/tree/master/builds/runtimes) are available as well.
