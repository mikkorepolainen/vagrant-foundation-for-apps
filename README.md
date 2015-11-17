Vagrant file for using Foundation for Apps
====================

Vagrant file for developing [Foundation for Apps](http://foundation.zurb.com/apps.html) sites without polluting your host box.

Initializing the VM
-------------------

First, make sure you've installed [Vagrant](http://docs.vagrantup.com/v2/getting-started/index.html) and [VirtualBox](https://www.virtualbox.org/).

Next, download the [Vagrantfile](https://raw.githubusercontent.com/mikkorepolainen/vagrant-foundation-for-apps/master/Vagrantfile) and place it somewhere convenient, `cd` into the directory and start up the Vagrant vm...
```
cd <path>
vagrant up
```

Building the vm takes a while, so I recommend suspending the vm instead of destroying it if you plan to use it frequently:
```
vagrant suspend
```
or
```
vagrant destroy
```

Using Foundation for Apps
------------

SSH into the VM:
```
vagrant ssh
```

When asked to `Enter passphrase for key xxx` press enter.
The default password for a vagrant vm is `vagrant`.

To create a new project:
```
foundation-apps new <app name>
```

To build and run the site:
```
cd <app name>
npm start
```

The server runs in the address `http://localhost:8079/` by default.
To access the server from the host, modify the host name configuration from `localhost` to `0.0.0.0` in `<app name>\gulpfile.js`.
```javascript
// Starts a test server, which you can view at http://localhost:8079
gulp.task('server', ['build'], function() {
  gulp.src('./build')
    .pipe($.webserver({
      port: 8079,
      host: '0.0.0.0',
      fallback: 'index.html',
      livereload: true,
      open: true
    }))
  ;
});
```

The Vagrant vm is configured to forward port 8079 by default.
Navigate to `localhost:8079` on your host box to view the site through the server.

For more information, see:

- [http://foundation.zurb.com/apps.html](http://foundation.zurb.com/apps.html)
- [https://scotch.io/tutorials/getting-started-with-foundation-for-apps](https://scotch.io/tutorials/getting-started-with-foundation-for-apps)

Note on SSH-forwarding
---------------------
The Vagrantfile enables ssh-forwarding so that you can use your host ssh keys to authenticate with github. Make sure to add you keys to the agent with ```ssh-add``` before running ```vagrant ssh``` if your keys aren't automatically added to the agent.
