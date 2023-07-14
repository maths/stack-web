# Updating this website

This guide aims to outline the process for anyone to contribute to the ongoing development of the STACK website. It is not necessarily complete and in some cases it may be useful to find additional tutorials.

## Basic requirements

In order to update the website you will need the following:

<ul>
    <li>A <a href="https://github.com/" target="_blank">GitHub account</a></li>
    <li>A code editor; there are plenty of free and / or open source editors online, a popular choice is <a href="https://code.visualstudio.com/" target="_blank">Visual Studio Code</a> (VSCode)</li>
    <li>A GitHub GUI; there are also plenty of choices, a popular choice is <a href="https://desktop.github.com/" target="_blank">GitHub Desktop</a>, and some code editors, e.g. VSCode, include git integration</li>
</ul>

This guide is based on using VSCode for code editing and GitHub management. However, other combinations of code editors and GitHub GUIs can be used in similar ways. To set up VSCode you can see <a href="https://code.visualstudio.com/docs/sourcecontrol/github" target="_blank">this guide</a> or follow the steps below.

<ol>
    <li>Create a GitHub account</li>
    <li>Install <a href="https://git-scm.com/download" href="_blank">Git</a></li>
    <li>Install VSCode and 
    <ol type="i">
        <li>Install the <a href="https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github" target="_blank">GitHub Pull Requests and Issues</a> extension</li>
        <li>Follow the prompts to set up your GitHub credentials</li>
    </ol>
    </li>
</ol>

## Forking the maths/stack-web repository
The STACK website is stored in and built from the GitHub repository `maths/stack-web`. To update the website you will need to create a copy into your own account to make the relevant changes in and then update them into the original repository. The process of creating such a copy is referred to as Forking and is done as follows:

1. Log in to Github
2. Go to the <a href="https://github.com/maths/stack-web" target="_blank">`maths/stack-web`</a> repostory
3. Click in the Fork button at the top-right of the page: <img style="display: inline-block;" src="/img/docs/fork.png" title="Fork button" alt="Fork button">. This will open the 'Create a new fork' page.
4. It is advisable not to change the Repostory name and ensure to copy the `master` branch only by checking the relevant box (you can choose to include branches by unchecking the box and all branches will be copied). Click Create fork: <img style="display: inline-block;" src="/img/docs/create_fork.png" title="Create fork button" alt="Create fork button">

A new repsitory `your-github-username/stack-web` will be created and you will be redirected to it. This is your own personal copy of the website files.

### Clone the repository
Brief description of cloning and how to do it

### Update the site as required
Short paragraph with links to the readme file that has general info

### Stay in sync
Brief description of syncing and how to do it

## Getting your changes into the website
Brief description of PRs, what happens to them, and how to create them

## Workflow summary
Diagmar similar to Sam's