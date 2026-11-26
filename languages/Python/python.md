## virtualenv
* its a concept in python to isolate dependencies of a project.
* it creates a environment specific to the project.
* installs all dependencies inside it.

## pip
* package managment system written in python used to install and manage software packages.
* it connects to online repository called python package index.
* its also useful to download dependencies for a project.
* its always better i guess to download dependencies inside a virtual env to keep the global clean.
* only bigger packages like numpy can be kept globally.

The site-packages directory is the target folder where Python installs all third-party libraries and modules that you download via package managers like pip.


# uv
It is extremely fast, all-in-one Python package and project manager written in Rust.
- This is a tool introduced in 2024 by a company called Astral.
- uv acts as a single drop in replacement for many traditional tools like pip, pip-tools, pipx, poetry, pyenv, twine and virtualenv.
- It is very faster than these traditional tools. It uses lot of parallel programing to achieve this.
- automatically downloads and manages python interpreters without requiring a pyenv setup. creates virtual env and handles universal lock files. 

# project toml file
- This is the unified standard configuration file for modern python projects. 
- This acts as a single source of truth that replaces setup.py, setup.cfg and requirements.txt files. 
- By using the human readable toml format it consolidates build definitions, project metadata ( includes python version requirement and project dependencies) and local development tool settings in one root level file.

# wheel file 
A Python wheel (.whl) is the standard, pre-built binary package format for distributing Python modules.
Defined by PEP 427, wheels are essentially specialized ZIP archives that let pip install software instantly by avoiding the lengthy and error-prone process of compiling source code on your machine.

Before wheels, packages were distributed as Source Distributions (.tar.gz or .zip), forcing your system to compile code locally. Wheels solve several major headaches:
• No Compiler Required: If a package wraps high-performance C, C++, or Rust code (like NumPy or TensorFlow), a pre-built platform wheel installs instantly without requiring local build tools.
• Blazing Fast Installation: Installing a wheel is as simple as unzipping files into your environment's site-packages directory, speeding up deployment and CI/CD pipelines.
• Enhanced Security: Because installing a wheel does not execute arbitrary setup.py scripts or run code during installation, it reduces potential security risks.

Wheel files follow a strict, standardized naming convention that tells pip exactly which systems are compatible:
\({}\text{\ \{distribution\}-\{version\}-\{python\_tag\}-\{abi\_tag\}-\{platform\_tag\}.whl}\)
For example, a file named cryptography-42.0.0-cp39-abi3-manylinux2014_x86_64.whl breaks down as:
1. Distribution & Version: cryptography, version 42.0.0.
2. Python Tag (cp39): Built for CPython 3.9.
3. ABI Tag (abi3): Uses the stable Python Application Binary Interface.
4. Platform Tag (manylinux2014_x86_64): Built specifically for 64-bit Linux systems.

