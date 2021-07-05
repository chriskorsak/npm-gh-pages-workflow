# Deployment workflow using npm (node package manager) gh-pages package
## This also covers adding a custom domain name to point to your gh-pages site

* Create a project folder, and inside that, create a folder called 'dist' or 'site' or whatever. This is where your deployed files will go (html, css, js)
* In command line, go to project folder. Run:
``` 
$ npm init -y
```
This creates the file _package.json_

* In command line, Run:
```
$ npm install gh-pages
```
This adds gh-pages package as a dependency to to _package.json_
* Add a key-value pair to _package.json_:
```
"homepage": "https://chriskorsak.github.io/name-of-github-branch-here",
```
* Update "scripts" value with this:
```
"scripts": {
    "deploy": "gh-pages -d dist"
  },
```
-d flag means the directory called dist (in this case). In essense it means you are running the gh-pages package on this directory.

### Project file creation and git workflow
* Create a _.gitignore_ file in project root folder and add _node_modules_ to this file. We don't need git to track this folder
* Create git repo on github with name of branch referenced in _package.json_ ("homepage")
* Initialize git in project folder
* Create project files 
* Add files with git 
* Commit files with git
* Add remote repository
* Push files with git

### To deploy to gh-pages
```
$ npm run deploy
```

## Adding a custom domain name
* Add your custom domain to the _pages_ section of _settings_ in your github repo. This will create a commit that adds a CNAME file in the root of your project folder.
* Add the github A RECORD ip addresses in the advanced DNS section of your domain registrar (for the specific domain)
```
Github A Record IPs:
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```
* The domain should now work, but it won't work if you type in wwww.domain.com. You have to configure a CNAME record with your domain registrar.
* Use these:
```
Type: CNAME
Host: www
Value: chriskorsak.github.io (don't include the repository name)



 