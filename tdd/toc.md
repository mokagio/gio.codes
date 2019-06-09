#### 1\. Introduction

_What the fuss is all about._

*   What's a test
*   Why testing
    *   Roll your own test. _Before looking at testing principles and TDD we'll look at how to write code that calls other code and checks its results._
*   TDD 101
    *   Re-write the examples above in a test-driven fashion.
*   TDD vs Testing

#### 2\. How to TDD a new object

_TDD starts with a failing test, and is about making that test pass. Only once you have a passing test you should focus on making the code you wrote better._

*   TDD your first property: `MenuDataSource` number of sections.
*   TDD your first method: number of rows in section.
*   Get `Pizza` for row in section
    *   The refactor step in red, green, refactor.

#### 3\. How to put a `UIViewController` in a test harness

_View controllers can be tested like any other object, as long as you are aware of a few gotchas._

*   Setting up the application scaffold: remove Xcode's unnecessary boilerplate.
*   TDD adding a view controller to the app: `MenuViewController`.
*   View controller life cycle and tests.
*   TDD adding a table view to the view controller.
*   TDD using `MenuDataSource` in the view controller.

#### 4\. How to test the contents of the UI

_You can test how views render their information using humble views._

*   Humble views: how to split _what_ to show from _how_ to show it.
*   TDD generating `PizzaViewConfiguration` from `Pizza`.
*   TDD configuring a table view cell using `PizzaViewConfiguration`.

#### 5\. How to change existing code driven by tests

_TDD is not only a tool to create new code, it also allows to change existing one._

*   From `Pizza` to `MenuItem`. _We'll introduce `Beverage` and `Dessert` types in the menu, and have `MenuDataSource` return them alongside `Pizza`_.
    *   TDD generating `MenuItemViewConfiguration` from `Beverage`
    *   TDD updating `MenuDataSource` to return `MenuItemViewConfiguration` from either `Pizza` or `Beverage`.
        *   The fixture pattern. _How to centralize the definition of input value types for the tests_.
    *   Exercise for the reader: TDD handling `Dessert`. _The process is exactly the same as the sections above._

#### 6\. How to test delegates

_You can write test doubles to inspect how components interact with each other, these are called Spies._

*   The minimum viable ordering system. _Before implementing a full ordering flow in the app let's just add a button to order that will make a phone call, and track if users interact with it._
*   How to use a delegate to abstract the navigation logic from `MenuViewController`
    *   TDD adding an order button to `MenuViewController`
    *   Using the Spy double to test the interaction with the delegate

#### 7\. How to TDD code talking with the network

_This is the hardest chapter to write, due to the different approaches and their tradeoffs. I am not yet settled on what's the approach to recommend to the readers, so the following outline is quite generic_

*   What you'll learn.
*   A test hitting the network directly
    *   The limitation of hitting the network directly
*   How to use a Stub test double to control the network dependency

#### 8\. How to TDD code storing data

_How to abstract the statefulness for storage behind a protocol, how to use a Fake test double to have an in-memory storage in the tests._

*   The storage business logic.
    *   Storing to the `UserDefaults`.
    *   Building a Fake for testing.
    *   Using the Fake to verify the behavior.
    *   Updating the favorites list.
    *   Reading from the storage.
*   Wiring up the UI.
    *   Adding a new button to `MenuItemTableViewCell`.
    *   Connecting the pieces in `MenuViewController`.
*   Exercise for the reader: swap the storage layer with one using Core Data or another database.

#### 9\. How to TDD code talking with third-party dependencies

_How to use a Dummy test double to satisfy a dependency requirement with something that doesn't affect the behavior of the system under test._

*   Introduction to the chapter feature. _Why we need to add events tracking via for analytics._
*   Using a protocol to insulate a third party dependency: `EventsLogger`.
*   TDD the interaction between `MenuViewController` and `EventsLogger`.
    *   How to satisfy the need for an injected `EventsLogger` in `MenuViewController` in those tests that don't care about logging using a Dummy.
    *   TDD logging the order started event.
    *   Exercise for the reader: TDD logging the order submitted event

#### 10\. How to fix a bug with TDD

_When you find a bug, write a test to reproduce it, then use the feedback from the TDD loop to implement a fix._

*   Introduction to the bug. _The favorites list can contain multiple instances of the same item._
*   Write a test to reproduce the bug.
*   Fix the bug by making the test pass.

#### 11\. Testing Behaviour vs. Testing Implementation

*   Why focusing on testing behaviour is valuable in the long run.
*   Example: show that if we had tested the networking using a Spy it would have been harder to change its implementation.

#### Conclusion

*   TDD as a software development philosophy.
    *   Writing tests first doesn't actually make you slower.
    *   It's all about the feedback loop.

#### Cheat-sheet

*   Xcode testing keyboard shortcuts
*   Asynchronous expectation.
*   Fake.
*   Stub.
*   Spy.
*   Dummy.

#### Where to go from here

*   Addressing the elephant in the room: the build time
*   Continuous Integration.
*   UI Testing.
*   Snapshot testing.
