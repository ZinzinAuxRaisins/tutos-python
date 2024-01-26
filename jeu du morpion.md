---
title: "Jeu du morpion"
order: 1
in_menu: true
---
```python
def afficher_plateau(plateau):
    for ligne in plateau:
        print("|".join(ligne))
        print("-" * 5)


def verifier_victoire(plateau, symbole):
    # Vérifier les lignes et colonnes
    for i in range(3):
        if all(plateau[i][j] == symbole for j in range(3)) or all(plateau[j][i] == symbole for j in range(3)):
            return True

    # Vérifier les diagonales
    if all(plateau[i][i] == symbole for i in range(3)) or all(plateau[i][2 - i] == symbole for i in range(3)):
        return True

    return False


def est_case_valide(plateau, ligne, colonne):
    return 0 <= ligne < 3 and 0 <= colonne < 3 and plateau[ligne][colonne] == " "


def jouer():
    plateau = [[" " for _ in range(3)] for _ in range(3)]
    tour = 0
    symboles = ["X", "O"]

    while True:
        afficher_plateau(plateau)
        symbole = symboles[tour % 2]
        print(f"C'est au tour de {symbole}")

        try:
            ligne = int(input("Entrez le numéro de ligne (0, 1, 2) : "))
            colonne = int(input("Entrez le numéro de colonne (0, 1, 2) : "))
        except ValueError:
            print("Veuillez entrer des nombres valides.")
            continue

        if est_case_valide(plateau, ligne, colonne):
            plateau[ligne][colonne] = symbole
            if verifier_victoire(plateau, symbole):
                afficher_plateau(plateau)
                print(f"Le joueur {symbole} a gagné !")
                break
            elif all(plateau[i][j] != " " for i in range(3) for j in range(3)):
                afficher_plateau(plateau)
                print("Match nul !")
                break
            tour += 1
        else:
            print("Case déjà occupée ou indices invalides. Veuillez réessayer.")


if __name__ == "__main__":
    jouer()


```
En résumé, ce script Python représente un jeu de morpion en mode console, où deux joueurs (X et O) jouent tour à tour jusqu'à ce qu'il y ait un gagnant ou un match nul.

## Fonction *afficher_plateau*:

```python
def afficher_plateau(plateau):
    for ligne in plateau:
        print("|".join(ligne))
        print("-" * 5)
```

- Cette fonction prend le plateau de jeu en paramètre et l'affiche à l'écran en utilisant des lignes et des colonnes.

- La boucle for ligne in plateau itère à travers chaque ligne du plateau, et print("|".join(ligne)) affiche les éléments de la ligne séparés par des "|".

- Ensuite, print("-" * 5) affiche une ligne horizontale pour séparer les lignes du plateau.

## Fonction *verifier_victoire*:

```python
def verifier_victoire(plateau, symbole):
    # Vérifier les lignes et colonnes
    for i in range(3):
        if all(plateau[i][j] == symbole for j in range(3)) or all(plateau[j][i] == symbole for j in range(3)):
            return True

    # Vérifier les diagonales
    if all(plateau[i][i] == symbole for i in range(3)) or all(plateau[i][2 - i] == symbole for i in range(3)):
        return True

    return False
```

- Cette fonction prend le plateau de jeu et un symbole ("X" ou "O") en paramètre.

- Elle vérifie si le symbole a remporté la partie en regardant les lignes, les colonnes et les diagonales du plateau.


## Fonction *est_case_valide*:

```python
def est_case_valide(plateau, ligne, colonne):
    return 0 <= ligne < 3 and 0 <= colonne < 3 and plateau[ligne][colonne] == " "
```

- Cette fonction prend le plateau de jeu, une ligne et une colonne en paramètre.

- Elle vérifie si les indices de ligne et de colonne sont valides et si la case correspondante est vide.

## Fonction *jouer*:

```python
def jouer():
    plateau = [[" " for _ in range(3)] for _ in range(3)]
    tour = 0
    symboles = ["X", "O"]

    while True:
        afficher_plateau(plateau)
        symbole = symboles[tour % 2]
        print(f"C'est au tour de {symbole}")

        try:
            ligne = int(input("Entrez le numéro de ligne (0, 1, 2) : "))
            colonne = int(input("Entrez le numéro de colonne (0, 1, 2) : "))
        except ValueError:
            print("Veuillez entrer des nombres valides.")
            continue

        if est_case_valide(plateau, ligne, colonne):
            plateau[ligne][colonne] = symbole
            if verifier_victoire(plateau, symbole):
                afficher_plateau(plateau)
                print(f"Le joueur {symbole} a gagné !")
                break
            elif all(plateau[i][j] != " " for i in range(3) for j in range(3)):
                afficher_plateau(plateau)
                print("Match nul !")
                break
            tour += 1
        else:
            print("Case déjà occupée ou indices invalides. Veuillez réessayer.")
```

- Cette fonction initialise le plateau de jeu, les tours, et les symboles ("X" et "O").

- La boucle while True continue jusqu'à ce qu'il y ait un gagnant ou un match nul.

- À chaque tour, le plateau est affiché, et le joueur en cours (déterminé par symboles[tour % 2]) est invité à entrer les indices de ligne et de colonne.

- Si les indices sont valides, le symbole est placé sur le plateau. Ensuite, on vérifie s'il y a un gagnant ou un match nul. Si c'est le cas, le jeu se termine.

- Si la case est déjà occupée ou si les indices sont invalides, un message est affiché et le joueur doit réessayer.

## Bloc if \_\_name__ == "\_\_main__":

```python
if __name__ == "__main__":
    jouer()
```

- Cela garantit que la fonction jouer est appelée uniquement si le script est exécuté directement (pas si le script est importé comme un module dans un autre script). 