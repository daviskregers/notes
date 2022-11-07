# Configure your editor to work with git

You can use config, to use a specific command as the git's core editor, I'll use Visual Studio Code.

```
git config --global core.editor "code"
```

Now we run a command:

```
git config --global -e
```
The git global configuration file will open up in Visual Studio Code editor.

Also, if we now run a `git commit` command without any parameters, the commit message will be opened in Visual Studio Code for editing.