# albionsnipe - depot de DISTRIBUTION

Ce depot ne contient pas de code. Il contient les deux zips que les joueurs
telechargent, et c'est tout.

| Fichier | Ce que c'est |
|---|---|
| `AlbionSnipe.zip` | bundle public, version anglaise |
| `AlbionSnipe-FR.zip` | bundle public, version francaise |

## Comment il se remplit

**Jamais a la main.** Les zips sont ecrits par `ship.py`, qui vit dans
`C:\repos\albionsnipe-app`. Son mode d'emploi est dans `albionsnipe-app/SHIP.md`.

```bash
cd C:\repos\albionsnipe-app
python ship.py --release X.Y
```

`--release` exige un numero de version depuis le 01/08 et publie une release NEUVE
(brouillon, verification des tailles, puis bascule). `--reuse-release` ecrase la
precedente, et sert uniquement a reprendre apres un echec.

## Pourquoi ca compte

Le bouton Download du site pointe en dur sur les Releases de CE depot :

```
github.com/AdilOkay/albionsnipe/releases/latest/download/AlbionSnipe.zip
```

Trois consequences a connaitre avant d'y toucher :

1. **Une release cassee casse le telechargement public**, immediatement, sans
   avertissement. Il n'y a pas de version de secours.
2. **Renommer le compte GitHub casse cette URL.** Elle fait partie des liens en dur
   recenses dans le plan de renommage (`00_SYSTEM/DECISIONS.md`, 31/07 et 01/08).
   Tester les redirections avant, pas apres.
3. **Le webhook Discord de ce depot est coupe depuis le 02/08** (hook `658993330`,
   `active=false`). Publier une release ne previent plus personne : l'annonce s'ecrit
   et se poste a la main. La commande pour le rallumer est dans `SHIP.md`.

## Contenu du zip, pour memoire

Le lanceur `AlbionSnipe.exe` EST le `pythonw.exe` signe Python Software Foundation,
copie et renomme. Ce n'est pas un contournement esthetique : Smart App Control bloque
en dur tout `.exe` non signe, ainsi que les `.bat` et `.lnk` telecharges. Un lanceur
compile maison est mort-ne sur Windows 11. Le demarrage passe par `sitecustomize`,
l'icone Python est assumee, et le build verifie par sha256 qu'aucun `.exe` non signe
n'entre dans le zip.

Documentation complete : `albionsnipe-app/SHIP.md` et
`G:\Mon Drive\ADIL_OS_CENTRAL\10_LIVE\CITY_BUY_LIST\CITY_BUY_LIST_STATUS.md`.
