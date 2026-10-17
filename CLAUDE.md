# Tuteur des enfants — instructions pour Claude

Tuteur local pour les 5 enfants de Catherine, instruits à la maison. Un parent dépose une matière ; le tuteur en fait des leçons simples et accompagne l'enfant. Les enfants tapent mal au clavier : tout se fait à l'oral, par boutons et par images.

Référence : section « Tuteur vocal local pour les enfants » du cahier des charges (doc partagé). Elle décrit la cible, pas l'existant.

## Repères (au 17/10/2026)

- Aucun code encore : ce dépôt ne contient que ce fichier, le README et le `.gitignore`.
- Ajouter ici les chemins et les commandes **dès qu'ils existent et ont été exécutés**. Ne rien annoncer comme fonctionnel sans l'avoir lancé.
- Stack envisagée, à confirmer au premier code : faster-whisper (reconnaissance vocale), Ollama (modèle de langue), Piper (voix française), application web locale utilisable sur tablette. Ne pas ajouter d'autre fournisseur sans accord de Didier.

## Règles non négociables

- **Tout reste à la maison.** Documents, profils, voix, réponses, inférences et journaux restent sur la machine. Aucun appel à une API cloud, aucune télémétrie, aucune sauvegarde distante, y compris en secours si le modèle local échoue. Les modèles sont téléchargés une fois, puis tout tourne hors ligne.
- **Le parent valide avant l'enfant.** Aucune leçon générée n'est montrée à un enfant sans approbation dans l'espace parent, vérifiée par le code qui sert la leçon (pas seulement masquée dans l'interface).
- **Traçable à la matière.** Chaque leçon renvoie aux passages de la matière déposée dont elle vient. Le tuteur reste dans cette matière : une question hors sujet ou une réponse incertaine est notée pour le parent, pas inventée.
- **Temps limité.** Durée maximale par séance et par jour, par enfant, réglée par le parent et toujours respectée.
- **Chaque enfant ne voit que son historique.** Profils sans mot de passe pour les enfants ; espace parent protégé par code ; application accessible uniquement sur le réseau de la maison.
- **Séparé de la plateforme MotàMot** (dépôt `langues-platform`) : aucun compte, aucune donnée, aucune synchronisation partagés.

## Deux modes

- **Lecture (par défaut, sans GPU)** : leçons générées à l'avance en tâche de nuit ; une idée par phrase, une dizaine de mots, vocabulaire adapté à l'âge ; une phrase à la fois en gros caractères ; bouton « écouter » avec mot lu surligné ; questions à boutons, avec images si possible ; réponse orale optionnelle d'un ou deux mots. Ce mode doit rester utilisable seul, sans le mode conversation.
- **Conversation (seulement si un GPU est détecté)** : explication et questions orales, réponses libres, correction bienveillante. Le parent peut toujours forcer le mode lecture.

## Pédagogie

- Distinguer ce qui est corrigé de façon certaine (réponse à boutons), ce que le modèle suggère, et ce que le parent évalue.
- Progression affichée comme une estimation, avec ce qui la justifie ; jamais présentée comme un niveau officiel.
- En instruction à domicile en Fédération Wallonie-Bruxelles : aligner les leçons sur les référentiels officiels, indexés comme matière de référence.
- Textes pour enfants : phrases courtes, ton encourageant, jamais de moquerie ni de comparaison entre enfants.

## Pièges connus

- Ne promettre ni vitesse ni qualité de voix sans test sur la machine cible. Référence de départ : PC sans GPU, 16 Go de RAM.
- Les tâches lourdes (génération des leçons) tournent en file de nuit, jamais pendant une séance.
- Voix d'enfants : tester la reconnaissance sur de vrais enregistrements de test, jamais sur des enregistrements des enfants versés dans le dépôt.

## Manière de travailler

- Répondre en français, court et concret. Pour un changement important : plan et critères de réussite d'abord.
- Une tranche fonctionnelle à la fois ; pas d'abstraction sans besoin établi ; poser seulement les questions qui changent le résultat.
- Jamais de données réelles des enfants (voix, photos, prénoms, réponses) dans le dépôt, les logs, les captures ou les prompts.
- Lancer réellement les contrôles disponibles ; bug corrigé = test qui le reproduit. Conclure par : livré, contrôles exécutés et résultats, limites ; distinguer « implémenté », « testé localement », « installé à la maison ».
- Une décision qui change passe par Didier : mettre ce fichier à jour au lieu d'empiler une règle contraire.
