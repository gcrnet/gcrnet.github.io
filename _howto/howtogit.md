---
layout: post
title: GitHub HowTos
feature-img: "https://i.imgur.com/4KpVtQF.png"
date: 6 January 2021
---

## Tips for GitHub
* After enabling a two-factor authentication in my GitHub account, when
I run the Git `git push` command it throws the following error message:
```
$ git push
Username for 'https://github.com': your username
Password for 'https://Username@github.com':
remote: Invalid username or password.
fatal: Authentication failed for 'https://github.com/username/repository.git/'
```
**Solution**
Creating a GitHub personal access token.

1. In the upper-right corner of any page, click your profile photo, then click Settings.
2. In the left sidebar, click Developer settings.
3. In the left sidebar, click Personal access tokens.
4. Click Generate new token.
5. Give your token a descriptive name.
6. Select the scopes, or permissions, you’d like to grant this token. To use your token to access repositories from the command line, select repo.
7. Click Generate token.
8. Copy the token to your clipboard. For security reasons, after you navigate off the page, you will not be able to see the token again.

Using a token on the command line.

Once we have a token, we can enter it instead of our password when performing Git operations over HTTPS. Just inter your token after prompted a password and then watch the magic happen…

```
$ git push origin remote_branch
Username: your_username
Password: your_token
```
