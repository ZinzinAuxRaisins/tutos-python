---
title: "Jeu devine le chiffre"
order: 1
in_menu: true
---
<script>
window.red = 0;
            window.green = 0;
            window.blue = 0;
            function func_1(value) {
                window.red = value;
                change_bg();
            }
            function func_2(value) {
                window.green = value;
                change_bg();
            }
            function func_3(value) {
                window.blue = value;
                change_bg();
            }
            function change_bg() {
                document.getElementById("output").innerHTML = window.red+", "+window.green+", "+window.blue;
                document.body.style.backgroundColor = "rgb("+window.red+","+window.green+","+window.blue+")";
            } </script> 

``` python
from random import randint

chiffreADeviner = randint(1,10)

print()
chiffreDevine = int(input("Devine le chiffre\n"))
print()


while chiffreDevine != chiffreADeviner:

    if chiffreDevine > chiffreADeviner:
        print("Plus petit")
        chiffreDevine = int(input("Devine le chiffre\n"))
        print()
    else:
        print("Plus grand")
        chiffreDevine = int(input("Devine le chiffre\n"))
        print()

print("Bravo tu as trouver le chiffre;",chiffreADeviner)
```

## Explication du code

```python
from random import randint
```
Ici on importe la fonction __*randint()*__ de la librairie __*random*__.

Elle nous permettera de generer un nombre au hasard a deviner.

```python
chiffreADeviner = randint(1,10)
```
Ici on crée notre chiffre a deviner de manière aléatoire.

```python
print()
chiffreDevine = int(input("Devine le chiffre\n"))
print()
```

Ici on demande à l'utilisateur un chiffre à deviner, on stock la valeur dans une variable que l'on nomme __*chiffreDevine*__.

Les deux lignes __*print()*__ servent à mettre un retour a la ligne avant et après le texte de demande, utile pour la mise en forme.

```python
while chiffreDevine != chiffreADeviner:
```
On entre ici dans une boucle seulement si l'utilisateur a entré le mauvais chiffre.

```python
if chiffreDevine > chiffreADeviner:
        print("Plus petit")
        chiffreDevine = int(input("Devine le chiffre\n"))
        print()
    else:
        print("Plus grand")
        chiffreDevine = int(input("Devine le chiffre\n"))
        print()
```
Dans notre boucle on vérifie si le chiffre deviné est plus petit ou plus grand, et on affiche le message correspondant.

```python
print("Bravo tu as trouver le chiffre;",chiffreADeviner)
```

Lorsque l'utilisateur a trouvé le chiffre a deviner on sort donc de la boucle et on affiche un message de victoire. 