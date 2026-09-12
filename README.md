# 👥 Dashboard RH  

> *Un tableau de bord Tableau permettant au Manager RH d'analyser les effectifs, la diversité, les corrélations de performance et les disparités salariales d'une entreprise fictive basée en Côte d'Ivoire.*

---

## ⚙️ Type de projet

- [x] Exploratory Data Analysis (EDA)
- [x] Dashboard / Visualisation de données
- [x] Nettoyage / Préparation de données

---

## Table des matières
1. [Vue d'ensemble du projet](#1-vue-densemble-du-projet)
2. [Besoin métier & User Stories](#2-besoin-métier--user-stories)
3. [Objectifs](#3-objectifs)
4. [Périmètre & Outils](#4-périmètre--outils)
5. [Structure du repository](#5-structure-du-repository)
6. [Flux de données](#6-flux-de-données)
7. [Préparation des données](#7-préparation-des-données)
8. [Structure du jeu de données](#8-structure-du-jeu-de-données)
9. [Tableau de bord](#9-tableau-de-bord)

---

## 1. Vue d'ensemble du projet

**Contexte :** La demande métier de ce projet est de fournir au Manager RH une visibilité globale et détaillée sur les données RH — effectifs, diversité, performance et rémunération — jusqu'ici dispersées sans vue d'ensemble consolidée.

**Problème :** Impossible de répondre rapidement à des questions stratégiques comme : combien d'employés actifs, quelle est la répartition démographique, existe-t-il des disparités salariales entre genres ou niveaux d'études, quelle est la corrélation entre études et performance.

**Approche :** Génération d'un jeu de données RH représentatif, structuration au format CSV, puis construction d'un dashboard Tableau en deux vues — une vue synthétique (Aperçu, Démographie, Revenus) et une vue détaillée (registre des employés filtrable).

**Résultat :** Un dashboard interactif à deux pages permettant de filtrer les données par genre, statut, localisation et date d'embauche, et de croiser effectifs, démographie et rémunération. 


---

## 2. Besoin métier & User Stories

### Vue d'ensemble de la demande

| Élément | Détail |
|---|---|
| **Rapporteur** | Manager RH (HR Manager) |
| **Valeur du changement** | Offrir une visibilité globale et détaillée sur les données RH pour analyser les effectifs, suivre la diversité, évaluer les corrélations de performance et détecter les disparités salariales |
| **Systèmes nécessaires** | Tableau |
| **Autres informations utiles** | Le tableau de bord doit être découpé en une vue synthétique (Aperçu, Démographie, Revenus) et une vue détaillée (Registre des employés) |

### Récits utilisateur (User Stories)

| N° | En tant que | Je souhaite | Afin que | Critères d'acceptation |
|---|---|---|---|---|
| 1 | Manager RH | Un aperçu général des effectifs (embauches, actifs, résiliations, répartition par département/poste, comparaison siège/filiales, répartition géographique) | Avoir une vue stratégique instantanée de la structure des effectifs | KPI Embauchés / Actifs / Résiliés ; évolution temporelle des embauches et départs ; ventilation par département et poste ; comparaison siège vs filiales ; répartition géographique |
| 2 | Manager RH | Visualiser la démographie des employés (genre, âge, niveau d'études, corrélation études/performance) | Analyser la diversité et la composition des effectifs | Ratio hommes/femmes ; distribution croisée âge × niveau d'études ; total par tranche d'âge ; total par niveau d'études ; corrélation niveau d'études / performance |
| 3 | Manager RH | Analyser les revenus par niveau d'études et par genre, ainsi que la corrélation âge/salaire par département | Détecter d'éventuelles disparités salariales | Comparaison des salaires par niveau d'études et par genre ; corrélation âge/salaire au sein de chaque département |
| 4 | Manager RH | Un registre détaillé et filtrable de tous les employés (nom, département, poste, genre, âge, niveau d'études, salaire) | Effectuer une analyse approfondie au cas par cas | Liste exhaustive des employés ; filtrage dynamique sur n'importe quelle colonne |

---

## 3. Objectifs

- **Objectif principal :** Construire un dashboard Tableau complet offrant une vue synthétique (Aperçu, Démographie, Revenus) et une vue détaillée (registre employés) des données RH.
- **Objectif secondaire 1 :** Générer un jeu de données RH représentatif (effectifs, démographie, performance, rémunération) exploitable pour l'analyse.
- **Objectif secondaire 2 :** Identifier des corrélations et disparités potentielles — salaire vs études/genre, âge vs salaire par département, études vs performance.

---

## 4. Périmètre & Outils

### Périmètre

| Dimension | Détail |
|---|---|
| **Inclus** | Données d'effectifs, démographie, performance et rémunération, à l'échelle employé |
| **Exclu** | Données RH réelles/nominatives d'une entreprise existante — le jeu de données est généré |
| **Période couverte** | Suivi multi-années des embauches et départs |
| **Granularité** | Une ligne par employé |

### Outils utilisés

| Catégorie | Outil(s) |
|---|---|
| Génération / structuration des données | Fichier CSV |
| Visualisation | Tableau Desktop |

---

## 5. Structure du repository

```
dashboard-rh-tableau/
│
├── data/
│   └── hr_employees.csv        # Jeu de données RH généré
│
├── visuels/
│   └── images/
│       ├── dashboard_overview.png
│       └── dashboard_details.png
│       
└── README.md

```

---

## 6. Flux de données

```
Génération du jeu de données RH (CSV)
      ↓
Import direct dans Tableau Desktop
      ↓
Champs calculés (tranches d'âge, ancienneté, ratios) dans Tableau
      ↓
Construction des vues (Aperçu, Démographie, Revenus, Registre détaillé)
      ↓
Dashboard interactif (filtres genre, statut, localisation, date d'embauche)
```

1. **Source :** Jeu de données RH généré et structuré au format CSV, représentatif d'une entreprise fictive basée en Côte d'Ivoire.
2. **Ingestion :** Import direct du fichier CSV dans Tableau Desktop
3. **Transformation :** Création de champs calculés directement dans Tableau (tranches d'âge, ancienneté, ratios de genre) pour les besoins des visuels.
4. **Analyse :** Construction des 4 blocs fonctionnels (Aperçu, Démographie, Revenus, Registre détaillé) répondant chacun à une user story.
5. **Sortie :** Dashboard Tableau à deux pages, avec filtres interactifs globaux.

---

## 7. Préparation des données

Les données de ce projet ont été **générées directement dans la structure finale nécessaire à l'analyse**, puis enregistrées en CSV et importées telles quelles dans Tableau Desktop.

Les seules transformations effectuées l'ont été via des **champs calculés Tableau**, pour dériver les catégories utilisées dans les visuels à partir des colonnes brutes.

### Exemples de champs calculés

```
// Tranche d'âge
IF [Age] < 25 THEN "<25"
ELSEIF [Age] >= 25 AND [Age] <= 34 THEN "25-34"
ELSEIF [Age] >= 35 AND [Age] <= 44 THEN "35-44"
ELSEIF [Age] >= 45 AND [Age] <= 54 THEN "45-54"
ELSE "55+"
END
```

```
// Ancienneté (en années, à partir de la date d'embauche)
DATEDIFF('year', [Date d'embauche], TODAY())
```

---

## 8. Structure du jeu de données

### Table : `hr_employees`

| Champ | Type | Description | Exemple |
|---|---|---|---|
| `EmployeeID` | string | Identifiant unique de l'employé | `CI-10008169` |
| `Nom` | string | Nom complet de l'employé | `Arnaud KOUASSI` |
| `Genre` | string | Genre de l'employé | `Masculin` |
| `Age` | int | Âge de l'employé | `45` |
| `Departement` | string | Département de rattachement | `Opérations & Logistique` |
| `Poste` | string | Intitulé du poste | `Gestionnaire de Stock` |
| `Ville` | string | Ville de travail | `Abidjan - Cocody` |
| `Region` | string | Région / District | `District d'Abidjan` |
| `Site` | string | Siège social ou filiale | `Siège` |
| `NiveauEtude` | string | Niveau d'études | `BAC`, `BTS`, `L`, `M`, `D` |
| `Performance` | string | Évaluation de performance | `Excellent`, `Bon`, `Satisfaisant`, `À améliorer` |
| `Salaire` | decimal | Salaire (FCFA) | `395000` |
| `Statut` | string | Statut d'emploi | `Embauché`, `Résilié` |
| `DateEmbauche` | date | Date d'embauche | `03/01/2025` |
| `Anciennete` | int | Ancienneté en années (champ calculé) | `1` |

> **Nombre de lignes (approx.) :** ~8 950 employés (embauchés cumulés)
> **Répartition Siège / Filiale :** 70% / 30%

---

## 9. Tableau de bord

Le dashboard final comporte deux pages : une **Vue d'ensemble** (Aperçu général, Démographie, Revenus) et une page **Détails** listant l'ensemble des employés avec filtrage dynamique.

### Vue d'ensemble

Effectifs clés : 8 950 employés embauchés au total, 7 999 actifs, 951 résiliations. Répartition par département (Opérations & Logistique en tête avec 2 371 employés), comparaison Siège/Filiale (70%/30%), répartition géographique par ville et région.

Démographie : ratio de genre 59% masculin / 41% féminin, distribution par tranche d'âge et niveau d'études, corrélation niveau d'études / performance.

Revenus : comparaison des salaires par niveau d'études et par genre, corrélation âge / salaire par poste et département.

![Vue d'ensemble du dashboard](docs/images/dashboard_overview.png)

### Détails — Registre des employés

Liste exhaustive et filtrable par ID, données démographiques, fonction, localisation, salaire, statut et ancienneté.

![Détails du registre des employés](docs/images/dashboard_details.png)
