+++
title = 'Functional Programming : Functor and Category' 
date = 2019-11-24T00:50:52+01:00
+++

## Definition intuitive d'un foncteur et d'une catégorie

En design pattern fonctionnel : 

### Un foncteur (functor) 
- est une structure de données composée d'éléments et d'une opération de transformation 
qui s'applique à chacun des éléments de la structure de données et qui conserve cette structure

Pour un exemple de code de functor voir https://github.com/jeandi7/gofunctional/tree/main/functor

![image info](./images/category.png)

Le terme functor provient de la théorie mathématique des catégories.

Je dessine ici 2 catégories A et B , notre foncteur 
- qui  fait passer notre structure de donnée avec des objets x, y ,z de la catégorie A  (y compris les fléches que l'on voit sur le dessin)  
- aux objets F(x),F(y) et F(z) de la catégorie B (toujours avec leurs les flèches )

On note qu'une catégorie est composée d'élements 
- qui sont soit des objets 
- soit des flèches

Les fléches d'une catégorie sont aussi appelées morphismes dans la théorie des catégories.
Ces fléches doivent vérifier certaines propriétées comme
- la composition
- l'associativité
- la neutralité

Pourquoi parler de catégorie ? 

<p> Je me souviens (il y a bien longtemps) de la démonstration par l'absurde que l'ensemble des ensembles n'existe pas.
Et bien , c'est une des raisons pour laquelle on parle de catégorie....et pas d'ensemble.
Mais si nos fléches  forment un ensemble, on parle de catégorie localement petite.
Et si nos objets forment un ensemble, on parle de petite catégorie </p>

En programmation fonctionelle, on restera toujours sur des petites catégories.

### Remarque sur le monoïde : 

- Un monoïde est une catégorie localement petite réduite à un unique objet.


## Definition mathématique d'un foncteur et d'une catégorie

### Définition : Une catégorie C est la donnée de :
- une classe C0 d’objets, notés A, B, C, D . . .
- Pour toute paire d’objets A,B une classe C(A,B) de flèches f de source A et de but B. 
On note f : A → B le fait que f ∈ C(A,B)
- Pour toute triplée d’objets A, B, C, une application appelée composition
 ◦ : C(B,C)×C(A,B) −→ C(A,C)
 avec les propriétés suivantes :
 - associativité : pour toutes f : A → B, g : B → C et h : C → D, h ◦ (g ◦f ) = (h ◦ g) ◦ f  
 - neutralité : pour tout A, il existe une flèche idA : A → A telle que, pour
toutes g:A→B et h:B→A, g◦idA = g et idA◦h=h

Un catégorie C est dite localement petite si, pour tous objets A, B, C(A, B) est un ensemble. 

Une catégorie localement petite C est petite si C0 est lui-même un ensemble. On utilise parfois la notation A ∈ C pour dire A ∈ C0.


### Définition : Soient A, B deux catégories. Un foncteur F : A → B est la donnée de :
- une application F _0_ : A _0_ → B _0_ 
- pour tous objets A, B de A, une application
F _A,B_ : A(A, B) → B(F _0_ (A), F _0_ (B)) avec les propriété suivantes :
  - préservation de la composition : pour toutes flèches f : A → B, g : B → C de A,
F _A,C_ (g◦ f) = F _B,C_ (g)◦F _A,B_ (f)
  - préservation des identités : pour tout objet A de A, F _A,A_ (idA) = id _F0_ (A).

- Les indices sont habituellement omis, ce qui donne les notations simplifiées F(A) et F(f) pour l’image d’un objet et d’une flèche de A, respectivement. Lorsque ce n’est pas nécessaire, on fait aussi économie de parenthèses, en écrivant FA et Ff au lieu de F(A) et F(f). 
- Avec ces conventions, les propriétés du foncteur deviennent plus concises et claires :
   
   F(g ◦ f ) = Fg ◦ F f 
   
   F(id _A_) = id _FA_


_source: 
j'ai repris les définitions du cours Paris 13 de Damiano Mazza_
_cours disponible sur https://www-lipn.univ-paris13.fr/~mazza/teaching/IntroCat.pdf_
ainsi que pour qui est quoi le lien :
http://s.dugowson.free.fr/recherche/connectologie/monoides.pdf