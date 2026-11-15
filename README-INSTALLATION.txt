LA POPOTE — PACK PWA DE TEST

CONTENU
- index.html : enveloppe PWA qui affiche l'application Apps Script de test.
- manifest.webmanifest, sw.js et icons/ : installation PWA et cache de la coque.
- Apps_Script_Test/Index.html : copie de l'interface V1.15.13 à conserver côté Apps Script.

IMPORTANT : CE PACK EST CONFIGURÉ UNIQUEMENT AVEC LE DÉPLOIEMENT DE TEST FOURNI.
Ne remplacez jamais le Code.gs de production. Ne reliez pas ce pack au tableur de production.

ÉTAPE OBLIGATOIRE AVANT L'HÉBERGEMENT : AUTORISER L'IFRAME DANS LE BACKEND DE TEST
Dans le projet Apps Script de TEST uniquement, ouvrez Code.gs et repérez doGet().
Remplacez uniquement cette fonction par :

function doGet(){
  return HtmlService.createHtmlOutputFromFile("Index")
    .setTitle("La Popote")
    .addMetaTag("viewport", "width=device-width, initial-scale=1")
    .setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}

Enregistrez puis Déployer > Gérer les déploiements > Modifier > Nouvelle version > Déployer.
L'URL utilisée par index.html reste celle du déploiement de test fourni.
Ne modifiez aucune autre fonction du backend.

HÉBERGEMENT
Publiez le CONTENU de ce dossier à la racine d'un dépôt GitHub destiné à GitHub Pages.
La page doit être servie en HTTPS. N'hébergez pas le dossier Apps_Script_Test comme page du site.

TESTS APRÈS PUBLICATION
1. Ouvrir l'adresse GitHub Pages.
2. Vérifier que l'écran La Popote apparaît dans l'iframe.
3. Se connecter avec les accès de test existants.
4. Tester une consommation et vérifier qu'elle est enregistrée uniquement dans le tableur de test.
5. Tester l'installation depuis le navigateur (Ajouter à l'écran d'accueil / Installer l'application).

SÉCURITÉ
Le mode ALLOWALL autorise l'intégration dans une iframe depuis d'autres sites. Ne l'appliquez qu'au projet de TEST. Gardez l'URL de test et les identifiants de test privés pendant les essais. Changez les codes de démonstration avant tout partage plus large.
