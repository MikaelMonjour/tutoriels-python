## Les fonctions lambdas


Python et d'autres langages comme Java, C# et même C++ ont vu des fonctions lambda ajoutées à leur syntaxe, alors que des langages comme LISP ou la famille de langages ML, Haskell, OCaml et F#, utilisent les lambdas comme concept de base.

Les lambdas Python sont de petites fonctions anonymes, soumises à une syntaxe plus restrictive mais plus concise que les fonctions Python ordinaires.

### Le calcul Lambda

Les expressions lambda en Python et dans d'autres langages de programmation ont leurs racines dans le calcul lambda, un modèle de calcul inventé par Alonzo Church.

Vous découvrirez à quel moment le lambda-calcul a été introduit et pourquoi c'est un concept fondamental qui a fini dans l'écosystème Python.

### Petite Histoire

Alonzo Church a formalisé le calcul lambda, un langage basé sur l'abstraction pure, dans les années 1930.

Les fonctions lambda sont également appelées abstractions lambda, une référence directe au modèle d'abstraction de la création originale de Alonzo Church.

Le calcul lambda peut encadrer n'importe quel calcul. Il est complémentaire à celui de Turing, mais contrairement au concept de machine de Turing, il est pur et ne conserve aucun état.


Les langages fonctionnels tirent leur origine de la logique mathématique et du calcul lambda, tandis que les langages de programmation impérative adoptent le modèle de calcul basé sur l'état inventé par Alan Turing.

Les deux modèles de calcul, le calcul lambda et les machines de Turing, peuvent être transposés l'un dans l'autre.

Cette équivalence est connue sous le nom d'hypothèse de Church-Turing.

Les langages fonctionnels héritent directement de la philosophie du calcul lambda, en adoptant une approche déclarative de la programmation qui met l'accent sur l'abstraction, la transformation des données, la composition et la pureté (pas d'état et pas d'effets secondaires).

Parmi les exemples de langages fonctionnels, on peut citer Haskell, Lisp ou Erlang.

### Premier Exemple

Voici quelques exemples pour vous mettre en appétit avec un peu de code Python fonctionnel.

La fonction `identity()`, est une fonction comme on peut la définir normalement avec python.

```python
def identity(x):
    return x
```

Si on vaut transcrire la foction en lambda on peut faire :

```python
lambda x: x
```

Comme toutes les autres fonctions lambdas, elle contient :

-  Le mot-clé : `lambda`
-  Une variable contrainte : `x`
-  Un corps : `x`


<b>Note : Dans le contexte de cet article, une variable contrainte est un argument d'une fonction lambda.</b>

Vous pouvez écrire un exemple un peu plus élaboré.

<b>Exemple avec une fonction qui ajoute 1 à l'argument passé :</b>

```python
lambda x: x + 1
```

Si vous compter passer un argument à la fonction lambda, c'est possible de le faire en factorisation :

```python
(lambda x: x + 1)(2)
```

```plaintext
RESULTAT:
3
```


<b>Comment fonctionne ce code ?</b>

On peut expliquer ce code en trois étapes :

1) (lambda x: x + 1)(2) = `lambda 2: 2 + 1`
2)                      = 2 + 1
3)                      = 3

Parce qu'une fonction lambda est une expression, elle peut être nommée. 

Vous pouvez donc écrire le code précédent comme suit :

```python
add_one = lambda x: x + 1
add_one(2)
```

```plaintext
RESULTAT:
3
```

On pourrait réecrire la fonction lambda `add_one` de manière traditionnelle:

```python
def add_one(x):
    return x + 1
```

Ces fonctions prennent toutes un seul et même argument.

Vous avez peut-être remarqué que, dans la définition des lambdas, les arguments n'ont pas de parenthèses autour d'eux.

