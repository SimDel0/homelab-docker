#homelab-docker

###Mini HomeLab Réseau avec Docker + Campagne d’attaques Wi-Fi/Bluetooth (M5StickC Nemo)

Ce projet met en place un environnement de **simulation réseau** avec Docker, axé sur le **monitoring**, la **sécurité** et l’étude du comportement d’un système sous **attaques radio**.
Afin de tester la robustesse de la plateforme, j’ai effectué une série d’attaques Wi-Fi et Bluetooth à l’aide d’un **M5StickC équipé du firmware Nemo**, ciblant directement le **Raspberry Pi 4** hôte.

##Objectifs du projet

* Comprendre et manipuler des réseaux Docker isolés
* Mettre en place un système de surveillance complet avec **Netdata**
* Configurer un **VPN WireGuard** pour accéder au lab depuis l’extérieur
* Centraliser et analyser les logs système avec **rsyslog**
* Tester la résistance du Raspberry Pi face à :

  * des attaques Wi-Fi (DeAuth, Beacon Flood, Fake AP…)
  * des attaques Bluetooth (BLE Flood)
* Observer l’impact de ces attaques sur :

  * les conteneurs Docker
  * le système hôte
  * les performances réseau

---

##Architecture du projet

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
├── logs/
│   └── rsyslog/
|       └── wifi.log
|       └── bluetooth.log           
└── docs/
    └── rapport.pdf

```

###Composants utilisés

* **Docker & Docker Compose**
* **Netdata** pour le monitoring
* **WireGuard** pour le VPN
* **Rsyslog** pour la collecte des logs système
* **Raspberry Pi 4 Model B** comme machine hôte
* **M5StickC (Firmware Nemo)** comme attaquant radio

---

##Campagne d’attaques radio (M5StickC + Nemo)

Pour tester la solidité du HomeLab, j’ai mené une campagne de tests avec un **M5StickC Nemo**, capable d’effectuer des attaques Wi-Fi et Bluetooth.
L’objectif principal était d’observer la **résilience du système**, analyser les **logs générés**, et mesurer l’impact sur les conteneurs Docker supervisés par Netdata.

###Attaques Wi-Fi réalisées

* Scan actif / passif
* **MAC Address Spoofing**
* **Créaion de faux point d'accès**

###Attaques Bluetooth réalisées

* Scan BLE continu
* **Fake BLE Devices** (périphériques fantômes)
* Tentatives de saturation

---

##Objectifs de la campagne de tests

* Analyser la stabilité du Raspberry Pi sous attaques radio
* Vérifier les perturbations sur :

  * l’accès réseau aux conteneurs
  * la consommation CPU/RAM
  * les I/O réseau Docker
* Vérifier l’intégrité des services en fonctionnement (VPN, Netdata…)
* Exploiter les logs générés :

  * kernel
  * wpa_supplicant
  * bluetoothd
  * journald
  * Netdata
  * services Docker

---

##Stack technique

* **Docker / Docker Compose**
* **Netdata** (supervision et métriques temps réel)
* **WireGuard** (VPN sécurisé)
* **Rsyslog** (collecte de logs)
* **Raspberry Pi OS**
* **M5StickC + Firmware Nemo** pour les attaques Wi-Fi & BLE

---

##Ce que j’ai appris

* Création de réseaux personnalisés avec Docker
* Mise en place d’un monitoring approfondi et lisible
* Lecture et corrélation de logs système pour la détection d’anomalies
* Effets concrets d’attaques radio sur un système Linux
* Impact réel sur les conteneurs Docker et les services exposés
* Configuration d’un VPN dans un environnement Dockerisé
* renforcement de la résilience d’un lab face à des perturbations extérieures

---

##Amélioration

* Rapport des résultat (coming soon)
