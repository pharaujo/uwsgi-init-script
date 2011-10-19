uWSGI init script
=================

why
---

Wanted to host in the same machine python2.5 and python2.7 projects.


usage
-----

usage for uwsgi-2.5:
```
uwsgi-2.5 {start|stop|restart|reload|force-reload|status} [CONFIG]...
```


examples
--------

  * Starting all 2.5 configs:
    /etc/init.d/uwsgi-2.5 start
  * Reload example.yml:
    /etc/init.d/uwsgi-2.7 reload example.yml


deploy
------

Example for a deploy using uwsgi compiled with python 2.5 and 2.7 (assuming you
already have them installed on your system):

```bash
# install uwsgi-2.5 and uwsgi-2.7
easy_install-2.7 uwsgi
mv /usr/local/bin/uwsgi /usr/local/bin/uwsgi-2.7
easy_install-2.5 uwsgi
mv /usr/bin/uwsgi /usr/local/bin/uwsgi-2.5
# deploy init scripts
mv uwsgi.init /etc/init.d/uwsgi
ln -s /etc/init.d/uwsgi /etc/init.d/uwsgi-2.7
ln -s /etc/init.d/uwsgi /etc/init.d/uwsgi-2.5
# create config folder structure
mkdir -p /etc/uwsgi/uwsgi-2.{5,7}/sites-{available,enabled}
```

uWSGI config files will be read from the `sites-enabled` folder.


bash completion
---------------

Just `source uwsgi.bash_completion` or, better yet, copy it to
`/etc/bash_completion.d/` (make sure you have bash\_completion enabled).


