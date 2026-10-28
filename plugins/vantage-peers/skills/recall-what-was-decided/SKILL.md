---
name: recall-what-was-decided
description: >
  Find what was decided or recorded in VantagePeers on a subject. Use this skill
  whenever the user asks about a past decision or what is already known ("what did
  we decide about", "do we have anything on", "remind me", "qu'avait-on décidé
  pour", "qu'est-ce qu'on sait sur", "rappelle-moi"), in English or in French.
user-invocable: true
---

## English

Searches your organisation's shared memory in VantagePeers and tells you, in plain
words, what was decided or recorded on a subject, and when.

Steps:

1. Turn the question into a short search phrase (the subject, in the user's
   words).
2. Call `whoami` and read where you are allowed to read (namespaceReadPrefixes).
   If there is none, you are not allowed to search: see rule 3.
3. For each of those places (at most five), call `recall` with query set to the
   search phrase, namespace set to the place, and limit 5. If nothing relevant
   comes back, try once with `hybrid_search` and the same arguments, which also
   matches exact words.
4. Answer in a few sentences: what was decided, and when it was recorded. Put the
   most recent first. If two results say different things, show both with their
   dates rather than choosing. Quote the recorded wording when it matters.
5. If nothing matches, say: "I found nothing recorded on this subject." and offer
   to search with other words.

Rules:

1. Report only what a tool returned. Never fill a gap with a guess or general
   knowledge, and say clearly when an answer comes from VantagePeers.
2. An answer that the tool returned without error and without results means
   nothing was found: say so plainly.
3. A refusal is not an absence. If a tool answers with REFUSED, RBAC_DENIED or
   Forbidden, say: "VantagePeers did not let you search there. That does not mean
   nothing was recorded. Your organisation's VantagePeers administrator can grant
   you access." Never present a refusal as "nothing found".
4. If the user asks to record something rather than find it, use the
   remember-a-decision skill instead.
5. Do not show identifiers, internal names or technical fields unless the user
   asks for them.
6. If the VantagePeers connector is not connected, say so and point the user to
   Claude's connector settings.

## Français

Cherche dans la mémoire partagée de votre organisation sur VantagePeers et vous
dit, simplement, ce qui a été décidé ou noté sur un sujet, et quand.

Étapes :

1. Transformer la question en une courte expression de recherche (le sujet, avec
   les mots de l'utilisateur).
2. Appeler `whoami` et lire où vous avez le droit de lire (namespaceReadPrefixes).
   S'il n'y en a aucun, vous n'avez pas le droit de chercher : voir la règle 3.
3. Pour chacun de ces emplacements (cinq au plus), appeler `recall` avec query
   égal à l'expression de recherche, namespace égal à l'emplacement, et limit 5.
   Si rien de pertinent ne revient, essayer une fois `hybrid_search` avec les
   mêmes arguments, qui retrouve aussi les mots exacts.
4. Répondre en quelques phrases : ce qui a été décidé, et quand cela a été noté.
   Le plus récent d'abord. Si deux résultats se contredisent, présenter les deux
   avec leur date plutôt que de trancher. Citer la formulation enregistrée quand
   elle compte.
5. Si rien ne correspond, dire : « Je n'ai rien trouvé d'enregistré sur ce
   sujet. » et proposer de chercher avec d'autres mots.

Règles :

1. Ne rapporter que ce qu'un outil a renvoyé. Ne jamais combler un manque par une
   supposition ou des connaissances générales, et dire clairement quand une
   réponse vient de VantagePeers.
2. Une réponse renvoyée sans erreur et sans résultat signifie que rien n'a été
   trouvé : le dire simplement.
3. Un refus n'est pas une absence. Si un outil répond REFUSED, RBAC_DENIED ou
   Forbidden, dire : « VantagePeers ne vous a pas autorisé à chercher à cet
   endroit. Cela ne veut pas dire que rien n'a été noté. L'administrateur
   VantagePeers de votre organisation peut vous en donner l'accès. » Ne jamais
   présenter un refus comme « rien trouvé ».
4. Si l'utilisateur veut enregistrer quelque chose plutôt que le retrouver,
   utiliser plutôt la compétence remember-a-decision.
5. Ne pas afficher d'identifiants, de noms internes ni de champs techniques, sauf
   si l'utilisateur le demande.
6. Si le connecteur VantagePeers n'est pas connecté, le dire et renvoyer
   l'utilisateur vers les réglages des connecteurs de Claude.
