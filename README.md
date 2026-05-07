# 🌌 TP 4 : Timers & Signaux PWM - Systèmes Embarqués

Bienvenue dans le dépôt du **Travail Pratique N°4**. L'objectif de cette session est d'apprendre à utiliser les périphériques matériels **Timers** du microcontrôleur **STM32 Nucleo-C031C6** pour générer un signal **PWM (Pulse Width Modulation)**, permettant ainsi de faire varier l'intensité d'une LED sans monopoliser le processeur.

Ce projet inclut le code source C (Bare Metal) et un **Rapport de Laboratoire Web Interactif (HTML/CSS/JS)** doté d'**Oscilloscopes Virtuels** pour visualiser la modulation du signal en temps réel.

## 🚀 Fonctionnalités du Jumeau Numérique (Web)

Le fichier `compte_rendu_tp4.html` est une application web autonome au design "Deep Space" qui comprend :
* **Architecture à 2 Simulateurs Isolés :** Deux environnements de simulation distincts pour garantir une exécution sans conflit.
* **Oscilloscopes Virtuels Dynamiques :** Un composant `<canvas>` trace instantanément le signal carré généré pour chaque manipulation.
* **Simulation de LED Dimmable :** L'intensité lumineuse (calculée via l'opacité et un effet de lueur CSS) varie proportionnellement au rapport cyclique (Duty Cycle).
* **Analyse d'Ingénierie (Post-Lab) :** Réponses détaillées aux 6 questions techniques du TP (Comportement CCR vs ARR, calcul de résolution minimale, impact du Prescaler sur la fréquence visible, rendement PWM vs Potentiomètre, seuil critique de fusion du scintillement, et problématique des fonctions bloquantes comme `HAL_Delay` face aux interruptions temps réel).

## 📋 Manipulations Réalisées (Code C & Simulation)

**Génération PWM sur Timer 3 (Canal 2 / Broche PA5) :**

1. **Manip 1 - Respiration Automatique (Fading) :**
   * *Principe :* Une boucle logicielle incrémente et décrémente automatiquement le registre de comparaison via la macro `__HAL_TIM_SET_COMPARE()`.
   * *Résultat :* La LED s'allume et s'éteint progressivement de manière fluide et autonome.

2. **Manip 2 - Contrôle Manuel (ADC + PWM) :**
   * *Principe :* Intégration des acquis du TP2. Le signal analogique d'un potentiomètre branché sur `PA0` est lu par l'ADC, mis à l'échelle, puis injecté directement dans le registre CCR du Timer.
   * *Résultat :* Contrôle en temps réel et de haute précision de la luminosité de la LED via le potentiomètre.

## 🛠️ Matériel & Outils Requis

* **Carte :** STM32 Nucleo-C031C6 (Matériel physique ou simulation via [Wokwi](https://wokwi.com/stm32)).
* **Composants :** 1x LED (sur PA5), 1x Potentiomètre (sur PA0), fils de connexion.
* **Environnement C :** STM32CubeIDE (Génération de code via CubeMX avec configuration du TIM3 CH2 en mode PWM Generation).
* **Environnement Web :** Navigateur web moderne pour lancer le rapport interactif et les oscilloscopes.

## ⚙️ Instructions d'Exécution

### 1. Visualiser le Jumeau Numérique (Web)
Double-cliquez sur le fichier `compte_rendu_tp4.html`. Naviguez entre les onglets pour observer l'effet de Fading automatique, puis testez le contrôle manuel en ajustant le curseur du potentiomètre virtuel.

### 2. Exécuter le Code C (STM32 / Wokwi)
1. Importez le projet dans STM32CubeIDE ou créez un environnement Wokwi.
2. Assurez-vous que le **TIM3** est activé, avec le Canal 2 configuré en PWM, et que l'**ADC1** est activé sur le Canal 0.
3. Paramétrez le Prescaler (ex: 47 ou 69) et la Counter Period / ARR (ex: 999 ou 499) selon la fréquence cible.
4. Compilez et exécutez pour observer la modulation matérielle.

## 👥 Équipe du Projet

**Année Universitaire :** 2025/2026
* **Binôme :** Dahane Ahmed Lamine & Tabbi Meriem
* **Enseignante Responsable :** Mme. Afaf Saoud
* **Département :** Électronique
