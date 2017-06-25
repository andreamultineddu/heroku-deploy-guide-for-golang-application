# heroku-deploy-guide-for-golang-application #

Before following this guide, be sure to have installed Go (any version is ok), Git and the Heroku CLI.

Open the Git Bash inside the folder of your Golang project that contains the file with the *function* **main()** of your application

Login to **Heroku** with the command line `heroku login`

Create a new **Heroku app** with the comman `heroku create` and remeber the name **Heroku** is randomly giving to your app cause you need to use it later

Create a new **git repository** with the command `git init`

Add the remote to yout just created repository `heroku git:remote -a (Name of the Heroku app)`

Commit all the source code of the package with `git add .` and `git commit -am "first commit"`

Now you have to install **Godep** (a manager for dependencies of Golang applications) with the command  `go get github.com/tools/godep`.
If everything else is correctly set up run the command `godep save`. it will create the folder *Godeps* containing the file that describe all the dependencies of your application.

```
{
	"ImportPath": "github.com/kr/hk",
	"GoVersion": "go1.6",
	"Deps": [
		{
			"ImportPath": "code.google.com/p/go-netrc/netrc",
			"Rev": "28676070ab99"
		},
		{
			"ImportPath": "github.com/kr/binarydist",
			"Rev": "3380ade90f8b0dfa3e363fd7d7e941fa857d0d13"
		}
	]
}
```

Commit all the dependecies file of the package with `git add .` and `git commit -am "Godeps"`

After this you just have to push the changes to the heroku with `git push heroku master`

Now if you have not received a message error while loading all the changes your Golang application is now running on **Heroku**.
To check it on your browser just run the command `heroku open`

You can also inspect:
  1. the requests via the log stream with `heroku logs --tail`
  2. the dyno(s) running your application with `heroku ps`
