# Test du Voting
Le fichier voting.test.js est le fichier de test de la correction du contrat de vote.

## Infos

### Nombre de test effectués : 14


- Pas de pourcentage du contrat couvert a cause du probleme avec solidity coverage.
- Je n'ai pas vérifié les autres fonctions d'état du workflowStatus car cela reste du copié collé du premier test. Si le premier marche, alors les autres marcheront aussi.
- De mmême pour les requires de status.
- Les revert pour cause de states (comme le deuxieme revert de addProposal) n'a été testé qu'une fois, pour la meme raison que les fonctions d'état du workflowStatus.
- Les getters et fonctions addVoter et addProposal ne peuvent pas etre testé séparement, alors vérifier addVoter consiste a verifier aussi getVoter, de même avec addProposal et getOneProposal.

## Ordre du fichier

### 1- Test des fonction d'etat (state)

  ##### J'ai testé:
  
    - si la fonction startProposalsRegistering changeait bien l'etat du workflowStatus en "ProposalsRegistrationStarted"
    - l'event WorkflowStatusChange qui doit renvoyer l'ancien et le nouveau état de workflowStatus.


### 2- Test de la fonction addVoter et des require
  #### J'ai véfifié:
  
    - si la fonction addVoter ajoutait bien un voter (verifié par le getter getVoter).
    - Si le revert "Already registered" marchait bien si une personne etait deja enregistrée en tant que voter.
    - l'event VoterRegistered qui doit renvoyer l'adresse du nouveau voter whitelist.
    

### 3- Test de la fonction addProposal et des require
  #### J'ai testé:
  
    - si la fonction addProposal ajoutait bien une proposal dans l'array proposalsArray (verifié par le getter getOneProposal).
    - le revert si il n'y a pas de string dans l'appelation de la fonction.
    - le revert avec un state different de ProposalsRegistrationStarted.
    - l'event ProposalRegistered qui doit renvoyer l'ID de la proposition
    
    
### 4- Test de la fonction setVote
  #### J'ai vérifié:
  
    - si la fonction setVote incrementait bien un vote au vote concerné.
    - si l'etat hasVoted du voter a bien été changé a true.
    - l'event Voted qui doit renvoyer l'adresse du voteur et la proposition pour laquelle il a voté.
 
 
### 5- Test de la fonction tallyVote
  ##### Bien que tallyVote sois dans le group de fonction d'etat, celle ci a besoin d'une catégorie a part:
  #### J'ai testé:
  
    - si la fonction tallyVote fait bien gagner la proposition qui a le plus de vote
    - si la fonction tallyVote fait bien gagner la premierere proposition en cas d'égalité avec une autre.
    


> Fait par Antoine Servant
