# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Présentation du projet

Projet d'analyse de données académique en Python sur les performances de tournois Mario Kart 8. L'analyse est entièrement contenue dans un seul notebook Jupyter : `projet_MK8.ipynb`.

## Lancer l'environnement

```bash
# Activer l'environnement virtuel
source .venv/Scripts/activate   # Windows (bash)

# Lancer Jupyter
jupyter notebook
```

## Structure

- `projet_MK8.ipynb` — notebook principal (35 cellules, tout le code d'analyse)
- `Data/MK8_Dataset.csv` — données source (2 109 lignes, tournois MK8 2021–2025)

## Dataset

| Colonne | Description |
|---------|-------------|
| Challenger | Nom du joueur (Sacha, Lev, Alex, Ilir…) |
| Pts | Points marqués dans la course |
| Elo | Classement Elo |
| Rank | Classement (1–4) |
| Tier | Niveau de compétence (C, B, A, S) |
| Game_phase | Phase du tournoi (1-Early, 2-Middle, 3-Late) |
| Company | Employeur (Trivadis, Accenture, External Company) |
| Year | Année (2021–2025) |

## Architecture du notebook

**Partie 1 – Inférence statistique**
- Q1 : t-test uniéchantillon (moyenne des scores ≠ 30 ?)
- Q2 : t-test biéchantillon (Sacha vs Lev)
- Q3 : Chi-carré (distribution Company × Tier)
- Q4 : Régression linéaire simple (Pts → Elo)

**Partie 2 – Data Mining**
- Q1 : Régression multiple (Elo ~ Pts + Year + Company)
- Q2 : Arbre de décision (prédire Tier depuis Elo, Company, Game_phase)

## Dépendances principales

pandas, numpy, scipy, statsmodels, scikit-learn, matplotlib, seaborn — toutes installées dans `.venv`.
