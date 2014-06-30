# Primitive Types

## Git remotes tutorial.

We need to start updating our local repositories with everyone else's changes. We can make this easy on ourselve by using [git's remotes feature](http://git-scm.com/book/en/Git-Basics-Working-with-Remotes). We are going to add this repository as a remote called `upstream`. Run the following command from within your repository:

`git remote add upstream https://github.com/codefellows/sea-c11-javascript.git`

or if you have an ssh key on your github account:

`git remote add upstream git@github.com:codefellows/sea-c11-javascript.git`

Then to merge in everyone else's changes run the following command:

`git pull upstream master`

This command is saying 'go to the Code Fellows repository. get the master branch. pull the master branch down to my local repository. and merge it into my local master branch.'

#Required Reading
- [A re-introduction to JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)

#Slides
- [Primitive Type Slides](http://hankyates.github.io/jsPrimitiveTypesSlides/)