Les fonctions multi-arguments (fonctions qui prennent plus d'un argument) avec les Lambdas Python sont définies en listant les arguments et en les séparant par une virgule (,) mais sans les entourer de parenthèses :

```python
full_name = lambda first, last: f'Full name: {first.title()} {last.title()}'
full_name('guido', 'van rossum')
```

```plaintext
RESULTAT:
'Full name: Guido Van Rossum'
```

### Les fonctions anonymes

Les termes suivants peuvent être utilisés de manière interchangeable selon le type de langage de programmation et la culture :

- Fonctions anonymes
- Fonctions lambdas
- Expressions lambdas
- Lambda form
- Fonctions littérales

Dans la suite de cet article, après cette section, vous verrez surtout le terme de fonction lambda.

Pris littéralement, une fonction anonyme est une fonction sans nom. En Python, une fonction anonyme est créée avec le mot-clé lambda.

De manière plus générale, un nom peut lui être attribué ou non.

Considérons une fonction anonyme à deux arguments définie avec lambda mais non liée à une variable. On ne lui attribue pas de nom :

```python
lambda x, y: x + y
```

La fonction ci-dessus définit une expression lambda qui prend deux arguments et renvoie leur somme.


Pour la fonction du dessous, la syntaxe est assez spéciale et je ne vois pas comment l'utiliser dans un exemple pratique

```python
>>> _(1, 2)
```

```plaintext
RESULTAT:
3
```

L'exemple ci-dessus tire profit de la fonction d'interprétation interactive fournie par le soulignement (_). Voir la note pour plus de détails.

---

Vous ne pourriez pas écrire un code similaire dans un module Python.

Considérez le _ dans l'interpréteur comme un effet secondaire dont vous avez profité.

Dans un module Python, vous assigneriez un nom au lambda, ou vous passeriez le lambda à une fonction.

---

Un autre schéma utilisé dans d'autres langages comme JavaScript consiste à exécuter immédiatement une fonction lambda en Python.

C'est ce que l'on appelle une expression de fonction immédiatement invoquée (IIFE, prononcer "iffy").

<b>Voici un exemple :</b>

```python
>>> (lambda x, y: x + y)(2, 3)
5
```

La fonction lambda ci-dessus est définie puis immédiatement appelée avec deux arguments (2 et 3).

Elle renvoie la valeur 5, qui est la somme des arguments.

Plusieurs exemples dans ce tutoriel utilisent ce format pour mettre en évidence l'aspect anonyme d'une fonction lambda et éviter de se focaliser sur la fonction lambda en Python comme moyen plus court de définir une fonction.


Python n'encourage pas l'utilisation d'expressions lambda immédiatement invoquées.

Il se contente de faire en sorte qu'une expression lambda puisse être invoquée, contrairement au corps d'une fonction normale.

Les fonctions lambda sont fréquemment utilisées avec les fonctions d'ordre supérieur, qui prennent une ou plusieurs fonctions comme arguments ou renvoient une ou plusieurs fonctions.

Une fonction lambda peut être une fonction d'ordre supérieur en prenant une fonction (normale ou lambda) comme argument, comme dans l'exemple suivant :

```python
>>> high_ord_func = lambda x, func: x + func(x)
>>> high_ord_func(2, lambda x: x * x)
```

```plaintext
RESULTAT:
6
```

```python
>>> high_ord_func(2, lambda x: x + 3)
```

```plaintext
RESULTAT:
7
```

Python propose des fonctions d'ordre supérieur sous forme de fonctions built-in ou dans la bibliothèque standard. 

Les exemples comprennent map(), filter(), functools.reduce(), ainsi que des fonctions clés comme sort(), sorted(), min() et max(). 

Vous utiliserez les fonctions lambda avec les fonctions Python d'ordre supérieur dans Utilisations appropriées des expressions lambda.

### Python Lambda et fonctions régulières

Cette citation de la FAQ ["Python Design and History"](https://docs.python.org/3/faq/design.html) semble donner le ton quant à ce que l'on attend globalement de l'utilisation des fonctions lambda en Python :

> Contrairement aux fonctions lambda dans d'autres langues qui ajoutent des fonctionnalités,  les lambdas en Python ne sont qu'une notation abrégée simplifée pour définir une fonction

Néanmoins, ne laissez pas cette affirmation vous dissuader d'utiliser le lambda de Python. 

A première vue, vous pouvez admettre qu'une fonction lambda est une fonction avec un certain [sucre syntaxique](https://en.wikipedia.org/wiki/Syntactic_sugar). 

Elle permet de raccourcir le code pour définir ou invoquer une fonction.

Les paragraphes suivants mettent en évidence les points communs et les différences subtiles entre les fonctions Python normales et les fonctions lambda.

#### Fonctions

Vous pouvez vous demander ce qui distingue fondamentalement une fonction lambda et variable d'une fonction régulière avec une seule ligne de retour.

Vérifions comment Python voit une fonction construite avec une seule déclaration de retour par rapport à une fonction construite comme une expression (lambda).

Le module [dis](https://docs.python.org/fr/3/library/dis.html) expose des fonctions permettant d'analyser le bytecode (l'envers du décors) Python généré par le compilateur Python :

```python
>>> import dis
>>> add = lambda x, y: x + y
>>> type(add)
<class 'function'>
>>> dis.dis(add)
  1           0 LOAD_FAST                0 (x)
              2 LOAD_FAST                1 (y)
              4 BINARY_ADD
              6 RETURN_VALUE
>>> add
<function <lambda> at 0x7f30c6ce9ea0>
```

Vous pouvez voir que `dis()` expose une version lisible du bytecode Python permettant l'inspection des instructions de bas niveau que l'interpréteur Python utilisera lors de l'exécution du programme.

Voyez-le maintenant avec une fonction ordinaire :



```python
>>> import dis
>>> def add(x, y): return x + y
>>> type(add)
<class 'function'>
>>> dis.dis(add)
  1           0 LOAD_FAST                0 (x)
              2 LOAD_FAST                1 (y)
              4 BINARY_ADD
              6 RETURN_VALUE
>>> add
<function add at 0x7f30c6ce9f28>
```

Le bytecode interprété par Python est le même pour les deux fonctions.

Mais vous pouvez remarquer que la dénomination est différente : le nom de la fonction est ajouté pour une fonction définie avec def, alors que la fonction Python lambda est considérée comme lambda.

#### Traceback

Vous avez vu dans la section précédente que, dans le contexte de la fonction lambda, Python n'a pas fourni le nom de la fonction, mais seulement `lambda`.

Cela peut être une limitation à considérer lorsqu'une exception se produit, et qu'un traceback ne montre que `lambda` :

```python
>>> div_zero = lambda x: x / 0
>>> div_zero(2)
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    File "<stdin>", line 1, in <lambda>
ZeroDivisionError: division by zero
```

Le traçage d'une exception levée lors de l'exécution d'une fonction lambda identifie uniquement la fonction à l'origine de l'exception comme `lambda`.

Voici la même exception soulevée par une fonction normale :

```python
>>> def div_zero(x): return x / 0
>>> div_zero(2)
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    File "<stdin>", line 1, in div_zero
ZeroDivisionError: division by zero
```

Une fonction normale provoque une erreur similaire, mais elle donne lieu à un retraçage plus précis car elle donne le nom de la fonction, `div_zero`.

### Syntaxe

Comme vous l'avez vu dans les sections précédentes, une forme lambda présente des distinctions syntaxiques par rapport à une fonction normale.

En particulier, une fonction lambda présente les caractéristiques suivantes :

- Il ne peut contenir que des expressions et ne peut pas inclure de déclarations dans son corps.
- Il est écrit en une seule ligne d'exécution.
- Il ne supporte pas les annotations de type.
- Il peut être immédiatement invoqué (IIFE).

#### No Statements

Une fonction lambda ne peut contenir de déclarations.

Dans une fonction lambda, des instructions telles que return, pass, assert ou raise entraînent une exception SyntaxError.

Voici un exemple d'ajout d'assert dans le corps d'un lambda :

```python
>>> (lambda x: assert x == 2)(2)
  File "<input>", line 1
    (lambda x: assert x == 2)(2)
                    ^
SyntaxError: invalid syntax
```

Cet exemple artificiel visait à affirmer que le paramètre x avait une valeur de 2, mais l'interpréteur identifie une SyntaxError lors de l'analyse du code qui implique une assertion dans le corps du lambda.

#### Expression unique

Contrairement à une fonction normale, une fonction de Python lambda est une expression unique.

Bien que, dans le corps d'un lambda, vous puissiez répartir l'expression sur plusieurs lignes en utilisant des parenthèses ou une chaîne de plusieurs lignes, elle reste une expression unique :

```python
>>> (lambda x:
... (x % 2 and 'odd' or 'even'))(3)
'odd'
```

L'exemple ci-dessus renvoie la chaîne "impair" lorsque l'argument lambda est impair, et "pair" lorsque l'argument est pair. 

Elle s'étend sur deux lignes car elle est contenue dans un ensemble de parenthèses, mais elle reste une expression unique.

#### Types d'annotations

Si vous avez commencé à adopter l'indication de type, qui est maintenant disponible en Python, alors vous avez une autre bonne raison de préférer les fonctions normales aux fonctions lambda de Python.

Consultez le guide de la vérification des types en Python pour en savoir plus sur les indices de type et la vérification des types en Python.

Dans une fonction lambda, il n'y a pas d'équivalent pour ce qui suit :

```python
def full_name(first: str, last: str) -> str:
    return f'{first.title()} {last.title()}'
```

Toute erreur de type avec full_name() peut être détectée par des outils comme mypy ou pyre, tandis qu'une SyntaxError avec la fonction lambda équivalente est levée à l'exécution :

```python
>>> lambda first: str, last: str: first.title() + " " + last.title() -> str
  File "<stdin>", line 1
    lambda first: str, last: str: first.title() + " " + last.title() -> str

SyntaxError: invalid syntax
```

Comme pour essayer d'inclure une déclaration dans un lambda, l'ajout d'une annotation de type entraîne immédiatement une SyntaxError à l'exécution.

##### IIFE

Vous avez déjà vu plusieurs exemples d'exécution de fonctions immédiatement invoquées :

```python
>>> (lambda x: x * x)(3)
9
```

En dehors de l'interpréteur Python, cette fonctionnalité n'est probablement pas utilisée dans la pratique.

C'est une conséquence directe du fait qu'une fonction lambda peut être appelée telle qu'elle est définie.

Par exemple, cela vous permet de passer la définition d'une expression lambda en Python à une fonction d'ordre supérieur comme map(), filter(), ou functools.reduce(), ou à une fonction clé.

#### Arguments

Tout comme une fonction normale est définie avec def, les expressions lambda de Python supportent toutes les différentes façons de passer des arguments. 

Cela inclut :


- Les arguments positionnels
- Les arguments nommés (keyword arguments)
- Des listes variable d'arguments (souvent appelées varargs)
- Des listes variable de keyword arguments
- Des arguments de mots-clés seulement

Les exemples suivants illustrent les options qui s'offrent à vous pour passer des arguments aux expressions lambda :

```python
>>> (lambda x, y, z: x + y + z)(1, 2, 3)
6
>>> (lambda x, y, z=3: x + y + z)(1, 2)
6
>>> (lambda x, y, z=3: x + y + z)(1, y=2)
6
>>> (lambda *args: sum(args))(1,2,3)
6
>>> (lambda **kwargs: sum(kwargs.values()))(one=1, two=2, three=3)
6
>>> (lambda x, *, y=0, z=0: x + y + z)(1, y=2, z=3)
6
```

En Python, un décorateur est l'implémentation d'un pattern qui permet d'ajouter un comportement à une fonction ou une classe.

Il est généralement exprimé avec la syntaxe @decorator qui préfixe une fonction.

Voici un exemple typique d'un décorateur en Python

```python
def some_decorator(f):
    def wraps(*args):
        print(f"Calling function '{f.__name__}'")
        return f(args)
    return wraps

@some_decorator
def decorated_function(x):
    print(f"With argument '{x}'")
```

Dans l'exemple ci-dessus, some_decorator() est une fonction qui ajoute un comportement à decorated_function(), de sorte que l'appel de decorated_function("Python") donne la sortie suivante :

```plaintext
Calling function 'decorated_function'
With argument 'Python'
```

decorated_function() affiche uniquement l'argument "Python", mais le décorateur ajoute un comportement supplémentaire qui affiche également la fonction d'appel "decorated_function".


Un décorateur peut être appliqué à un lambda. Bien qu'il ne soit pas possible de décorer un lambda avec la syntaxe @decorator, un décorateur n'est qu'une fonction, il peut donc appeler la fonction lambda :


<b>1) Créer un décorateur `trace`</b>

```python
def trace(f):
    def wrap(*args, **kwargs):
        print(f"[TRACE] func: {f.__name__}, args: {args}, kwargs: {kwargs}")
        return f(*args, **kwargs)

    return wrap

```


<b>2) On décore le fonction add_two</b>

```python
@trace
def add_two(x):
    return x + 2
```


<b>3) Appel de la fonction décorée add_two</b>

