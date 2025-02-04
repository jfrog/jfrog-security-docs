# Shell Auto Completion

If you're using JFrog CLI from a bash, zsh, or fish shell, you can install JFrog CLI's auto-completion scripts.

#### Install JFrog CLI with Homebrew

If you're installing JFrog CLI using Homebrew, the bash, zsh, or fish auto-complete scripts are automatically installed by Homebrew. Please make sure that your `.bash_profile` or `.zshrc` are configured as described in the Homebrew Shell Completion documentation.

#### Using Oh My Zsh

With your favorite text editor, open `$HOME/.zshrc` and add `jfrog` to the plugin list. For example:

```
plugins=(git mvn npm sdk jfrog)
```

#### Other Installation Methods

To install auto-completion for bash, run the following command and follow the instructions to complete the installation:

```
jf completion bash --install
```

To install auto-completion for zsh, run the following command and follow the instructions to complete the installation:

```
jf completion zsh --install
```

To install auto-completion for fish, run the following command:

```
jf completion fish --install
```
