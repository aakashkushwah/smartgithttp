# smartgithttp
Docker Image for creating a Git Server using Smart http and Example of a post-receive hook in git

Docker Image for setting up a sample git repository over smart http is akushwah/git_http with tag firsttry
Run the docker container via the following command

>docker run -dit -p 8182:80 akushwah/git_http:latest

This starts a git server at 8182 port. 
Following link was used to setup git smart http server on this ubuntu image.
(http://www.codepool.biz/git-server-ssh-http-ubuntu.html)

There are two sample repositories already created (admin/admin is the credentials for making a commit)
- http://localhost:8182/git/dynamsoft (Repo1)
- http://localhost:8182/git/myrepo (Repo2)

Git repository location in the container image is located at below location.
>/var/www/html/git

More repositories can be created at this location.

Once the repositories are created, we need to restart the apache2 service. Use the following command.
>service apache2 restart

### post-receive hook
Repo1 has been modified for demonstrating a git post-receive hook. The hook file can be found at the below location
>/var/www/html/git/dynamsoft.git/hooks/post-receive.

Once any thing is pushed to this repository post-receive script also runs which can be used for variety of purposes such as
-Analysing comments
-Calling a Jenkins Job etc.
