
read:
[wiki-Finite-state_machine](https://en.wikipedia.org/wiki/Finite-state_machine), [johnsantic.com](http://johnsantic.com/comp/state.html)

**Q**:     What is a state machine?
**Ans**:     A mathematical model of computation used to design computer programs and sequential logic.

**Q**:     What are acceptors and recognizers?
**Ans**:     Acceptors (or recognizers) produce a binary input indicating whether an input is accepted or not into a state.

**Q**:     What are the two methods to implement state\-machine? Pros/Cons?
**Ans**:     Using nested switch statements: One way uses a set of nested `switch` statements. The outer `switch` has a `case` for each possible state. Each of these outer `cases` has an inner `switch` with a `case` for each possible event. The actual code that gets selected performs the actions for that state/event. Alternately, the outer `switch` could have a `case` for each event, and the inner `switch` could have a `case` for each state.

Another more concise way of coding is to use a lookup table. First, number all your states consecutively, starting with 0—an `enum` is a convenient way to do this. Do the same for your events. Then make up a set of tables, one table per state. Each table has one entry per event, in the same order as the event `enum`. Then the entire set of tables is arranged in the same order as the state `enum`. Each item in a table is the function to execute to perform the action for that particular event in that particular state.

**Q**: Design a state\-machine, in which the language recognized is composed of strings that start and finish with 0 and may contain any string formed from the set {0,1} between. Examples: 00, 01110, 01101010. Strings which aren't accepted: 01, 10001, 010101.

Draw a state diagram regarding the above problem.

|state\\event

|0
         |1
         |
|------------|----------|----------|
|init
        |one
       |error
     |
|one
         |accepted
  |do nothing
|
|accepted
    |do nothing
|one
       |
|error
       |error
     |error
     |