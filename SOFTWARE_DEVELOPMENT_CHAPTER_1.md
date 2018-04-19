SAM THOMPSON'S *SOFTWARE DEVELOPMENT 101*

## INTRODUCTION

Three things are important to successful software development:

1. A concrete goal.  The example goal we will use is "I want details for the NYC MTA schedule for the train stations closest to my house, so I can decide which station to use to go to work."
1. Next you need a desire to solve this problem yourself, specifically by writing software.
1. Next you need a computer.

We are ready to begin.

## CHAPTER 1: SETUP PROJECT FILES AND GET THE NODEJS "HELLO WORLD" RUNNING LOCALLY ON OUR MAC

### INTRO: DECIDE ON A FRAMEWORK

We could start by writing our own web server framework, but this is not efficient as we are not really interested in this part of the problem.  Rather, we choose a 'framework' to do virtually all of the heavy-lifting for us, so we may focus on the core problem.

We decide on the 'nodejs' web framework for a few reasons:

1. It is a web framework that is very popular in the zeitgeist right now.
1. It is fairly simple to set up on our local MacOS environments.
1. I know from experience that nodejs apps can easily 'get data from an API' such as the API provided by the MTA, and it can also print the interesting (to me) parts of the data in a straightforward and useful way.
1. I know also that nodejs apps are 'deployable' later to a public web server where we can access it using our phone / browser.

### STEP 1: PICK A "STACK" OR SEED PROJECT

For every project we need to google a bit to find the right "stack" of tools.  For this project, I followed this process:

Googled "nodejs seed project".  I am looking for a starter project for nodejs, the "seed" project for any framework is often the most bare-bones starter with 1 or 2 easy-to-use, canonical examples in it.

I picked the first google result and read through it to be sure it matched what I want: https://www.npmjs.com/package/node-seed.  It says it is a skeleton for a "typical" application, and has "good practices".  However the statistics in the right-hand side say it has only been downloaded (cloned) 4 times in the last 7 days.  This is not a lot (a popular project may have 100's to 1000's of daily installs, depending somewhat on how obscure it may be), so it turns out **I don't like this example** based on this low number of downloads.

Went back to google results and picked the second result: https://github.com/PauloLuan/node-express-seed.  This has **A LOT of words I don't immediately understand**, but it happens to mention another project - "this is based on the 'angular-fullstack' generator...'.  I think I maybe want that angular thing, so clicking on that now.

Looking at 'angular-fullstack' link: https://github.com/angular-fullstack/generator-angular-fullstack, it also seems to have **too much going on for what I want**.  I don't want a "mongodb" back-end - that is a database and I am not interested in that right now.  There are too many files listed on this page, I have a feeling we can start with something simpler.

Going back to google, searching more simply for "nodejs" so I can land on the homepage for nodejs, https://nodejs.org/en/.  There should be more bare-bones instructions there.

Clicking on the "docs" link at the top of nodejs.org, so I can see if there is a "hello world" documentation for nodejs.  I am hoping it tells me in 3-5 lines of code how to: 1) get nodejs onto my mac, 2) write a line of code to print "hello world" and 3) get this text to print in a browser.  I know this is what nodejs is meant for, so I reasonably expect it should do this in **3-5 lines of code**.

There is a "guides" link, so clicking on that.  Clicking "getting started guide" after that.  The "getting started guide" shows me the **3-5 lines of code** I had in mind, so I know I have found my stack.

### STEP 2: INSTALL THE TOOLS REQUIRED FOR THE STACK:

This "guides" page seems to think I have nodejs already installed on my Mac - I know that I do not, so going back to look for an 'installation' link on nodejs.org.

Going back to the nodejs.org homepage and clicking on 'download'.  I choose the latest 'LTS' version.  I know this means this version will have 'long term support', so I know my project is not going to break six months from now due to some lack of support -  it will break for other reasons, usually my own typos and errors, for sure ;).  The download is a MacOS package, so I am installing it.

