# Design Goals

## Audience

- Targetting anyone who can use a computer, read english, has internet.

- should be able to be followed easily by someone who has programmed before in another language

- No need to understand any jargon before starting course.

  - someone who has never programmed before should be able to follow while clicking one or two levels deep into definitions and "see also" links.

- avoid teaching any bad practices or anything that isn't best practice, even as stepping stones towards best practice.

  - teaching older/more manual practices as a drill down to explain best practices is ok though, as long as its clearly marked as such for people who might come directly to that page from a google search.

### Best practices

- short functions

- verbose names

- no raw loops

- never use `new` or `delete`

  - go into exceptions to this rule at some point

- classes are for protecting invariants

  - unit testing private functions is ok

- if code can be in a separate module, it should be

  - e.g. separate executable module from the implementation of logic module

- if code can be in a separate header, it should be

  - this one has some grey area, but if functions in a header have different #include dependencies, they should be separated if not insane.

- SOLID

  - single responsibility principle

  - Open/Closed Principle

    - open for extension, closed for modification

  - Liskov Substitution Principle

  - Interface Segregation Principle

  - Dependency Inversion Principle

- think about, and document invariants, preconditions and postconditions

#### Testing

- keep black box and white box unit tests separate

- test all code

- test all postconditions and invariants



## End result for audience

- End result should be someone who can write a program in C++
  - TODO elborate

## Terms / glossary

- All terms should be able to be clicked to get further information - more information about the term itself, and links to related terms, etc

- Terms used in-situ should have enough contextual explanation for them to make sense in-situ, but the drill-down into the term will give a more complete and general description for any context

## Responsiveness to feedback

- Any time someone says that something is not as clear as they would like, or that a term is not understood and not explained, that feedback should be taken seriously and every effort should be made to meet their expectations

  - For example, if a term is assumed to be universally understood by English speakers, but someone doesn't know what it means, we should add it to the glossary
