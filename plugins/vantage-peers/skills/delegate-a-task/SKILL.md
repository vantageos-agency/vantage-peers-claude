---
name: delegate-a-task
description: >
  Give a task to my agent in VantagePeers. Use this skill whenever the user wants
  their agent to take something on ("ask my agent to", "delegate", "create a task
  for", "confie à mon agent", "délègue", "crée une tâche pour"), in English or in
  French.
user-invocable: true
---

## English

Creates a task for your agent in VantagePeers, after you have checked it. You say
what needs doing, and by when if there is a date; Claude does the rest.

Steps:

1. Find your agent: call `whoami`; if it names an acting agent, that is your
   agent. Then call `list_peers` and take that agent's name and its agent ID from
   the list. If `whoami` named no agent, and the list holds exactly one agent,
   that one is your agent; if it holds several, show their names and ask which
   one. Never ask the user to type an identifier.
2. Ask what the task is, if the user has not said it. Ask for a date only if the
   user mentions a deadline; never invent one.
3. Write a short title (one line) and, if useful, a description in the user's
   own words. Priority is "medium" unless the user asks for another (urgent,
   high, medium or low).
4. Show the user what will be created: for whom, the title, the description, the
   priority, the due date if any. Ask: "Shall I create it?" Create nothing
   without a clear yes.
5. On yes, call `create_task` with title, description, assignedTo set to the
   agent's name, assignedToAgentId set to the agent ID from `list_peers`,
   priority, and dueDate (in milliseconds) only if a date was given. Do not pass
   createdBy: a signed-in person acts in their own name.
6. Confirm in one sentence with the title the tool returned.

Rules:

1. Report only what the tool returned. If the tool did not confirm the task, it
   was not created: say so.
2. A refusal is not a success. If the tool answers with REFUSED, RBAC_DENIED or
   Forbidden, say: "VantagePeers did not let you give this task to that agent.
   Your organisation's VantagePeers administrator can grant you this right."
3. Do not show the task identifier or the agent identifier unless the user asks.
4. If the VantagePeers connector is not connected, say so and point the user to
   Claude's connector settings.

## Français

Crée une tâche pour votre agent dans VantagePeers, après votre validation. Vous
dites ce qu'il faut faire, et pour quand s'il y a une date ; Claude s'occupe du
reste.

Étapes :

1. Retrouver votre agent : appeler `whoami` ; s'il indique un agent qui agit pour
   vous, c'est votre agent. Puis appeler `list_peers` et y lire le nom de cet
   agent et son identifiant d'agent. Si `whoami` n'a indiqué aucun agent et que
   la liste n'en compte qu'un, c'est le vôtre ; s'il y en a plusieurs, présenter
   leurs noms et demander lequel. Ne jamais demander à l'utilisateur de saisir un
   identifiant.
2. Demander quelle est la tâche, si l'utilisateur ne l'a pas dit. Ne demander une
   date que si l'utilisateur parle d'une échéance ; ne jamais en inventer une.
3. Rédiger un titre court (une ligne) et, si c'est utile, une description avec
   les mots de l'utilisateur. La priorité est « medium » (normale), sauf si
   l'utilisateur en demande une autre (urgent, high, medium ou low).
4. Montrer à l'utilisateur ce qui va être créé : pour qui, le titre, la
   description, la priorité, l'échéance éventuelle. Demander : « Je la crée ? »
   Ne rien créer sans un oui clair.
5. Sur un oui, appeler `create_task` avec title, description, assignedTo égal au
   nom de l'agent, assignedToAgentId égal à l'identifiant d'agent lu dans
   `list_peers`, priority, et dueDate (en millisecondes) seulement si une date a
   été donnée. Ne pas passer createdBy : une personne connectée agit en son
   propre nom.
6. Confirmer en une phrase, avec le titre renvoyé par l'outil.

Règles :

1. Ne rapporter que ce que l'outil a renvoyé. Si l'outil n'a pas confirmé la
   tâche, elle n'a pas été créée : le dire.
2. Un refus n'est pas une réussite. Si l'outil répond REFUSED, RBAC_DENIED ou
   Forbidden, dire : « VantagePeers ne vous a pas autorisé à confier cette tâche
   à cet agent. L'administrateur VantagePeers de votre organisation peut vous
   donner ce droit. »
3. Ne pas afficher l'identifiant de la tâche ni celui de l'agent, sauf si
   l'utilisateur le demande.
4. Si le connecteur VantagePeers n'est pas connecté, le dire et renvoyer
   l'utilisateur vers les réglages des connecteurs de Claude.
