---------------------------------------------------
TP2 de INF 231 : Implémentation de Listes Chaînées
---------------------------------------------------

Ce projet en langage C implémente diverses structures de listes chaînées :
1.  Listes simplement chaînées triées.
2.  Listes doublement chaînées triées.
3.  Listes simplement chaînées circulaires.
4.  Listes doublement chaînées circulaires.

Il offre des fonctionnalités de base telles que l'insertion, la suppression et l'affichage pour chaque type de liste.

---------------------------------------------------
Structures de Données
---------------------------------------------------

1.  **Liste Simplement Chaînée (`struct List`)**
    *   `val` : entier stocké dans le nœud.
    *   `suiv` : pointeur vers le nœud suivant.
    *   `typedef struct List *listc;`

2.  **Liste Doublement Chaînée (`struct Dlist`)**
    *   `prec` : pointeur vers le nœud précédent.
    *   `val` : entier stocké dans le nœud.
    *   `suiv` : pointeur vers le nœud suivant.
    *   `typedef struct Dlist *listdc;`

3.  **Liste Simplement Chaînée Circulaire (`struct Clist`)**
    *   `val` : entier stocké dans le nœud.
    *   `suiv` : pointeur vers le nœud suivant (le dernier élément pointe vers la tête).
    *   `typedef struct Clist *listcc;`

4.  **Liste Doublement Chaînée Circulaire (`struct CDlist`)**
    *   `prec` : pointeur vers le nœud précédent (circulaire).
    *   `val` : entier stocké dans le nœud.
    *   `suiv` : pointeur vers le nœud suivant (circulaire).
    *   `typedef struct CDlist *listdcc;`

---------------------------------------------------
Fonctions Implémentées et Algorithmes
---------------------------------------------------

### 1. `void aff(listc L)`
*   **Description** : Affiche les éléments d'une liste simplement chaînée du début à la fin.
*   **Algorithme** : (voir version précédente)

### 2. `void affi(listdc L)`
*   **Description** : Affiche les éléments d'une liste doublement chaînée.
*   **Algorithme** : (voir version précédente)

### 3. `void affic(listcc L)`
*   **Description** : Affiche les éléments d'une liste simplement chaînée circulaire.
*   **Algorithme** : (voir version précédente)

### 4. `void affidc(listdcc L)`
*   **Description** : Affiche les éléments d'une liste doublement chaînée circulaire.
*   **Algorithme** :
    ```
    Algorithme Afficher_Liste_Double_Circulaire(L)
        Si L est NUL, alors
            Afficher "NULL"
            Retourner
        Fin Si

        P <-- L
        Afficher "Header <-> "
        Faire
            Afficher P.val
            Afficher " <-> "
            P <-- P.suiv
        Tant que P n'est pas L
        Afficher "Header"
    Fin Algorithme
    ```

### 5. `listc insert_lsct(listc L, int a)`
*   **Description** : Insère un entier `a` dans une liste simplement chaînée `L` en maintenant l'ordre croissant.
*   **Algorithme** : (voir version précédente)

### 6. `listc supp_elmt(listc L, int a)`
*   **Description** : Supprime toutes les occurrences de l'entier `a` d'une liste simplement chaînée `L`.
*   **Algorithme** : (voir version précédente)

### 7. `listdc insert_listdc(listdc L, int a)`
*   **Description** : Insère un entier `a` dans une liste doublement chaînée `L` en maintenant l'ordre croissant.
*   **Algorithme** : (voir version précédente)

### 8. `listcc creer_listcc(int a)`
*   **Description** : Crée un nouveau nœud pour une liste simplement circulaire avec la valeur `a`.
*   **Algorithme** : (voir version précédente)

### 9. `listcc insert_listcc_queue(listcc L, int a)`
*   **Description** : Insère un entier `a` en queue d'une liste simplement chaînée circulaire `L`.
*   **Algorithme** : (voir version précédente)

