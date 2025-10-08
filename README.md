# homelab-docker
Mini HomeLab Réseau avec Docker

Ce projet met en place un petit environnement de **simulation réseau** avec Docker, destiné à l’expérimentation et à l’apprentissage de la **surveillance système et réseau**.

## Objectif du projet
- Comprendre comment interconnecter plusieurs conteneurs dans un réseau isolé
- Mettre en place un système de monitoring (Netdata)
- Tester la configuration et la connexion via un VPN

## Architecture
```
homelab-docker/
├── README.md
├── docker-compose.yml
├── .gitignore
├── netdata/
│   └── config/...
├── vpn/
│   └── docker-compose.yml
├── bridge-vm/
│   └── Dockerfile
└── docs/
    ├── architecture.png
    ├── network_topology.md
    └── lessons_learned.md
```
- **Netdata** : supervise les conteneurs et les ressources hôtes  
- **VPN** : permet de relier le lab à l’extérieur de façon sécurisée

## Stack technique
- Docker & Docker Compose  
- Netdata  
- WireGuard  

## Ce que j’ai appris
- Configuration de réseaux Docker personnalisés
- Surveiller les performances système via Netdata
- Bases du monitoring et de la connectivité inter-conteneurs
- Mise en place d’un VPN dans un environnement Dockerisé

##Améliorations futures
- Ajouter un systeme de logs
- Automatiser le déploiement du lab avec Ansible
