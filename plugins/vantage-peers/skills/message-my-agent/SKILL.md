---
name: message-my-agent
description: >
  Send a message to my agent in VantagePeers. Use this skill whenever the user
  wants to tell their agent something, pass on information or ask it a question
  ("tell my agent", "send my agent a message", "préviens mon agent", "envoie un
  message à mon agent", "dis à mon agent"), in English or in French.
user-invocable: true
---

## English

Sends a message to your agent in VantagePeers. Your agent is addressed by the
identifier VantagePeers gives it, never by a typed name, so the message cannot
reach the wrong recipient.

Steps:

1. Find your agent: call `whoami`; if it names an acting agent, that is your
   agent. Then call `list_peers` and take that agent's agent ID from the list. If
   `whoami` named no agent, and the list holds exactly one agent, that one is
   your agent; if it holds several, show their names and ask which one. An agent
   listed without an agent ID cannot receive messages: say so. Never ask the user
   to type an identifier.
2. Ask what the message should say, if the user has not said it. Keep the user's
   own words; only tidy them if asked.
3. Show the message and its recipient's name, and ask: "Shall I send it?" Send
   nothing without a clear yes.
4. On yes, call `send_message` with recipientAgentIds set to a list holding only
   that agent ID, and content set to the message. Do not pass channel, and do not
   pass from: a signed-in person acts in their own name.
5. Confirm in one sentence that the message was sent, naming the agent.

Rules:

1. Report only what the tool returned. If the tool did not confirm the message, it
   was not sent: say so.
2. A refusal is not a success. If the tool answers with REFUSED, RBAC_DENIED or
   Forbidden, say: "VantagePeers did not let you send this message. Your
   organisation's VantagePeers administrator can grant you this right."
3. Never put a name in recipientAgentIds, and never guess an agent ID: it comes
   from `list_peers` only.
4. Do not show identifiers unless the user asks for them.
5. If the VantagePeers connector is not connected, say so and point the user to
   Claude's connector settings.

## Français

Envoie un message à votre agent dans VantagePeers. Votre agent est désigné par
l'identifiant que VantagePeers lui attribue, jamais par un nom saisi à la main :
le message ne peut pas partir vers le mauvais destinataire.

Étapes :

1. Retrouver votre agent : appeler `whoami` ; s'il indique un agent qui agit pour
   vous, c'est votre agent. Puis appeler `list_peers` et y lire l'identifiant
   d'agent de cet agent. Si `whoami` n'a indiqué aucun agent et que la liste n'en
   compte qu'un, c'est le vôtre ; s'il y en a plusieurs, présenter leurs noms et
   demander lequel. Un agent listé sans identifiant d'agent ne peut pas recevoir
   de message : le dire. Ne jamais demander à l'utilisateur de saisir un
   identifiant.
2. Demander le contenu du message, si l'utilisateur ne l'a pas donné. Garder ses
   propres mots ; ne les reformuler que s'il le demande.
3. Montrer le message et le nom du destinataire, puis demander : « Je l'envoie ? »
   Ne rien envoyer sans un oui clair.
4. Sur un oui, appeler `send_message` avec recipientAgentIds égal à une liste
   contenant uniquement cet identifiant d'agent, et content égal au message. Ne
   pas passer channel, ni from : une personne connectée agit en son propre nom.
5. Confirmer en une phrase que le message est parti, en nommant l'agent.

Règles :

1. Ne rapporter que ce que l'outil a renvoyé. Si l'outil n'a pas confirmé l'envoi,
   le message n'est pas parti : le dire.
2. Un refus n'est pas une réussite. Si l'outil répond REFUSED, RBAC_DENIED ou
   Forbidden, dire : « VantagePeers ne vous a pas autorisé à envoyer ce message.
   L'administrateur VantagePeers de votre organisation peut vous donner ce
   droit. »
3. Ne jamais mettre un nom dans recipientAgentIds, ni deviner un identifiant
   d'agent : il vient uniquement de `list_peers`.
4. Ne pas afficher d'identifiants, sauf si l'utilisateur le demande.
5. Si le connecteur VantagePeers n'est pas connecté, le dire et renvoyer
   l'utilisateur vers les réglages des connecteurs de Claude.
