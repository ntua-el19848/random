# ASKHSH 3

### Α ΕΡΩΤΗΜΑ 

##### Έχουμε τα παρακάτω αξιώματα ΚΛΠΤ που περιγράφουν τις ζητούμενες σχέσεις

### Updated FOPC Rules (with "woman" and "man")

1. **Mother and Father**:
   - **Mother**: 
     \[
     \forall x \, \forall y \, (parent(x, y) \land woman(x) \Rightarrow mother(x, y))
     \]
     (If x is a parent of y and x is a woman, then x is the mother of y.)

   - **Father**: 
     \[
     \forall x \, \forall y \, (parent(x, y) \land man(x) \Rightarrow father(x, y))
     \]
     (If x is a parent of y and x is a man, then x is the father of y.)

2. **Grandparent Relations**:
   - **Grandfather**: 
     \[
     \forall x \, \forall y \, \forall z \, ((parent(x, z) \land parent(z, y)) \land man(x) \Rightarrow grandfather(x, y))
     \]
     (If x is a parent of z and z is a parent of y, and x is a man, then x is the grandfather of y.)

   - **Grandmother**: 
     \[
     \forall x \, \forall y \, \forall z \, ((parent(x, z) \land parent(z, y)) \land woman(x) \Rightarrow grandmother(x, y))
     \]
     (If x is a parent of z and z is a parent of y, and x is a woman, then x is the grandmother of y.)

3. **Grandchild**:
   \[
   \forall x \, \forall y \, \exists z \, (parent(y, z) \land parent(z, x) \Rightarrow grandchild(x, y))
   \]
   (If y is a parent of z and z is a parent of x, then x is the grandchild of y.)

4. **Siblings (Brother and Sister)**:
   - **Brother**: 
     \[
     \forall x \, \forall y \, \forall z \, (parent(z, x) \land parent(z, y) \land man(x) \land x \neq y \Rightarrow brother(x, y))
     \]
     (If z is a parent of both x and y, and x is a man and x is not equal to y, then x is the brother of y.)

   - **Sister**:
     \[
     \forall x \, \forall y \, \forall z \, (parent(z, x) \land parent(z, y) \land woman(x) \land x \neq y \Rightarrow sister(x, y))
     \]
     (If z is a parent of both x and y, and x is a woman and x is not equal to y, then x is the sister of y.)

5. **Son and Daughter**:
   - **Son**: 
     \[
     \forall x \, \forall y \, (parent(y, x) \land man(x) \Rightarrow son(x, y))
     \]
     (If y is a parent of x and x is a man, then x is the son of y.)

   - **Daughter**: 
     \[
     \forall x \, \forall y \, (parent(y, x) \land woman(x) \Rightarrow daughter(x, y))
     \]
     (If y is a parent of x and x is a woman, then x is the daughter of y.)

6. **Uncle and Aunt**:
   - **Uncle**: 
     \[
     \forall x \, \forall y \, \exists z \, (parent(z, y) \land brother(x, z) \Rightarrow uncle(x, y))
     \]
     (If z is a parent of y and x is the brother of z, then x is the uncle of y.)

   - **Aunt**:
     \[
     \forall x \, \forall y \, \exists z \, (parent(z, y) \land sister(x, z) \Rightarrow aunt(x, y))
     \]
     (If z is a parent of y and x is the sister of z, then x is the aunt of y.)

7. **First Cousin**:
   - **First Cousin (Man)**:
     \[
     \forall x \, \forall y \, \exists z \, (uncle(z, y) \land son(x, z) \Rightarrow first\_cousin\_man(x, y))
     \]
     (If z is the uncle of y and x is the son of z, then x is a man first cousin of y.)

   - **First Cousin (Woman)**:
     \[
     \forall x \, \forall y \, \exists z \, (aunt(z, y) \land daughter(x, z) \Rightarrow first\_cousin\_woman(x, y))
     \]
     (If z is the aunt of y and x is the daughter of z, then x is a woman first cousin of y.)

8. **Great-Grandparent**:
   - **Great-Grandfather**:
     \[
     \forall x \, \forall y \, \exists z \, (parent(x, z) \land grandfather(z, y) \Rightarrow great\_grandfather(x, y))
     \]
     (If x is a parent of z and z is a grandfather of y, then x is a great-grandfather of y.)

   - **Great-Grandmother**:
     \[
     \forall x \, \forall y \, \exists z \, (parent(x, z) \land grandmother(z, y) \Rightarrow great\_grandmother(x, y))
     \]
     (If x is a parent of z and z is a grandmother of y, then x is a great-grandmother of y.)

9. **Ancestor**:
   \[
   \forall x \, \forall y \, (parent(x, y) \Rightarrow ancestor(x, y))
   \]
   (If x is a parent of y, then x is an ancestor of y.)

   For indirect ancestors, the rule is:
   \[
   \forall x \, \forall y \, \forall z \, (parent(x, z) \land ancestor(z, y) \Rightarrow ancestor(x, y))
   \]
   (If x is a parent of z and z is an ancestor of y, then x is also an ancestor of y.)


### B ΕΡΩΤΗΜΑ

##### Ορισμός βασικών σχέσεων βάση του γενεολογικού δέντρου που δόθηκε
Παρακάτω φαίνεται η σχέση όλων των ανθρώπων μεταξύ τους σε γλώσσα Prolog αντίστοιχα με το διάγραμμα
```prolog
% Γονείς
parent(george, elizabeth).
parent(mum, elizabeth).
parent(elizabeth, charles).
parent(elizabeth, anne).
parent(elizabeth, andrew).
parent(elizabeth, edward).
parent(philip, charles).
parent(philip, anne).
parent(philip, andrew).
parent(philip, edward).
parent(charles, william).
parent(charles, harry).
parent(anne, peter).
parent(anne, zara).
parent(andrew, beatrice).
parent(andrew, eugenie).
parent(edward, louise).
parent(edward, james).

% Σχέση Γάμου (για πληρότητα)
married(elizabeth, philip).
married(philip, elizabeth).
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

man(george).
man(philip).
man(charles).
man(mark).
man(andrew).
man(edward).
man(spencer).
man(kidd).
man(william).
man(harry).
man(peter).
man(james).
```


##### Παράγωγες σχέσεις

```prolog
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
    aunt(Z, Y), daughter(X, Z)

% Προ-πάππους/Προ-γιαγιά
great_grandfather(X, Y) :- parent(X, Z), grandfather(Z, Y).
great_grandmother(X, Y) :- parent(X, Z), grandmother(Z, Y).

% Πρόγονος
ancestor(X, Y) :- parent(X, Y).
ancestor(X, Y) :- parent(X, Z), ancestor(Z, Y).

```


### Β ΕΡΩΤΗΜΑ


