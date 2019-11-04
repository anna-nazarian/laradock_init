# laradock/ laravel initialization
Files to init laradock and laravel project

# instructions
Put ```Makefile``` and ```run-project.sh``` to your root project folder

Go to run-project.sh and change LARADOCK_DIR to unique name for laradock dir for your project. 

You can also specify laravel version:

```docker run --rm -v $(pwd)/$dir:/app composer composer create-project laravel/laravel ."5.8.*"```

and add containers you will need for your project in DOCKER_CONTAINERS=... .

Run ```make``` or ```make start``` in console

After installing laradock it will ask you to “change configs in file laradock_dir/.env and restart command”. Change this next params:

code path to project folder: 
```APP_CODE_PATH_HOST=../project```

data path to some unique value (so your project will have its own docker data path): 
```DATA_PATH_HOST=~/.currentprojectname-laradock/data```

compose project name = your laradock folder: 
```COMPOSE_PROJECT_NAME=currentprojectname-laradock```

Run “make” again, it will install laravel. 
If it ask again for changing configs - copy project/.env.example to project/.env and run “make” again

Don't forget to add laradock folder to .gitignore.

You can also create settings files ```project.env-example``` and ```laradock.env-example```, so other people could use your project settings

If there will be problem with MySQL, check MySQL connection settings in project/.env (see example for mariadb in "project.env - example")

Other make-commands you will need:
* stop - stopping and removing project containers;
* exec - passing to container with project files. There you can install extra composer packages or firing some artisan commands. 
