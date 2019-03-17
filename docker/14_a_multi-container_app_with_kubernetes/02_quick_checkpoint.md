# Quick checkpoint

Because we are using the same application as the previous project, we are going to copy it:

```
$ cp -r 06_building_a_multicontainer_application 08_multicontainer_application_with_kubernetes 
$ cd 08_multicontainer_application_with_kubernetes
$ rm -rf .git
$ git init
```

And verify that it is still working:

```
$ docker-compose up
```

And visiting `http://localhost:3050`.

