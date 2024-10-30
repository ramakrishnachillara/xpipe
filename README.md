# XPipe Vault (Keep this repository private!)

This repository contains all connection information that is designated to be shared.

You can sync with this repository in all XPipe application instances the same way, every change you make in one instance will be reflected in the repository. 

## Category list

- **Connections**
  - [**Oracle Cloud**](categories/390817b1-f071-4d08-a6cf-0b4cc249733e)
- **Scripts**

## Connection list

**All connections / Oracle Cloud**

- [**OC01-ubuntu-152.67.182.131**](stores/0c8bb798-d441-47f4-b72e-44549cd8ac08)
  - [**LXD**](stores/fc96b338-bf28-458d-ba74-1c6dedc82793)
  - [**Shell Environments**](stores/41f256e8-865e-3a3a-9f51-d6e0f5a7784a)
    - [**bash**](stores/9ee33878-79a0-4cda-84f7-833d0c1e392a)
    - [**dash**](stores/7edac009-1d1d-42e7-aa76-4f2618c0f8d5)
    - [**root**](stores/acb2d51e-9249-4184-a7ac-6ab73a26aef4)
- [**OC02-Ubuntu-150.230.142.107**](stores/99cb56f2-3e67-4737-8394-fcc536e1d29a)
  - [**LXD**](stores/2bab33d0-6451-45c9-a251-a53be0b6c301)
  - [**Shell Environments**](stores/63289696-122b-3c47-a8c9-0989843f1293)
    - [**root**](stores/ff12dd35-3f3c-4a5e-aeb3-86e986b2ffe8)
  - [**Teleport**](stores/dd684490-487b-4359-b77c-385418f10873)


## Secret encryption

You have the option to fetch any sensitive information like passwords from outside sources like password managers or enter them at connection time through a prompt window. In that case, XPipe doesn't have to store any secrets itself.

In case you choose to store passwords and other secrets within XPipe, all sensitive information is encrypted when it is saved using AES with either:

- A dynamically generated key file `vaultkey` (The data can then only be decrypted with that file present)
- A custom master passphrase that can be set by you in the settings menu, combined with the vault key file (This option is only as secure as the password you choose)

By default, general connection data is not encrypted, only secrets are.
So things like hostnames and usernames are stored without encryption, which is in line with many other tools.
There is an available vault setting in the settings menu to encrypt all connection data if you want to do that.

## Cloning the repository on other systems

Nowadays, most providers require a personal access token (PAT) to authenticate from the command-line instead of traditional passwords.
You can find common (PAT) pages here:
- **GitHub**: [Personal access tokens (classic)](https://github.com/settings/tokens)
- **GitLab**: [Personal access token](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)
- **BitBucket**: [Personal access token](https://support.atlassian.com/bitbucket-cloud/docs/access-tokens/)
- **Gitea**: `Settings -> Applications -> Manage Access Tokens section`
Set the token permission for repository to Read and Write. The rest of the token permissions can be set as Read.

Even if your git client prompts you for a password, you should enter your token unless your provider still uses passwords.

If you don't want to enter your credentials every time, you can use any git credentials manager for that.
For more information, see for example:
- https://git-scm.com/doc/credential-helpers
- https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git

Some modern git clients also take care of storing credentials automatically.

## Troubleshooting

### Adding categories to the repository

By default, no categories are set to shared so that you have explicit control on what connections to commit.

To have your connections of a category put inside your git repository,
you need to click on the `⚙️` icon (when hovering over the category)
in your `Connections` tab under the category overview on the left side.
Then click on `Add to git repository` to sync the category and connections to your git repository.
This will add all shareable connections to the git repository.

### Local connections are not synced

Any connection located under the local machine can not be shared as it refers to connections and data that are only available on the local system.

Certain connections that are based on a local file, for example SSH configs, can be shared via git if the underlying data, in this case the file, have been added to the git repository as well.

### Other issues

If you encounter any other issues, you can try interacting with the cloned repository manually.
You can find it at `%USERPROFILE%\.xpipe\storage\` or `~/.xpipe/storage/`.
XPipe will call your installed git client, so any potential issues with your local git client also transfer to XPipe.

To understand what went wrong, you can also launch XPipe in debug mode at `Settings -> Troubleshoot -> Launch in debug mode`.
This will tell you in detail what git commands are executed.
