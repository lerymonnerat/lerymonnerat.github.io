+++
showSummary = true
date = '2022-04-01'
draft = false 
title= "Coloration de colliers"
tags=['tipe','mathématiques']
+++
{{< katex >}}
{{< link href="/uploads/tipe_1a_maths.pdf" title="PDF" >}}

Ce tipe était un problème de dénombrement :  quel est le  nombre de coloriage possible d'un collier de \\(n\\) perles avec \\(p\\) couleurs ?

Evidemment, certains coloriages sont les mêmes (isomorphes) lorsque l'on tourne le collier (rotation), ou le retourne (symétrie).

La première stratégie a été de générer toutes les configurations possibles, et à implanter un algorithme du type Erasthostène. On calcule, pour une configuration donnée,
   toutes ses images par le groupe diedral \\(D_n\\), que l'on supprime.

Malheureusement,  Cette solution ne fonctionne que pour des "petites" instances du problème.


\\(D_n\\) ayant une action naturelle de groupe sur l'ensemble des colorations, la formule de Burnside permet heureusement un calcul direct du nombre 
d'orbites (colorations différentes), pourvu qu'on connaisse pour chaque transformation \\(g\\) son nombre de points fixes \\(|Fix(g)|\\).
$$
n_{orb} = \frac{1}{|G|} \sum_{g\in G} |Fix(g)|
$$

On trouve ainsi le nombre de coloration est (\\(\phi\\) est l'indicatrice d'Euler): 
- pour \\(n\\) impair :
$$
			\frac{1}{2n}(\sum_{d|n} \phi(d) p^{\frac{n}{d}} + np^{\frac{n+1}{2}})
$$
- pour \\(n\\) pair :
$$
			\frac{1}{2n}(\sum_{d|n} \phi(d) p^{\frac{n}{d}} + \frac{n}{2}(p^{\frac{n+2}{2}} + p^{\frac{n}{2}})))
$$

La méthode peut généraliser à des colorations avec contraintes sur le nombre de perles de chaque couleurs.


Heureusement, une généralisation pour la coloration avec contraintes existe avec un théorème de Polya, qui fait intervenir des polynomes multivariés.
$$
W=\frac{1}{|G|}\sum_{g\in G}\prod_{i=1}^{n}(X_1^i+X_2^i+\ldots + X_p^i)^{e_i(g)}
$$
		où \\(e_i(g)\\) est le nombre de cycles de longueur \\(i\\) de \\(g\\) (vue comme une permutation).

On montre que le coefficient de \\(X_1^{n_1}X_2^{n_2}\ldots X_p^{n_p}\\) dans \\(W\\) est le nombre de colaration correspondant à
\\(n_1\\) perles de couleurs \\(1\\), \\(\ldots\\), \\(n_p\\) perles de couleur \\(p\\).


J'ai implanté le calcul de \\(W\\) pour \\(n=12\\) et \\(p=3\\) avec le logiciel sagemath.
