+++
title = 'Functional Programming : Functor' 
date = 2019-11-24T00:50:52+01:00
+++

En design pattern fonctionnel 

>un foncteur (functor) est une structure de données composée d'éléments et d'une opération de transformation 
>qui s'applique à chacun des éléments de la structure de données et qui conserve cette structure

Pour un exemple de code voir https://github.com/jeandi7/gofunctional/tree/main/functor

![image info](./images/category.png)

Le terme functor provient de la théorie mathématique des catégories.

Je dessine ici 2 catégories C et D , notre foncteur 
- qui  fait passer notre structure de donnée avec des objets x, y ,z de la catégorie C  (y compris les fléches que l'on voit sur le dessin)  
- aux objets F(x),F(y) et F(z) de la catégorie D (toujours avec leurs les flèches )

On note qu'une catégorie est composé d'élements 
- qui sont soit des objets 
- soit des flèches

Les fléches sont aussi appelées morphismes dans la théorie des catégories.