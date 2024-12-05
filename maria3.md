# ASKHSH 3

## Α ΕΡΩΤΗΜΑ 

##### Έχουμε τα παρακάτω αξιώματα ΚΛΠΤ που περιγράφουν τις ζητούμενες σχέσεις

1. **Μητέρα και Πατέρας**:
   - **Μητέρα**: 
     ```
     ∀x ∀y (γονιός(x, y) ∧ γυναίκα(x) → μητέρα(x, y))
     ```
     (Αν x είναι γονιός του y και η x είναι γυναίκα, τότε η x είναι η μητέρα του y.)

   - **Πατέρας**: 
     ```
     ∀x ∀y (γονιός(x, y) ∧ άντρας(x) → πατέρας(x, y))
     ```
     (Αν x είναι γονιός του y και η x είναι άντρας, τότε η x είναι ο πατέρας του y.)

2. **Σχέσεις Παππού και Γιαγιά**:
   - **Παππούς**: 
     ```
     ∀x ∀y ∀z ((γονιός(x, z) ∧ γονιός(z, y)) ∧ άντρας(x) → παππούς(x, y))
     ```
     (Αν x είναι γονιός του z και το z είναι γονιός του y, και η x είναι άντρας, τότε η x είναι ο παππούς του y.)

   - **Γιαγιά**: 
     ```
     ∀x ∀y ∀z ((γονιός(x, z) ∧ γονιός(z, y)) ∧ γυναίκα(x) → γιαγιά(x, y))
     ```
     (Αν x είναι γονιός του z και το z είναι γονιός του y, και η x είναι γυναίκα, τότε η x είναι η γιαγιά του y.)

3. **Εγγονός**:
   ```
   ∀x ∀y ∃z (γονιός(y, z) ∧ γονιός(z, x) → εγγονός(x, y))
   ```
   (Αν y είναι γονιός του z και το z είναι γονιός του x, τότε το x είναι εγγονός του y.)

4. **Αδέλφια (Αδελφός και Αδελφή)**:
- **Αδελφός**: 
  ```
  ∀x ∀y ∀z (γονιός(z, x) ∧ γονιός(z, y) ∧ άντρας(x) ∧ x ≠ y → αδελφός(x, y))
  ```
  (Αν το z είναι γονιός και των x και y, και το x είναι άντρας και το x δεν είναι ίσο με το y, τότε το x είναι ο αδελφός του y.)

- **Αδελφή**:
  ```
  ∀x ∀y ∀z (γονιός(z, x) ∧ γονιός(z, y) ∧ γυναίκα(x) ∧ x ≠ y → αδελφή(x, y))
  ```
  (Αν το z είναι γονιός και των x και y, και το x είναι γυναίκα και το x δεν είναι ίσο με το y, τότε το x είναι η αδελφή του y.)

5. **Γιος και Κόρη**:
- **Γιος**: 
  ```
  ∀x ∀y (γονιός(y, x) ∧ άντρας(x) → γιος(x, y))
  ```
  (Αν y είναι γονιός του x και το x είναι άντρας, τότε το x είναι ο γιος του y.)

- **Κόρη**: 
  ```
  ∀x ∀y (γονιός(y, x) ∧ γυναίκα(x) → κόρη(x, y))
  ```
  (Αν y είναι γονιός του x και το x είναι γυναίκα, τότε το x είναι η κόρη του y.)

6. **Θείος και Θεία**:
- **Θείος**: 
  ```
  ∀x ∀y ∃z (γονιός(z, y) ∧ αδελφός(x, z) → θείος(x, y))
  ```
  (Αν το z είναι γονιός του y και το x είναι ο αδελφός του z, τότε το x είναι ο θείος του y.)

- **Θεία**:
  ```
  ∀x ∀y ∃z (γονιός(z, y) ∧ αδελφή(x, z) → θεία(x, y))
  ```
  (Αν το z είναι γονιός του y και το x είναι η αδελφή του z, τότε το x είναι η θεία του y.)

7. **Πρώτος Ξάδερφος/η**:
- **Πρώτος Ξάδερφος**:
  ```
  ∀x ∀y ∃z (((θείος(z, y) ∧ γιος(x, z))∨(θεία(z, y) ∧ γιος(x, z))) → πρώτος_ξάδερφος(x, y))
  ```
  (Αν το z είναι ο θείος του y και το x είναι ο γιος του z, τότε το x είναι ο πρώτος ξάδερφος του y και είναι άντρας.)

