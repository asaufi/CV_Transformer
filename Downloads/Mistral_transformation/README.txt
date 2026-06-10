CV Transformer MCE - Application Web
====================================

Application principale
----------------------

Ouvrir directement ce fichier dans Chrome ou Edge :

    index.html

Il n'y a pas de serveur, pas de npm, pas de Python, pas d'installation.
Tout est dans un seul fichier HTML : interface, CSS, JavaScript, logique IA et
génération du fichier Word.


Mode IA
-------

L'application propose 3 modes :

1. Auto : essaie d'abord l'IA locale Chrome, puis Gemini API si nécessaire.
2. IA locale Chrome uniquement : aucune clé API, données traitées localement.
3. Gemini API uniquement : utilise la clé API Gemini.

Le mode recommandé est :

    Auto : IA locale puis Gemini


Sans clé API
------------

C'est possible uniquement si Chrome expose l'IA locale intégrée
via LanguageModel / Gemini Nano.

Dans ce cas :

- pas de clé API
- pas d'abonnement
- traitement local dans Chrome
- fonctionne surtout pour les CV .docx

La disponibilité dépend du poste, de la version Chrome, de la région et des
paramètres Chrome. Utiliser le bouton "Tester IA locale" dans l'application.


Avec clé API Gemini
-------------------

La clé reste utile comme fallback :

- si l'IA locale Chrome n'est pas disponible
- si le CV est un PDF
- si le résultat local est insuffisant

Créer une clé gratuite ici :

    https://aistudio.google.com/app/apikey

La clé est sauvegardée uniquement dans le navigateur de l'utilisateur via
localStorage. Elle n'est pas écrite dans un fichier.


Ce que fait l'application
-------------------------

- Upload d'un CV .docx ou .pdf
- Analyse IA du CV
- Neutralisation du nom : Prénom N.
- Restructuration au format MCE
- Prévisualisation du CV transformé
- Téléchargement d'un fichier Word .docx


Formats supportés
-----------------

- .docx : extraction du texte directement dans le navigateur
- .pdf  : traité via Gemini API uniquement

Les anciens fichiers .doc ne sont pas supportés par cette version 100% HTML.
Convertissez-les d'abord en .docx.


Utilisation
-----------

1. Ouvrir index.html.
2. Garder le mode "Auto : IA locale puis Gemini".
3. Cliquer sur "Tester IA locale".
4. Déposer ou sélectionner un CV .docx ou .pdf.
5. Si l'IA locale est indisponible ou si le fichier est un PDF, coller une clé API Gemini.
6. Cliquer sur Transformer.
7. Vérifier la prévisualisation.
8. Télécharger le Word.
9. Valider le Word puis exporter en PDF depuis Word si besoin.


Limite PDF
----------

Une app HTML seule ne peut pas extraire proprement le texte d'un PDF sans grosse
bibliothèque intégrée. Pour garder un seul fichier léger, les PDF passent par
Gemini API. Pour un usage sans clé, convertir le PDF en DOCX avant traitement.


Confidentialité
---------------

En IA locale Chrome, les données restent dans le navigateur.
En Gemini API, le CV est envoyé à Google Gemini pour analyse.
