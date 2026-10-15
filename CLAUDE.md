# Tuteur des enfants — instructions pour Claude

Tuteur local pour 5 enfants instruits à la maison. Un parent dépose une matière ; le tuteur en fait des leçons simples et accompagne l'enfant.
Les enfants ne tapent pas encore bien au clavier : tout doit se faire à l'oral, par boutons et par images.
Référence fonctionnelle : section « Tuteur vocal local pour les enfants » du cahier des charges.

## Règles non négociables

1. **Tout reste à la maison.** Aucune donnée d'enfant (profil, voix, réponses, progression) ne quitte la machine. Aucun appel à une API cloud, aucune télémétrie. Les modèles sont téléchargés une fois, puis tout tourne hors ligne.
2. **Le parent valide avant l'enfant.** Aucune leçon générée n'est montrée à un enfant sans avoir été approuvée dans l'espace parent.
3. **Le tuteur reste dans la matière déposée.** Une question hors sujet est notée pour le parent, pas traitée.
4. **Séparation stricte avec la plateforme de cours.** Comptes, données et code séparés de `langues-platform`. Aucune synchronisation par défaut.
5. **Temps limité.** La durée maximale par séance et par jour, par enfant, est réglée par le parent et toujours respectée.

## Deux modes

### Mode lecture (par défaut, fonctionne sans GPU)

- Le LLM ne tourne pas en direct : il génère les leçons à l'avance, en tâche de nuit.
- Format des leçons : une idée par phrase, une dizaine de mots maximum, vocabulaire adapté à l'âge de l'enfant.
- Affichage : une phrase à la fois, en gros caractères.
- Bouton « écouter » : lecture par Piper, avec le mot lu surligné.
- Questions de compréhension à boutons, avec images quand c'est possible.
- Réponse orale optionnelle d'un ou deux mots, reconnue par un petit modèle Whisper.

### Mode conversation (seulement si un GPU est détecté)

- Explication orale, questions orales, réponses libres de l'enfant, correction bienveillante, nouvel essai si besoin.
- Les leçons du mode lecture restent utilisables telles quelles.

Le mode est choisi automatiquement selon le matériel ; le parent peut forcer le mode lecture.

## Stack

- Reconnaissance vocale : faster-whisper (petit modèle en mode lecture)
- LLM : Ollama, modèle choisi selon la machine
- Synthèse vocale : Piper, voix française
- Matière : documents indexés localement (PDF, photos de pages, listes de notions)
- Interface : application web locale, accessible uniquement sur le réseau de la maison, utilisable sur tablette

## Deux interfaces

- **Enfant** : choix du profil par photo et prénom, sans mot de passe ; gros boutons, bouton micro, aucun champ texte obligatoire.
- **Espace parent**, protégé par code : profils (âge, niveau, matières), dépôt de matière, relecture et validation des leçons, réglage du temps, suivi de la progression (leçons faites, réponses justes, notions qui coincent).

L'espace parent suit la même logique d'interface que le CMS de la plateforme de cours, pour que la même personne s'y retrouve sans formation.

## Conventions

- Tout fonctionne sur un PC sans GPU avec 16 Go de RAM.
- Les tâches lourdes (génération des leçons) tournent en file d'attente de nuit, jamais pendant une séance.
- Si les enfants sont en instruction à domicile en Fédération Wallonie-Bruxelles, les leçons s'alignent sur les référentiels officiels, indexés comme matière de référence.
- Textes pour enfants : phrases courtes, ton encourageant, jamais de moquerie ni de comparaison entre enfants.
- Chaque enfant ne voit que son propre historique.
