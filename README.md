# Instructions on Creating and Hosting a static website 
Arthur McMullen 
2025/03/04
## Table of Contents:
- [Purpose](#Purpose)
- [Prerequisites](#Prerequisites)
- [Instructions](#Instructions)
	- [Setting up distributed version control and Forge](#Setting-up-distributed-version-control-and-Forge)
	- [Making a website with Markdown](#Making-the-Website-with-MarkDown)
	- [Creating a static website](#Creating-the-Static-Website)
	- [Enabling GitHub Pages](#Enabling-GitHub-Pages)
	- [Publishing Content onto the Website](#Publishing-Content-onto-the-Website)
- [Further Reading](#Further-Reading)
- [FAQ](#FAQ)
- [Credits](#Credits)
## Purpose
This is a guide for Martin McLaren on creating a static website to host a resume. Will be employing tools like Forges, Version Control and Static website generators to achieve this. Furthermore, will expand on Andrew Etters Principles of Modern Technical writing. Will use tools like VScode and GitHub to get familiar with tools developers use.
## Prerequisites 
- A computer
- A resume to host 
- [VSCode](https://code.visualstudio.com/), a text editor will use for modifying files.
- Pelican installed, will touch on this later 
- [Git installed](https://git-scm.com/install/windows) for version control
- A GitHub account, for a forge to host the website. [You can sign up here](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://github.com/signup&ved=2ahUKEwiL9IHr_4eTAxVVDjQIHShIG3wQFnoECAwQAQ&usg=AOvVaw0a6qEmIZVdziwPUb-hFApr)
- A free evening or weekend and a Dr. pepper 

## Instructions 

### Setting up distributed version control and Forge
We will use Git for our distributed version control and GitHub for our forge. Git is the underlying mechanism that allows us to easily manage our system, create backups, and allow for collaboration if we so desire. As for technical writing, will want to use them because other developers use them. (Andrew Etter)

Go to GitHub and create a new repository.
> Repositories > new 

In the repository name field, enter:
```
[insert your username].github.io
```
Will use this format to access GitHub Pages which is GitHubs free service for hosting static websites. 
- Check that visibility is set to public.

This is the URL for your static website that will need for later.

- Move the online repository onto your PC:
	- Download GitHub Desktop app from: https://desktop.github.com/download/
	- Run the executable
	- Log into your GitHub desktop account
	- clone the repository onto GitHub desktop.
		- click on "current repository" at the top left of the app.
		- click on "add"
		- click on "clone repository..."
		- copy + paste the link of your repository to the repository URL field under the URL tab.
			- WARNING, the link to your repository is different then the link to your static website.
		- Decide where the folder will be located under local path. Leaving the default option is fine.
		- click on "clone" 

- Confirm in the GitHub Desktop App that the name of our repository is assigned the correct name, you can see the name on the top left of the app.

### Making the Website with MarkDown
Will now design our website using a lightweight mark up language, in this case markdown. Static websites are made up of HTML which looks complicated and hard to read. Instead of bashing our heads against a wall, we can convert markdown, which is simple to learn and even easier to read, into HTML using a static website generator later.

For that, will have to learn how to write in markdown. 

[Here is a guide on some of the basic syntax](https://www.markdownguide.org/basic-syntax/).
To make writing in markdown easier, will need a program to render the text, thankfully VSCode is able to somewhat render the files, but its missing some functionality. Instead, I would suggest trying [obsidian](https://obsidian.md/) which is a free and open source markdown rendering tool.

### Creating the Static Website
Etter recommends using a Static website generator to automate publishing our document over manually creating it. So, we will use a static website generator to turn a markdown document into a website written in HTML. 

- navigate to the website folder you had assigned earlier in VSCode.
	- Open: >file >open folder
		- Find the path to your project folder.
		- Note: If you created the repository with the default path, it should look something like this: C:\Users\[your user name]\Documents\GitHub

 Install pelican, if you already have it installed, you can skip this step
	 - Make sure python is installed. 
	 - [You can install Python here](https://www.python.org/downloads/)

Run the command:
```
python -m pip install "pelican[markdown]"
```
this will install pelican.

- Type In the terminal at the bottom of the VSCode:
```
pelican-quickstart
```
	- This will start pelican's static website creation process.

- The console will prompt you with a few questions.

What will be the title of this web site? 
	> Reply with: [Enter the name of your website]
	
Who will be the author of this web site? 
	> Reply with: Martin McLaren
  
What will be the default language of this web site? 
	> Leave default or reply with:[en]

Do you want to specify a URL prefix? e.g., https://example.com   (Y/n) 
	> Reply with: y

What is your URL prefix? (see above example; no trailing slash)
	> Reply with: [insert your username].github.io

Do you want to enable article pagination? (Y/n) 
	> Reply with no.
 
> What is your time zone? [Europe/Rome] 
	> Reply with: America/Winnipeg

> Do you want to generate a tasks.py/Makefile to automate generation and publishing? (Y/n)
	> Reply with: y

Answer the next 5 questions with until:

> Do you want to upload your website using GitHub Pages? (y/N) 
 	- Type y to confirm yes, we are using GitHub pages.
 
> Is this your personal page (username.github.io)? (y/N) 
	- Type y to confirm yes

Confirm in VS code

- Navigate to your pelicanconf.py file.
- Add the line:
	```
	OUTPUT_PATH = 'docs'
	``` 
  at the bottom of the file.
	- Without this, GitHub Pages wont know where to look to generate the static website.

Either:
- Place the markdown file you created into the content folder on VSCode
- Create a new markdown file in the content folder
	- it ends with .md
	- Copy and paste the lightweight markup context into markdown

Convert the lightweight mark up language into HTML in Pelican by typing:

```
pelican content
```
into the terminal 


We can preview the website your hosting by typing:
```
pelican --listen
```
into the terminal.

Press CTRL + Click on the blue hyperlink in the console to make sure the website opens. It should look like this, the default theme.

![Example website](images/example_website.png)

### Enabling GitHub Pages
GitHub Pages is GitHub's way to allow users to host their own static websites. However, we have to enable this feature in our repository. GitHub is a forge which is a platform which hosts repositories, allows for collaboration, and version control. Because of it's ease of accessibility, shareability and proximity to developers, Etter recommends using them for technical documentation.

- Navigate to your GitHub repository website.
- click on the cog icon for the specific repository
![find_gear](images/find_gear.png)
- Enable the "Use your GitHub Pages website" option

To make sure GitHub Pages can find the output created by pelican's Static Forge, we must change where it looks.

- Navigate to the GitHub repository website.
- click on the repository's settings tab
- click on "Pages" under "Code and automation" on the sidebar
- Make sure the Source under Build and Deployment is set to "Deploy from a branch"
- Make sure the branch is set to main 
- Change the folder from "./root" to "./docs"
- Make sure the result looks like this 

![build and deploy](images/build_and_deploy.png)

# Publishing Content onto the Website

Now to change the contents of the webpage:
- Navigate to the GitHub Desktop App
- Type, in the summary required field, publish
	- What you enter can be anything 
	- Click Commit to main
	- Push to Origin
		- this sends it to the website

Now go check the website to make the sure the appropriate content is there.

You did it!
# Further Reading
For further reading, you can check out:

For use of GitHub Pages
https://docs.github.com/en/pages/quickstart

Using Obsidian:
https://obsidian.md/

Viewing a variety of Pelican Themes:
https://pelicanthemes.com/
# FAQ

##### Q: Why am I getting [windows error 5] when running pelican content?
A: That's because VSCode doesn't have permission to delete the contents of the docs folder, its likely an issue caused by Window's One Drive cloud service. Deleting the docs folder manually instead works perfectly. 

##### Q: Why is it easier to use Markdown over HTML.
A: Markdown has a simpler syntax and is significantly easier to read. 

## Credits

- Nikolaas Christie 
- Bradley 
