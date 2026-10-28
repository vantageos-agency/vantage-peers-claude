---
name: my-tasks
description: >
  List my open tasks and my agent's open tasks in VantagePeers. Use this skill
  whenever the user asks what is on their plate, what their agent is working on,
  or what is still open ("my tasks", "what's pending", "mes tâches", "où en est
  mon agent", "qu'est-ce qui reste à faire"), in English or in French.
user-invocable: true
---

## English

Shows the open tasks you can see in VantagePeers: yours, and your agent's. You do
not need to know any identifier: Claude finds out who you are and who your agent
is through the VantagePeers connector.

Steps:

1. Call `whoami`. If it names an acting agent, that is your agent.
2. Call `list_peers` to read your organisation's agents by name. If `whoami` named
   no agent, and the list holds exactly one agent, that one is your agent. If it
   holds several, show their names and ask which one is yours. Never ask the user
   to type an identifier.
3. Call `list_tasks` with status "open" to read the open tasks you can see. Then
   call it again with status "open" and assignedTo set to your agent's name, to
   be sure none of your agent's tasks is missing.
4. Show two short lists: "Assigned to your agent" and "Other open tasks". For each
   task: its title, its priority, its status, and its due date if it has one.
   Newest first. If there are more than about ten, show ten and offer the rest.

Rules:

1. Report only what a tool returned. Never invent a task, a status or a date.
2. An empty list that the tool returned without error means there is nothing
   open: say so plainly.
3. A refusal is not an empty list. If a tool answers with REFUSED, RBAC_DENIED or
   Forbidden, say: "VantagePeers did not let you see these tasks. That does not
   mean there are none. Your organisation's VantagePeers administrator can grant
   you access." Never present a refusal as "no tasks".
4. Do not show identifiers, internal names or technical fields unless the user
   asks for them. Speak of tasks by their title.
5. If the VantagePeers connector is not connected, say so and point the user to
   Claude's connector settings.

## Français

Affiche les tâches ouvertes que vous pouvez voir dans VantagePeers : les vôtres
et celles de votre agent. Vous n'avez besoin d'aucun identifiant : Claude
retrouve qui vous êtes et qui est votre agent grâce au connecteur VantagePeers.

Étapes :

1. Appeler `whoami`. S'il indique un agent qui agit pour vous, c'est votre agent.
2. Appeler `list_peers` pour lire les agents de votre organisation, par leur nom.
   Si `whoami` n'a indiqué aucun agent et que la liste n'en compte qu'un, c'est
   le vôtre. S'il y en a plusieurs, présenter leurs noms et demander lequel est
   le vôtre. Ne jamais demander à l'utilisateur de saisir un identifiant.
3. Appeler `list_tasks` avec le statut « open » pour lire les tâches ouvertes
   que vous pouvez voir. Puis l'appeler une seconde fois avec le statut « open »
   et assignedTo égal au nom de votre agent, pour ne manquer aucune de ses tâches.
4. Présenter deux listes courtes : « Confiées à votre agent » et « Autres tâches
   ouvertes ». Pour chaque tâche : son titre, sa priorité, son statut et son
   échéance si elle en a une. Les plus récentes d'abord. Au-delà d'une dizaine,
   en montrer dix et proposer la suite.

Règles :

1. Ne rapporter que ce qu'un outil a renvoyé. Ne jamais inventer une tâche, un
   statut ou une date.
2. Une liste vide renvoyée sans erreur signifie qu'il n'y a rien d'ouvert : le
   dire simplement.
3. Un refus n'est pas une liste vide. Si un outil répond REFUSED, RBAC_DENIED ou
   Forbidden, dire : « VantagePeers ne vous a pas autorisé à voir ces tâches.
   Cela ne veut pas dire qu'il n'y en a aucune. L'administrateur VantagePeers de
   votre organisation peut vous en donner l'accès. » Ne jamais présenter un refus
   comme « aucune tâche ».
4. Ne pas afficher d'identifiants, de noms internes ni de champs techniques, sauf
   si l'utilisateur le demande. Désigner les tâches par leur titre.
5. Si le connecteur VantagePeers n'est pas connecté, le dire et renvoyer
   l'utilisateur vers les réglages des connecteurs de Claude.
