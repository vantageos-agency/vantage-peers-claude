---
name: remember-a-decision
description: >
  Record a decision in VantagePeers so that it is not lost. Use this skill
  whenever the user says a decision has been made and should be kept ("remember
  that we decided", "note this decision", "keep a record", "retiens qu'on a
  décidé", "note cette décision", "garde une trace"), in English or in French.
user-invocable: true
---

## English

Keeps a decision in your organisation's shared memory in VantagePeers, worded as
you approved it, so that you, your colleagues and your agents can find it later.

Steps:

1. Write the decision in one or two plain sentences: what was decided, and, if the
   user said so, why, by whom and from when. Start it with "Decision:". Use the
   user's words; add nothing they did not say.
2. Show that wording and ask: "Shall I record it like this?" Adjust it until the
   user says yes. Record nothing without a clear yes.
3. Call `whoami` and read where you are allowed to write (namespaceWritePrefixes).
   If there is exactly one place, use it. If there are several, describe them in
   plain words and ask which one fits. If there is none, you are not allowed to
   record: see rule 2.
4. On yes, call `store_memory` with namespace set to that place, type "project",
   and content set to the approved wording. Do not pass createdBy: a signed-in
   person is recorded under their own account.
5. Confirm in one sentence that the decision is recorded.

Rules:

1. Report only what the tool returned. If the tool did not confirm the memory, it
   was not recorded: say so.
2. A refusal is not a success. If a tool answers with REFUSED, RBAC_DENIED or
   Forbidden, or if you have no place to write, say: "VantagePeers did not let
   you record this decision. Your organisation's VantagePeers administrator can
   grant you this right."
3. Never record a password, a bank detail or any other secret, even if asked.
4. Do not show identifiers or the internal name of the place unless the user asks.
5. If the VantagePeers connector is not connected, say so and point the user to
   Claude's connector settings.

## Français

Conserve une décision dans la mémoire partagée de votre organisation sur
VantagePeers, dans la formulation que vous avez validée, pour que vous, vos
collègues et vos agents puissiez la retrouver plus tard.

Étapes :

1. Rédiger la décision en une ou deux phrases simples : ce qui a été décidé et,
   si l'utilisateur l'a précisé, pourquoi, par qui et à partir de quand. La faire
   commencer par « Décision : ». Reprendre les mots de l'utilisateur ; ne rien
   ajouter qu'il n'ait dit.
2. Montrer cette formulation et demander : « Je l'enregistre ainsi ? » L'ajuster
   jusqu'à ce que l'utilisateur dise oui. Ne rien enregistrer sans un oui clair.
3. Appeler `whoami` et lire où vous avez le droit d'écrire
   (namespaceWritePrefixes). S'il n'y a qu'un seul emplacement, l'utiliser. S'il
   y en a plusieurs, les décrire simplement et demander lequel convient. S'il n'y
   en a aucun, vous n'avez pas le droit d'enregistrer : voir la règle 2.
4. Sur un oui, appeler `store_memory` avec namespace égal à cet emplacement, type
   « project », et content égal à la formulation validée. Ne pas passer
   createdBy : une personne connectée est enregistrée sous son propre compte.
5. Confirmer en une phrase que la décision est enregistrée.

Règles :

1. Ne rapporter que ce que l'outil a renvoyé. Si l'outil n'a pas confirmé
   l'enregistrement, la décision n'est pas enregistrée : le dire.
2. Un refus n'est pas une réussite. Si un outil répond REFUSED, RBAC_DENIED ou
   Forbidden, ou si vous n'avez aucun emplacement où écrire, dire : « VantagePeers
   ne vous a pas autorisé à enregistrer cette décision. L'administrateur
   VantagePeers de votre organisation peut vous donner ce droit. »
3. Ne jamais enregistrer un mot de passe, des coordonnées bancaires ni aucun
   autre secret, même sur demande.
4. Ne pas afficher d'identifiants ni le nom interne de l'emplacement, sauf si
   l'utilisateur le demande.
5. Si le connecteur VantagePeers n'est pas connecté, le dire et renvoyer
   l'utilisateur vers les réglages des connecteurs de Claude.