```python
add_two(3)
```

```plaintext
[TRACE] func: add_two, args: (3,), kwargs: {}
```

<b>4) Utiliser un décorateur sur une fonction lambda</b>

```python
print((trace(lambda x: x ** 2))(3))
```

```plaintext
[TRACE] func: <lambda>, args: (3,), kwargs: {}
9
```


Voyez comment, comme vous l'avez déjà vu, le nom de la fonction lambda apparaît comme lambda, alors que add_two est clairement identifié pour la fonction normale.

Décorer la fonction lambda de cette façon pourrait être utile pour le débogage.

Eventuellement pour déboguer le comportement d'une fonction lambda utilisée dans le contexte d'une fonction d'ordre supérieur ou d'une fonction clé. Voyons un exemple avec map() :

```python
list(map(trace(lambda x: x*2), range(3)))
```

Le premier argument de map() est un lambda qui multiplie son argument par 2.

Ce lambda est décoré avec trace(). Lorsqu'il est exécuté, l'exemple ci-dessus produit ce qui suit :

```plaintext
[TRACE] Calling <lambda> with args (0,) and kwargs {}
[TRACE] Calling <lambda> with args (1,) and kwargs {}
[TRACE] Calling <lambda> with args (2,) and kwargs {}
[0, 2, 4]
```

