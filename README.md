# Calculateur d'Intérêts Composés

Un outil interactif pour visualiser la puissance des intérêts composés, avec support des versements récurrents et plusieurs devises. 100% statique — aucun serveur, aucune dépendance à installer.

---

## Aperçu

![Thème Vert Forêt · Style Finance](https://img.shields.io/badge/Thème-Vert%20Forêt-1a4d3e?style=flat-square) ![Statique](https://img.shields.io/badge/Type-HTML%20statique-00A878?style=flat-square) ![Licence](https://img.shields.io/badge/Licence-MIT-gray?style=flat-square)

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
git clone https://github.com/primo25ai/int-composes-cap-variable-blk.git

# Ouvrir directement
open index.html
# ou double-cliquer sur le fichier
```

### Déployer en ligne (GitHub Pages)

1. Fork ou crée un dépôt contenant `index.html`
2. Va dans **Settings → Pages**
3. Source : `Deploy from a branch` → branche `main` → dossier `/`
4. Ton URL sera : `https://primo25ai.github.io/int-composes-cap-variable-blk`

---

## Paramètres disponibles

| Paramètre             | Plage        | Description                                 |
| --------------------- | ------------ | ------------------------------------------- |
| Capital initial       | 0 – 100 000  | Montant placé au départ                     |
| Taux annuel           | 0,5 % – 25 % | Taux d'intérêt annuel brut (pas de 0,25 %)  |
| Durée                 | 1 – 50 ans   | Horizon de placement                        |
| Versement mensuel     | 0 – 5 000    | Montant ajouté chaque mois                  |
| Versement trimestriel | 0 – 10 000   | Montant ajouté chaque trimestre             |
| Versement annuel      | 0 – 20 000   | Montant ajouté chaque année                 |

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
- **Google Fonts** — DM Serif Display, Instrument Sans, DM Mono
- Fonctionne hors ligne après le premier chargement des polices

---

## Structure du projet

```text
/
├── index.html     # Application complète (fichier unique)
└── README.md      # Ce fichier
```

---

## Sécurité

Application 100 % statique côté client : aucune donnée collectée, aucun backend, aucune persistance.

- **SRI** — Chart.js est chargé depuis le CDN avec un hash `integrity` (Subresource Integrity) : toute altération du fichier distant est rejetée par le navigateur.
- **Content-Security-Policy** — une CSP est appliquée via balise `<meta>` : scripts limités à l'origine + cdnjs, le script inline étant autorisé par son hash SHA-256. Toute modification du bloc `<script>` impose de recalculer ce hash (`openssl dgst -sha256 -binary | openssl base64 -A`), sinon le navigateur le bloque.
- **Pas d'entrée texte utilisateur** — toutes les valeurs proviennent de curseurs/boutons numériques ; aucun puits dangereux (`eval`, `innerHTML` avec données externes, etc.).

### En-têtes recommandés au déploiement

`frame-ancestors` et `X-Content-Type-Options` ne sont pas applicables via `<meta>`. Si vous déployez derrière un serveur configurable (note : GitHub Pages ne permet pas d'en-têtes personnalisés), ajoutez :

```text
X-Content-Type-Options: nosniff
Content-Security-Policy: frame-ancestors 'none'   # anti-clickjacking
Referrer-Policy: strict-origin-when-cross-origin
Strict-Transport-Security: max-age=31536000; includeSubDomains
```

---

## Licence

MIT — libre d'utilisation, de modification et de distribution.
