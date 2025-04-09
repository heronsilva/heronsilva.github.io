---
layout: post
title: "Mise: The Last Version Manager You'll Ever Need"
author: 'Heron Silva'
categories: journal
tags: [about]
image: "mise-en-place.png"
---

### Why Version Management is a Headache (Until Now)

Ever found yourself debugging an issue for hours, only to realize you're using the wrong Node.js version? Or struggling to get your Python environment just right? Version managers promise to solve these issues, but managing multiple tools can be a headache—until now.

Enter [mise-en-place (mise)](https://mise.jdx.dev/), an all-in-one package version manager designed for simplicity, performance, and compatibility. With mise, you can forget about juggling multiple version managers and focus on coding.

### What is mise?

Mise is a modern, fast, and flexible version manager that aims to replace tools like asdf while maintaining compatibility with its ecosystem. It allows you to manage multiple versions of programming languages, databases, and other dependencies with ease, all within a unified and intuitive interface.

### Why mise Should Be Your Default Version Manager

1. **Unified Version Management**
    Instead of installing and managing multiple version managers (e.g., nvm for Node.js, pyenv for Python, etc.), mise consolidates everything into one tool. This simplifies your development environment and reduces conflicts.

2. **Speed and Performance**
    Mise is designed for speed, leveraging Rust’s performance benefits. It runs 2-5x faster than asdf when switching environments or installing new versions, making it a compelling alternative for developers looking for efficiency.

3. **Cross-Compatibility with asdf**
    If you're already using asdf, you don’t have to start over. Mise is compatible with `.tool-versions` files, so migrating is seamless. Just install mise, and it will pick up your existing configurations.

4. **Better Defaults, Less Configuration**
    Mise improves upon asdf by offering sane defaults and reducing the need for extensive configuration. It also supports global, project-level, and shell-specific version management with ease.

5. **Simple and Intuitive CLI**
    The mise CLI is straightforward and user-friendly. Installing a tool version is as simple as:

    ```sh
    mise use node@20
    mise use python@3.12
    ```

    It also supports lazy-loading, reducing overhead in shell startup times.

6. **Automatic Version Switching**
    Like asdf, mise automatically switches tool versions based on `.tool-versions` or `.mise.toml` files, ensuring you’re always using the correct version for each project.

7. **Built-in Plugin System**
    Mise has its own plugin system while also supporting asdf plugins, allowing you to manage a wide variety of tools and languages effortlessly.


### Mise vs Other Version Managers: Pros and Cons

|     | mise | asdf | nvm | pyenv | Best For |
| --- | --- | --- | --- | --- | --- |
| **Speed** | ✅ Fast (Rust-based) | ❌ Slower (Bash-based) | ⚠️ Moderate | ⚠️ Moderate | Mise for speed |
| **Unified Tool Management** | ✅ Yes | ✅ Yes | ❌ No (Node.js only) | ❌ No (Python only) | Mise for all-in-one |
| **Cross-Compatibility** | ✅ Supports asdf plugins | ✅ Native support | ❌ No | ❌ No | Developers migrating from asdf |
| **Automatic Version Switching** | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | All tools |
| **Lazy Loading** | ✅ Yes | ❌ No | ✅ Yes | ❌ No | Faster shell startup |
| **Global & Project-Specific Versions** | ✅ Yes | ✅ Yes | ❌ No | ✅ Yes | Consistency across projects |
| **Simplicity & Ease of Use** | ✅ Very Simple | ❌ Requires Plugins | ⚠️ Moderate | ⚠️ Moderate | Developers who want minimal setup |

### Who Should Use Mise?

* Developers using multiple languages (Node.js, Python, Rust, etc.)

* Teams that want consistent tooling across projects

* People frustrated with slow version managers

* Those looking for a simple, high-performance alternative to asdf


### Getting Started with mise

#### Installation on macOS

```sh
brew install mise
```

Or, using the official installation script:

```sh
curl -fsSL https://mise.jdx.dev/install.sh | sh
```

Then, add mise to your shell configuration:

```sh
eval "$(mise activate zsh)"  # or bash/fish
```

#### Installation on Linux

If you’re using a Debian-based system, you can install mise via the official script:

```sh
curl -fsSL https://mise.jdx.dev/install.sh | sh
```

For Arch Linux users:

```sh
pacman -S mise-bin
```

Once installed, follow the shell activation step:

```sh
eval "$(mise activate bash)"  # or zsh/fish
```

#### Day-to-Day Usage Examples

1. **Setting a Global Version**

    ```sh
    mise global node@18 python@3.11
    ```

    This ensures that whenever you’re outside a project directory, these versions are used.

2. **Setting a Project-Specific Version**

    ```sh
    mise use --local node@20
    mise use --local python@3.12
    ```

    This creates a `.tool-versions` or `.mise.toml` file in your project, automatically switching versions when you enter the directory.

3. **Checking Installed Versions**

    ```sh
    mise list
    ```

4. **Uninstalling a Version**

    ```sh
    mise uninstall node@18
    ```

5. **Running a Temporary Version Without Installing**

    ```sh
    mise shell node@20 -- node -v
    ```


### Final Thoughts

If you're tired of juggling multiple version managers and want a unified, high-performance solution, mise is an excellent choice. With its speed, compatibility, and simplicity, it’s a strong contender for becoming your default package version manager.

Ditch the clutter, simplify your setup, and give mise a try today at [mise.jdx.dev](https://mise.jdx.dev/)! 🚀
