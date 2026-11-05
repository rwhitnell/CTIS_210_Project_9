### CTIS 210 Project 9
### Organizing and manipulating data in `List` objects

#### Goals for this project

* Construct and manipulate an ordered sequence of objects using a `List` object
* Work with loops to examine and evaluate the elements of a `List` object
* Create a new class definition file that uses a `List` object

#### Initial task

The provided program does nothing more than generate a random card from a standard deck. 

1. Run the program and examine the output. Run it again to verify that a random card is being generated each time. 
2. Examine the `Card` class in the Card.java file. Make sure you know the answer to the following questions (but you do not need to include these answers in what you submit).
    * What are the attributes of the `Card` class? (Ignore the ones that are labeled as "static attributes".)
    * How many constructors are present?
        * What does each constructor do?
    * Which attributes have getters and setters associated with them?
    * What other methods are present?

#### Making a list and checking it twice task

***Important note**: You will be using several (perhaps new) Java classes in this project. If you see an error message when you add lines with those classes, check whether you need to import them.

Let's generate a hand of five `Card` objects and put them in a list that we can use for further analysis. 

We will use an `ArrayList` object to hold objects of a specified class. By specifying that class, we ensure that the `ArrayList` object holds that kind of object and **only** that kind of object.

`ArrayList` uses a different declaration and instantiation than any object we've examined so far. 

1. Add the following line just below the last line of the `main` method in the `CTIS210Project9` driver program.

    ```java
    ArrayList<Card> cards = new ArrayList<Card>();
    ```

    This line creates an `ArrayList` object with the identifier `cards` that will be a list of `Card` objects. So for `ArrayList` objects, we can't just say it's an `ArrayList`, we also must state what kind of objects we will store in the `ArrayList`. The use of `<` and `>` show how we specify the specific type of objects this `ArrayList` will hold.

2. Because `ArrayList` is a class, we can send messages to an `ArrayList` object to invoke specific behaviors. In particular, we can `add` items to the list, we can `get` items to examine them, and we can `remove` them. So let's try these in turn. First, we'll add the `firstCard` object. 

    ```java
    cards.add(firstCard);
    ```

    Run the program and you won't see anything different because all we did is add an item to the list. But if you then add the line

    ```java
    System.out.println("The size of the list is " + cards.size());
    ```

    you should then see that the list contains one object.

3. Can we add a different kind of item to the list? Let's try to add a `String` object with the following lines:

    ```java
    String testString = "Will this work?";
    cards.add(testString);
    ```

    * **What error appears when you add these lines? Why is there an error?**

    Comment out these two lines you just added before continuing and confirm that the program does run without error.

4. So how do we get an item from the list? One way is to use the index of the item. Just as with other kinds of lists we've used in Java, like characters in a `String` object, the index of the first object is 0. We can therefore use the `get` method with the parameter 0 to get the first object in the list. 

    The `get` method returns an object of whatever class the `ArrayList` was instantiated with--`Card` in our case. Let's use the `get` method and assign the result to another `Card` identifier.

    ```java
    Card testCard = cards.get(0);
    ```

    Did that work? Well, use the same kind of `println` statements you used earlier to check that `testCard` has the same information as `firstCard`. (In fact, it's *exactly* the same object.)

5. Let's remove this object so we can start with a clean list. That's done with the `remove` method:

    ```java
    cards.remove(0);
    ```

    After adding this line, add a line like above to confirm that the size of the list is back to zero.

That's all great and good, but we don't want to add lots of cards to our list one at at time. Let's build some other tools for doing that.

#### Building a larger list task

Let's just start with 5 cards. (It's always better to start with a small number and then add in more as you need them.) We want to build a counting loop that starts at 0 and counts to 4, adding a new `Card` object to our list each time. Here's what the skeleton will look like, using only code that we've used before in projects or class.

```java
// declare and initialize the variable with the number of students

// declare an index variable that keeps track of where we are in the loop
// and initializes it to 0

// start a while loop that runs while the index is less than the number of cards we want

// in the while loop, instantiate a random Card object with the empty constructor
// add that object to the list
// increment the index


// end the loop

// confirm that we've added enough objects
```

**Challenge exercise** Before reading any further, try building this code yourself in CTIS210Project9.java. Use the code below to help out if you get stuck.

And now here's what everyone does:

1. Here's the full set of code that you can use in StudentProject.java. It is vital that you work on understanding why each line does what it does. Don't just copy it in without paying attention to that.

    ```java
    // declare and initialize the variable with the number of students

    int nCards = 5;

    // declare an index variable that keeps track of where we are in the loop
    // and initializes it to 0

    int iCard = 0;

    // start a while loop that runs while the index is less than the number of
    // students

    while (iCard < nCards) {
        // in the while loop, instantiate a random Card object with the empty constructor
        Card nextCard = new Card();
        // add that object to the list
        cards.add(nextCard);
        // increment the index
        iCard = iCard + 1;
    // end the loop
    }

    // confirm that we've added enough objects
    System.out.println("The size of the list is " + cards.size());

    // and let's look at the list itself
    System.out.println(cards);
    ```

    Now we have a list of 5 cards. Let's work with that before making the list larger.

#### Evaluating the cards task

We now want to evaluate each of the cards in the `cards` list and keep track of how many are face cards (Ace, Jack, Queen, or King). 

