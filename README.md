# XPipe Vault (Keep this repository private!)

This repository contains all connection information that is designated to be shared.

You can sync with this repository in all XPipe application instances the same way, every change you make in one instance will be reflected in the repository. 

## Category list

- **Connections**
  - [**Oracle Cloud**](categories/390817b1-f071-4d08-a6cf-0b4cc249733e)
- **Scripts**

## Connection list

**All connections / Oracle Cloud**

- [**OC-WS01 - 144.24.148.244**](stores/fee55e30-2bd1-48b5-b2a0-dcba991c459d)
  - [**Docker**](stores/024dcd8d-67a4-411f-ada1-ae9af20d0679)
  - [**Shell Environments**](stores/80a7e806-41f8-3b6b-b494-b3bdce8b8115)
    - [**bash**](stores/77d34711-7c07-464f-83fa-83d11408f228)
    - [**dash**](stores/ed59ca6b-9ae1-441b-860b-41ba4bca7f5e)
    - [**root**](stores/2ef790e5-ef7d-4a3e-9091-859252ffe2d8)
- [**OC-WS02 - 144.24.147.68**](stores/31383563-600c-4184-96a8-6f5e58256830)


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
