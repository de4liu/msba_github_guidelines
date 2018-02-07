

# MSBA Github Usage Guidelines & Best Practices

<!-- MarkdownTOC autolink="true" bracket="round" -->

- [1. Can I make my repositories public?](#1-can-i-make-my-repositories-public)
- [2. Can I take my UMN repositories and put them on public Github?](#2-can-i-take-my-umn-repositories-and-put-them-on-public-github)
- [3. How do I take a UMN repository and put it on public Github?](#3-how-do-i-take-a-umn-repository-and-put-it-on-public-github)
- [4. How do I deal with sensitive information in a Github repository?](#4-how-do-i-deal-with-sensitive-information-in-a-github-repository)

<!-- /MarkdownTOC -->


Github has become a useful tool for developing and showcasing coding projects. Employers often value candidates who have a meaningful github profile. In the mean time, MSBA faculty members are also increasingly leveraging github.umn.edu for teaching and student projects. As MSBA students use Github more frequently, questions arise, especially regarding sharing course related repositories, how to use UMN github (github.umn.edu), which is an Enterprise Github system that is separated from the public Github(github.com) and inaccessible from outside of UMN. 

### 1. Can I make my repositories public? 

You can choose your repositories to be private or public (including within the github.umn.edu). It is important to note that you:

- Should not make your *assignments or exam related repositories* (either the questions or the answers) public, for these are detrimental to future students' learning experiences.
- Should not never make your *CAL project or live case related repositories* public as this violates the confidentiality agreement with our corporate partners. In fact, you should check whether you are allowed to put CAL project/live case in UMN github in the first place. 
- Certain Professors may allow you to share certain course related repositories publicly (e.g. the trend marketplace projects for the big data course), but you should ask before proceeding.
- Should feel free to make your *personal projects* public (in fact, you are encouraged to start such projects on the public Github).

Before you make a repository public (in fact, when you create any repository), [**it is important to make sure that your committed codes do not contain passwords, API keys, or other sensitive information.**](#4-how-do-i-deal-with-sensitive-information-in-a-github-repository) 


### 2. Can I take my UMN repositories and put them on public Github?

Once you graduate from U of Minnesota, the repositories that belong to you [will be removed](https://it.umn.edu/git-frequently-asked-questions) will be removed with four weeks notice. If you want to take some of these repositories with you, it is important to read the following.

First, the public Github defaults all repositories to be public to the world, unless you have a paid account. So, in many cases, moving your repositories to Github means that you are making it public. As such, the same considerations mentioned in [Bullet 1](#1-can-i-make-my-repositories-public) apply when you are deciding whether you can move a repository from UMN to public github. 

Therefore, we additionally recommend the following:

- It is advisable to create your *personal projects* on public Github instead of UMN github, since the goal of these are to share and show case. 
- If you have already started your personal projects on UMN github, you are encouraged to move it to public Github before graduation. 
- You should ask your professor whether it is okay to share certain *course-related repositories* (e.g. your final project) publicly before you take them to the public Github. 
- *If you have a paid account*, you may be allowed to save a private copy of certain course-related repositories on Github, but check with your professor first.

### 3. How do I take a UMN repository and put it on public Github?

It is actually pretty simple. 

- **Step 1**: Make sure you already have a local clone of the source UMN repository. If not, you can use `git clone https://github.umn.edu/smith/myrepo` to make one.

- **Step 2**: Create a blank repository on the public Github (say, `https://github.com/smith/myrepo`) -- **do not initialize the repository with a README**.

- **Step 3**: Change the remote to the public github repo
```bash
# first detach from your umn repo
git remote rm origin   
# then set public git repo as your new remote
git remote add origin https://github.com/smith/myrepo
```
You can also list verify the remote URL of your local repository with command `git remote -v`.
- **Step 4**: Push the repo to the new Public github repository.
```
git push -u origin master
```

### 4. How do I deal with sensitive information in a Github repository?

You should never commmit sensitive information such as passwords and API keys to a Git repository. 

- The typical way of dealing with password is to read the password from a configuration file which is not committed to the repo (you should [create a `.gitignore` file](https://stackoverflow.com/questions/10744305/how-to-create-gitignore-file) in your repository and instruct git to [ignore the configuration file](https://www.atlassian.com/git/tutorials/gitignore)). If your configuration file is called `foobar.config`, then you would commit a file called `foobar.config.example` to the repository instead, containing sample data. This way, any clone will have the example file, which the user can use to re-create `foobar.config` and enter his/her password before running the code.
```bash
# content of .gitignore
footbar.config
```
- If you already have already committed such sensitive information previously, you should filter out your existing password from previous commits, see the GitHub help page on [Removing sensitive data](http://help.github.com/removing-sensitive-data/).