Le résultat [0, 2, 4] est une liste obtenue en multipliant chaque élément de la range(3).

Pour l'instant, on considère que range(3) est équivalent à la liste [0, 1, 2].

Vous trouverez plus de détails sur map() dans la section Carte.

Un lambda peut aussi être un décorateur, mais ce n'est pas recommandé.

Si vous vous trouvez dans cette situation, [consultez le PEP 8](https://www.python.org/dev/peps/pep-0008/#programming-recommendations), Recommandations de programmation.

#### Closure

Une closure est une fonction dans laquelle chaque variable libre.

Tout ce qui est utilisé dans cette fonction, à l'exception des paramètres, est lié à une valeur spécifique définie dans le champ d'application de cette fonction.

En effet, les closures définissent l'environnement dans lequel elles fonctionnent et peuvent donc être appelées de n'importe où.

Les concepts de lambdas et de closure ne sont pas nécessairement liés, bien que les fonctions lambda puissent être des closures de la même manière que les fonctions normales peuvent également être des closures.

Certains langages ont des constructions spéciales pour les closures ou lambdas (par exemple, Groovy avec un bloc de code anonyme comme objet Closure), ou une expression lambda (par exemple, l'expression lambda de Java avec une option limitée pour les closures).

Voici une fermeture construite avec une fonction Python normale :

```python
def outer_func(x):
    y = 4

    def inner_func(z):
        print(f"x = {x}, y = {y}, z = {z}")
        return x + y + z

    return inner_func

for i in range(3):
    closure = outer_func(i)
    print(f"closure({i+5}) = {closure(i+5)}")
```

`outer_func()` renvoie `inner_func()`, une fonction imbriquée qui calcule la somme de trois arguments :


- x est passé en argument à outer_func().
- y est une variable locale à outer_func().
- z est un argument passé à inner_func().

Pour tester le comportement de `outer_func()` et `inner_func()`, `outer_func()` est invoqué trois fois dans une boucle for qui imprime ce qui suit :

```plaintext
x = 0, y = 4, z = 5
closure(5) = 9
x = 1, y = 4, z = 6
closure(6) = 11
x = 2, y = 4, z = 7
closure(7) = 13
```

inner_func() est renvoyé par l'invocation de outer_func() est lié à la fermeture du nom.

inner_func() capture x et y parce qu'elle a accès à son environnement d'intégration, de sorte que lors de l'invocation de la closure, elle est capable d'opérer sur les deux variables libres x et y.

De même, un lambda peut aussi être une fermeture.

Voici le même exemple avec une fonction lambda en Python :

```python
def outer_func(x):
    y = 4
    return lambda z: x + y + z


for i in range(3):
    closure = outer_func(i)
    print(f"closure({i+5}) = {closure(i+5)}")
```

Lorsque vous exécutez le code ci-dessus, vous obtenez le résultat suivant :

```plaintext
closure(5) = 9
closure(6) = 11
closure(7) = 13
```

`outer_func()` renvoie un lambda et l'affecte à la variable closure.

Le corps de la fonction lambda fait référence à x et y.

La variable y est disponible au moment de la définition, tandis que x est définie au moment de l'exécution lorsque `outer_func()` est invoquée.

Dans cette situation, la fonction normale et la fonction lambda se comportent de manière similaire.

Dans la section suivante, vous verrez une situation où le comportement d'un lambda peut être trompeur en raison de son temps d'évaluation (temps de définition vs temps d'exécution).

#### Temps d'évaluation

Dans certaines situations impliquant des boucles, le comportement d'une fonction de Python lambda comme fermeture peut être contre-intuitif.

Il faut comprendre quand des variables libres sont liées dans le contexte d'un lambda.

Les exemples suivants montrent la différence entre l'utilisation d'une fonction classique et l'utilisation d'une fonction Python lambda.

Testez d'abord le scénario en utilisant une fonction classique :

```python
>>> def wrap(n):
...     def f():
...         print(n)
...     return f
...

>>> numbers = 'one', 'two', 'three'
>>> funcs = []
>>> for n in numbers:
...     funcs.append(wrap(n))
...
>>> for f in funcs:
...     f()
...
```

```plaintext
RESULTAT:
one
two
three
```

Dans une fonction normale, n est évalué au moment de la définition, lorsque la fonction est ajoutée à la liste : funcs.append(wrap(n)).

Maintenant, avec l'implémentation de la même logique avec une fonction lambda, observez le comportement inattendu :

```python
>>> numbers = 'one', 'two', 'three'
>>> funcs = []
>>> for n in numbers:
...     funcs.append(lambda: print(n))
...

>>> for f in funcs:
...     f()
...
```

```plaintext
RESULTAT:
three
three
three
```

Le résultat inattendu se produit parce que la variable libre n, telle qu'elle est implémentée, est liée au moment de l'exécution de l'expression lambda. 

La fonction lambda de Python sur la ligne 4 est une closure qui capture n, une variable libre liée au moment de l'exécution.

Au moment de l'exécution, en invoquant la fonction f sur la ligne 7, la valeur de n est de trois.

Pour surmonter ce problème, vous pouvez assigner la variable libre au moment de la définition comme suit :

```python
>>> numbers = 'one', 'two', 'three'
>>> funcs = []
>>> for n in numbers:
...     funcs.append(lambda n=n: print(n))
...

>>> for f in funcs:
...     f()
...
one
two
three
```

Une fonction de Python lambda se comporte comme une fonction normale en ce qui concerne les arguments.

Par conséquent, un paramètre lambda peut être initialisé avec une valeur par défaut : le paramètre n prend le n extérieur comme valeur par défaut.

La fonction Python lambda aurait pu être écrite sous la forme lambda x=n : print(x) et avoir le même résultat.

La fonction Python lambda est invoquée sans aucun argument sur la ligne 7, et elle utilise la valeur par défaut n fixée au moment de la définition.


### Les expressions lambdas et ses abus

Plusieurs exemples dans cet article, s'ils étaient écrits dans le contexte du code Python professionnel, seraient qualifiés d'abus.

Si vous vous trouvez à essayer de surmonter quelque chose qu'une expression lambda ne supporte pas, c'est probablement un signe qu'une fonction normale serait mieux adaptée.

La docstring pour une expression lambda dans la section précédente est un bon exemple.

Tenter de surmonter le fait qu'une fonction lambda de Python ne supporte pas les expressions est un autre drapeau rouge.

Les sections suivantes illustrent quelques exemples d'utilisations lambda qui devraient être évitées.

Ces exemples peuvent être des situations où, dans le contexte de Python lambda, le code présente le schéma suivant :

- Il ne suit pas le guide du style Python (PEP 8)
- Il est lourd et difficile à lire.
- Il est inutilement intelligent au prix d'une lisibilité difficile.

#### Lever une exception

Essayer de lever une exception dans un Python lambda devrait vous faire réfléchir à deux fois.

Il existe des moyens astucieux de le faire, mais il vaut mieux éviter de faire quelque chose comme ce qui suit :

```python
>>> def throw(ex): raise ex
>>> (lambda: throw(Exception('Something bad happened')))()
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    File "<stdin>", line 1, in <lambda>
    File "<stdin>", line 1, in throw
Exception: Something bad happened
```

Parce qu'une instruction n'est pas syntaxiquement correcte dans un corps Python lambda, la solution dans l'exemple ci-dessus consiste à abstraire l'appel d'instruction avec une fonction dédiée throw().

Ce type de contournement doit être évité.

Si vous rencontrez ce type de code, vous devriez envisager de refactoriser le code pour utiliser une fonction classique.

#### Style cryptique

Comme dans tout langage de programmation, vous trouverez du code Python qui peut être difficile à lire en raison du style utilisé.

Les fonctions lambda, de par leur concision, peuvent être propices à l'écriture de code difficile à lire.

L'exemple lambda suivant contient plusieurs mauvais choix de style :

```python
>>> (lambda _: list(map(lambda _: _ // 2, _)))([1,2,3,4,5,6,7,8,9,10])
[0, 1, 1, 2, 2, 3, 3, 4, 4, 5]
```

Le trait de soulignement (_) fait référence à une variable à laquelle vous n'avez pas besoin de vous référer explicitement.

Mais dans cet exemple, trois _ se réfèrent à des variables différentes.

Une amélioration de ce code pourrait consister à nommer les variables :

```python
>>> (lambda some_list: list(map(lambda n: n // 2,
                                some_list)))([1,2,3,4,5,6,7,8,9,10])
[0, 1, 1, 2, 2, 3, 3, 4, 4, 5]
```

Certes, il est encore difficile à lire.

En tirant toujours parti d'un lambda, une fonction régulière contribuerait grandement à rendre ce code plus lisible, en répartissant la logique sur quelques lignes et appels de fonction :

```python
>>> def div_items(some_list):
      div_by_two = lambda n: n // 2
      return map(div_by_two, some_list)
>>> list(div_items([1,2,3,4,5,6,7,8,9,10])))
[0, 1, 1, 2, 2, 3, 3, 4, 4, 5]
```

Ce n'est pas encore optimal mais vous montre un chemin possible pour rendre le code, et les fonctions Python lambda en particulier, plus lisibles.

Dans la partie alternatives aux lambdas, vous apprendrez à remplacer map() et lambda par des compréhensions de liste ou des expressions génératrices.

Cela améliorera considérablement la lisibilité du code.


#### Classes Python

Vous pouvez mais ne devez pas écrire des méthodes de classe comme les fonctions Python lambda.

L'exemple suivant est un code Python parfaitement légal mais présente un code Python non conventionnel qui repose sur lambda.

Par exemple, au lieu d'implémenter `__str__` comme une fonction régulière, il utilise un lambda.

De même, la marque et l'année sont des propriétés également implémentées avec des fonctions lambda, au lieu de fonctions régulières ou de décorateurs :

```python
class Car:
    """Car with methods as lambda functions."""
    def __init__(self, brand, year):
        self.brand = brand
        self.year = year

    brand = property(lambda self: getattr(self, '_brand'),
                     lambda self, value: setattr(self, '_brand', value))

    year = property(lambda self: getattr(self, '_year'),
                    lambda self, value: setattr(self, '_year', value))

    __str__ = lambda self: f'{self.brand} {self.year}'  # 1: error E731

    honk = lambda self: print('Honk!')     # 2: error E731
```

L'exécution d'un outil comme `flake8`, un outil d'application du guide de style, affichera les erreurs suivantes pour `__str__` et honk :

```plaintext
RESULTAT:
E731 do not assign a lambda expression, use a def
```

Bien que flake8 ne signale pas de problème pour l'utilisation des fonctions Python lambda dans les propriétés, elles sont difficiles à lire et sujettes à des erreurs en raison de l'utilisation de chaînes multiples comme `"_brand"` et `"_year"`.

La mise en œuvre correcte de `__str__` devrait être la suivante :

```python
def __str__(self):
    return f'{self.brand} {self.year}'
```

`brand` serait écrite comme suit :

```python
@property
def brand(self):
    return self._brand

@brand.setter
def brand(self, value):
    self._brand = value
```

En règle générale, dans le contexte du code écrit en Python, préférez les fonctions régulières aux expressions lambda.

Néanmoins, il y a des cas qui bénéficient de la syntaxe lambda, comme vous le verrez dans la section suivante.

### Utilisations appropriées des expressions lambda

Les lambdas en python ont tendance à faire l'objet de controverses.

Certains des arguments contre les lambdas en python sont :


- Problèmes de lisibilité
- L'imposition d'un mode de pensée fonctionnel
- Syntaxe lourde avec le mot-clé lambda

Malgré les débats passionnés qui remettent en question la simple existence de cette fonctionnalité en Python, les fonctions lambda ont des propriétés qui apportent parfois une valeur au langage Python et aux développeurs.

Les exemples suivants illustrent des scénarios où l'utilisation de fonctions lambda est non seulement appropriée mais encouragée dans le code Python.

#### Constructions fonctionnelles classiques

Les fonctions lambda sont régulièrement utilisées avec les fonctions intégrées [map(](https://docs.python.org/3/library/functions.html#map) et [filter()](https://docs.python.org/3/library/functions.html#filter), ainsi que [functools.reduce()](https://docs.python.org/3/library/functools.html?highlight=reduce#functools.reduce), exposées dans le module [functools](https://docs.python.org/3/library/functools.html).

Les trois exemples suivants illustrent respectivement l'utilisation de ces fonctions avec des expressions lambda comme compagnons :

```python
>>> list(map(lambda x: x.upper(), ['cat', 'dog', 'cow']))
['CAT', 'DOG', 'COW']
>>> list(filter(lambda x: 'o' in x, ['cat', 'dog', 'cow']))
['dog', 'cow']
>>> from functools import reduce
>>> reduce(lambda acc, x: f'{acc} | {x}', ['cat', 'dog', 'cow'])
'cat | dog | cow'
```

Vous devrez peut-être lire un code ressemblant aux exemples ci-dessus, mais avec des données plus pertinentes. 

Pour cette raison, il est important de reconnaître ces constructions. 

Néanmoins, ces constructions ont des alternatives équivalentes qui sont considérées comme plus pythoniennes. 

Dans Alternatives to Lambdas, vous apprendrez comment convertir des fonctions d'ordre supérieur et les lambdas qui les accompagnent en d'autres formes plus idiomatiques.

#### Fonctions clés

Les fonctions clés en Python sont des fonctions d'ordre supérieur qui prennent une clé de paramètre comme argument nommé.

La clé reçoit une fonction qui peut être un lambda.

Cette fonction influence directement l'algorithme piloté par la fonction clé elle-même. Voici quelques fonctions clés :


- sort() : méthode de la liste
- sorted(), min(), max() : fonctions intégrées
- nlargest() et nsmallest() : dans le module d'algorithme de file d'attente heapq

Imaginez que vous vouliez trier une liste d'identifiants représentés par des chaînes de caractères. 

Chaque ID est la concaténation de la chaîne d'ID et d'un nombre. 

Le tri de cette liste avec la fonction intégrée sorted(), par défaut, utilise un ordre lexicographique car les éléments de la liste sont des chaînes de caractères.

Pour influencer l'exécution du tri, vous pouvez attribuer un lambda à la clé d'argument nommée, de sorte que le tri utilise le numéro associé à l'ID :

```python
>>> ids = ['id1', 'id2', 'id30', 'id3', 'id22', 'id100']
>>> print(sorted(ids)) # Lexicographic sort
['id1', 'id100', 'id2', 'id22', 'id3', 'id30']
>>> sorted_ids = sorted(ids, key=lambda x: int(x[2:])) # Integer sort
>>> print(sorted_ids)
['id1', 'id2', 'id3', 'id22', 'id30', 'id100']
```

#### Monkey Patching

Pour les tests, il est parfois nécessaire de s'appuyer sur des résultats répétables, même si pendant l'exécution normale d'un logiciel donné, les résultats correspondants sont censés être différents, voire totalement aléatoires.

Supposons que vous vouliez tester une fonction qui, à l'exécution, gère des valeurs aléatoires.

Mais, pendant l'exécution du test, vous devez vous assurer que les valeurs prévisibles sont répétables.

L'exemple suivant montre comment, avec une fonction lambda, le patching de singe peut vous aider :

```python
from contextlib import contextmanager
import secrets

def gen_token():
    """Generate a random token."""
    return f'TOKEN_{secrets.token_hex(8)}'

@contextmanager
def mock_token():
    """Context manager to monkey patch the secrets.token_hex
    function during testing.
    """
    default_token_hex = secrets.token_hex
    secrets.token_hex = lambda _: 'feedfacecafebeef'
    yield
    secrets.token_hex = default_token_hex

def test_gen_key():
    """Test the random token."""
    with mock_token():
        assert gen_token() == f"TOKEN_{'feedfacecafebeef'}"

test_gen_key()
```

Un gestionnaire de contexte permet d'isoler le fonctionnement du patching de singe d'une fonction de la bibliothèque standard (secrets, dans cet exemple).

La fonction lambda affectée à secrets.token_hex() remplace le comportement par défaut en renvoyant une valeur statique.

Cela permet de tester toute fonction dépendant de token_hex() de manière prévisible.

Avant de quitter le gestionnaire de contexte, le comportement par défaut de token_hex() est rétabli pour éliminer tout effet secondaire inattendu qui affecterait d'autres domaines du test pouvant dépendre du comportement par défaut de token_hex().

Les cadres de test unitaire comme unittest et pytest portent ce concept à un niveau de sophistication plus élevé.

Avec pytest, toujours en utilisant une fonction lambda, le même exemple devient plus élégant et plus concis :

```python
import secrets

def gen_token():
    return f'TOKEN_{secrets.token_hex(8)}'

def test_gen_key(monkeypatch):
    monkeypatch.setattr('secrets.token_hex', lambda _: 'feedfacecafebeef')
    assert gen_token() == f"TOKEN_{'feedfacecafebeef'}"
```

Avec le dispositif pytest monkeypatch, `secrets.token_hex()` est écrasé par un lambda qui retournera une valeur déterminée, feedfacecafebeef, permettant de valider le test.

La fixture pytest monkeypatch  vous permet de contrôler l'étendue de l'écrasement.

Dans l'exemple ci-dessus, l'invocation de `secrets.token_hex()` dans les tests suivants, sans utiliser le monkey patching, exécuterait l'implémentation normale de cette fonction.

L'exécution du test pytest donne le résultat suivant :

```shell
$ pytest test_token.py -v
============================= test session starts ==============================
platform linux -- Python 3.8.2, pytest-4.3.0, py-1.8.0, pluggy-0.9.0
cachedir: .pytest_cache
rootdir: /home/andre/AB/tools/bpython, inifile:
collected 1 item

test_token.py::test_gen_key PASSED                                       [100%]

=========================== 1 passed in 0.01 seconds ===========================
```

### Alternatives aux lambdas

S'il existe de bonnes raisons d'utiliser les lambda, il y a aussi des cas où leur utilisation est contestée. Quelles sont donc les alternatives ?

Les fonctions d'ordre supérieur comme `map()`, `filter()` et `functools.reduce()` peuvent être converties en des formes plus élégantes avec de légères touches de créativité, en particulier pour la compréhension de listes ou les générateurs.

#### Map

La fonction built-in `map()` prend une fonction comme premier argument et l'applique à chacun des éléments de l'itérable placé en deuxième argument.

Rappel : itérables peuvent être, par exemple, des chaînes de caractères, des listes ou des tuples.

`map()` renvoie un itérateur correspondant à la liste transformée.

Par exemple, si vous souhaitez transformer une liste de chaînes de caractères en une nouvelle liste avec chaque chaîne en majuscule, vous pouvez utiliser `map()`, comme suit :

```python
>>> list(map(lambda x: x.capitalize(), ['cat', 'dog', 'cow']))
```

```plaintext
RESULTAT:
['Cat', 'Dog', 'Cow']
```

Vous devez invoquer `list()` pour convertir l'itérateur renvoyé par `map()` en une liste étendue qui peut être affichée dans l'interpréteur de commandes Python.

L'utilisation de la compréhension de liste élimine le besoin de définir et d'invoquer la fonction lambda :

```python
>>> [x.capitalize() for x in ['cat', 'dog', 'cow']]
```

```plaintext
RESULTAT:
['Cat', 'Dog', 'Cow']
```

#### Filter

Le filtre de fonction builtin `filter()`, autre construction fonctionnelle classique, peut être converti en une compréhension de liste.

Il prend un prédicat comme premier argument et un itérable comme second argument.

Il construit un itérateur contenant tous les éléments de la collection initiale qui satisfont la fonction de prédicat.

Voici un exemple qui filtre tous les nombres pairs dans une liste d'entiers donnée :

```python
>>> even = lambda x: x%2 == 0
>>> list(filter(even, range(11)))
```

```plaintext
RESULTAT:
[0, 2, 4, 6, 8, 10]
```

Notez que `filter()` renvoie un itérateur, d'où la nécessité d'invoquer la liste de types intégrée qui construit une liste avec un itérateur.

L'implémentation utilisant la construction de la compréhension de la liste donne ce qui suit :

```python
>>> [x for x in range(11) if x%2 == 0]
```

```plaintext
RESULTAT:
[0, 2, 4, 6, 8, 10]
```

#### Reduce

Depuis Python 3, `reduce()` est passé d'une fonction intégrée à une fonction de module functools.

Comme `map()` et `filter()`, ses deux premiers arguments sont respectivement une fonction et un itérable.

Il peut également prendre un initialisateur comme troisième argument qui est utilisé comme valeur initiale de l'accumulateur résultant.

Pour chaque élément de l'itérable, `reduce()` applique la fonction et accumule le résultat qui est renvoyé lorsque l'itérable est épuisé.

Pour appliquer `reduce()` à une liste de paires et calculer la somme du premier élément de chaque paire, vous pouvez écrire ceci :


```python
>>> import functools
>>> pairs = [(1, 'a'), (2, 'b'), (3, 'c')]
>>> functools.reduce(lambda acc, pair: acc + pair[0], pairs, 0)
```

```plaintext
RESULTAT:
6
```

Une approche plus idiomatique utilisant une expression génératrice, comme argument pour `sum()` dans l'exemple, est la suivante :

```python
>>> pairs = [(1, 'a'), (2, 'b'), (3, 'c')]
>>> sum(x[0] for x in pairs)
```

```plaintext
RESULTAT:
6
```


Une solution légèrement différente et éventuellement plus propre évite de devoir accéder explicitement au premier élément de la paire et d'utiliser à la place le déballage :

```python
>>> pairs = [(1, 'a'), (2, 'b'), (3, 'c')]
>>> sum(x for x, _ in pairs)
```

```plaintext
RESULTAT:
6
```

L'utilisation de l'underscore (_) est une convention Python indiquant que vous pouvez ignorer la deuxième valeur de la paire.

`sum()` prend un argument unique, de sorte que le générateur n'a pas besoin d'être entre parenthèses.


## Les Lambdas sont pythonique ou une orgie syntaxique ?

Pour conclure rapidement utiliser des lambdas c'est comme utiliser des mots techniques ou en latin.

C'est cool quand il y en à un dans une phrase courte, par contre c'est épuisant quand ils s'enchaînent les uns à la suite des autres.

> Un bon dev est celui qui est lu comme les autres


