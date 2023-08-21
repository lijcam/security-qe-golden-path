# Commit signing

Setting up and maintaining GPG signing for Git commits on a Macbook Pro using VSCode as your IDE can be straightforward. Here's a step-by-step guide to help you get started:

## Install GPG Suite 
Download and install GPG Suite, which provides GPG tools for macOS. You can find it at https://gpgtools.org/.

Generate GPG Key Pair:
Open "GPG Keychain" from the applications. Click on the "+", then "New" to generate a new GPG key pair. Follow the instructions, and make sure to choose a strong passphrase for your key.

## Configure Git
Open your terminal and configure Git to use your GPG key for signing commits:

```bash
git config --global user.signingkey <YOUR_GPG_KEY_ID>
git config --global commit.gpgsign true
```

## Add GPG Key to GitHub

If you're using GitHub, add your GPG public key to your GitHub account. You can export your public key from GPG Keychain:

```bash
gpg --armor --export <YOUR_GPG_KEY_ID>
```

Copy the output and add it to your GitHub account settings.

## Configure VSCode
If you're using VSCode, make sure it's aware of your GPG configuration.

- Open VSCode, go to File > Preferences > Settings.
- Search for "git path" and make sure the "Git: Path" setting points to the correct path to your Git executable (usually `/usr/local/bin/git`).
- Search for "commit signing" and make sure "Git: Commit Signing" is set to "true".

## Testing
Create a new commit using VSCode. You should be prompted to enter your GPG passphrase to sign the commit. After entering your passphrase, the commit will be signed.

## Verify commit signature
After pushing your commits to a remote repository, you can verify the commit signatures on GitHub. Look for the "Verified" label next to your commit message.

Remember to keep your GPG key secure and back it up. If you ever need to work on a different machine, you can import your GPG key there to maintain consistent signing.

Please note that the exact steps and settings might change slightly based on updates to software. Always refer to the official documentation for GPG Suite, Git, VSCode, and any other related tools you're using.

# Pipeline verification in OpenShift

To store your GPG public key as an OpenShift secret, you can follow these steps:

### Export GPG Public Key
First, export your GPG public key in ASCII-armored format. You can do this using the following command:

```bash
gpg --armor --export <YOUR_GPG_KEY_ID> > gpg-public-key.asc
```

Replace `<YOUR_GPG_KEY_ID>` with the actual key ID you want to export.

### Create OpenShift secret
Use the oc create secret command to create an OpenShift secret containing your GPG public key. You'll need to provide the secret type, data, and a name for the secret.

```bash
oc create secret generic gpg-public-key --from-file=gpg-public-key.asc
```

This command creates a secret named gpg-public-key and loads the contents of the gpg-public-key.asc file into the secret's data.
