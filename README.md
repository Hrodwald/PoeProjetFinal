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
...
        
# Commentaire

```
