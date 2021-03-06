# **Projet d'entreprise Epsilon Corporation**

## Sommaire

[I. Le projet](#I-Le-projet)
&nbsp; &nbsp; [1. Le contexte](#1-Le-contexte)
&nbsp; &nbsp; [2. L'équipe](#2-L'équipe)
[3. Structure](#2-Structure)
[II. Le projet](#I-Le-projet)
[1. Le contexte](#1-Le-contexte)
[2. L'équipe](#2-L'équipe)
[III. Le projet](#I-Le-projet)
[1. Le contexte](#1-Le-contexte)
[2. L'équipe](#2-L'équipe)
  
---

## I. Le projet


### 1. Le contexte :

L'entreprise Epsilon Corporation a besoin de trois applications Web :

* Un blog statique (Jekyll)
* Une application JAVA Tomcat
* Un web serveur Python

La solution Cloud retenue : Amazon web services. Le cloud AWS ne servira que de ressources
VM.

Epsilon Corporation souhaiterait un déploiement de l'infrastructure le plus dynamique possible,
souple , automatisé. (provisionning de l'infrastructure AWS , conteneurisation).

Précision techniques :

Les données des applications (data) devront êtres sur des volumes dediés ISCSI ou NFS.
La mise en place de monitoring serait un plus (outils monitoring).

La securité :
L'infrastructure aws sera accessible par SSH , FTPs, VPN , filtrage accés (Reverse Proxy, Netfilter...)
La présence de chaîne CI/CD est fortement recommandé pour les trois applications web.

Les outils :
* Gitlab - CI/CD
* Serveurs LAMP
* Jenkins
* Containerisation
* Ansible

### 2. L'équipe :

* Amine AHMAMOU
* Romuald SENIGALLIA
* Matthieu RAMANANARIVO
* Moustapha Mohamedou TALL


### TITRE GRAS
**Texte gras** 

## I. Organisation
Organisation qui a été adopter sur ce projet était quasi similaire à une méthodologie agile vue la disparité des niveaux de l'équipe projet,il était obligatore de faire plusieurs mêlées par jour afin de s'aligner sur un objectif commun et de pouvoir débloquer rapidement les points bloquants.
Cette organisation à été la cléf de l'aboutissement de ce projet et de pouvoir.


### 1. 
### 2. 

* liste
* 

Exemple code :
```yaml
---
- hosts: localhost
  connection: local
  gather_facts: False
```
        
# Commentaire

### Le serveur web python 
**1.Objectif**

L'objectif est de mettre en place un serveur web python sur le dépot Gitlab qui va permettre via un commit de faire un build de l'image docker.

**2.Travaux** 
Pour la mise en place du serveur python, nous avons créer un reprtoire python_serv_install dans notre repertoire roles. On y retrouvera deux sous-répertoire files et tasks, qui contiennent l'ensemble de nos fichiers nécessaire pour la mise en place se notre serveur dont les fichiers simple_server.py,Dockerfile, main.yml et Jenkinsfile.




Exemple code simple_server.py : 
```yaml
from http.server import HTTPServer, SimpleHTTPRequestHandler

def run(server_class=HTTPServer, handler_class=SimpleHTTPRequestHandler):
    """Entrypoint for python server"""
    server_address = ("0.0.0.0", 8000)
    httpd = server_class(server_address, handler_class)
    print("launching server...")
    httpd.serve_forever()

if __name__ == "__main__":
    run()
 ```

 Exemple code du main : 
 
 ```yaml
   ---
- name: Create Project Directory
  file:
    path: ~/project
    state: directory
    owner: centos
    group: centos

- name: Src file Python Server
  copy:
    src: target/
    dest: ~/project/
    owner: centos
    group: centos
    mode: 775
    directory_mode: yes

- name: Dockerfile Python Server
  copy:
    src: "Dockerfile"
    dest: ~/project/
    owner: centos
    group: centos
    mode: 755
    directory_mode: yes

- name: copy Jenkinsfile 
  copy:
    src: "Jenkinsfile"
    dest: ~/project/
    owner: centos
    group: centos
    mode: 755
    directory_mode: yes
   ```
 Exemple code du Jenkinsfile  :
```yaml
   ---
node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Initialize'){
        def dockerHome = tool 'docker'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("python/server")
    }
}
```
 **3.Difficltés **

La première difficulté sur mise en place de serveur web python était de bien comprendre les attendus sur sa fonctionnalité et ses interactions avec les autres serveurs.
La deuxièume difficulé était liée à un travail de recherche sur le web afin de comprendre les bonnes libraries python à importer dont HTTPserver. 
 


  
