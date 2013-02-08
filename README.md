Description
===========
Set up Nginx to proxy all requests except ``/static`` to the WSGI server
(gunicorn). Shoud be usable for other WSGI servers than gunicorn.

Does the following:
- Create a site in ``/etc/nginx/sites-available``
- Enable the site (symling from ``/etc/nginx/sites-enabled``)
- Restart nginx


Requirements
============
- The ``nginx`` recipe.

Attributes
==========

Required
---------
- ``node["django_nginx"]["statichome"]`` - Path to a directory containing a
  subdirectory named ``static/`` where the static files collected by
  ``collectstatic`` is located.

Optional
--------
- ``node["django_nginx"]["gunicorn_port"]`` - The gunicorn port.
  Defaults to ``8002``.
- ``node["django_nginx"]["sitename"]`` - The name of the site
  config placed in ``/etc/nginx/sites-available/``.
  Defaults to ``django``.
- ``node["django_nginx"]["listenaddr"]`` - The listen-address
  for the nginx virtual host. Usually just a port number.
  Defaults to ``80``.



Usage
=====

Add ``"run_list": [ "recipe[chef_django_nginx]" ]``. You need to, at least,
configure the ``statichome``-attribute.
