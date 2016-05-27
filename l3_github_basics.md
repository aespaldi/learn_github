---
layout: page
title: GitHub Basics
permalink: /github_basics/
---

<p>Git allows us to have version control for our code on our local machines, but what if we want to share this code with others or work on a team. GitHub is an online tool that allows you to share and manage code as well as provide an online backup should something happen to your local computer.</p>

<h2>Introduction to GitHub</h2>

<p>GitHub provides an online hosting service for your code.  You store your projects on GitHub using Git repositories.  These repositories are an online copy of your local Git repository and provide online backup for your code.</p>
<img src="{{site.baseurl}}/images/github_copy.png">

<p>You can use GitHub to work with teams because multiple people can copy the GitHub repository to their own local repository (called cloning) or to their own GitHub account (called forking).</p>

<p>GitHub implements version control and conversation when working with teams using the Git tools of commits, branching and merging as well as additional tools of pull requests to request a merge and issues for online conversations about the project. </p>

<img src="{{site.baseurl}}/images/github_pull.png">


<p>When working with GitHub, you will establish a GitHub workflow that incorporates your local Git workflow. The next sections describe the process of working with a common GitHub workflow.  Each step has a set of commands to perform on GitHub or run in the Command Line.

<div class="challenge-heading">GitHub workflow</div>
<div class="challenge-instructions">
  <ul>
<li>Either <strong>Fork</strong> and existing repository or <strong>Create </strong>a new one.</li>
<li>Once you have a repository on GitHub, <strong>Clone</strong> it to your local computer to make changes.</li>
</ul>
<p>Updates are done on your local repository and then the remote repository is updated. You will repeat this cycle many times as you add features to your project.</p>
<ul>
<li>Verify your master branch is in sync with the remote repository by <strong>Pulling</strong> updates before making changes.</li>
<li>Make changes locally using <strong>Git workflow. </strong></li>
<li>After making changes, <strong>Push </strong>your feature-branch to GitHub.</li>
<li>Submit a <strong>Pull Request</strong> to merge your feature branch back into the master branch.</li>
<li>Once your pull request is <strong>Merged </strong>repeat this cycle to make additional changes.</li>
</ul>
</div>
Let's look at each of these commands in detail.</p>
<ol>
<li><strong>Creating a Repository: </strong>As a developer, you always want to have a backup of your code, as well as being able to access it from anywhere and easily share it with others. When you start a new coding project you should also create a GitHub repository for this backup. There are two main ways to do this:
<ol>
<li>If you're starting a new project, you can create the repository on GitHub and then clone it to your computer before you start.</li>
<li>If you have existing code project you want to store on GitHub, you can push this to a blank repository on GitHub</li>
</ol></li>


<li><strong>Forking an Existing Repository: </strong> Forking is a way to share code using GitHub. When you fork a repository, you make a copy of that repository on your GitHub account. You can fork any repository on GitHub that is public. Many developers and open source projects make their code public on GitHub so they can share it with other developers. The steps are:
<ol>
<li>Navigate to the repository on the other account</li>
<li>Choose the <strong>fork</strong> option</li>
<li>Select which of your accounts you want to fork into (if you have more than one)</li>
<li>View the forked repository on your own account (you should be redirected there automatically when GitHub finishes forking)</li>
</ol></li>


<li><strong>Cloning a Repository: </strong>
Cloning is the process of copying a repository from GitHub to your personal computer. When you clone a repository, a new folder is created on your computer with the repository name, and all of the files inside the repository are copied into this folder. The steps to clone are: 
<ol>
<li>Navigate online to the GitHub repository you want to clone and copy its url. (If you are using SSH Keys, select SSH before copying - otherwise select HTTPS)</li>
<li>On your local computer use the Command Line to navigate to the directory you wish to clone the GitHub repository into. Verify that this directory is <strong>NOT</strong> already a Git repository by typing <pre> ls -la</pre> and verifying there is no <span class='inline-code-tt'>.git</span> folder. You <strong>NEVER</strong> want to clone a repository into another local Git repository</li>

