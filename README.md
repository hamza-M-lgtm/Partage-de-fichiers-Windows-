# Partage de fichiers (Windows)


# Configuration d'un serveur de fichiers sur Windows Server 2022

## 1. Installation du rôle Serveur de fichiers
1. Ouvrez le Gestionnaire de serveur.
2. Cliquez sur "Ajouter des rôles et des fonctionnalités".
3. Sélectionnez "Installation basée sur un rôle ou une fonctionnalité" et cliquez sur "Suivant".
4. Sélectionnez le serveur et cliquez sur "Suivant".
5. Cochez la case "Serveur de fichiers et services de stockage" et cliquez sur "Suivant".
6. Cochez la case "Serveur de fichiers" et cliquez sur "Suivant".
7. Cliquez sur "Installer" et attendez la fin de l'installation.
   ![Image](https://github.com/user-attachments/assets/1f56e272-c8b6-4cf5-8477-772f079ffc87)

## 2. Création du dossier "Documents_Entreprise"
1. Ouvrez l'Explorateur de fichiers.
2. Accédez à la racine du disque C:.
3. Créez un nouveau dossier nommé "Documents_Entreprise".
4. ![Image](https://github.com/user-attachments/assets/1eee4f4e-5f53-451e-a9e0-32d9067b0097)

## 3. Configuration du partage "Docs"
1. Faites un clic droit sur le dossier "Documents_Entreprise" et sélectionnez "Propriétés".
2. Allez dans l'onglet "Partage" et cliquez sur "Partager".
3. Dans le menu déroulant, sélectionnez "Tout le monde" et définissez les permissions sur "Lecture".
4. Cliquez sur "Partager" puis sur "Terminer".
5. Cliquez sur "Partage avancé" dans l'onglet "Partage".
6. Cochez la case "Partager ce dossier" et nommez le partage "Docs".
7. Cliquez sur "Autorisations" et configurez les permissions de partage :
    - Ajoutez le groupe "Direction" avec les permissions "Contrôle total".
    - Ajoutez le groupe "RH" avec les permissions "Lecture/Écriture".
    - Ajoutez le groupe "Comptabilité" avec les permissions "Lecture/Écriture".
    - Cliquez sur "OK" et sur "Appliquer".

## 4. Création des sous-dossiers
1. Dans le dossier "Documents_Entreprise", créez trois sous-dossiers nommés "RH", "Comptabilité" et "Direction".

## 5. Configuration des permissions NTFS
1. Faites un clic droit sur le dossier "RH" et sélectionnez "Propriétés".
2. Allez dans l'onglet "Sécurité" et cliquez sur "Modifier".
3. Ajoutez le groupe "RH" avec les permissions "Lecture/Écriture".
4. ![Image](https://github.com/user-attachments/assets/e5e72c22-3de8-4be7-bd2d-a3e2dbb703a7)
5. Répétez les étapes ci-dessus pour le dossier "Comptabilité" avec le groupe "Comptabilité".
6. ![Image](https://github.com/user-attachments/assets/40fca992-3703-4da6-b7c6-1ee95fc93175)
7. Pour le dossier "Direction", ajoutez le groupe "Direction" avec les permissions "Lecture/Écriture".
8. Pour le dossier "Documents_Entreprise", ajoutez "Tout le monde" avec les permissions "Lecture seule".

## 6. Liste des partages avec PowerShell

**Get-SmbShare**
![Image](https://github.com/user-attachments/assets/75aa8ab8-d088-40de-b82b-d4a833e86b8e)


## 7. Sur un poste client Windows 10, configure un lecteur réseau pointant vers ce partage via PowerShell

```powershell
New-PSDrive -Name "Z" -PSProvider FileSystem -Root "\\nom_serveur\Documents_Entreprise" -Persist

```


## 8. Teste 

Vérifier  l'accès depuis le poste client avec différents comptes utilisateurs bour voir si les autorisations fonctionnent 





