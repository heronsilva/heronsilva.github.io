---
layout: post
title: "Mise En Place: The Last Version Manager You'll Ever Need"
date: 2025-04-07
updated_date: 2025-04-13
author: 'Heron Silva'
categories: "journal"
tags: [ mise, node, python, git ]
image: "mise-en-place.png"
---

### Mise: The Last Version Manager You'll Ever Need

#### Why Version Management is a Headache (Until Now)

Ever found yourself debugging an issue for hours, only to realize you're using the wrong Node.js version? Or struggling
to get your Python environment just right? Version managers promise to solve these issues, but managing multiple tools
can be a headache—until now.

Enter [mise-en-place (mise)](https://mise.jdx.dev){:target="_blank"}: an all-in-one package version manager designed for simplicity,
performance, and compatibility. With mise, you can forget about juggling multiple version managers and focus on coding.

#### What is mise?

Mise is a modern, fast, and flexible version manager that aims to replace tools
like [asdf](https://github.com/asdf-vm/asdf){:target="_blank"} while maintaining compatibility with its ecosystem. It
allows you to manage multiple versions of programming languages, databases, and other dependencies with ease, all within
a unified and intuitive interface.

#### Why mise Should Be Your Default Version Manager

1. **Unified Version Management**
   Instead of installing and managing multiple version managers (
   e.g., [nvm for Node.js](https://github.com/nvm-sh/nvm){:target="_
   blank"}, [pyenv for Python](https://github.com/pyenv/pyenv){:target="_blank"}, etc.), mise consolidates everything
   into one tool. This simplifies your development environment and reduces conflicts.

2. **Speed and Performance**
   Mise is designed for speed, leveraging Rust’s performance benefits. It runs 2-5x faster than asdf when switching
   environments or installing new versions, making it a compelling alternative for developers looking for efficiency.

3. **Cross-Compatibility with asdf**
   If you're already using asdf, you don’t have to start over. Mise is compatible with `.tool-versions` files, so
   migrating is seamless. Just install mise, and it will pick up your existing configurations.

4. **Better Defaults, Less Configuration**
   Mise improves upon asdf by offering sane defaults and reducing the need for extensive configuration. It also supports
   global, project-level, and shell-specific version management with ease.

5. **Simple and Intuitive CLI**
   The mise CLI is straightforward and user-friendly. Installing a tool version is as simple as:
   ```sh
   mise use node@20
   mise use python@3.12
   ```
   It also supports lazy-loading, reducing overhead in shell startup times.

6. **Automatic Version Switching**
   Like asdf, mise automatically switches tool versions based on `.tool-versions` or `.mise.toml` files, ensuring you’re
   always using the correct version for each project.

7. **Built-in Plugin System**
   Mise has its own plugin system while also supporting asdf plugins, allowing you to manage a wide variety of tools and
   languages effortlessly.

#### Before and After Mise

| Workflow         | Without Mise                            | With Mise                      |
|------------------|-----------------------------------------|--------------------------------|
| Node Version     | `nvm use 18`                            | Automatic via `.tool-versions` |
| Python Version   | `pyenv activate project-env`            | Automatic via `mise`           |
| Install New Tool | Install separate version manager & tool | `mise use go@1.22`             |

#### Mise vs Other Version Managers: Pros and Cons

| Feature                                | mise                    | asdf                  | nvm                 | pyenv              | Best For                          |
|----------------------------------------|-------------------------|-----------------------|---------------------|--------------------|-----------------------------------|
| **Speed**                              | ✅ Fast (Rust-based)     | ❌ Slower (Bash-based) | ⚠️ Moderate         | ⚠️ Moderate        | Mise for speed                    |
| **Unified Tool Management**            | ✅ Yes                   | ✅ Yes                 | ❌ No (Node.js only) | ❌ No (Python only) | Mise for all-in-one               |
| **Cross-Compatibility**                | ✅ Supports asdf plugins | ✅ Native support      | ❌ No                | ❌ No               | Developers migrating from asdf    |
| **Automatic Version Switching**        | ✅ Yes                   | ✅ Yes                 | ✅ Yes               | ✅ Yes              | All tools                         |
| **Lazy Loading**                       | ✅ Yes                   | ❌ No                  | ✅ Yes               | ❌ No               | Faster shell startup              |
| **Global & Project-Specific Versions** | ✅ Yes                   | ✅ Yes                 | ❌ No                | ✅ Yes              | Consistency across projects       |
| **Simplicity & Ease of Use**           | ✅ Very Simple           | ❌ Requires Plugins    | ⚠️ Moderate         | ⚠️ Moderate        | Developers who want minimal setup |

#### Real-World Developer Workflow

Imagine switching from a Node.js monorepo to a Python-based data science project. With mise:

```sh
cd my-node-app  # Automatically uses node@18
cd ../ml-project  # Automatically uses python@3.12
```

No manual switching, no broken environments. Just code.

#### Getting Started with mise

##### Installation on macOS

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

##### Installation on Linux

If you’re using a Debian-based system, you can install mise via the official script:

```sh
curl -fsSL https://mise.jdx.dev/install.sh | sh
```

There's also an available package for Arch Linux users:

```sh
pacman -S mise-bin
```

Once installed, follow the shell activation step:

```sh
eval "$(mise activate bash)"  # or zsh/fish
```

#### [Demo](https://mise.jdx.dev/demo.html){:target="_blank"}

<video src="https://mise.jdx.dev/assets/demo.BP9cL2Fi.mp4" width="100%" controls></video>

##### Day-to-Day Usage Examples

1. **Setting a Global Version**
   ```sh
   mise use --global node@18 python@3.11
   ```

2. **Setting a Project-Specific Version**
   ```sh
   mise use --pin node@20 --path .
   mise use --pin python@3.12 --path .
   ```

    Or, even more explicitly:
    ```sh
    mise use --pin node@20 --path ~/Projects/github/node-project
    ```

    This creates or updates a `.tool-versions` or `.mise.toml` file _in the current directory_. Without `--path`, `mise` might save it to the nearest parent folder instead.

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

#### Tips and Troubleshooting

- **Update all plugins**: `mise plugins update`
- **Clean unused versions**: `mise prune`
- **See what's installed**: `mise list`
- **View available versions**: `mise ls-remote <plugin>`

#### Who Should Use Mise?

- Developers using multiple languages (Node.js, Python, Rust, etc.)
- Teams that want consistent tooling across projects
- People frustrated with slow version managers
- Those looking for a simple, high-performance alternative to asdf

#### Final Thoughts

If you're tired of juggling multiple version managers and want a unified, high-performance solution, mise is an
excellent choice. With its speed, compatibility, and simplicity, it’s a strong contender for becoming your default
package version manager.

Ditch the clutter, simplify your setup, and give mise a try today at [mise.jdx.dev](https://mise.jdx.dev)! 🚀
