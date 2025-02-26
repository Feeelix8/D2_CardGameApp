# Exercise project "CardGameApp"
Playing Cards is FUN!

![Logo](logo.jpg)

## Team
- Eric Langer (Docs for Code)
- Felix Ossmann (Testing)
- Hannes Brottrager (Data)
- Markus Hilbert (Lead/Architecture)

## Targets
Create a small but extendable project in Java using OOP concepts and prozedures.

### Prozedures
- [x] if/else
- [x] case
- [x] while/for
- [x] early return

### OOP
- [x] Encapsulation
- [x] Inheritance
- [~] Abstraction
- [ ] Interfaces
- [x] Types
- [x] Enumeration
  - [x] Primitive Types
  - [x] Complex Types
- Classes
  - [x] Constructors
  - [x] Setters & Getters
  - [x] Modifiers
    - [x] public
    - [x] private 
    - [x] protected
    - [x] abstract
    - [x] final
  - [x] Return value Type

### Java STD Classes:
- [x] Scanner (Terminal input)
- [ ] StringBuffer
- [~] File I/O
- [~] Date

### Frameworks
- [~] Logging via java.util.logging.*
- [~] Testing via "JUnit"
- [x] Code versioning via GIT

### Documentation
- [x] Write a project documentation in MarkDown
- [~] Write a code documentation with javadoc

## NOT targets
- a (G)UI
- a Gaming AI to play against
- a production ready application

# CardGameApp
Base idea of this project is to create an extensible Base of (abstract) Types, to create and play several different Card Games.
Each Game implements it's own set of rules how

Possible Games are: ([List of Card Games by Amount of Cards](https://de.wikipedia.org/wiki/Liste_von_Kartenspielen_nach_Kartenanzahl_geordnet))
- BlackJack (17+4)
- Schnapsen (Cards could be "Französisch" or "DoppelDeutsch")
  - Schnapsen
  - BauernSchnapsen
  - TalonSchnapsen (DreierSchnapsen)
- Uno
- Rommé
- etc


### Diagram
<!-- insert image here -->
![Diagram](uml-models/overview.png)

### Card
Is an abstract class to represent a gaming card in a Deck of Cards.

### Card designs
- [Poker](https://www.piatnik-individual.com/produkt/4-eckzeichen-nur-rueckseite-gestalten-hochladen/)
- [Französische Schnapskarten](https://www.piatnik-individual.com/produkt/franzoesische-25-karten-nur-rueckseite-gestalten-hochladen/)
- [Doppeldeutsche Schnapskarten](https://www.piatnik-individual.com/produkt/doppeldeutsche-36-karten-nur-rueckseite-gestalten/)

### Deck
Is a set of Cards.
Each Card is unique in **most** decks.

### Player
Is a Person with a PlayerName.

### Dealer
Is a Person dealing Cards to Player(s).

### Game
The specific game itself. Depending on the game, rules, decks, amount of players, ... are different.

### Pick Pile
Is one or more Cards Decks flattened to a random List of Cards from given Decks.
Players or Dealer can pull one or more Cards from this Pile.

### Discard Pile
Is a List of Cards, Dealers or Players discard.

### Tray
A Game and/or a Player can have a Tray for Cards already played or tricks

### Exceptions
#### Game
- TooManyPlayers
- NotEnoughPlayers
- PlayerNotOldEnough
- NoMoreCardsOnStack
- StackIsEmpty

### Interfaces

#### Stakeable
Allows a Game and Player to be gamble.


### Code Structure
Use [Maven Styled Structure](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html)
- cardgame
  - src
    - main/java/ddb/international
      - card
        - Card.java
        - PokerCard.java
        - images
      - deck
        - Deck.java
        - PokerDeck.java
        - cards
          - uno.csv
          - schnapsen.csv|.json    
      - pile
        - 
      - person
      - game
        - Game.java
        - PokerGame.java
        - BlackJackGame.java
    - test
      - CardTest.java
      - PokerCardTest.java
    - resources
      - cards
        - uno.csv
        - schnapsen.csv|.json
      - gamerules
        - uno.md
        - blackjack.md


## Storage (optional)
- Hibernate (ORM)


## BlackJack game process:

1.	The game starts with a card deck containing 312 (6*52) cards

2.	Player and dealer start with two random cards

3.	The player has the option to pick another card (hit) or to end their round (stand)

4.	Card values are counted with the number cards having their number value und the face cards are counted as 10. Aces are counted either as 11 or, if their addition would lead to a value exceeding 21 then an Ace is counted as 1

5.	If a player (or the dealer) has 21 right at the start with their first cards they win (BlackJack!). If both the player and the dealer have 21 the game ends with a draw

6.	Once the player chooses to stand, the dealer draws his cards until he reaches a combined value of 17 or higher

7.	If neither the player nor the dealer reaches BlackJack or exceeds 21 (fails) then the highest score wins

8.	If all cards are played, the deck is reshuffled
