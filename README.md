# Calculateur d'Intérêts Composés

Un outil interactif pour visualiser la puissance des intérêts composés, avec support des versements récurrents et plusieurs devises. 100% statique — aucun serveur, aucune dépendance à installer.

---

## Aperçu

![Thème Océan Bleu · Style Finance](https://img.shields.io/badge/Thème-Océan%20Bleu-0057B8?style=flat-square) ![Statique](https://img.shields.io/badge/Type-HTML%20statique-00A878?style=flat-square) ![Licence](https://img.shields.io/badge/Licence-MIT-gray?style=flat-square)

---

## Fonctionnalités

- **Calcul en temps réel** — résultats mis à jour instantanément à chaque glissement de curseur
- **Versements récurrents** — simulation avec dépôts mensuels, trimestriels ou annuels
- **Moment du versement** — choix entre début ou fin de période (annuité immédiate vs à terme)
- **3 devises** — Euro (€), Dollar ($), Franc Pacifique (XPF)
- **Graphique en barres empilées** — décomposition visuelle entre capital initial, versements cumulés et intérêts
- **Tableau de détail annuel** — vue chiffrée sur les jalons clés de la simulation
- **Formule dynamique** — affichage de la formule mathématique adaptée au mode actif
- **Mode sombre automatique** — suit les préférences système de l'utilisateur
- **Responsive** — optimisé pour mobile, tablette et desktop

---

## Utilisation

### Ouvrir localement

Aucune installation requise. Télécharge le fichier et ouvre-le dans n'importe quel navigateur :

```bash
# Cloner le dépôt
git clone https://github.com/ton-pseudo/calculateur-interets.git

# Ouvrir directement
open index.html
# ou double-cliquer sur le fichier
```

### Déployer en ligne (GitHub Pages)

1. Fork ou crée un dépôt contenant `index.html`
2. Va dans **Settings → Pages**
3. Source : `Deploy from a branch` → branche `main` → dossier `/`
4. Ton URL sera : `https://ton-pseudo.github.io/nom-du-depot`

---

## Paramètres disponibles

| Paramètre             | Plage       | Description                     |
| --------------------- | ----------- | ------------------------------- |
| Capital initial       | 0 – 100 000 | Montant placé au départ         |
| Taux annuel           | 1 % – 25 %  | Taux d'intérêt annuel brut      |
| Durée                 | 1 – 50 ans  | Horizon de placement            |
| Versement mensuel     | 0 – 5 000   | Montant ajouté chaque mois      |
| Versement trimestriel | 0 – 10 000  | Montant ajouté chaque trimestre |
| Versement annuel      | 0 – 20 000  | Montant ajouté chaque année     |

---

## Formules utilisées

**Sans versements** (capitalisation simple) :

```text
A = P × (1 + r)ⁿ
```

**Avec versements récurrents** (valeur future d'une annuité) :

```text
FV = P × (1 + r/m)^(m×n)  +  d × [((1 + r/m)^(m×n) − 1) ÷ (r/m)]
```

Où `P` = capital initial · `r` = taux annuel · `n` = années · `m` = périodes/an · `d` = versement par période

---

## Technologies

- **HTML5 / CSS3 / JavaScript** — vanilla, zéro framework
- **Chart.js 4.4** — graphiques en barres empilées
- **Google Fonts** — Space Grotesk, Inter, JetBrains Mono
- Fonctionne hors ligne après le premier chargement des polices

---

## Structure du projet

```text
/
├── index.html     # Application complète (fichier unique)
└── README.md      # Ce fichier
```

---

## Licence

MIT — libre d'utilisation, de modification et de distribution.