### 10. `listcc insert_listcc_tete(listcc L, int a)`
*   **Description** : Insère un entier `a` en tête d'une liste simplement chaînée circulaire `L`.
*   **Algorithme** : (voir version précédente)

### 11. `listdcc creer_listdcc(int a)`
*   **Description** : Crée un nouveau nœud pour une liste doublement chaînée circulaire avec la valeur `a`.
*   **Algorithme** :
    ```
    Algorithme Creer_Noeud_Double_Circulaire(a)
        Allouer memoire pour P
        Si allocation echoue, alors
            Retourner NUL
        Fin Si
        P.val <-- a
        P.suiv <-- NUL
        P.prec <-- NUL
        Retourner P
    Fin Algorithme
    ```

### 12. `listdcc insert_listdcc_tete(listdcc L, int a)`
*   **Description** : Insère un entier `a` en tête d'une liste doublement chaînée circulaire `L`.
*   **Algorithme** :
    ```
    Algorithme Inserer_Tete_Double_Circulaire(L, a)
        Creer P <-- Creer_Noeud_Double_Circulaire(a)
        Si P est NUL, retourner L

        Si L est NUL, alors
            L <-- P
            L.suiv <-- L
            L.prec <-- L
        Sinon
            P.suiv <-- L
            P.prec <-- L.prec
            L.prec.suiv <-- P
            L.prec <-- P
            L <-- P
        Fin Si
        Retourner L
    Fin Algorithme
    ```

### 13. `listdcc insert_listdcc_queue(listdcc L, int a)`
*   **Description** : Insère un entier `a` en queue d'une liste doublement chaînée circulaire `L`.
*   **Algorithme** :
    ```
    Algorithme Inserer_Queue_Double_Circulaire(L, a)
        Creer P <-- Creer_Noeud_Double_Circulaire(a)
        Si P est NUL, retourner L

        Si L est NUL, alors
            L <-- P
            L.suiv <-- L
            L.prec <-- L
        Sinon
            P.suiv <-- L
            P.prec <-- L.prec
            L.prec.suiv <-- P
            L.prec <-- P
        Fin Si
        Retourner L
    Fin Algorithme
    ```

### 14. `listdcc supp_elmt_dcc(listdcc L, int a)`
*   **Description** : Supprime toutes les occurrences de l'entier `a` d'une liste doublement chaînée circulaire `L`.
*   **Algorithme** :
    ```
    Algorithme Supprimer_Element_Double_Circulaire(L, a)
        Si L est NUL, retourner NUL

        Current <-- L
        initial_size <-- compter le nombre d'elements dans L
        count <-- 0

        Faire
            Next_node <-- Current.suiv
            Si Current.val est egal à a, alors
                Si Current est L, alors // Tete de liste
                    Si L.suiv est L, alors // Seul element
                        Liberer L
                        Retourner NUL
                    Fin Si
                    L.prec.suiv <-- L.suiv
                    L.suiv.prec <-- L.prec
                    L <-- L.suiv
                    Liberer Current
                Sinon // Pas la tete
                    Current.prec.suiv <-- Current.suiv
                    Current.suiv.prec <-- Current.prec
                    Liberer Current
                Fin Si
            Fin Si
            Current <-- Next_node
            count <-- count + 1
            Si L est NUL ou (Current est L et count est superieur ou egal à initial_size), alors
                Sortir de la boucle
            Fin Si
        Tant que Current n'est pas L ou count est inferieur à initial_size + 1

        Retourner L
    Fin Algorithme
    ```

### 15. Fonctions de Libération de Mémoire (`free_listc`, `free_listdc`, `free_listcc`, `free_listdcc`)
*   **Description** : Ces fonctions parcourent les listes respectives et libèrent la mémoire allouée dynamiquement pour chaque nœud, évitant ainsi les fuites de mémoire. Il est crucial de les appeler avant la fin du programme.

---------------------------------------------------
Compilation et Exécution
---------------------------------------------------

Pour compiler le code, utilisez un compilateur C comme GCC :
```bash
gcc listes_chainees.c -o listes_chainees
