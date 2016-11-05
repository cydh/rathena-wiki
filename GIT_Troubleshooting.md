---
title: GIT Troubleshooting
permalink: /GIT_Troubleshooting/
---

Cloning Problem
---------------

`Cloning into 'rathena'...`
`POST git-upload-pack (250 bytes)`
`remote: Counting objects: 102175, done.`
`remote: Compressing objects: 100% (16110/16110), done.`
`fatal: The remote end hung up unexpectedlyMiB | ##.## KiB/s`
`fatal: early EOF`
`error: RPC failed; result=18, HTTP code = 200`
`fatal: index-pack failed`

-   Cloning process is terminated with error messages above
    -   Use Git Bash and do `git` `config` `--global` `http.postBuffer` `524288000` *(the last number just a speculation size, but it works)*
    -   See: [Git clone return result=18 code=200 on a specific repository](http://stackoverflow.com/questions/12236415/git-clone-return-result-18-code-200-on-a-specific-repository)

Updating Problem
----------------

-   git stash
    -   Problem encounter when Git can identified 'who you are'. **\*\*\* Please tell me who you are.**
    -   Just do a command **example** `git` `config` `--global` `user.email` `"youremail@domain.com"`, and
    -   Just do a command **example** `git` `config` `--global` `user.name` `"My` `Name"`