<li>Clone the repository. <pre> git clone COPIED-URL</pre>
If you are using HTTPS, you will be prompted to enter your GitHub username and password. (You won't be able to see what you type just press enter when you finish each)</li>
<li>Cloning creates a new folder with the same name as the repository on GitHub. Navigate into this folder.<pre>
ls
cd FOLDER-NAME</pre></li>
<li>The folder you have created is a Git repository and the cloning process has set up a <strong>remote</strong> to link it back to the repository you cloned from on GitHub. A remote contains the location information for the repository on GitHub. You can verify this by using the Git command to view a remote <pre>git remote -v</pre>.
</li>
</ol>
</li>


<li><strong>Updating a Repository: </strong>Once you have cloned a repository to your computer, you can edit the files and folders. The repository is a Git repository, so you should use <strong>Git workflow</strong> to protect your work as you make changes.

<p>Before you make changes locally pull a current version of the remote master into your local master to make sure you have the latest version of the project.</p>

<pre>git checkout master
git pull origin master</pre>

<p>Once you have made changes, you will want to push these changes back to GitHub so your remote and local files are in sync.
The <strong>push</strong> command in Git uses a remote to send the code in a branch to the linked repository on GitHub.

<pre>git push origin FEATURE-BRANCH-NAME</pre>
</p>
<p>The template for the push command is:
<pre>git push REMOTE-NAME BRANCH-NAME
REMOTE NAME = name of remote or defaults to origin.
BRANCH NAME =  name of branch you want to push or defaults to the current branch..
</pre>
Thus, the push command can be called without a remote or origin.

<pre>it push </pre>
But this can result in accidentally pushing the wrong branch (like master), so always add the remote and the branch.</p></li>


<li><strong>Pull Requests : </strong> A pull request is a operation made on GitHub which requests to merge code from a feature branch into the master branch.  Its like a friendly way of saying: "Hey! I'm done implementing this feature your asked for, can you review my code?" After a pull request is made, it needs to be merged to update the master branch on GitHub.  When working in a team, it is best practice to have at least one other person review your pull request and they should be the person to merge it once the changes are approved.

The steps to create a pull request are:
<ol>
<li>Push a feature branch to GitHub</li>
<li>Navigate to the GitHub repository online and either choose the <strong>Compare and Pull Request </strong> option if it is available or the <strong>Create New Pull Request</strong> option</li>
<li>Verify the base branch you are requesting to merge code into (master) and the branch you are merging code from (feature-branch).</li>
<li>Fill in the title and description of your pull request</li>
<li>Choose the <strong>Create Pull Request</strong> option</li>
<li>Wait for your pull request to be merged according to your team GitHub policy.</li>
</ol></li>

<li><strong>Merge Pull Request : </strong>If you are using GitHub for your own project without a team you can still create a pull request and then merge your own pull request.  <strong>You would usually NOT merge your own pull request unless you are working solo on a project.</strong> 
The steps to merge a pull request are: 
<ol>
<li>Select the <strong>Merge Pull Request</strong> option</li>
<li>Select the <strong>Confirm Merge</strong> option</li>
<li>Verify your changes have been merged into the base branch (master)</li>
<li>Delete your feature branch to keep things cleaned up (optional).</li>
</ol>

</p></li></ol>

<h2>Watch it Live</h2>
<p>The video shows how all these commands work on an actual project. 
<p><iframe style="width: 640px; height: 480px;" title="GitHub Workflow." src="https://player.vimeo.com/video/168406376/" width="300" height="150" allowfullscreen="allowfullscreen" webkitallowfullscreen="webkitallowfullscreen" mozallowfullscreen="mozallowfullscreen"></iframe></p>
</p>

<h2>Your Turn</h2>
<p>Let's practice all of this by working on an existing GitHub repository. 

<div class="challenge-heading">do the thing</div>
<div class="challenge-instructions">
<p>Part 1: Clone an existing repository to your computer. 
  <ol>
<li>Navigate to the <a href="https://github.com/coder-sheep/travel">Travel</a> repository in a browser. 
</li>
<li>Fork the repository to your personal GitHub account using the <strong>Fork</strong> button.</li>
<li>Navigate back to your personal GitHub account and explore your new repository online. You can open folders, read code, look at commit messages and more. Now that you have forked the repository, a complete copy is now in your personal GitHub account and any changes you make locally will only be pushed to this copy. </li>
<li>Clone your copy of the course materials from your personal GitHub repository to your computer following Clone A Repository Steps</li>
<li>This will create a folder on your local computer. Navigate in this folder and verify the same files are here as are on your GitHub repository.</li>

</ol></p>


<p><strong>Part 2:</strong>  Update the <code>"summer_destinations.txt"</code> file using Git workflow  and upload your changes to your repository on GitHub. Here are the detailed steps:
  <ol>
    <li>Navigate to the folder on your computer. </li>
    <li>Create and checkout a new feature branch <pre> git checkout FEATURE-BRANCH-NAME</pre></li>
    <li>Add some of your favorite travel destinations to the <strong>summer_destinations.txt</strong> file.</li>
    <li>Add your files to the staged Git files and commit your changes 
      <pre>git add .
git commit -m "your commit message" </pre></li>
    <li>Push your feature branch to GitHub <code>git push origin FEATURE-BRANCH-NAME</code>.</li>
    <li>Submit a pull request on GitHub from your feature branch to your master branch.</li>
    <li>Wait for your feature branch to be merged</li>
  </ol>
<p><strong>Step 3: </strong>For this step you will put on your manager hat (it's purple) and merge the pull request the other (non-manager) you just submitted to simulate working on a team. </p>
<ol>
<li>View the pull request on GitHub.  Look at the commit messages and files changed and verify you want to merge this code into the master code. </li>
    <li>Merge your pull request on GitHub so the changes are on your master branch</li>

  <li>Navigate to the updated file on GitHub and verify your changes are there.
  </li>
  <li>Delete the feature branch on GitHub if that is part of your GitHub workflow.</li>
</ol>
  </p>

  <strong>Nice work!</strong>
</div></p>


<h2>Review</h2>
<p>In this challenge you learned the basics of working with Git.  You should be comfortable with the following concepts and how to implement them in code: <ul>
<li>Create a repository on GitHub</li>
<li>Fork an existing GitHub repository to your personal GitHub account</li>
<li>Clone a GitHub repository to your local computer</li>
<li>Update a GitHub repository by pushing changes from your local computer</li>
<li>Submit a pull request for your changes to be merged into the existing project</li>
<li>Verify a pull request is valid and merge it into a GitHub repository</li>
</ul></p>
<p>
If you would like to learn more we recommend working through the <a href="https://help.github.com/">GitHub tutorials</a></p>