# Facebook Echo Bot
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/3afc05a50a5d4e1ca06fe46a288146c4)](https://www.codacy.com/app/jagreetdg/facebook-echo-bot?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=jagreetdg/facebook-echo-bot&amp;utm_campaign=Badge_Grade)

## What is this project about?

This project showcases an echo bot for Facebook, built on the [Vert.x toolkit](http://vertx.io), and primarily deployed on the [Heroku platform](https://heroku.com).

## Contents
* [Setting up the project](#setup)
* [Environment properties](#env)
* [Accessing the app](#ass)
* [Setting up your Facebook app](#set)
* [Making contributions](#contr)
* [References](#ref)


This project shows how to deploy a facebook echo bot Vert.x application to Heroku. The same application can be deployed using a one-click badge, the maven plugin, or the git interface.

If you use a fat-jar then deploying on Heroku is as simple as a click. The only requirement is to create a Heroku specific [Procfile](../Procfile) with a `Dyno` of type `web`.


## <a id="setup"></a>Setting up the project
* [Deploying on Heroku](#setup_heroku)
* [Deploying on a local environment](#setup_local)


#### For Linux

1. First you need to install [Git](https://git-scm.com/downloads) (if it is not installed). This command will install Git into the system.

```bash
$ sudo apt-get install -y git
```
2. Then you need to install [Maven](https://maven.apache.org/download.cgi) with the following command.
```bash
$ sudo apt-get install -y maven
```

3. After all this, you need to clone this repository which you can do it with the given code or download[.zip](https://github.com/jboss-outreach/facebook-echo-bot/archive/master.zip) file:

```bash
$ git clone https://github.com/jboss-outreach/facebook-echo-bot
```

#### For Windows

 1. First you need to download and install [Git](https://git-scm.com/downloads) (if it is not installed).
 2. Download it from here(https://git-scm.com/download/win)
 3. Run the installer
 4. Download and install maven from here(https://maven.apache.org/download.cgi)
 5. After all this, you need to clone this repository which you can do it with the given code or download[.zip](https://github.com/jboss-outreach/facebook-echo-bot/archive/master.zip) file:

### <a id="setup_heroku"></a>Deploying on Heroku

[Heroku](https://www.heroku.com/) is a cloud platform that allows developers to build, run and operate applications entirely in the cloud. A limited, free tier is available for trying out this app.


There are 3 approaches to deploying the app:
 * Using the [Heroku Maven plugin](https://github.com/heroku/heroku-maven-plugin)
 * Using the [Git interface](https://devcenter.heroku.com/articles/git)
 * Using a one-click badge

#### Deploying with the Heroku Maven Plugin

1. Install the [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
2. Create a Heroku remote:
```bash
$ heroku create
```
3. Deploy the app using the [Heroku Maven Plugin](https://devcenter.heroku.com/articles/deploying-java-applications-with-the-heroku-maven-plugin):
```bash
$ mvn package heroku:deploy
```

#### Deploying with the Git Interface

1. Install the [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
2. Install [Git](https://git-scm.com)
3. Create a Heroku remote:
```sh-session
$ heroku create
```
4. Deploy the app by pushing the code to the Heroku remote:
```sh-session
$ git push heroku master
```

*Note:* If you use a [fat-jar](https://devcenter.heroku.com/articles/deploying-executable-jar-files) then deploying on heroku is as simple as one click. The only requirement is to create the Heroku specific [Procfile](../Procfile) with a `Dyno` of type web.

### <a id="setup_local"></a>Deploying on a local environment [localhost](https://en.wikipedia.org/wiki/Localhost)
Build the app with [Maven](https://maven.apache.org/); set up the HTTPS tunnel and deploy the app with [Ngrok](https://ngrok.com/):
```sh-session
$ mvn clean package
$ java -jar target/facebook-echo-bot-3.5.0-jar-with-dependencies.jar
$ ./ngrok http 8080
```

* If file is being **Denied** to open then use ```chmod +x filename``` in Linux or MacOS. For Windows, run Command Prompt as administrator.


## <a id="env"></a>Environment properties
Properties must be configured before the app can be accessed:
```
 facebook.verify.token    # You have to decide. This value has to be the same for both the app and Facebook.
 facebook.access.token    # This is used to send pi hits to Facebook on your behalf.
 http.port                # This is 8080 by default.
 http.address             # This is 0.0.0.0 by default.
```
One method of setting the properties is by the command: `-D<prop-name>=<prop-val>`.
Example:
```
$ java -Dhttp.port=$PORT -jar target/facebook-echo-bot-3.5.0-jar-with-dependencies.jar
```
When creating a project of your own, you'll need to borrow from the [`Procfile`](https://github.com/jboss-outreach/facebook-echo-bot/blob/master/Procfile) in the root directory of this project, and the `MAVEN_CUSTOM_OPTS` will only be necessary if your app is not the primary module of your Maven project.

## <a id="ass"></a>Accessing the app
The app's web hook is at `<host>:<port>/webhook`.
For Heroku-deployed apps, it is at `<app-name>.herokuapp.com/webhook`.

## <a id="set"></a>Setting up your Facebook app
Refer the following link to set up your Facebook app:
`https://developers.facebook.com/docs/messenger-platform/getting-started/app-setup`


# <a id="contr"></a>Making contributions
* [Fork](#fork)
* [Configuring Git](#git_conf)
* [Coding](#code)
* [Sending a pull request](#pull)
* [Amending your pull request](#pull_amend)
* [Cleaning up](#clean_up)

### Contents
The first thing to do is create an account on GitHub (if you do not have one yet). You should then read the rules of participation in the development for the project you selected. These rules are usually found in a file called CONTRIBUTING.md in the root of the repository. This repository does not have it yet.

Usually, there are several ways to participate in the development of a project. The main ones are to send a message about some error or desired improvement (Submitting Issue), or directly creating a Pull Request with your correction or improvement (Code Contributing). You can also participate in the improvement of documentation, answers to questions that have arisen from other developers, and much more.


### <a id="fork"></a>Forking the project
Make your way to the project page and click on the button that says *Fork*. This command will create your own copy of the project's repository in your github[https://github.com] account.

![](https://image.ibb.co/fyStZm/fork.png)

After forking thr git, the next thing you need to do is to clone (ie. copy or download) the repository onto your local machine, this can be done by:
```bash
$ cd ~/work/git #folder in which there will be a code
$ git clone https://github.com/[YOUR-USERNAME]/wiki-explorer.git #clone repository
```


### <a id="git_conf"></a>Configuring Git
Next, you need to make a small adjustment to your Git, so that when you send commits, your name will be displayed.
For this it is enough to execute these commands:
```bash
$ git config --global user.name "Your name"
$ git config --global user.email you@example.com
```

##### Setting git remotes
Next, you will need to link remote repositories to git, remote repositories are nothing but versions of your project that are hosted on the internet or network somewhere (in this case, the jboss-outreach main repository). You can add this by setting the upstream (preferably) in your git local repository. This can be done by:
```
$ git remote add upstream $ https://github.com/jboss-outreach/facebook-echo-bot
```
To check if the previous step was successful run:
```
$ git remote -v
```
If the process was successful, you would see the following output:
```
origin https://github.com/[YOUR-USERNAME]/facebook-echo-bot (fetch)

origin https://github.com/[YOUR-USERNAME]/facebook-echo-bot (push)

upstream https://github.com/jboss-outreach/facebook-echo-bot (fetch)

upstream https://github.com/jboss-outreach/facebook-echo-bot (push)
```

Remotes are necessary for fetching and pulling files from the main repository
.
### <a id="code"></a>Coding

Starting to work on your fix, you must first create the corresponding Git branch, based on the current code from the base repository.

Choose a clear and concise name for the branch, which would reflect the essence of the changes.
It is considered a good practice to include the number of the GitHub issue in the branch name.
```bash
$ git fetch upstream    # fetches data from the main repository (or upstream)
$ git checkout -b <your-name-branch>  #Creates a new branch
```

Now you can easily start working on the code. While working, keep the following rules in mind:
* Follow the coding standards (usually PSR standards);
* Write unit tests to prove that the bug is fixed, or that the new function actually works;
* Try not to violate backward compatibility without extreme necessity;
* Use simple and logical whole commits;
* Write clear, complete messages when you commit changes.
* Specify Relevent Details in your pull request(like files changed or reasons for such ammends)
* Use documentation comments wherever necessary


### <a id="pull"></a>Sending a pull request

While you were working on the code, other changes could be made to the main branch of the project. Therefore, before submitting your changes, you need to fetch the new changes and rebase your branch.
This is done like this:
```bash
$ git checkout <your-name-branch>
$ git fetch upstream
$ git rebase upstream/master
```
The next step is to add and then commit your change, this can be done by:

* Adding changes:
```bash
git status        # This will list all the edited files
git add filename.extension #To add individual files OR
git add .            # To add all the files at once
```
* Commiting the changes:
```bash
git commit -m"Enter your commit message here"
```
The commit message should be very brief but at the same time informative. Use your words wisely!

* Now you can send your changes.
```bash
$ git push origin <your-name-branch>
```

  After that, we go to your project clone repository, in which you participate and click the button "New Pull Request".
And we see the following form:

![New Pull Request](https://habrastorage.org/files/191/d14/269/191d14269eae48e29d2179e32cf4fb2c.png)
* On the left, you must select the branch in which you want to push the changes (this is usually the master, well, in general, this is the branch you rebase to) and on the right is a branch with your changes.

* Next, you will see a message from GitHub whether it is possible to automatically merge the changes or not. In most cases, you will get a success message which says "Able to merge."

* If there are conflicts, you will most likely need to review your changes.
* Then click on - Create Pull Request.
When filling out the name and description of your Pull Request it is considered good practice to specify the Issue number for which your Pull Request is created.
After creating the Pull Request, it will run the tests, perhaps some tools for metrics and so on. The results of his work you will see in your Pull Request as shown below:

* Remmber to describe your changes/feature in detail in the pull request message.
![results](https://habrastorage.org/files/46c/e42/a41/46ce42a41ef24141a5c74d76cdb71f13.png)

In case the tests are not passed or the build is not compiled, you will see a red error message and by clicking the Details link you will see what is wrong. In most cases, you will need to fix your Pull Request so that all checks are successful.

###### And also look this [article](https://help.github.com/articles/creating-a-pull-request/) and this [video](https://www.youtube.com/watch?v=YTbRzhQju4c)

## Contributing to the project
1. Fork and clone this repository.
2. Make changes to your local copy of this repository.
3. Commit and push your local changes to your fork on GitHub.
4. Review the changes on your fork.
5. Create a pull request to merge your changes into this repository. Write a very conscise but informative pull request message. Remember to use your words wisely!

## Video Demonstration
A Video Demonstration is uploaded to [`Youtube`](https://www.youtube.com/watch?v=hklLfa8096I) which can help to setup Facebook Echo Bot on any cloud.


### <a id="pull_amend"></a>Amending your pull request

If everything is good with your pull request, then soon it will be merged by a project collaborator.
However, it is more likely that a reviewer asks for some changes to be made to your pull request.
To do so, simply return to step 6 and after making the changes and commit we perform the following commands:
```bash
$ git checkout <your-name-branch>
$ git fetch upstream
$ git rebase upstream/master
$ git push origin <your-name-branch>
```
### <a id="clean_up"></a>Cleaning up

After your pull request has been accepted or rejected, you need to delete the branch with your changes.
This is simply done with:
```bash
$ git checkout master
$ git branch -D <your-name-branch>
$ git push origin --delete <your-name-branch>
```
Instead of the last command, you can also run
```bash
$ git push origin :<your-name-branch>
```

### How to open command prompt

 1. Use the shortcut `Windows+R`and type `cmd`
 2. Now cmd will open automatically.


### How to open terminal in Linux

1. Open `Dashboard Search` and type `terminal`
2. Open `Terminal`

### How to open Terminal in MacOS

1. Use the shortcut `Cmd+Space` or open `launcher`and type `Terminal`
2. Open `Terminal`

### <a id="ref"></a> References
  * [How to use GitHub](https://guides.github.com/activities/hello-world/)
  * [Git basics](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics)
  * [Git commands handbook](https://git-scm.com/docs)
  * [Try git and have fun!](www.try.github.io)
  * [Command Prompt handbook](http://www.makeuseof.com/tag/a-beginners-guide-to-the-windows-command-line/)
  * [Linux Terminal handbook](http://linuxcommand.org/)
  * [MacOS Terminal handbook](https://developer.apple.com/library/content/documentation/OpenSource/Conceptual/ShellScripting/CommandLInePrimer/CommandLine.html)
  * [Heroku Handbook](https://devcenter.heroku.com/)
  * [Maven Handbook](http://www.jcabi.com/jcabi-heroku-maven-plugin/example-start.html)
  * [Chat with us !](https://gitter.im/jboss-outreach)