- **Πρώτη Ξάδερφη**:
  ```
  ∀x ∀y ∃z (((θεία(z, y) ∧ κόρη(x, z))∨(θείος(z, y) ∧ κόρη(x, z))) → πρώτη_ξαδέρφη(x, y))
  ```
  (Αν το z είναι η θεία του y και το x είναι η κόρη του z, τότε το x είναι η πρώτη ξαδέρφη του y και είναι γυναίκα.)

8. **Προ-παππούς**:
- **Προ-παππούς**:
  ```
  ∀x ∀y ∃z (γονιός(x, z) ∧ παππούς(z, y) → προ_παππούς(x, y))
  ```
  (Αν x είναι γονιός του z και το z είναι ο παππούς του y, τότε το x είναι ο προ-παππούς του y.)

- **Προ-γιαγιά**:
  ```
  ∀x ∀y ∃z (γονιός(x, z) ∧ γιαγιά(z, y) → προ_γιαγιά(x, y))
  ```
  (Αν x είναι γονιός του z και το z είναι η γιαγιά του y, τότε το x είναι η προ-γιαγιά του y.)

9. **Πρόγονος**:
    ```
    ∀x ∀y (γονιός(x, y) → πρόγονος(x, y))
    ```
   (Αν x είναι γονιός του y, τότε το x είναι πρόγονος του y.)

   Για έμμεσους προγόνους, ο κανόνας είναι:
   ```
   ∀x ∀y ∀z (γονιός(x, z) ∧ πρόγονος(z, y) → πρόγονος(x, y))
   ```
   (Αν x είναι γονιός του z και το z είναι πρόγονος του y, τότε το x είναι επίσης πρόγονος του y.)

## B ΕΡΩΤΗΜΑ

##### Ορισμός βασικών σχέσεων βάση του γενεολογικού δέντρου που δόθηκε
Παρακάτω φαίνεται η σχέση όλων των ανθρώπων μεταξύ τους σε γλώσσα Prolog αντίστοιχα με το διάγραμμα
```prolog
% Γονείς
parent(george, elizabeth).
parent(mum, elizabeth).
parent(george, margaret).
parent(mum, margaret).

parent(elizabeth, charles).
parent(elizabeth, anne).
parent(elizabeth, andrew).
parent(elizabeth, edward).
parent(philip, charles).
parent(philip, anne).
parent(philip, andrew).
parent(philip, edward).

parent(spencer, diana).
parent(kydd, diana).

parent(charles, william).
parent(charles, harry).
parent(diana, william).
parent(diana, harry).

parent(anne, peter).
parent(anne, zara).
parent(anne, mark).
parent(anne, mark).

parent(andrew, beatrice).
parent(andrew, eugenie).
parent(sarah, eugenie).
parent(sarah, beatrice).

parent(edward, louise).
parent(edward, james).
parent(sophie, louise).
parent(sophie, james).

% Σχέση Γάμου (για πληρότητα)
married(george, mum).
married(mum, george).

married(elizabeth, philip).
married(philip, elizabeth).

married(spencer, kydd).
married(kydd, spencer).

married(charles, diana).
married(diana, charles).

married(anne, mark).
married(mark, anne).

married(andrew, sarah).
married(sarah, andrew).

married(edward, sophie).
married(sophie, edward).

% Βοηθητική Σχέση - Μητέρα και Πατέρας
mother(X, Y) :- parent(X, Y), woman(X).
father(X, Y) :- parent(X, Y), man(X).

% Φύλο (για βοηθητικούς κανόνες)
woman(elizabeth).
woman(mum).
woman(margaret).
woman(diana).
woman(anne).
woman(sarah).
woman(sophie).
woman(beatrice).
woman(eugenie).
woman(louise).
woman(zara).
woman(kydd).

man(george).
man(philip).
man(charles).
man(mark).
man(andrew).
man(edward).
man(spencer).
man(william).
man(harry).
man(peter).
man(james).

% Παππούς/Γιαγιά
grandfather(X, Y) :- parent(X, Z), parent(Z, Y), man(X).
grandmother(X, Y) :- parent(X, Z), parent(Z, Y), woman(X).

% Εγγόνι
grandchild(X, Y) :- parent(Y, Z), parent(Z, X).

% Αδερφός/Αδερφή
brother(X, Y) :- parent(Z, X), parent(Z, Y), man(X), X \= Y.
sister(X, Y) :- parent(Z, X), parent(Z, Y), woman(X), X \= Y.

% Κόρη/Γιος
son(X, Y) :- parent(Y, X), man(X).
daughter(X, Y) :- parent(Y, X), woman(X).

% Θείος/Θεία
uncle(X, Y) :- parent(Z, Y), brother(X, Z).
aunt(X, Y) :- parent(Z, Y), sister(X, Z).

% Πρώτος Ξάδερφος/Ξαδέρφη
first_cousin_man(X, Y) :-
    uncle(Z, Y), son(X, Z).
first_cousin_man(X, Y) :-
    aunt(Z, Y), son(X, Z).

first_cousin_woman(X, Y) :-
    uncle(Z, Y), daughter(X, Z).
first_cousin_woman(X, Y) :-
    aunt(Z, Y), daughter(X, Z).

% Προ-πάππους/Προ-γιαγιά
great_grandfather(X, Y) :- father(X, Z), grandchild(Y, Z).
great_grandmother(X, Y) :- mother(X, Z), grandchild(Y, Z).

% Πρόγονος
ancestor(X, Y) :- parent(X, Y).
ancestor(X, Y) :- parent(X, Z), ancestor(Z, Y).
```


