<head>
    <base href="https://ibnaleem.github.io/Haskell-Simplified/Introduction/" />
</head>

# INSTALLING HASKELL

Before we begin learning Haskell, let's start by installing it to interact with the compiler and how to load functions. The more you code, the easier and faster you'll pick up Haskell syntax.

## GHCup: universal installer
GHCup is a simple tool to set up Haskell on your computer. It helps you install everything you need for Haskell programming and lets you manage those installations easily. You don't need special permissions to use GHCup. You can use GHCup to set up the Haskell toolchain, which includes:

1. **GHC (Haskell Compiler):** This is the main tool for running Haskell code. While we'll use GHC for our examples, in real projects, you might use tools like Cabal or Stack.

2. **HLS (Haskell Language Server):** HLS works in the background with your code editor to enhance your Haskell coding experience.

3. **Cabal (Haskell Build Tool):** Cabal helps organize and build your Haskell projects, manage dependencies, and more.

4. **Stack (Alternative Build Tool):** Stack is another option to Cabal for building Haskell projects.

### Installation
Use these commands to fetch the ghcup binary and run it. It will be stored in `~/.ghcup/bin` (or `C:\ghcup\bin` on Windows). This process will help you install the Haskell Toolchain interactively. Remember to execute these commands as a regular user, **not as a root or admin user.**

For Linux, macOS, FreeBSD or Windows Subsystem 2 for Linux, run this in a terminal:
```
curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | sh
```

For Windows, run this command in a PowerShell session:
```
Set-ExecutionPolicy Bypass -Scope Process -Force;[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; try { Invoke-Command -ScriptBlock ([ScriptBlock]::Create((Invoke-WebRequest https://www.haskell.org/ghcup/sh/bootstrap-haskell.ps1 -UseBasicParsing))) -ArgumentList $true } catch { Write-Error $_ }
```

*[Here's a YouTube video for installing Haskell on Windows](https://www.youtube.com/watch?v=bB4fmQiUYPw)*

To understand the functionality of these scripts, refer to the [source code at this repository](https://github.com/haskell/ghcup-hs/tree/master/scripts/bootstrap). Experienced users might prefer a [manual installation](https://www.haskell.org/ghcup/install/#manual-installation) and GPG verification of the binaries.

### Versions
GHCup provides two primary channels for each tool: *recommended* and *latest*. By default, it installs the *recommended* version.

The *latest* channel corresponds to the most recent release of each tool. In contrast, the *recommended* version is selected by GHCup maintainers, considering factors such as community adoption (hackage libraries, tools like HLS, stackage support, etc.) and addressing known bugs.

For additional details, refer to [tags and shortcuts.](https://www.haskell.org/ghcup/guide/#tags-and-shortcuts)

### GHC Command
Begin by launching your system's command line interface (CLI) and executing `ghc --version` to confirm the successful installation of the Haskell toolchain.
```
>> ghc --version
The Glorious Glasgow Haskell Compilation System, version 9.2.8
```

If your output matches above (except the version) then you have successfully installed Haskell on your machine. If you're having issues, [read the installation guide by Haskell](https://www.haskell.org/ghcup/install/). You may need to perform a manual installation.

### Uninstallation
For Linux users, run `ghcup nuke` and remove any ghcup added lines in your `~/.bashrc`.

For Windows users, a `Uninstall Haskell.ps1` script should be downloaded on your Desktop after installation. `Right click > Run with PowerShell` to uninstall Haskell.

### VSCode Integration
To begin, follow these steps for seamless integration with the Haskell Language Server (HLS):

1. Install GHCup, ensuring you choose to install the Haskell Language Server (HLS) during the installation process.
2. Install the extension (in VSCode: `Ctrl + P` and then `ext install haskell.haskell`).
3. Verify that your project utilizes the GHC version installed through GHCup (otherwise, HLS may encounter launch issues):

4. On Linux, if encountering an issue ("cannot find ghc version") when VSCode is not launched from a terminal, resolve it by informing HLS about your GHCup on `$PATH`.

### Vim Integration
See [ghcup.vim](https://github.com/hasufell/ghcup.vim). I'm a little jealous you know how to use Vim.

Finally, we can begin [02-Loading Modules](./02-Loading%20Modules) in Haskell.