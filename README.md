# projet-ETL
# 📊 Projet ETL - Nettoyage et Transformation de Données de Ventes

## 👥 Réalisé par
- BACHIRI Imane
- BOUAYAD Zineb

## 📁 Structure du projet

```
/projet_etl/
│
├── data/
│   ├── jeu_donnees_etl_5000_lignes.csv       # Données originales
│   └── donnees_nettoyees.csv                 # Données nettoyées et transformées
│
├── docs/
│   └── rapport.md                            # Compte rendu détaillé du projet
│
├── logs/
│   └── etl_process.log                       # Fichier de log des erreurs et opérations
│
├── scripts/
│   ├── etl.py                                # Script principal de nettoyage et transformation
│   └── test_etl.py                           # Tests unitaires
│
└── README.md                                 # Ce fichier
```

## 🎯 Objectif

Mettre en œuvre un processus ETL robuste pour nettoyer, enrichir et transformer un fichier de ventes incomplètes avant son intégration dans un entrepôt de données.

## 🔍 Problèmes détectés

- **Valeurs manquantes** : dans les colonnes `Nom_produit`, `Quantite_vendue`, `Prix_unitaire`
- **Valeurs aberrantes** : quantités à zéro, prix irréalistes
- **Dates invalides** : formats incohérents, dates futures
- **Doublons** : lignes dupliquées
- **Incohérences** : formats de texte, casse, orthographes variables

## 🔧 Transformations appliquées

- Suppression des doublons
- Remplacement des valeurs manquantes :
  - `Nom_produit` → "Inconnu"
  - `Quantite_vendue` et `Prix_unitaire` → médiane par catégorie
- Normalisation des dates
- Détection et correction des valeurs aberrantes (méthode IQR)
- Ajout de colonnes dérivées :
  - `Montant_total = Quantite × Prix`
  - `Mois_vente` (extraction du mois)
- Normalisation Min-Max sur les variables numériques

## 🛡️ Gestion des erreurs

- Blocs `try-except`
- Logging dans `etl_process.log`
- Assertions pour valider les contraintes

## ✅ Résultat

Les données finales sont propres, enrichies, cohérentes et prêtes pour l'analyse.

## ▶️ Exécution du script

```bash
cd scripts/
python etl.py
```

Les fichiers nettoyés seront sauvegardés dans `data/` et les logs dans `logs/`.

## 📦 Prérequis

- Python 3.x
- Bibliothèques : `pandas`, `numpy`, `logging`, `sklearn` (optionnel pour la normalisation)

## 📚 Documentation

Voir le fichier `docs/rapport.md` ou `docs/Compte_rendu_ETL.docx`.
