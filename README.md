# towercraft-updates

Fichiers de mise a jour consommes automatiquement par TowerCraft Launcher (fork de Prism Launcher)
au demarrage : `manifest.json` (nom/taille/SHA-256/URL par fichier) + `mods/`.

`manifest.json` :
```json
{
    "manifestVersion": 1,
    "gameVersion": "26.2",
    "fabricLoaderVersion": "0.19.3",
    "files": [
        { "name": "mods/<fichier>.jar", "size": 0, "sha256": "...", "url": "https://raw.githubusercontent.com/..." }
    ]
}
```

Pour publier une mise a jour : remplace le(s) fichier(s) dans `mods/`, recalcule taille+SHA-256, mets
a jour l'entree correspondante dans `manifest.json`, commit et push. Le launcher compare chaque
fichier local par taille+SHA-256 (pas juste le nom) et supprime automatiquement tout fichier qui
disparait de la liste `files` au prochain lancement.

(L'ancien systeme JavaFX + `publish-tool` qui maintenait ce depot a ete abandonne - voir DECISIONS.md
du depot `towercraft` principal.)
