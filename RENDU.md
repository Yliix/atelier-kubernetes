# Rendu — Atelier Kubernetes

> Complétez ce fichier au fil de l'atelier, puis faites un commit et un push (voir la section « Rendu » du README).

**Nom / Prénom :**
**Groupe :**

---

## Exercice 1 — Cluster

1. Combien de nœuds affiche `kubectl get nodes` ? Quel est le rôle de chacun ?
   > 3 noeuds, lab-agent-0/lab-agent-1(=worker), et lab-server-0(=control-plane).
2. Que montre `docker ps` ? Qu'est-ce qu'un « nœud » dans k3d, concrètement ?
   >docker ps montre 4 conteneurs actif, dont 3 avec les mêmes nom que les noeuds. 3 conteneurs k3s = les 3 nœuds Kubernetes + 1 conteneur serverlb = le load balancer. Chaque nœud du cluster Kubernetes correspond à un conteneur Docker 

## Exercice 2 — Premier déploiement

3. Quels objets Kubernetes ont été créés par `kubectl create deployment` ? (indice : `kubectl get all`)
   >kubectl create deployment web --image=nginx a créé : un Deployment, un ReplicaSet, un Pod 

4. Vous avez supprimé le pod `web-...` : que s'est-il passé, et pourquoi ?
   >Le pod a disparu puis a été recréé automatiquement. Parce que le Deployment maintient un état désiré, on veut 1 pod pour l'app web. Et donc le replicaSet surveille et créer des pods pour atteindre le nombre souhaité / attendus.

## Exercice 3 — Modifier un conteneur en direct

5. Après suppression du pod, votre message « Bienvenue... » a-t-il survécu ? Pourquoi ?
   >Non. Le message n’a pas survécu car le conteneur est éphémère. Le nouveau pod repart de l’image d’origine de nginx
6. Pourquoi le `port-forward` a-t-il cessé de fonctionner après la suppression du pod ?
   >Le port-forward ciblait un pod précis et quand le pod a été supprimé, le tunnel a cassé. Le nouveau pod a un autre conteneur et une autre adresse.

## Exercice 4 — Déclaratif

7. Quelle différence entre `kubectl create` et `kubectl apply` ?
   >create crée une ressource. apply décrit l’état voulu et met à jour si besoin. apply est utilisé en déclaratif.
8. À quoi sert le `selector` d'un Service ? Que se passe-t-il s'il ne correspond à aucun pod ?
   >Le selector dit au Service quels pods viser. S’il ne correspond à aucun pod, le Service n’a pas d’endpoints. Le site ne répond pas.

## Exercice 5 — Scaling & mises à jour

9. Sur quels nœuds se trouvent vos 3 réplicas ? Collez la sortie de `kubectl get pods -l app=site -o wide`.
   ```

   ```
10. Avec l'image `nginx:9.99`, quel statut avait le pod ? Quelle commande vous a donné la cause ?
    >
11. Pendant la panne, le site restait-il accessible ? Pourquoi ?
    >

## Exercice 6 — Portainer & Mario

12. URL publique de votre Mario :
    >
13. Retrouvez le Deployment `mario` en ligne de commande. Portainer et `kubectl` parlent-ils au même composant ? Lequel ?
    >

## Bonus (facultatif)

14. Bonus réalisés et remarques :
    >

---

**Score obtenu avec `./scripts/check.sh` :** ... / ...
