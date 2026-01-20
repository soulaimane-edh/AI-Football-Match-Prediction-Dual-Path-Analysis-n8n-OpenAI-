# AI Football Match Result Prediction (Dual-Path Analysis)
<img width="1534" height="548" alt="image" src="https://github.com/user-attachments/assets/fb7ff7de-5ede-4485-bfc9-d4735209b7a0" />


Ce projet est un système intelligent de prédiction de résultats de football pour la Premier League. Il utilise une architecture hybride unique via n8n pour comparer deux types d'analyses : l'intelligence artificielle générative (OpenAI) et l'analyse statistique historique (Données CSV).

 Aperçu du Projet
Contrairement aux prédicteurs classiques, ce système suit deux trajets distincts pour chaque match :

Trajet IA Générale : Utilise les connaissances internes de GPT-4o-mini sur le football mondial.

Trajet Data CSV : Analyse un dataset de 25 ans d'histoire de la Premier League (epl_final.csv) pour extraire des tendances réelles basées sur les confrontations passées.

Le tout est orchestré par n8n et intégré directement dans un site WordPress.

🛠️ Technologies Utilisées
n8n : Plateforme d'automatisation low-code pour orchestrer le workflow.

OpenAI (GPT-4o-mini) : Modèle de langage pour l'analyse prédictive.

Google Sheets : Base de données intermédiaire pour l'historique des matchs.

WordPress : Interface utilisateur (Frontend) via Webhooks et Shortcodes PHP.

CSV : Dataset contenant les statistiques de la PL de 2000 à 2025.

📋 Architecture du Workflow n8n
Le workflow se compose des étapes suivantes :

Webhook WordPress : Réception des noms des deux équipes (Team 1 vs Team 2).

Branche A (IA seule) : L'agent IA génère un pronostic basé sur ses connaissances.

Branche B (Data Historique) :

Lecture du fichier Google Sheets.

Filtrage automatique des matchs impliquant uniquement les deux équipes saisies.

Agrégation des scores passés (Buts domicile/extérieur).

Analyse de ces données par un second agent IA.

Fusion (Merge) : Combinaison des deux analyses en une seule réponse structurée.

Réponse Finale : Envoi du résultat consolidé vers WordPress.

💻 Installation
1. Configuration n8n
Importez le fichier workflow.json (fourni dans ce repo) dans votre instance n8n.

Connectez vos credentials OpenAI API et Google Sheets API.

Remplacez l'ID de la Spreadsheet dans le nœud "Lire Stats".

2. Intégration WordPress
Ajoutez le code PHP (fourni dans le dossier integration) dans votre fichier functions.php.

Remplacez VOTRE_URL_PRODUCTION_N8N par votre URL de webhook de production.

Utilisez le shortcode [match_predictor] sur n'importe quelle page de votre site.

📊 Dataset (epl_final.csv)
Le système s'appuie sur une base de données exhaustive comprenant :

Période : Saisons 2000/01 à 2024/25.

Colonnes Clés : MatchDate, HomeTeam, AwayTeam, FullTimeHomeGoals, FullTimeAwayGoals, Shots, Corners, etc.

🌟 Exemple de Résultat
Une fois le formulaire validé, l'utilisateur reçoit :

🔵 ANALYSE IA GÉNÉRALE : Basé sur la forme actuelle, Arsenal a 65% de chances de gagner contre Chelsea...

🟢 ANALYSE DATA CSV (2000-2025) : Historiquement, sur les 20 dernières confrontations, l'équipe à domicile a gagné 50% du temps avec une moyenne de 1.8 buts...
