# ⚙️ FMC2E - Industrie 4.0 : Vision Industrielle, Tri Automatique & Machine Learning

Bienvenue sur le dépôt officiel du projet d'intégration technologique développé pour la ligne de production de **FMC2E**. 

Ce projet propose une architecture logicielle moderne et découplée (micro-services) répondant aux exigences de l'Industrie 4.0, notamment pour le contrôle qualité automatisé des cartes électroniques (conformément à la norme **IPC-A-610 classe 3**).

---

## 🏗️ Architecture Globale du Système

Le projet est structuré en trois composants autonomes qui communiquent de manière synchrone et asynchrone :

```text
       [ COCKPIT DECISIONNEL ] (Streamlit)
         /                 \
    (Axe 1 & 2)          (Axe 3)
       /                     \
[Modèle Random Forest]     [API DE VISION] (Flask + OpenCV)
                             ^
                             | (Appel synchrone à 15s)
                           [ORCHESTRATEUR n8n] ---> [ALERTE DISCORD]
