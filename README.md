# Penombre pour macOS

Penombre met en valeur la fenêtre sur laquelle vous travaillez : elle pose un voile sous la fenêtre active et assombrit
tout le reste, sur chaque écran. L'app vit dans la barre des menus (petite lune) ; ⌃⌥D active ou coupe le voile. Une fenêtre à barre latérale
regroupe les réglages, les autorisations et les mises à jour.
Le voile ne reçoit aucun clic. Aucun compte, aucune licence, aucune télémétrie.

- **Minuteur** : pause de 15 minutes, 1 heure ou jusqu'à demain 6 h (le voile revient seul) ; séance de concentration de
  25 minutes avec compte à rebours dans la barre des menus.
- **Réglage par app** : plus léger, plus sombre ou pas de voile, app par app.
- **Plusieurs écrans** : le voile se coupe écran par écran.
- **Raccourcis** : ⌃⌥D active ou coupe · ⌃⌥↑ et ⌃⌥↓ intensité · ⌃⌥P pause d'1 heure · ⌃⌥I ignorer l'app.
- **Apparence** : fondu vif, doux ou lent ; pourcentage à côté de la lune ; voile demandé hors partage d'écran.

Ce dépôt ne contient que les versions à installer. Le code source n'est pas public.

## Ce qu'il faut

- un Mac à puce Apple (M1 ou plus récent) ;
- macOS 14 ou plus.

Aucun compte GitHub, aucun outil à installer, aucun mot de passe administrateur.

## Installer

Dans Terminal (Cmd + Espace, « Terminal »), une seule commande, qui installe aussi les mises à jour :

```
curl -fsSL https://raw.githubusercontent.com/LucasHRCHatReply/penombre-releases/main/installer.sh | zsh
```

Le script télécharge la dernière version, vérifie l'empreinte SHA-256 du zip, l'identifiant de l'app et sa signature
(équipe Apple `JT9FY7PP7K`, `codesign --verify --deep --strict`), copie `Penombre.app` dans `~/Applications`, puis ouvre
l'app. Il garde les réglages.

Une autorisation facultative : pour que le voile suive chaque changement de fenêtre dans une même app, Réglages Système ›
Confidentialité et sécurité › Accessibilité › Penombre. Sans elle, le voile suit seulement les changements d'app.

Autre voie : télécharger `Penombre.dmg` dans les [Releases](../../releases/latest), l'ouvrir, glisser Penombre sur
Applications. Le disque est signé, non notarisé : au premier lancement, clic droit sur l'app › Ouvrir.

Au premier lancement, un didacticiel de quatre essais s'ouvre ; il se rouvre depuis le menu de la lune.

## Avertissement : app non validée par Apple

Penombre est signée mais pas « notarisée » : cela demande un compte développeur payant. macOS la juge donc non vérifiée
au premier lancement. Le script retire pour cela le blocage du premier lancement (l'attribut de quarantaine posé par le
téléchargement), seulement sur `Penombre.app`. À ne lancer que si vous faites confiance à l'auteur ; le script se lit en
entier : [installer.sh](installer.sh). Le contrôle d'équipe et d'empreinte protège contre un zip altéré en route, pas
contre quelqu'un qui détiendrait aussi ce dépôt.

## Mettre à jour

Dans l'app : icône du menu › « Mises à jour ». Au démarrage, et au plus une fois par jour, Penombre lit la page publique
des versions de ce dépôt (la seule connexion qu'elle fait) ; la case « Vérifier au démarrage » la coupe, et « Vérifier
maintenant… » interroge à la demande. Quand une version est publiée, Penombre la propose, contrôle l'équipe, la
signature et la version, remplace l'app et se relance ; si cela échoue, l'ancienne version revient. Ou relancer la
commande ci-dessus. Journal : `~/Library/Logs/Penombre-mise-a-jour.log`.

## Désinstaller

Télécharger le zip de la dernière version dans les [Releases](../../releases/latest), le décompresser, puis lancer
`./uninstall.sh` dans le dossier `Penombre-X.Y.Z` : l'app est supprimée, et le script demande avant d'effacer les réglages.
