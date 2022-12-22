---
title: "Use Your Fingerprint with 1Password to Authenticate the Twilio CLI"
date: 2022-12-07T12:00:27+06:00
writtenDate: "December 07, 2022"
authors: "Anthony Dellavecchia"
featureImage: images/blog/1password-1.png
postImage: images/blog/1password-1.png
tags: ["twilio", "cli", "security", "developer-experience"]
---

> **TLDR:** Learn how to configure 1Password to use your fingerprint to authenticate within the Twilio CLI and reduce how often you manually type in credentials. 

---

I'd like to highlight a [1Password Shell Plugin](https://developer.1password.com/docs/cli/shell-plugins/) that makes authentication with the [Twilio CLI](https://www.twilio.com/docs/twilio-cli/quickstart) as easy as scanning your fingerprint.

You can configure 1Password to securely authenticate the Twilio CLI, so you never have to manually type your credentials in the terminal again.

> Please note that this is currently only available for Mac/Linux.
> Bash and Zsh are the shells currently supported.


![gif of the CLI in action](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8snxyl0l84imska6yubg.gif)

Currently, developers using the [Twilio CLI](https://www.twilio.com/blog/twilio-cli-is-now-generally-available) must first authenticate (login) before they can run commands. This often requires locating credentials in a separate window then manually entering them in the terminal.

Users are prompted to enter an Account SID and Auth Token, both of which can be found on the dashboard of the [Twilio Console](https://www.twilio.com/console). Then, users are asked to enter them into the terminal like so:

```
$ twilio login
You can find your Account SID and Auth Token at https://www.twilio.com/console
 » Your Auth Token will be used once to create an API Key for future CLI access to your Twilio Account or Subaccount, and then forgotten.
? The Account SID for your Twilio Account or Subaccount: ACXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
? Your Twilio Auth Token for your Twilio Account or Subaccount: [hidden]
? Shorthand identifier for your profile: dev
```

This article will walk you through installing the [1Password Shell Plugin for Twilio](https://developer.1password.com/docs/cli/shell-plugins/twilio/) on Mac/Linux, so you can benefit from a smoother login experience.

## Prerequisites

- A free or paid Twilio account - If you haven’t yet, [sign up for a free Twilio account](https://www.twilio.com/try-twilio)
- Install the latest version of the Twilio CLI - [Get it here](https://www.twilio.com/docs/twilio-cli/quickstart#install-the-twilio-cli)
- A 1Password account - [Sign up for a 14 day trial](https://1password.com/sign-up/)
- Install the 1Password 8 app - For [Mac](https://1password.com/downloads/mac/) or [Linux](https://1password.com/downloads/linux/)
- Add your 1Password Account to the app - [Add an account](https://support.1password.com/add-account/)
- Install the 1Password CLI version 2.9.0 (or above) - [Downloads available here](https://app-updates.agilebits.com/product_history/CLI2#beta)
- Connect the 1Password CLI with the 1Password 8 app - [See here](https://developer.1password.com/docs/cli/about-biometric-unlock/#step-1-connect-1password-cli-with-the-1password-app)

## Step 1: Configure your default credentials

To ensure you have the correct version of the 1Password CLI, run:

```
op --version

```

> It should output version 2.9.0 (or above).

To get started with the Twilio shell plugin, run:

```
op plugin init twilio

```

You’ll be prompted with two options, to either import new Twilio credentials into 1Password or to search for existing Twilio credentials in 1Password.

> If users want to switch to another profile, run `op plugin init twilio` again and select a new set of credentials.

![Import into 1Password or Search in 1Password
](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yk99358vjz0z3nz1ckdw.png)

## Step 1.1: Import or select an item

### Import a new item

If you haven't saved your Twilio credentials in 1Password yet, select **Import into 1Password**.

If 1Password detects your credentials in your local development environment, you'll be prompted to import them automatically. Otherwise, you'll need to enter your credentials manually.

You can find these credentials by [creating an API Key](https://www.twilio.com/docs/glossary/what-is-an-api-key#how-can-i-create-api-keys) from the Twilio Console with these steps:

1. Navigate to **Settings** and select **API Keys**, or simply follow this link.
1. Click the **Create new API Key** button, or click on the plus **(+)** icon if you have other API Keys already.
1. Enter a friendly name for your API Key.
1. Select the key type — **Standard** or **Main**.
1. Click the **Create API Key** button.

You'll then be prompted to enter a name for the new 1Password item and select the vault where you want to save the item.


![Manually import your credentials if they are not already stored in 1Password
](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yebs49vxhn3atnm7ypgo.png)

### Select an existing item

If you've already saved your Twilio credentials in 1Password, select **Search in 1Password**.

You'll see a list of related items and the vaults where they're saved. If you don't see your credentials, select "Expand search" to browse all items in your account.


![If your Twilio credentials are saved in 1Password, Search in 1Password
](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/66vcjz6r8x1tkovu1i92.png)

### Step 1.2: Set default credential scope

After you select or import your credentials, you'll be prompted to select which vault to save your API key in; feel free to choose whichever vault you’d like.

Lastly, you’ll then be asked to configure when to use the item to authenticate the Twilio CLI.

![Select when to prompt for authentication
](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3bofjuavmqz7dmzp7t9v.png)

> - "**Prompt me for each new terminal session**" will only configure the credentials for the duration of the current terminal session. Once you exit the terminal, the default will be removed.
> - "**Use automatically when in this directory or subdirectories**" will make the credentials the default in the current directory and all of its subdirectories, as long as no other directory-specific defaults are set in them. A terminal-session default takes precedence over a directory-specific one.
> - "**Use as global default on my system**" will set the credentials as the default in all terminal sessions and directories. A directory-specific default takes precedence over a global one.

## Step 2: Source the plugins.sh file

To make the plugin available, run the following command in your terminal:

> The file path for your op folder may vary. `op plugin init` will output a source command with the correct file path.

If you’re a legacy 1Password CLI user:

```
source ~/.op/plugins.sh

```

If you’re setting this up the first time:

```
source ~/.config/op/plugins.sh

```

> Note: There are other [supported third-party plugins](https://developer.1password.com/docs/cli/shell-plugins/#get-started). If this is your first time installing a shell plugin for 1Password, you'll also need to add the source command to your RC file or shell profile, to persist the plugin beyond the current terminal session.

For Zsh:

```
echo "source /Users/{your_user_name}/.config/op/plugins.sh" >> ~/.zshrc && source ~/.zshrc
```

## Step 3: Use the CLI

The next time you enter a command with the Twilio CLI, you'll be prompted to authenticate with fingerprint biometrics or system authentication (logging in with a system account password).


![TouchID prompt when running Twilio commands](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/gjn2hgipa9jjx1rh2fhr.png)

## Get Help: Inspect or clear your credentials

### Inspect your configuration

To inspect your current Twilio configuration:

```
op plugin inspect twilio

```

1Password CLI will return a list of the credentials you've configured to use with Twilio and their default scopes, as well as a list of aliases configured for Twilio.


![List of configured credentials
](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/pwicbprtedhp294wpdw3.png)

### Clear your credentials

To reset the credentials used with Twilio:

```
op plugin clear twilio

```

You can clear one configuration at a time, in this order of precedence:

1. Terminal session default
2. Directory default, from the current directory to $HOME
3. Global default

For example, if you're in the directory `$HOME/projects/awesomeProject` and you have a terminal session default, directory defaults for `$HOME` and `$HOME/projects/awesomeProject`, and a global default credential configured, you would need to run `op plugin clear twilio` four times to clear all of your defaults.

To clear your global default credentials, terminal session default, and the defaults for your current directory at the same time, run `op plugin clear twilio --all`.

## Reference: For more information

1Password authenticates with Twilio by injecting environment variables with the credentials required by the Twilio CLI commands directly from your 1Password account.

### How long is the timeout?

You’ll be asked to re-authenticate via fingerprint after 10 minutes of inactivity.

### Add Twilio credentials in the 1Password 8 app

Another way to input your credentials in 1Password is through the app (rather than the CLI).

1. Open the 1Password 8 application
2. Create a **+New Item**
3. Select **API Credential** and name it **Twilio API Key**
4. **+Add another field** as **Password**
5. The titles should match the Field names from the table below
6. The values should match your Twilio credentials


![Add Twilio credentials in the 1Password 8 app
](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/0co2fc1q06e3jdqrq0h7.png)

If you saved your Twilio credentials in the 1Password 8 app manually rather than using `op plugin` to import a new item, make sure that your field names match the table below.

| 1Password Field names      | Environment variables |
| ----------- | ----------- |
| Account SID      |   TWILIO_ACCOUNT_SID    |
| API Key   |     TWILIO_API_KEY   |
| API Secret   |    TWILIO_API_SECRET    |
| Region (optional)   |    TWILIO_REGION   |

If your credentials are stored in a different field, you'll be prompted to select the field manually. Field names are case insensitive. Field name tokens can be separated by whitespaces, underscores, dashes, or nothing.

## Next Steps: Explore other Twilio CLI plugins

The Twilio CLI can be extended through plugins which give access to new commands. You can publish your own plugins to share with the wider Twilio community, or make them private for your own—or your clients’—business workflows.

You can also explore a list of [available plugins](https://www.twilio.com/docs/twilio-cli/plugins#available-plugins), which include:

- [Dev Phone](https://github.com/twilio-labs/dev-phone) — A developer tool for testing Twilio SMS and Voice applications, even if you don't have service.
- [Serverless Toolkit](https://github.com/twilio-labs/serverless-toolkit/tree/main/packages/plugin-serverless) — Use this to streamline your development workflow with Twilio Functions & Assets.
- [Twilio Assets Plugin](https://github.com/twilio-labs/serverless-toolkit/tree/main/packages/plugin-assets) — Allows you to upload and manage static assets in a Twilio Assets service.
- [Twilio Webhook Plugi](https://github.com/twilio-labs/plugin-webhook)n — Allows you to emulate webhook events to validate your applications and TwiML Bins.
- [twilio watch](https://github.com/twilio-labs/plugin-watch) — Allows you to watch debugger alerts, voice calls, and messages as they come in, in real time.
- [twilio token](https://github.com/twilio-labs/plugin-token) — Install and use this plugin to generate a token for use in a client-side SDK, e.g., a chat application.
- [twilio flex](https://github.com/twilio/flex-plugin-builder/tree/main/packages/plugin-flex) — Allows you to create, build, and deploy Flex plugins.

### Try other third-party CLIs with the plugin

Interested in authentication with other CLI tools? 1Password Shell Plugins support [over a dozen third-party CLIs](https://developer.1password.com/docs/cli/shell-plugins). To see a list of supported CLIs:

```
op plugin list

```

To choose another plugin to get started with:

```
op plugin init

```

For more information about the 1Password Shell Plugin, [check out the official documentation](https://developer.1password.com/docs/cli/shell-plugins/twilio/).

You can find the code for the shell plugins on this [GitHub repo](https://github.com/1Password/shell-plugins).

Or contact 1Password via Twitter [@1password](https://twitter.com/1password) or via Slack at [https://join.slack.com/t/1password-devs/shared_invite/zt-1halo11ps-6o9pEv96xZ3LtX_VE0fJQA](https://1password-devs.slack.com)

> Anthony Dellavecchia is a Staff Developer Evangelist at Twilio who writes code on stage in front of a crowd. He is an experienced software developer who teaches thousands of people how to build cool things with code. His goal is to help you build deep experiences and connections with technology so that they stick with you forever. Check him out on [Twitter](https://twitter.com/anthonyjdella), [GitHub](https://github.com/anthonyjdella), [Dev.to](https://dev.to/anthonyjdella), or [LinkedIn](https://www.linkedin.com/in/anthonydellavecchia/)


---