## Γ ΕΡΩΤΗΜΑ

1. **Ποια είναι τα εγγόνια της Elizabeth;**:
   ```prolog
   grandchild(X, elizabeth).
   ```
   Και η έξοδος είναι:
   ```prolog
   ?- grandchild(X, elizabeth).
   X = william ;
   X = harry ;
   X = peter ;
   X = zara ;
   X = beatrice ;
   X = eugenie ;
   X = louise ;
   X = james.
   ```

2. **Ποιοι είναι προπάπποι/προγιαγιάδες της Zara;**:
   ```prolog
   great_grandfather(X, zara).
   ```
   Και η έξοδος είναι:
   ```prolog
   X= george ;
   ```
   ```prolog
   great_grandmother(X, zara).
   ```
   Και η έξοδος είναι:
   ```prolog
   X= mum ;
   ```


3. **Ποιοι είναι οι πρόγονοι της Eugenie;**: 
   ```prolog
   ancestor(X, eugenie).
   ```
   Και η έξοδος είναι:
   ```prolog
   X = andrew ;
   X = sarah ;
   X = george ;
   X = mum ;
   X = elizabeth ;
   X = philip ;
   ```


## Δ ΕΡΩΤΗΜΑ

- Για Πρώτα ξαδέλφια:
   Δύο άτομα είναι πρώτα ξαδέλφια αν οι γονείς τους είναι αδέλφια (brother ή sister), και δεν είναι το ίδιο άτομο.

- Για Δεύτερα και ανώτερα ξαδέλφια:
   Αναδρομικά, δύο άτομα είναι ξαδέλφια αν οι γονείς τους είναι ξαδέλφια.
  
Έτσι ο Prolog κώδικας που επεκτείνει την ιδιότητα "ξάδερφος" είναι ο παρακάτω:

```prolog
% Ξάδελφος: Πρώτα ξαδέλφια
cousin(X, Y) :- 
    parent(Z1, X), 
    parent(Z2, Y), 
    (brother(Z1, Z2) ; sister(Z1, Z2)), 
    X \= Y.

% Ξάδελφος: Αναδρομή για δεύτερα και ανώτερα ξαδέλφια
cousin(X, Y) :- 
    parent(Z1, X), 
    parent(Z2, Y), 
    cousin(Z1, Z2), 
    X \= Y.
```

Και εισάγουμε την Margarita ως εγγόνι της margaret με τον εξής τρόπο (έστω ότι ο γίος της margaret που έχει κόρη την margarita λέγεται son): 

```prolog
parent(margaret, son).
parent(son, margarita).
```

Έτσι το query για να πάρουμε όλα τα ξαδέρφια του william (χωρίς duplicates) είναι το εξής:

```prolog
?- findall(X, cousin(X, william), Cousins), list_to_set(Cousins, DistinctCousins), write(DistinctCousins).
```

