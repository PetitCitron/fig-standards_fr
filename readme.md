# Résumé des PSR - PHP Standard Recommendation Fr en Français

  Voici regroupé des notes sur les PSR pour bien coder en PHP.
  Source : https://www.php-fig.org/psr/

## Sommaire

* [1 . PSR - DE CODING STYLE](#1--psr---de-coding-style)
* [1.1 PSR-1 : Norme de base pour coder](#11-psr-1--norme-de-base-pour-coder)
* [1.2 PSR-12: Style de codage étendu](#12-psr-12-style-de-codage-étendu)
* [1.2.1 Les Fichiers :](#121-les-fichiers-)
* [1.2.2 Les Lignes :](#122-les-lignes-)
* [1.2.3 L'Indentation :](#123-lindentation-)
* [1.2.4  Mots clés et types :](#124--mots-clés-et-types-)
* [1.2.5 En-tête de fichier PHP:](#125-en-tête-de-fichier-php)
   * [1.2.5.1 Fichiers HTML et PHP :](#1251-fichiers-html-et-php-)
* [1.2.6 La profondeur maximale des espaces de noms :](#126-la-profondeur-maximale-des-espaces-de-noms-)
* [1.2.7 Le mot-clé "declare" :](#127-le-mot-clé-declare-)
* [1.2.8 Classes, propriétés et méthodes :](#128-classes-propriétés-et-méthodes-)
   * [1.2.8.1 Les Traits :](#1281-les-traits-)
   * [1.2.8.2  Propriétés et constantes](#1282--propriétés-et-constantes)
* [1.2.9 Méthodes et fonctions :](#129-méthodes-et-fonctions-)
   * [1.2.9.1 : Arguments de méthode et de fonction](#1291--arguments-de-méthode-et-de-fonction)
   * [1.2.9.2 :  abstract, final et static](#1292---abstract-final-et-static)
   * [1.2.9.3 : Appels de méthode et de fonction](#1293--appels-de-méthode-et-de-fonction)
* [1.2.10 Structure de contrôles :](#1210-structure-de-contrôles-)
   * [1.2.10.1 if, elseif, else :](#12101-if-elseif-else-)
   * [1.2.10.2 switch, case :](#12102-switch-case-)
   * [1.2.10.3  while, do while](#12103--while-do-while)
   * [1.2.10.4  for](#12104--for)
   * [1.2.10.5 foreach](#12105-foreach)
   * [1.2.10.6 try, catch, finally](#12106-try-catch-finally)
* [1.2.11 Opérateurs](#1211-opérateurs)
   * [1.2.11.1 opérateurs unaires:](#12111-opérateurs-unaires)
   * [1.2.11.2 opérateurs binaires :](#12112-opérateurs-binaires-)
   * [1.2.11.3 opérateurs ternaires :](#12113-opérateurs-ternaires-)
* [1.2.12 Les Closures](#1212-les-closures)
* [1.2.13 Les Classes Anonymes](#1213-les-classes-anonymes)
* [2 PSR - Documentation PHPDoc - DocStrings](#2-psr---documentation-phpdoc---docstrings)
* [2.1 PSR-5 : PHPDoc Standard](#21-psr-5--phpdoc-standard)
* [2.2 PSR-19 : PHPDoc tags](#22-psr-19--phpdoc-tags)
* [3 PSR - D'interfaces](#3-psr---dinterfaces)
* [3.1 PSR-3 : Logger Interface - Interface de Journalisation](#31-psr-3--logger-interface---interface-de-journalisation)
* [3.2 PSR-4 : Autoloader - Interface de chargement automatique](#32-psr-4--autoloader---interface-de-chargement-automatique)
* [3.4 PSR-6: Interface de mise en cache](#34-psr-6-interface-de-mise-en-cache)
* [3.5 PSR-7 : HTTP message interfaces - Interface de manipulate des Messages HTTP](#35-psr-7--http-message-interfaces---interface-de-manipulate-des-messages-http)
* [3.6 PSR-11: Container interface](#36-psr-11-container-interface)
* [3.7 PSR-13: Link definition interfaces - Interface des Liens hypermédias](#37-psr-13-link-definition-interfaces---interface-des-liens-hypermédias)
* [3.8 PSR-14:  Event Dispatcher - Interface des Répartiteurs d'événements](#38-psr-14--event-dispatcher---interface-des-répartiteurs-dévénements)
* [3.9 PSR-15: HTTP Server Request Handlers | Gestionnaire de requêtes de serveur HTTP](#39-psr-15-http-server-request-handlers--gestionnaire-de-requêtes-de-serveur-http)
* [3.10 PSR-17 :  HTTP  Factories](#310-psr-17---http--factories)
* [3.11 PSR-18 :  HTTP  Client](#311-psr-18---http--client)


## 1 . PSR - DE CODING STYLE

### 1.1 PSR-1 : Norme de base pour coder

  * les fichiers *DOIVENT* utiliser uniquement `<?php` et `<?=`
  * les fichiers *DOIVENT* utiliser UTF-8 sans BOM pour écrire le code PHP
  * Les fichiers DEVRAIENT soit déclarer des symboles ( classe, fonctions, constantes), soit provoquer délclencher des effets secondaires (générer une sortie, modifier les parmètres, etc ...). Ils ne DEVRAIENT pas faire les deux. Cela permet d'importer des classes et fonctions sans risque, d'eviter de nombreux effets de bords. D'isoler le code actif, du code passif.
  * Les Namespaces et classes DOIVENT suivre les PSR  “autoloading” : [[PSR-0](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md), [PSR-4](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md)].
    * Chaque classe est dans un fichier unique portant son Nom
    * L'espace de nom de la classe doit comporter au minimum 1 niveau de fournisseur.
  
       ex : 
  
        ```php
        <?php
        // PHP 5.3 and later:
        namespace Vendor\Model;
        
        class Foo
        {
        }
        ```
  
  * Les **classes** DOIVENT  $être nommée en `StudlyCaps` (`PascalCase`) ( la première lettre de chaque mot est en majuscule, y compris la toute première lettre.)
  * Les **constantes** DOIVENT être nommée en `MAJUSCULE` (séparé par des underscore `_`)
  * Le nommage des **propriété est libre**, il suffit d'établir une convention de nommage de la suivre de manière cohérente dans une portée raisonnable.
    * ex : portée du fornisseur, du package, d'une classe ou d'une méthode
    * convention autorisée : `$StudyCaps`, `$camelCase`, `under_score`
  * les **méthodes** DOIVENT être déclarée en `camelCase()`
  * plus : https://www.php-fig.org/psr/psr-1/

### 1.2 PSR-12: Style de codage étendu

  * Le but : Réduire le travail de compréhension lors de la lecture de code provenant de différents développeurs.
  * Il s'agit de règle sur la façon de formater le code PHP.
  * Quand plusieurs developpeurs travaillent sur plusieurs projets, il est utile defixer des directives, c'est le but de cette PSR.
  * Cette PSR montre un exemple de l'établissement de règles partagées.

#### 1.2.1 Les Fichiers :

  * Tous les fichiers PHP DOIVENT utiliser la **fin de ligne Unix LF (saut de ligne)** uniquement.
  * Tous les fichiers PHP DOIVENT se terminer par une ligne non vierge, terminée par un seul LF.
  * La `?> `balise de fermeture DOIT être omise des fichiers contenant uniquement PHP.

#### 1.2.2 Les Lignes :

  * Il NE DOIT **PAS y avoir de limite stricte** sur la longueur de la ligne.
  * **La limite souple** de la longueur de la ligne DOIT être de 120 caractères.
  * Les lignes NE DEVRAIENT PAS dépasser 80 caractères; les lignes plus longues DEVRAIENT être divisées en plusieurs lignes subséquentes ne dépassant pas 80 caractères chacune.
  * Il NE DOIT PAS y avoir **d'espaces blancs à la fin des lignes**.
  * Des lignes vierges PEUVENT être ajoutées pour améliorer la lisibilité et pour indiquer les blocs de code associés, sauf lorsque cela est explicitement interdit.
  * Il NE DOIT PAS y avoir plus d'une instruction par ligne.

#### 1.2.3 L'Indentation :

  * Le code DOIT utiliser un retrait de 4 espaces pour chaque niveau d'indentation
  * PAS utiliser de tabulations pour l'indentation.

#### 1.2.4  Mots clés et types :

  * Tous les mots-clés et types PHP réservés DOIVENT être en minuscules (ex : `true/false`).
  * Tous les nouveaux types et mots-clés ajoutés aux futures versions de PHP DOIVENT être en minuscules.
  * Les formes courtes des mots-clés de type DOIVENT être utilisée. ( ex `bool`  à la place de `boolean`,  et`int`au lieu de `integer`etc.)

#### 1.2.5 En-tête de fichier PHP: 

  * Le `<?php` est toujours la première ligne du fichier, sans aucune autre instruction.
  * Les différents blocs DOIVENT être séparé par une seule ligne vierge
  * Les blocs ne DOIVENT pas contenir de ligne vierge
  * Les instructions d'importation NE DOIVENT jamais commencer par une barre oblique inversée, elles doivent tjours êtres pleinement qualifiées.
  * Chaque bloc DOIT être dans l'ordre ci-dessous :

    * le `<?php`
    * le Dockblock du fichier
    * Une ou plusieurs instructions de déclaration
    * Déclaration de l'espace de nom du fichier  `namespace`
    * Un ou plusieurs imports de classe via 'use'
    * Un ou plusieurs imports de fonctions via 'use'
    * Un ou plusieurs imports de constantes via 'use'
    * Le reste du code dans le fichier

    ##### 1.2.5.1 Fichiers HTML et PHP :
    
      * Faire la même chose, même si le reste du fichier est un mélange de HTML et PHP
      * La première ligne est un `<?php` même si la suite du code consiste simplement à fermer la balise `?>`
      * Liste complète de tous les blocs et de l'ordre :
    
        ```php
        <?php
        
        /**
         * This file contains an example of coding styles.
         */
        
        declare(strict_types=1);
        
        namespace Vendor\Package;
        
        use Vendor\Package\{ClassA as A, ClassB, ClassC as C};
        use Vendor\Package\SomeNamespace\ClassD as D;
        use Vendor\Package\AnotherNamespace\ClassE as E;
        
        use function Vendor\Package\{functionA, functionB, functionC};
        use function Another\Vendor\functionD;
        
        use const Vendor\Package\{CONSTANT_A, CONSTANT_B, CONSTANT_C};
        use const Another\Vendor\CONSTANT_D;
        
        /**
         * FooBar is an example class.
         */
        class FooBar
        {
            // ... additional PHP code ...
        }
        ```

#### 1.2.6 La profondeur maximale des espaces de noms :

  * Valide

    ```php
    <?php
    
    use Vendor\Package\SomeNamespace\{
        SubnamespaceOne\ClassA,
        SubnamespaceOne\ClassB,
        SubnamespaceTwo\ClassY,
        ClassZ,
    };
    ```

  * Invalide :

    ```php
    <?php
    
    use Vendor\Package\SomeNamespace\{
        SubnamespaceOne\AnotherNamespace\ClassA,
        SubnamespaceOne\ClassB,
        ClassZ,
    };
    ```
#### 1.2.7 Le mot-clé "declare" :

  * Si on déclare des types stricts dans des fichiers contenant du balisage en dehors des balises d'ouverture et de fermeture PHP, la déclaration DOIT être sur la première ligne du fichier et inclure une balise PHP d'ouverture, la déclaration des types stricts et la balise de fermeture.

    ```php
    <?php declare(strict_types=1) ?>
    <html>
    <body>
        <?php
            // ... additional PHP code ...
        ?>
    </body>
    </html>
    ```

  * Les instructions `declare` NE DOIVENT contenir aucun espace et DOIVENT être exactement `declare(strict_types=1)`
  * Les instructions de délcaration de bloc sont aurisées et DOIVENT être formatées comme ci-dessous

    ```
    declare(ticks=1) {
        // some code
    }
    ```

#### 1.2.8 Classes, propriétés et méthodes :

  * le terme "classe" fit référence à tous les classes, interfaces, traits.
  * Toute accolade fermante NE DOIT PAS être suivie d'un commentaire ou d'une déclaration sur la même ligne.
  * Lors de l'instanciation d'une nouvelle classe, les parenthèses DOIVENT toujours être présentes même si aucun argument n'est passé au constructeur.

    ```php
    new Foo();
    ```

  * Les mots `extends` et `implements`  et DOIVENT être déclarés sur la même ligne que le nom de la classe.
  * L'accolade ouvrante de la classe DOIT aller sur sa propre ligne et NE DOIVENT PAS être précédées ou suivies d'une ligne vide. .
  * L'accolade fermante de la classe DOIT aller sur la ligne suivante après le corps et NE DOIVENT PAS être précédées d'une ligne vide.

    ```php
    <?php
    
    namespace Vendor\Package;
    
    use FooClass;
    use BarClass as Bar;
    use OtherVendor\OtherPackage\BazClass;
    
    class ClassName extends ParentClass implements \ArrayAccess, \Countable
    {
        // constants, properties, methods
    }
    ```

  * Les listes `implements`et, dans le cas des interfaces, `extends` PEUVENT être divisées sur plusieurs lignes, où chaque ligne suivante est indentée une fois. Le premier élément de la liste DOIT être sur la ligne suivante, et il DOIT y avoir une seule interface par ligne.

    ```php
    <?php
    
        namespace Vendor\Package;
        
        use FooClass;
        use BarClass as Bar;
        use OtherVendor\OtherPackage\BazClass;
        
        class ClassName extends ParentClass implements
            \ArrayAccess,
            \Countable,
            \Serializable
        {
            // constants, properties, methods
        }
    ```

##### 1.2.8.1 Les Traits :

  * `use` DOIT être déclaré sur la ligne suivant après l'ouverture d'accolade.
  * Chaque trait importé doit être sur sa propore ligne et son propre `use`.
  * Si la classe n'a rien après le dernier `use`, l'accolade fermante DOIT être sur la ligne suivante.
  * Sinon il doit y avoir une ligne vide après le dernier `use`

    ```php
    <?php
    
    namespace Vendor\Package;
    
    use Vendor\Package\FirstTrait;
    use Vendor\Package\SecondTrait;
    use Vendor\Package\ThirdTrait;
    
    class ClassName
    {
        use FirstTrait;
        use SecondTrait;
        use ThirdTrait;
    }
    ```

  * Lorsque vous utilisez les opérateurs `insteadof`et `as`, ils doivent être utilisés tenant compte de l'indentation, de l'espacement et des nouvelles lignes.

    ```php
    <?php
    
    class Talker
    {
        use A;
        use B {
            A::smallTalk insteadof B;
        }
        use C {
            B::bigTalk insteadof C;
            C::mediumTalk as FooBar;
        }
    }
    ```


##### 1.2.8.2  Propriétés et constantes

  * La visibilité DOIT être déclarée sur toutes les propriétés.

  * La visibilité DOIT être déclarée sur toutes les constantes 

  * Le `var`mot clé NE DOIT PAS être utilisé pour déclarer une propriété.

  * Il NE DOIT PAS y avoir plus d'une propriété déclarée par instruction.

  * Les noms de propriété NE DOIVENT PAS être précédés d'un seul trait de soulignement pour indiquer une visibilité protégée ou privée. Autrement dit, un préfixe de soulignement n'a explicitement aucune signification. 

    * invalide :

    ```php
    <?php
    
    namespace Vendor\Package;
    
    class ClassName
    {
       public $_pythonPrivate = null;
    }
    ```

    * valide :

    ```php
    <?php
    
    namespace Vendor\Package;
    
    class ClassName
    {
       private $pythonPrivate = null;
    }
    ```

  * Il DOIT y avoir un espace entre la déclaration de type et le nom de la propriété.
  * Une déclaration de propriété ressemble à :

    ```php
    <?php
    
    namespace Vendor\Package;
    
    class ClassName
    {
        public $foo = null;
        public static int $bar = 0;
    }
    ```

#### 1.2.9 Méthodes et fonctions :

  * La visibilité DOIT être déclarée sur toutes les méthodes.
  * Les noms de méthode NE DOIVENT PAS être précédés d'un seul trait de soulignement pour indiquer une visibilité protégée ou privée.

  * invalide :

    ```php
    <?php
    
    namespace Vendor\Package;
    
    class ClassName
    {
        public function _dontTouchPythonStyle() 
        {
          // corps
        }
    }
    ```

  * valide :
  
    ```php
    <?php
    
    namespace Vendor\Package;
    
    class ClassName
    {
        private function dontTouchPythonStyle() 
        {
          // corps
        }
    }
    ```

  * Il DOIT y avoir un espace entre la déclaration de type et le nom de la propriété.
  * L'accolade ouvrante DOIT aller sur sa propre ligne, et l'accolade fermante DOIT aller sur la ligne suivante suivant le corps. 
  * Il NE DOIT PAS y avoir d'espace après la parenthèse ouvrante, et il NE DOIT PAS y avoir d'espace avant la parenthèse fermante.
  * Une déclaration de méthode ressemble à ce qui suit. Notez l'emplacement des parenthèses, virgules, espaces et accolades:

    ```php
    <?php
    
    namespace Vendor\Package;
    
    class ClassName
    {
        public function fooBarBaz($arg1, &$arg2, $arg3 = [])
        {
            // method body
        }
    }
    ```

  * Une déclaration de fonction ressemble à ce qui suit. Notez l'emplacement des parenthèses, virgules, espaces et accolades:

    ```php
    <?php
    
    function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // function body
    }
    ```

##### 1.2.9.1 : Arguments de méthode et de fonction

  * Dans la liste d'arguments, il NE DOIT PAS y avoir d'espace avant chaque virgule.
  * IL DOIT y avoir un espace après chaque virgule.
  * Les arguments de méthode et de fonction avec des valeurs par défaut DOIVENT aller à la fin de la liste d'arguments.

    ```php
    <?php
    
    namespace Vendor\Package;
    
    class ClassName
    {
        public function foo(int $arg1, &$arg2, $arg3 = [])
        {
            // method body
        }
    }
    ```

  * Les listes d'arguments PEUVENT être divisées sur plusieurs lignes.
    * Chaque ligne suivante étant indentée une fois.
    * Le premier élément de la liste DOIT être sur la ligne suivante.
    * Il DOIT y avoir un seul argument par ligne

      ```php
      <?php
      
      namespace Vendor\Package;
      
      class ClassName
      {
          public function aVeryLongMethodName(
              ClassTypeHint $arg1,
              &$arg2,
              array $arg3 = []
          ) {
              // method body
          }
      }
      ```

      

  * Lorsque vous avez une déclaration de type de retour présente :

    * il DOIT y avoir un espace après les deux points suivi de la déclaration de type.
    * Les deux points et la déclaration DOIVENT être sur la même ligne que la liste d'arguments fermant la parenthèse sans espaces entre les deux caractères.
  
       ```php
      ?php
      
      declare(strict_types=1);
      
      namespace Vendor\Package;
      
      class ReturnTypeVariations
      {
          public function functionName(int $arg1, $arg2): string
          {
              return 'foo';
          }
      
          public function anotherFunction(
              string $foo,
              string $bar,
              int $baz
          ): string {
              return 'foo';
          }
      }
       ```

  * Dans les déclarations de type Nullable, il NE DOIT PAS y avoir d'espace entre le point d'interrogation et le type.

    ```php
    <?php
    
    declare(strict_types=1);
    
    namespace Vendor\Package;
    
    class ReturnTypeVariations
    {
        public function functionName(?string $arg1, ?int &$arg2): ?string
        {
            return 'foo';
        }
    }
    ```

  * Lorsque vous utilisez l'opérateur de référence `&`avant un argument, il NE DOIT PAS y avoir d'espace après lui, comme dans l'exemple précédent.
  * Il NE DOIT PAS y avoir d'espace entre l'opérateur variadique à trois points et le nom de l'argument:

    ```php
    public function process(string $algorithm, ...$parts)
    {
        // processing
    }
    ```

  * Lors de la combinaison de l'opérateur de référence et de l'opérateur variadique à trois points, il NE DOIT PAS y avoir d'espace entre les deux:

    ```php
    public function process(string $algorithm, &...$parts)
    {
        // processing
    }
    ```

##### 1.2.9.2 :  abstract, final et static

  * Les déclarations `abstract` et `final` DOIVENT précéder la déclaration de visibilité.
  *  la déclaration `static` DOIT venir après la déclaration de visibilité.

  ```php
  <?php
  
  namespace Vendor\Package;
  
  abstract class ClassName
  {
      protected static $foo;
  
      abstract protected function zim();
  
      final public static function bar()
      {
          // method body
      }
  }
  ```

##### 1.2.9.3 : Appels de méthode et de fonction

  * Il NE DOIT PAS y avoir d'espace entre le nom de la méthode ou de la fonction et la parenthèse ouvrante.
  * Il NE DOIT PAS y avoir d'espace après la parenthèse ouvrante.
  * Il NE DOIT PAS y avoir d'espace avant la parenthèse fermante.
  * Dans la liste d'arguments, il NE DOIT PAS y avoir d'espace avant chaque virgule **mais après**

    ```php
    <?php
    
    bar();
    $foo->bar($arg1);
    Foo::bar($arg2, $arg3);
    ```

  * Les listes d'arguments PEUVENT être divisées sur plusieurs lignes :

    * Chaque ligne suivante étant indentée une fois.
    * Le premier élément de la liste DOIT être sur la ligne suivante.
    * Il DOIT y avoir un seul argument par ligne.

      ```php
      <?php
      
      $foo->bar(
          $longArgument,
          $longerArgument,
          $muchLongerArgument
      );
      <?php
      
      somefunction($foo, $bar, [
        // ...
      ], $baz);
      
      $app->get('/hello/{name}', function ($name) use ($app) {
          return 'Hello ' . $app->escape($name);
      });
      ```

#### 1.2.10 Structure de contrôles :

  * Il DOIT y avoir un espace après le mot clé de la structure de contrôle.
  * Il NE DOIT PAS y avoir d'espace après la parenthèse ouvrante.
  * Il NE DOIT PAS y avoir d'espace avant la parenthèse fermante
  * Il DOIT y avoir un espace entre la parenthèse fermante et l'accolade ouvrante.
  * Le corps de la structure DOIT être indenté une fois.
  * Le corps DOIT être sur la ligne suivante après l'accolade d'ouverture.
  * L'accolade de fermeture DOIT être sur la ligne suivante après le corps.
  * **Le corps de chaque structure DOIT être entouré d'accolades.**

##### 1.2.10.1 if, elseif, else :

  * Utilisez `elseif` (pour que les mots-clés de contrôle soit tous des mots uniques)
  * Les expressions entre parenthèses PEUVENT être divisées sur plusieurs lignes, chaque ligne suivante étant indentée au moins une fois. Ce faisant, la première condition DOIT être sur la ligne suivante. La parenthèse fermante et l'accolade ouvrante DOIVENT être placées ensemble sur leur propre ligne avec un espace entre elles. Les opérateurs booléens entre les conditions DOIVENT toujours être au début ou à la fin de la ligne, pas un mélange des deux.

    ```php
      <?php
      
      if ($expr1) {
          // if body
      } elseif ($expr2) {
          // elseif body
      } else {
          // else body;
      }
      ```
    
      ```php
      <?php
      
      if (
          $expr1
          && $expr2
      ) {
          // if body
      } elseif (
          $expr3
          && $expr4
      ) {
          // elseif body
      }
    ```

##### 1.2.10.2 switch, case :

  * L'instruction  `case` DOIT être indentée une fois à partir de `switch`.
  * Il DOIT y avoir un commentaire tel que `// no break`lorsque son absence est intentionnelle.

    ```php
    <?php
    
    switch ($expr) {
        case 0:
            echo 'First case, with a break';
            break;
        case 1:
            echo 'Second case, which falls through';
            // no break
        case 2:
        case 3:
        case 4:
            echo 'Third case, return instead of break';
            return;
        default:
            echo 'Default case';
            break;
    }
    ```

* Les expressions entre parenthèses PEUVENT être divisées sur plusieurs ligne (idem que le if)

##### 1.2.10.3  while, do while

  ```php
  <?php
  
  while (
      $expr1
      && $expr2
  ) {
      // structure body
  }
  ```
  
  ```php
  <?php
  
  do {
      // structure body;
  } while ($expr);
  ```

##### 1.2.10.4  for

  ```php
  <?php
  
  for ($i = 0; $i < 10; $i++) {
      // for body
  }
  ```

  ```php
  <?php
  
  for (
      $i = 0;
      $i < 10;
      $i++
  ) {
      // for body
  }
  ```

##### 1.2.10.5 foreach

  ```php
  <?php
  
  foreach ($iterable as $key => $value) {
      // foreach body
  }
  ```

##### 1.2.10.6 try, catch, finally

  ```php
  <?php
  
  try {
      // try body
  } catch (FirstThrowableType $e) {
      // catch body
  } catch (OtherThrowableType | AnotherThrowableType $e) {
      // catch body
  } finally {
      // finally body
  }
  ```

#### 1.2.11 Opérateurs

##### 1.2.11.1 opérateurs unaires: 

  * Les opérateurs d'incrémentation / décrémentation NE DOIVENT PAS avoir d'espace entre l'opérateur et l'opérande.

    ```php
    $i++;
    ++$j;
    ```

  * Les opérateurs de conversion de type NE DOIVENT PAS avoir d'espace entre les parenthèses:

    ```php
    $intValue = (int) $input;
    ```

##### 1.2.11.2 opérateurs binaires :

  * Tous les opérateurs d' [arithmétique](http://php.net/manual/en/language.operators.arithmetic.php) binaire , de [comparaison](http://php.net/manual/en/language.operators.comparison.php) , d' [affectation](http://php.net/manual/en/language.operators.assignment.php) , de [bit](http://php.net/manual/en/language.operators.bitwise.php) , [logique](http://php.net/manual/en/language.operators.logical.php) , de [chaîne](http://php.net/manual/en/language.operators.string.php) et de [type](http://php.net/manual/en/language.operators.type.php) DOIVENT être précédés et suivis d'au moins un espace:

    ```php
    if ($a === $b) {
        $foo = $bar ?? $a ?? $b;
    } elseif ($a > $b) {
        $foo = $a + $b * $c;
    }
    ```

##### 1.2.11.3 opérateurs ternaires :

  * L'opérateur conditionnel ou opérateur ternaire, DOIT être précédé et suivi d'au moins un espace autour des caractères ? et ::

    ```php
    $variable = $foo ? 'foo' : 'bar';
    ```

    

  * Lorsque l'opérande du milieu de l'opérateur conditionnel est omis, l'opérateur DOIT suivre les mêmes règles de style que les autres opérateurs de [comparaison](http://php.net/manual/en/language.operators.comparison.php) binaire :

    ```php
    $variable = $foo ?: 'bar';
    
    ```

#### 1.2.12 Les Closures

  * DOIVENT être déclarées avec un espace après le mot-clé `function` et espace avant et après le mot-clé `use`.
  * L'accolade ouvrante DOIT aller sur la même ligne et l'accolade fermante DOIT aller sur la ligne suivante suivant le corps.
  * Il NE DOIT PAS y avoir d'espace après la parenthèse ouvrante de la liste d'arguments ou de la liste de variables, et il NE DOIT PAS y avoir d'espace avant la parenthèse fermante de la liste d'arguments ou de la liste de variables.
  * Dans la liste d'arguments et la liste de variables, il NE DOIT PAS y avoir d'espace avant chaque virgule, et il DOIT y avoir un espace après chaque virgule.
  * Les arguments de fermeture avec des valeurs par défaut DOIVENT être à la fin de la liste d'arguments.
  * Si un type de retour est présent, il DOIT suivre les mêmes règles qu'avec les fonctions et méthodes normales.

    ```php
    <?php
    
    $closureWithArgs = function ($arg1, $arg2) {
        // body
    };
    
    $closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
        // body
    };
    
    $closureWithArgsVarsAndReturn = function ($arg1, $arg2) use ($var1, $var2): bool {
        // body
    };
    ```

  * Les listes d'arguments et les listes de variables PEUVENT être divisées sur plusieurs lignes: 

    ```php
    <?php
    
    $longArgs_noVars = function (
        $longArgument,
        $longerArgument,
        $muchLongerArgument
    ) {
       // body
    };
    
    $noArgs_longVars = function () use (
        $longVar1,
        $longerVar2,
        $muchLongerVar3
    ) {
       // body
    };
    
    $longArgs_longVars = function (
        $longArgument,
        $longerArgument,
        $muchLongerArgument
    ) use (
        $longVar1,
        $longerVar2,
        $muchLongerVar3
    ) {
       // body
    };
    
    $longArgs_shortVars = function (
        $longArgument,
        $longerArgument,
        $muchLongerArgument
    ) use ($var1) {
       // body
    };
    
    $shortArgs_longVars = function ($arg) use (
        $longVar1,
        $longerVar2,
        $muchLongerVar3
    ) {
       // body
    };
    ```

  * Les règles de mise en forme s'appliquent également lorsque la fermeture est utilisée directement dans un appel de fonction ou de méthode en tant qu'argument :

    ```php
    <?php
    
    $foo->bar(
        $arg1,
        function ($arg2) use ($var1) {
            // body
        },
        $arg3
    );
    ```

#### 1.2.13 Les Classes Anonymes

  * Les classes anonymes DOIVENT suivre les mêmes directives et principes que les Closures.

    ```php
    <?php
    
    $instance = new class {};
    ```

    ```php
    <?php
    
    // Brace on the same line
    $instance = new class extends \Foo implements \HandleableInterface {
        // Class content
    };
    
    // Brace on the next line
    $instance = new class extends \Foo implements
        \ArrayAccess,
        \Countable,
        \Serializable
    {
        // Class content
    };
    ```

## 2 PSR - Documentation PHPDoc - DocStrings

### 2.1 PSR-5 : PHPDoc Standard

*  TODO

### 2.2 PSR-19 : PHPDoc tags

* TODO

## 3 PSR - D'interfaces

Les interfaces sont des modèles de code, de classe ayant pour objectif de standardiser les framework et les librairies. 
L'objectif est de retrouver les mêmes logiques, méthodes quelque soit les framework et librairies utilisée.
Cela permet d'avoir un large éventail de modules, de codes pouvant facilement s'interconnecter.
Les interfaces sont souvent de simples Classes contenant des méthodes vides.
On les trouvent via le namespace Psr\.
Même si vous ne coder pas de framework ou lib, c'est utile de les connaîtres pour mieux comprendre leur framework que vous utilisez.

### 3.1 PSR-3 : Logger Interface - Interface de Journalisation

* L'objectif est de fournir un modèle (une interface) pour que les developpeurs implémentent une `LoggerInterface` de la même manière.
* Standardiser les frameworks et les bibliothèques.
* Le mot `implementor` désigne celui qui code la `LoggerInterface`. Le mot `user` celui qui utilise la `LoggerInterface` pour écrire dans les logs
* La `LoggerInterface` a 8 méthodes pour écrire des logs : 
  * debug : informations détaillées pour le debuggage
  * info : êvenements intéressant (log utilisateur, logs sql etc ...)
  * notice : êvenements normaux mais signifiant  
  * warning : êvenements exceptionnels qui ne sont pas des erreurs (utilisation d'une API abandonée)
  * error :  erreurs de fonctionnement ne demandant pas d'action mais qui doivent être logguée et monitorée
  * critical : conditions critique (composant d'application manquant, exception non interceptée)
  * alert : une action est requise immédiatement (siteweb down, base de donée introuvable ...)
  * emergency : système inutilisable
  * **log** : méthode spéciale qui permet d'apeller les autres avec une constante ex `log(ERROR, 'foo')`
* Classe "modèle" : `Psr\Log\AbstractLogger`, ou via un Trait `Psr\Log\LoggerAwareTrait`,
* Liste des constante : `Psr\Log\LogLevel`
* plus : https://www.php-fig.org/psr/psr-3/

### 3.2 PSR-4 : Autoloader - Interface de chargement automatique

* Description du modèle des classes pour le chargement automatique à partir des chemin de fichiers.
* Standardiser les frameworks et les bibliothèques.
* Nom de clase pleinenment qualifié :

  ```
   \<NomNamespace>(\<SousNomNamespace>)*\<NomClass>
  ```

* Le nom du fichier doit correspondre au nom complet de la Classe qu'il contient
  * `Maclasse.php` contient uniquement `class Maclasse {`
* Hormis le nom principal du Namespace, les autres SousNom  ou sous-espaces de noms doivent correspondre à des dossiers et sous dossiers.
* L'autoloader ne DOIT pas lever d'expections, ni d'erreur et ne DEVRAIT pas retourner de valeur.

* Exemples :

  ```
  Fully Qualified Class Name : \Acme\Log\Writer\File_Writer
  Namespace Prefix : Acme\Log\Writer
  Base Directory: ./acme-log-writer/lib/
  Resulting File Path : ./acme-log-writer/lib/File_Writer.php
  ```

  ```
  Fully Qualified Class Name : \Aura\Web\Response\Status
  Namespace Prefix : Aura\Web
  Base Directory: /path/to/aura-web/src/
  Resulting File Path : /path/to/aura-web/src/Response/Status.php
  ```

  ```
  Fully Qualified Class Name : \Symfony\Core\Request
  Namespace Prefix : Symfony\Core
  Base Directory: ./vendor/Symfony/Core/
  Resulting File Path : ./vendor/Symfony/Core/Request.php
  ```

  ```
  Fully Qualified Class Name : \Zend\Acl
  Namespace Prefix : Zend
  Base Directory: /usr/includes/Zend/
  Resulting File Path : /usr/includes/Zend/Acl.php
  ```

* Exemple d'autoloaders : https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader-examples.md

* plus : https://www.php-fig.org/psr/psr-4/

### 3.4 PSR-6: Interface de mise en cache

* Description d'un modèle d'interface commune pour la mise en place d'un système de cache.
* Standardiser les frameworks et les bibliothèques.
* Permettre au développeurs de créer des bibilotèques prenant en charge le cache sans avoir besoin de développement personnalité
* Pool (piscine) : referentiel logique de tous les élements contenu dans le système de mise en cache. Tous les élements pouvant être mis en cache sont récupérés du poll en tant qu'objet Item, toute interaction avec les objets en cache se fait via le pool.
* Items (articles) : Un élement lié a une seule paire clé/valeur dans le pool. La clé est immuable, la valeur peut être modifiée.
* plus : https://www.php-fig.org/psr/psr-6/



### 3.5 PSR-7 : HTTP message interfaces - Interface de manipulate des Messages HTTP

* Description d'un modèle d'interface pour manipuler les messages et requêtes HTTP et les URI.

* Standardiser les frameworks et les bibliothèques.

* Requête d'un client à une serveur voir `Psr\Http\Message\RequestInterface`

* Reponse d'un serveur à un client voir `Psr\Http\Message\ResponseInterface`

* En-têtes HTTP , méthode de get doivent être insensibles à la casse.

  ```php
  // insensible casse
  
  $message = $message->withHeader('foo', 'bar');
  echo $message->getHeaderLine('foo'); // bar
  echo $message->getHeaderLine('FOO'); // bar
  
  
  $message = $message->withHeader('fOO', 'baz');
  echo $message->getHeaderLine('foo'); // baz
  ```

* En-tête HTTP contenant plusieurs valeurs, plusieurs valeurs soit en chaîne via `getHeaderLine` soit en array via `getHeader`

  ```php
  $message = $message
      ->withHeader('foo', 'bar')
      ->withAddedHeader('foo', 'baz');
  
  $header = $message->getHeaderLine('foo');
  // $header contains: 'bar,baz'
  
  $header = $message->getHeader('foo');
  // ['bar', 'baz']
  ```

* Demander des cibles et des URI

  ```php
  $request = $request
      ->withMethod('OPTIONS')
      ->withRequestTarget('*')
      ->withUri(new Uri('https://example.org/'));
  ```

* Fichiers téléchargés `UploadedFileInterface` via `getUploadedFiles()` au lieu de `$_FILES`

* Utilisez directement `$file->moveTo($targetPath)` au lieu de `move_uploaded_file()`

* Utilisez `$file->getStream()`

* Détails des interfaces :

  * Psr \ Http \ Message \ MessageInterface
  * Psr \ Http \ Message \ RequestInterface
  * Psr \ Http \ Message \ ServerRequestInterface
  * Psr \ Http \ Message \ ResponseInterface
  * Psr \ Http \ Message \ StreamInterface
  * Psr \ Http \ Message \ UriInterface
  * Psr \ Http \ Message \ UploadedFileInterface

* plus : https://www.php-fig.org/psr/psr-7/

### 3.6 PSR-11: Container interface

* Description d'une interface commune pour les conteneur d'injection de dépendances.
* Standardiser la façon dont les frameworks utilisent un conteneur pour obtenir des objets et des paramètres.
* Standardiser les frameworks et les bibliothèques.
* Le conteneur `Psr\Container\ContainerInterface` expose deux méthodes :
  * `get`  :  prend un paramètre chaîne obligatoire, retourne la valeur ou lève ``NotFoundExceptionInterface`
  *  `has` :  prend un paramètre chaîne obligatoire, retourne `true/false`
* plus : https://www.php-fig.org/psr/psr-11/

### 3.7 PSR-13: Link definition interfaces - Interface des Liens hypermédias

* Cette spécification vise à fournir aux développeurs PHP un moyen simple et courant de représenter un lien hypermédia.
* Standardiser les frameworks et les bibliothèques.
* Un lien hypermédia comprend au minimum:
  * Un URI représentant la ressource cible référencée.
  * Une relation définissant la relation entre la ressource cible et la source.
* interface  : Psr \ Link \ LinkInterface
* plus : https://www.php-fig.org/psr/psr-13/

### 3.8 PSR-14:  Event Dispatcher - Interface des Répartiteurs d'événements

* Etablir un mécanisme commun pour la gestion de événements afin que les bibliothèques et composants puissent être réutilisés plus librement entre diveses applications et frameworks.

* Event : 

  * Un Event (évenement) est un message produit par un *Emitter* (émetteur). Il peut s'agit de n'importe quel objet PHP.
  * Unité de commincation entre un Emitter et un Listener.
  * Ils PEUVENT être muttable si les Listener doivent fournir des informations à l'Emitter.
  * Si il n'ya pas de communcation bidirectionelle, il est RECOMMANDE qu'il soit immuable. 
  * Un même Event doit être passé à tous les Listener sans distinction.
  * Stoppable Events : élement particulier qui contient des moyens pour empêcher d'autres Listener d'être appelés.

* Listener : 

  * Un listener (écouteur) est n'importe quel code PHP appelable qui s'attend à recevoir un événement.  Zéro ou plusieurs listener peuvent écouter un même évenement. Un listener PEUT mettre en file d'attente un autre comportement asynchrone si'il le souhaite.
  * Doit avoir Un et Un seul paramètre qui est l'Event auquel il répond.
  * Un Listener DEVRAIT retourner un `void` and SHOULD type hint that return explicitly.
  * Un Dispatcher DOIT ignorer les valeurs de retour issus d'un Listener.
  * Un Listener PEUT déléguer les actions à un autre code. 
  * Un Listener PEUT mettre en file d'attente un Event pour le traiter plutard dans un processus secondaire, en utilisant une tâche cron, une file d'attente ou autre. 
  * Un Listener PEUT sérialiser l'objet Event lui-même pour le stocker, il faut donc veiller à ce que tous les Event soit bien sérialisables.
  * Un processus secodaire DOIT supposer qu'une modification apportée à l'Event ne se propage PAS à d'autress Listener.

* Emitter :  

  * Un Emitter (émetteur) est tout code qui souhaite envoyer un événement. Il est aussi appellé "calling code". Il n'est pas représenté par une structure de donnée particulière mais fait référence à un cas d'utilisation.
  * 

* Dispatcher : Un dispatcher (répartiteur) est un objet qui reçoit un object Event provenant d'un Emitter. Le dispatcher s'assure que l'événement est transmis à tous les Listener écoutant ce type d'Event. Il doit déterminer qui sont les Listener conercné via un Listener Provider.

  * `EventDispatcherInterface`
  * DOIT être appeler par les Ecouteurs de façon synchrone dans l'ordre dans lequel ils sont revoyés par un ListernerProvider.
  * DOIT retourner le même objet Event qu'il a reçu après avoir appelé les Listeners.
  * NE DOIT PAS retourner à l'émetteur tant que tous les écouteurs n'ont pas été exécutes.
  * Si un Stoppable Event arrive :
    * DOIT appeler la méthode  `isPropagationStopped()` de l'Event, avant chaque appel de Listener. Si cette méthode renvoie `true` elle DOIT renvoyer l'Event à l'Emitter immédiatement et NE DOIT PAS appeler d'autres Listener.
    * En bref, si un Event est passé au Dispatcher, et qu'il retourne toujours `true` à l'appel de `isPropagationStopped()`, alors aucun listener n'est appelé.
  * DEVRAIT supposer que tout Listener qui lui est retourné par un Listener Provider est de type sûr. L'appel de $listener($event) ne doit jamais lever de `TypeError`.

  

* Listernet Provider : 

  * Un Listener Provider (Fournisseur d'écouteurs) doit déterminer quel Listener doit recevoir un Event, mais NE DOIT PAS appeler les Listeners lui-même. Un Listener Provider peut retourner zéro ou pluiseurs Listener.

* Gestion des erreurs : 
  * Une exception ou erreur levée par un Listener DOIT bloquer l'execution des autres Listener. 
  * Une exception ou erreur levée par un Listener DOIT aussi être autorisée  à se propagé vers l'Emitter.
  * Un Dispatcher PEUT attraper une exception ou une erreur pour la consigner, permettre une action supplémentaire mais DOIT ensuite lever à nouveau l'exception ou erreur d'origine.
* plus : https://www.php-fig.org/psr/psr-14/

### 3.9 PSR-15: HTTP Server Request Handlers | Gestionnaire de requêtes de serveur HTTP

* TODO

### 3.10 PSR-17 :  HTTP  Factories

* TODO

### 3.11 PSR-18 :  HTTP  Client

* TODO











