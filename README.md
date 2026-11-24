# XPipe Vault (Keep this repository private!)

This repository contains all connection information that is designated to be shared.

You can sync with this repository in all XPipe application instances the same way, every change you make in one instance will be reflected in the repository. 

## Category list

- **All connections**
  - [**VPSы**](categories/0878685f-1092-43b3-9f5d-00a631888afa)
  - [**RDP Работа**](categories/03baf590-1cbb-449a-bee1-f9fffacd1daf)
- **All scripts**
- **All identities**
  - [**Synced**](categories/69aa5040-28dc-451e-b4ff-1192ce5e1e3c)

## Connection list

**All connections / VPSы**

- [**Hermes**](stores/9ab33863-9675-4f0f-a407-96c8f41c1910)
- [**Латвия**](stores/84d28c3d-68cf-4ef7-b005-5ab4fd8649fe)
- [**Москва**](stores/a7165ad2-8da0-4eae-b9ad-16e548fc31d2)
- [**Москва еще один**](stores/abd4aa08-ef88-46c9-bd45-aa9cf1b7e924)
- [**Москва Сайт**](stores/dbbd44f0-6401-4b25-8d92-7cea916df237)
- [**Польша**](stores/9a671c72-b65e-4e82-8e8a-a808b06c88ef)
- [**Санкт-Петербург**](stores/08b760e5-f23e-4096-ab68-da4b11827213)
  - [**LXD containers**](stores/d3bd1a6a-030e-4e1f-b86b-eca7b6d867bd)
- [**Финляндия**](stores/a7f3e2c7-b536-4dcd-90ad-c6d511b87208)

**All connections / RDP Работа**

- [**it-1cserver01**](stores/72760720-1c86-48e8-aab3-7e6a8cdbda4c)
- [**TRM-SRV**](stores/13a40cba-16cc-4b46-93b0-db23da2fbff7)
- [**Мегаклимат**](stores/c0f995bb-4cab-4b34-a0ab-8dc3127edd4c)
- [**Рабочий компьютер\**](stores/21852c57-4d9f-46c4-b784-1133a889b660)

**All identities / Synced**

- [**RDP Профиль**](stores/d20c6690-39ff-4763-b921-86dd81fb4581)



## Secret encryption

You have the option to fetch any sensitive information like passwords from outside sources like password managers or enter them at connection time through a prompt window. In that case, XPipe doesn't have to store any secrets itself.

In case you choose to store passwords and other secrets within XPipe, all sensitive information is encrypted when it is saved with either:

- A dynamically generated key file `vaultkey` (The data can then only be decrypted with that file present)
- A custom passphrase that can be set for your user in the vault settings menu (This option can only as secure as the password you choose)
- Role-based secret encryption keys for team vaults (Data can only be decrypted by having access to a certain role and its secret key)

See the vault access settings menu for configuring the vault access.

By default, general connection data is not encrypted, only secrets are.
So things like hostnames and usernames are stored without encryption, which is in line with many other tools.
There is an available setting in the vault access settings menu to encrypt all connection data if you want to do that.

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

### Adding connections to the repository

By default, no connection categories are set to sync so that you have explicit control on what connections to commit.

To have your connections of a category put inside your git repository, you first need to change its sync configuration.
In your `Connections` tab under the category overview on the left side, you can open the category configuration menu either by right-clicking the category or click on the `⚙️` icon when hovering over the category, and then clicking on the `🔧` configure button.

Then, set the `Sync with git repository` value to `Yes` to sync the category and connections to your git repository.
This will add all syncable connections in that category to the git repository.
The sync settings for a category are inherited by default from its parent if not explicitly set.

### Local connections are not synced

Any connections located under the local machine are not synced as they are only available on the local system. You can sync any other types of remote connections like SSH connections.

Some types of connection entries that are local by default, e.g. an SSH config file, can be configured to sync by syncing the underlying data, e.g. files, with this repository as well. You can find details for each type of connection entry at https://docs.xpipe.io/.
