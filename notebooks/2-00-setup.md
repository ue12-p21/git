---
jupytext:
  cell_metadata_filter: all,-hidden,-heading_collapsed
  notebook_metadata_filter: all,-language_info,-toc,-jupytext.text_representation.jupytext_version,-jupytext.text_representation.format_version
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Calysto Bash
  language: bash
  name: calysto_bash
nbhosting:
  title: configuration
---

<div class="licence">
<span>Licence CC BY-NC-ND</span>
<div style="display:grid">
    <span>Thierry Parmentelat</span>
    <span>Valérie Roy</span>
</div>
</div>

<img src="media/inria-25-alpha.png" />
<img src="media/ensmp-25-alpha.png" />

+++

# configuration

+++

avant de continuer le cours, faisons le point sur la configuration 

+++

## votre identité

+++

pour pouvoir créer un commit, git a besoin de savoir votre nom et votre adresse de messagerie

```bash
git config --global user.name "Jean Mineur"
git config --global user.email jean.mineur@mines-paristech.fr
```

+++

## l'éditeur

+++

toujours pour commiter, git a besoin de savoir **quel éditeur de code** vous voulez utiliser pour entrer le message qui va avec le commit (sauf si vous utilisez l'option `-m` pour donner le message sur la ligne de commande)

pour utiliser **vs-code**:

```bash
git config --global core.editor "code --wait"
```

**remarque**  
lorsque vous faites par exemple `git commit` et que l'éditeur se lance pour vous laisser entrer le message, il va falloir que vous puissiez dire à un moment "ça y est, j'ai fini de saisir le message, on peut finir le commit"

pour cela, avec le réglage ci-dessus, ce que vous devez faire  
c'est de **fermer l'onglet** qui édite le message  
il ne suffit pas de simplement sauver le fichier (c'est nécessaire bien sûr, mais pas suffisant)  
et dans l'autre sens ce n'est pas non plus la peine de terminer toute votre sessions vs-code (vous pouvez avoir plein d'autres fichiers ouverts à ce moment-là dans vs-code)

+++ {"tags": ["level_intermediate"]}

## la config, comment ça marche ?

+++ {"tags": ["level_intermediate"]}

pour les curieux, il y a deux niveaux de configuration

1. limité au repo courant
1. ou au contraire valable pour tous les repos

il y a une commande `git config` qui permet d'inspecter la configuration  
par défaut on regarde ou change la première famille  
mais avec l'option `--global` on regarde la seconde


+++ {"tags": ["level_intermediate"]}

### lire / vérifier un réglage

+++ {"tags": ["level_intermediate"]}

pour vérifier (lire) la configuration, vous pouvez faire

```bash
# voir toute la config (locale + globale)
git config -l
# du coup pour voir seulement la config globale 
git config -l --global
# ou juste locale
git config -l --local
```

et surtout pour vérifier la valeur d'**un** réglage, par exemple

```bash
git config user.name
```

+++ {"tags": ["level_intermediate"]}

### écrire / changer un réglage

+++ {"tags": ["level_intermediate"]}

eh bien on l'a déjà fait plus haut  
il suffit de décider si on veut ranger le réglage dans la zone locale ou globale  
et se souvenir que la syntaxe c'est `git config param value`

il faut juste comprendre que si vous aviez tapé

```bash
git config --global user.name Jean Mineur  # ne marche pas
```

ça n'aurait pas fonctionné car le shell (bash) ici aurait vu **deux paramètres** différents  
et c'est pourquoi il faut mettre les `"` autour de `Jean Mineur` comme ceci

```
git config --global user.name "Jean Mineur"  # ok maintenant
```

+++ {"tags": ["level_intermediate"]}

### dans quels fichiers

+++ {"tags": ["level_intermediate"]}

enfin si vous êtes vraiment curieux, sachez que les deux familles de config sont rangées dans

* `.gitconfig` - dans votre *home directory* - pour la config globale
* `.git/config` - à la racine du repo - pour la config locale
