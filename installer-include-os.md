# IncludeOS

## Installation

Etapes :

        # sources
        git clone "https://github.com/hioa-cs/IncludeOS.git" --depth 1

        # dans le bashrc
        export INCLUDEOS_PREFIX=~/includeos/
        export PATH=$PATH:$INCLUDEOS_PREFIX/bin

        # dépendances python
        sudo pip install jsonschema junit-xml filemagic pystache antlr4-python2-runtime psutil

        # dépendances système
        sudo apt install curl make cmake nasm bridge-utils qemu jq python-pip g++-multilib gcc clang-3.8