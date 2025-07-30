# 🎵 🎵 Spotify Data Pipeline avec AWS & Snowflake

## Présentation
Ce projet consiste à implémenter un pipeline ETL intégrant l’API Spotify, AWS et Snowflake.
Le pipeline extrait des données musicales (albums, artistes et songs) via l’API Spotify, les traite à l’aide d’AWS Glue (Spark), puis stocke les données transformées dans Amazon S3. Enfin, ces données sont automatiquement ingérées dans Snowflake pour permettre une analyse structurée et un reporting interactif.

## Architecture
![Architecture Diagram](Diagram.png)

Spotify API → AWS Lambda (Extraction des données) → Amazon S3 (Données brutes) ↑ Amazon CloudWatch (Déclencheur quotidien)

Amazon S3 (Données brutes) → AWS Glue (Transformation des données avec Apache Spark) → Amazon S3 (Données transformées) ↑ Déclencheur S3 (Dépôt d’objet)

Amazon S3 (Données transformées) → Snowpipe → Snowflake (chargement automatique dans les tables) → Power BI (visualisation & reporting)


## Composants clés
### Data Extraction
- **Spotify API :**  Utilisée pour récupérer des données musicales : artistes, albums et songs.
- **AWS Lambda :** Intégration du protocole OAuth 2.0 pour sécuriser l’accès aux endpoints de l’API.
- **Amazon CloudWatch :** Un job CloudWatch lance la fonction Lambda tous les jours pour aller chercher les nouvelles données.

### Data Transformation
- **AWS Glue (Spark) :**
    - 	Nettoie et normalise les fichiers JSON en tables structurées.
    - 	Convertit les données au format CSV pour un stockage optimal.
    - 	Gère l’évolution du schéma et traite les gros volumes de données efficacement.

### Data Loading & Analytics
- **Amazon S3 :** Stocke les données brutes et transformées.
- **Snowpipe (Snowflake) :**
    -  Automatise l'ingestion des données transformées dans les tables Snowflake.
    -  Fournit une exécution de requêtes évolutive et performante.
- **Power BI :** Génère des tableaux de bord interactifs pour l’analyse des tendances musicales.

## Stack techniques

### Langage de programmation :
- **Python** pour les interactions API et les scripts ETL

### Services AWS :
- **AWS Lambda :** pour l’extraction des données et le déclenchement automatique des workflows de transformation.
- **Amazon CloudWatch :** pour planifier et déclencher les fonctions Lambda à intervalles réguliers.
- **AWS Glue (Apache Spark) :** pour le traitement et la structuration de grands volumes de données.
- **Amazon S3 :** pour stocker les données brutes et transformées.
  
### Data Warehouse
- **Snowflake:** entrepôt centralisé avec ingestion automatique via Snowpipe.

### Visualisation & Reporting
- **Power BI:**  pour créer des rapports interactifs et des dashboards exploitables.

## Avantages
- **Automatisation complète :** les processus planifiés assurent des mises à jour continues et sans intervention.
- **Scalabilité et performance :** AWS Glue et Snowflake optimisent le traitement des données à grande échelle.

## Pistes d’amélioration
- Mettre en place du streaming en temps réel pour une ingestion dynamique des données
- Développer des modèles de machine learning pour anticiper les tendances musicales