Και η έξοδος φαίνεται παρακάτω:



   
Ο τελικός κώδικας φαίνεται παρακάτω:

```prolog
% Γονείς
parent(george, elizabeth).
parent(mum, elizabeth).
parent(george, margaret).
parent(mum, margaret).

parent(elizabeth, charles).
parent(elizabeth, anne).
parent(elizabeth, andrew).
parent(elizabeth, edward).
parent(philip, charles).
parent(philip, anne).
parent(philip, andrew).
parent(philip, edward).

parent(spencer, diana).
parent(kydd, diana).

parent(charles, william).
parent(charles, harry).
parent(diana, william).
parent(diana, harry).

parent(anne, peter).
parent(anne, zara).
parent(anne, mark).
parent(anne, mark).

parent(andrew, beatrice).
parent(andrew, eugenie).
parent(sarah, eugenie).
parent(sarah, beatrice).

parent(edward, louise).
parent(edward, james).
parent(sophie, louise).
parent(sophie, james).

% Για το δ ερώτημα
parent(margaret, son).
parent(son, margarita).

% Σχέση Γάμου (για πληρότητα)
married(george, mum).
married(mum, george).

married(elizabeth, philip).
married(philip, elizabeth).

married(spencer, kydd).
married(kydd, spencer).

married(charles, diana).
married(diana, charles).

married(anne, mark).
married(mark, anne).

married(andrew, sarah).
married(sarah, andrew).

married(edward, sophie).
married(sophie, edward).

% Βοηθητική Σχέση - Μητέρα και Πατέρας
mother(X, Y) :- parent(X, Y), woman(X).
father(X, Y) :- parent(X, Y), man(X).

% Φύλο (για βοηθητικούς κανόνες)
woman(elizabeth).
woman(mum).
woman(margaret).
woman(diana).
woman(anne).
woman(sarah).
woman(sophie).
woman(beatrice).
woman(eugenie).
woman(louise).
woman(zara).
woman(kydd).

man(george).
man(philip).
man(charles).
man(mark).
man(andrew).
man(edward).
man(spencer).
man(william).
man(harry).
man(peter).
man(james).

% Παππούς/Γιαγιά
grandfather(X, Y) :- parent(X, Z), parent(Z, Y), man(X).
grandmother(X, Y) :- parent(X, Z), parent(Z, Y), woman(X).

% Εγγόνι
grandchild(X, Y) :- parent(Y, Z), parent(Z, X).

% Αδερφός/Αδερφή
brother(X, Y) :- parent(Z, X), parent(Z, Y), man(X), X \= Y.
sister(X, Y) :- parent(Z, X), parent(Z, Y), woman(X), X \= Y.

% Κόρη/Γιος
son(X, Y) :- parent(Y, X), man(X).
daughter(X, Y) :- parent(Y, X), woman(X).

% Θείος/Θεία
uncle(X, Y) :- parent(Z, Y), brother(X, Z).
aunt(X, Y) :- parent(Z, Y), sister(X, Z).

% Πρώτος Ξάδερφος/Ξαδέρφη
first_cousin_man(X, Y) :-
    uncle(Z, Y), son(X, Z).
first_cousin_man(X, Y) :-
    aunt(Z, Y), son(X, Z).

first_cousin_woman(X, Y) :-
    uncle(Z, Y), daughter(X, Z).
first_cousin_woman(X, Y) :-
    aunt(Z, Y), daughter(X, Z).

% Προ-πάππους/Προ-γιαγιά
great_grandfather(X, Y) :- father(X, Z), grandchild(Y, Z).
great_grandmother(X, Y) :- mother(X, Z), grandchild(Y, Z).

% Πρόγονος
ancestor(X, Y) :- parent(X, Y).
ancestor(X, Y) :- parent(X, Z), ancestor(Z, Y).


% Ξάδελφος: Πρώτα ξαδέλφια
cousin(X, Y) :- 
    parent(Z1, X), 
    parent(Z2, Y), 
    (brother(Z1, Z2) ; sister(Z1, Z2)), 
    X \= Y.

% Ξάδελφος: Αναδρομή για δεύτερα και ανώτερα ξαδέλφια
cousin(X, Y) :- 
    parent(Z1, X), 
    parent(Z2, Y), 
    cousin(Z1, Z2), 
    X \= Y.
```