(i didn't actually install nodejs this way as i have other methods for using it, but this is a perfectly valid option).

### STEP 3: GET THE STACK RUNNING "HELLO WORLD" LOCALLY

Now that I have nodejs package installed, going back to the 'guides / getting started': https://nodejs.org/en/docs/guides/getting-started-guide/.  I see there 3-5 lines of code for a "Hello World". Great, we found it.  It says to "create a file" and paste code into it.

Before I create this file, I think briefly about organizing my work.  From past experience, I am thinking carefully at this step about 'namespacing': I am just doing a scratch 'hello world' right now, but I know I might extend this later into a bona-fide app, and the name of my folder will probably correspond to the name of my project.  Since we are working on Sterkel's 'MTA' idea, but just the data 'server' (or web service) portion, I choose the simplest folder name for my project, while being as descriptive as possible: 'sterkel-mta-server'.

So, following the example, I create 'Documents/sterkel-mta-server/app.js' file and paste the sample code into it.  I prefer the command line for most of this, so I am opening the Terminal app (under Applications/Utilities) and typing:

``` bash
cd Documents
mkdir sterkel-mta-server
cd sterkel-mta-server
touch app.js
```

The last command creates an empty file, 'app.js'.  Now I need to paste the sample code into it.

### STEP 4: SET UP YOUR IDE TO MODIFY THE CODE

Take a minute to set up your editor tools.

Right now I have an app.js file which is blank.  I will need to open my preferred text editor (or "IDE") so I can paste the sample code into this file.  MacOS 'TextEdit' may not work, because it may add undesireable markup to the file.

I prefer a popular, paid IDE called WebStorm https://www.jetbrains.com/webstorm/, but another popular option is the free Sublime: https://www.sublimetext.com/.

I open my IDE, 'open' the app.js file, and paste the sample code from nodejs.org into it and save it.

### STEP 5: EXECUTE THE SAMPLE CODE

I still have my Terminal open, so now I follow the instructions to run the app, typing this into the terminal:

```bash
node app.js
```

I press enter and observe this response in the Terminal:

```
'Server running at http://127.0.0.1:3000/'.
```

Quick http background: I know that '127.0.0.1' is an internet address that points to my local Mac (whether I am connected to the internet or not).  I know also that the '3000' is a 'port' that nodejs is using to serve the results of our app.js.  If we didn't specify a port when visiting a website in our browser, the default is assumed to be '80' (or '443' for https).  But nodejs is politely using an alternate port so that it doesn't 'collide' with other services using port 80 or 443 on my Mac.

So I copy/paste this http://127.0.0.1:3000/ link into my browser to observe the result.  I am using the Chrome browser because I know it has Developer Tools built in that I will use later to inspect my app's behavior (Firefox has these tools also).  In the browser I see a white screen with the text "Hello World".  Success.

For fun I cancel the running app at the Terminal with Control+C, then try to reload the page in Chrome.  Chrome reports it is 'unable to connect'.

This demonstrates that I can successfully start and stop the nodejs Hello World app on my "local" MacOS environment with a simple command.

### CONCLUSION:

Now that I have a nodejs app working on my local environment like this, it is safe to continue to build out the functionality of this app, by extending the code in app.js, and using the simple 'node app.js' command to start / restart / stop the server, and checking the output in the browser.

So long as my app.js works on my local environment, I can be reasonably certain that it is 'deployable' later to a publicly accessible server of some kind, where we can start and stop the app in more-or-less the same manner - or more likely in a more sophisticated manner which we can decide on later.

In the next chapter, we will explore ways to extend app.js to fetch the necessary data from an api endpoint provided by the MTA.  Then 'wrangle' the MTA data a bit, before printing only the most relevant data for our purposes, so it is visible in our local browser.

The result of our work on this project will always be a white screen in a browser, with either plain text, or perhaps 'JSON' formatted output.  We will treat the beautification or formatting of this output as a later step, using slightly different tools which we will google to find later.  This is the concept of 'decoupling' our data layer from our presentation layer - this concept is virtually universal in any serious project work.

## END CHAPTER 1

## ADDENDUM A: TOOLS FOR COLLABORATION ON SOFTWARE PROJECTS

Now that I have an 'app.js' and would like to collaborate on it, I will use a tool called Git to push the current version of the code to a shared 'code repository' - in this case, a public repository under my account on github.com.

Git is a command-line tool used for collaboration on software projects.  MacOS installation instructions for Git are here: https://gist.github.com/derhuerst/1b15ff4652a867391f03#file-mac-md.  An popular, optional UI for Git is called Tower: https://www.git-tower.com/mac/.  Many users prefer Tower for ease of use, but I use command line because I am used to it.

I followed these steps to 'push' the current 'app.js' code, and the document you are reading, to github.com:

1. login to github.com as myself ('samtny') and create a project called 'samtny/sterkel-mta-server'.  Note that github also checks the *namespace* 'sterkel-mta-server' to be sure it is not already in use by another github.com project.  This is one reason why project naming is important.
1. initialize a local Git repository, and push my files onto the github repository.
1. all of these files are now publicly visible on github.com at: https://github.com/samtny/sterkel-mta-server.

## END ADDENDUM A