Let's start with a new kind of loop that is known as a "for-each" loop: *For* *each* item in the list, we want to execute the same kind of actions. The basic structure for a for-each loop is (don't enter this code into your program!):

    ```java
    for (Card card : cards;)
    {

    }
    ```

The keyword is `for`. The statement in parentheses says to take **each** object in `cards`, one after the other, and assign it to the temporary `Card` object `card`. Then, in the for loop body, we can use `card` in whatever way we want. The nature of this loop is that each object in `card` will have the same code applied to it. 

What are we going to do in this loop? First, we will initialize a variable named `faceCards` that will keep track of how many face cards are in the list. Then, in the loop, we will use the `countFaceCards` method in the `Card` class to decide whether each card is a face card. If so, we'll increment `faceCards.`

1. Add the following code just after you've created your list with multiple students.

    ```java
    int faceCards = 0;
    for (Card card : cards) {
        if (card.isFaceCard()) {
            faceCards++;
        }
    }
    ```
  

    Then, print out the number of face cards in the list. Remember to have your program annotate any values that it prints out.



2. Now a big test: Everything you've done so far is with a list of 5 cards. Change the initialization of `nCards` so that it's now 10. Run the program again and verify that the output has appropriate changes.


#### Building a `Deck` class to represent a deck of cards task

If you run the program several times, you'll see a problem. Each card should only appear once if we want our list to represent a hand of cards, but since we're generating each `Card` object randomly, it's possible to have the same card values appear multiple times. Let's fix that by building a new class, `Deck`.

Note that this task gives you general guidance, but only occasionally detailed code. So there is more you'll have to implement.. Essentially everything in this task is something that you've done before in this project or previous ones. Ask questions if you get stuck or something doesn't seem to work. 

1. In your project, create a new Java class definition file with the name `Deck` making sure that it is stored in the file Deck.java.
2. The `Deck` class will have one attribute. That attribute has the identifier `deck` and will be an `ArrayList<Card>` object. Declare that attribute in the `Deck` class.

    You may need to add the line `import java.util.ArrayList;` at the top of the file to tell Java that you will be using the `ArrayList` functionality.

3. The default constructor should instantiate the `deck` object and add all possible cards to it. 

    Define that constructor with the first line of the method body using the `new` keyword to instantiate an `ArrayList` object and assign it to `deck`.

    And here's some code to fill that `deck` objet with all the cards since we haven't talked about nested loops. Add this code below the line you just added to complete the constructor definition.

    ```java
            for (int i = 0; i < Card.SUITS.length; i++) {
            for (int j = 0; j < Card.RANKS.length; j++) {
                deck.add(new Card(j, i));
            }
        }

    ```

4. Add a getter for the `deck` attribute.

5. We need a method to shuffle the deck. Java provides a way to shuffle the objects in any list using the `Collections.shuffle` method. So `Collections.shuffle(deck);` will perform that action. Add a `shuffle` method that has just this one line as its method body. It does not need to return anything. (You may need to add `import java.util.Collections;` at the top of the class definition file just below the `package` line for this part to work properly.)

6. Now write a method `dealCard` that deals one card from the top of the deck. It should return a `Card` object. It should remove that top card from the deck. If the deck is empty, it should return `null` to indicate that no object is available. (There are multiple ways to do this step correctly. The table of `List` methods in the Lists activity from class can help.)

All of these steps create the `Deck` class, but now we need to test that class.

#### Testing the `Deck` class

Testing happens in the driver program. So let's return to the `main` method in that program and do some useful testing.

The strategy will be to have a list of cards with the identifier `hand`. We'll instantiate a new `Deck` object and then deal cards into the hand. As with the previous task, these steps are an outline of what you to do, and you will work on adding (and understanding!) the code to make everything work.

Be sure that you're adding all statements to end of the `main` method, before the closing `}` for that method.

1. Declare and instantiate a `Deck` object using the default constructor. `deck` is a good identifier for tha object.

2. Declare and instantiate an object for the hand of cards. It's an `ArrayList` object that can hold `Card` objects. `hand` is a good identifier to use.

3. Write a loop that uses the `dealCard` method of the `Deck` class to obtain the next card in the deck and add it to the `hand` list. You can choose the size of the hand.

4. After the loop is done, display the hand. You should verify that no cards are repeated in the hand.

Once you know how to deal a hand, you have the starting point of what you need to write card games, but we won't do that particular step here.

#### Submitting your assignment

Make sure all files are saved. Commit and sync the project as you've done with other project. You do not need to close an issue.

You should go into the Project 9 assignment in Canvas and just submit the text "My Project 9 is now ready for evaluation". That indicates that your project on GitHub is complete.

#### Optional challenge exercises


1. Add a `toString` method to the `Deck` class. The tricky part here is to be able to display a deck (which might be the full deck or a deck after it's built) in a way that's readily readable.

2. Build two hands of cards. Then, use the `compareTo` method of the `Card` class to compare the two hands card by card and decide which hand wins. (That method first compares suit and then compares rank.)

3. Everything here is almost set up to be able to use the `Collections.sort` method to sort any `ArrayList` of cards. Research what change is needed in the `Card` class to make that work and then test the ability to sort lists of cards in the driver program.


3. We might want to save the data we generate for later use in another program. Research how Java can write data to a file and output the `Card` objects in a hand into a file, one card's suit and rank (as integer values) on each line. Then demonstrate you can read the data back in and perform the analysis. 



