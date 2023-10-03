# Getting Help

## Objectives

- man command
- --help

## man command

Linux command documentations are available via the `man` command

The syntax is **man \<command>** where \<command> is the command you want the manual page for.  The following command will show the manual page for the man command:

```bash
man man
```

![Output of man man](./img/Getting_Help_01.png)

The **SYNOPSIS** section shows the basic syntax of the command, including its options and arguments. It provides a quick reference for how to use the command.

To navigate through a man page, you can use the arrow keys to scroll, and you can exit the manual by pressing 'q'. If the manual is long, you can also search for specific terms using the '/' key.

## Missing man pages

If you are unable to find any manual pages after a fresh installation, you may have to run the command `mandb` as the root user to generate the manual pages.  To do so, run the command:

```bash
sudo mandb
```

**sudo** execute a command as another user. To read the manual page for sudo, run the command:

```bash
man sudo
```

## --help

Most commands have the `--help` option. This shows the various options of the command. For example:

```bash
man --help
```

will show the different options available for the **man** command:

![Output of man --help](./img/Getting_Help_02.png)

## Lab

1. Read up the man page for the command `apropos`

2. Search the man page for the command to display calendar

3. Display this month's calendar

4. Display 3 months calendar, spanning the current date

## Conclusion
The `man` command is essential in Linux for providing instant access to comprehensive documentation, offering standardized and offline information about commands, enabling users to understand, use, and automate various aspects of the system.