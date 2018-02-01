# IncludeOS

## Installation

Etapes :
        # ATTENTION il faut clang-3.9 pour compiler et non la 3.8 (au cas ou on a un bug de compile : error: support for type '__float128' is not
      yet implemented)
        # et du coup il faut désinstaller clang-3.8 et clang++-3.8 si ils sont installés
        # comme des projets dont dépend IncludeOS sont téléchargés à la volée et utilisent clang-3.8 (qui ne supporte pas les headers linux modernes utilisant les float_128), on fait un petit hack pour utiliser la 3.9 qui elle supporte les float 128 bits :
        sudo ln -s /usr/bin/clang++-3.9 /usr/bin/clang++-3.8
        sudo ln -s /usr/bin/clang-3.9 /usr/bin/clang-3.8

        # sources
        git clone "https://github.com/hioa-cs/IncludeOS.git" --depth 1

        # à ajouter dans le bashrc
        # ATTENTION on dirait un bug dans les scripts d'install, bien utiliser ce case pour le répertoire : 'IncludeOS' sinon il fait de la merde
        export INCLUDEOS_PREFIX=~/IncludeOS/
        export PATH=$PATH:$INCLUDEOS_PREFIX/bin

        # dépendances python
        sudo pip install jsonschema junit-xml filemagic pystache antlr4-python2-runtime psutil

        # dépendances système
        sudo apt install curl make cmake nasm bridge-utils qemu jq python-pip g++-multilib gcc clang-3.9

Maintenant compiler l'ensemble en lançant :

        ./install.sh

Cela va produire les binaire IncludeOs

## Test

Lancer :

        ./test.sh

Ceci va compiler le projet example/demo_service

Pour le lancer :

        cd examples/demo_service/build
        ~/IncludeOS/bin/boot IncludeOS_example

Ceci lance un mini serveur web qui écoute sur le bridge (créé par include os) sur le port 80.

Donc pour tester, cette commande dans un autre terminal doit réussir :

        telnet 10.0.0.42 80

        # tu peux envoyer GET / (requete HTTP minimal) et tu devrais recevoir une réponse du serveur.