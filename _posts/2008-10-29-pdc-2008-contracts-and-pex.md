Contract based development

Add contracts to code that ensure adherence to spec and implementation

-   Contract.Requires( 0 \< x);
-   Contract.Ensures(Contract.Result\<string\>() != null)
-   System.Diagnostics.Contracts
-   .NET 4.0

Contracts document design decisions

Contracts are executable

-   Checked documentation

Contracts help static verification

Assertions help, but not perfect

-   Not a contract between 2 parties

Demo of contracts

Creating a Rational number

You can get a preview of code contracts now for 2008

By default it looks at IL and can generate warnings of possible runtime
errors even without any contracts

Adding contracts make the contracts part of the method signature

Contracts look at the type as a whole, not just the standard constructor

Use ObjectInvariant method

-   This binds the object to a state that has to be true at the end of
    each method and each constructor

Using Pex with Contracts

-   Pex finds all the values that would violate the contract

What can I do with Contracts?

-   Static Checking
-   Runtime Checking
-   Test Generation (Pex)
-   Documentation

What contracts are there?

Requires

Ensures

-   what is true at method exit

Invariants

-   what is true at ANY method exit

What can be put in a contract?

Any boolean expression (including method calls)

-   Contract.Requires( value != null);

Contract.Result

-   Contract.Ensures(Contract.Result\<int\>() ==
    Contract.OldValue(Count));

(SOMETHING ELSE that i missed. Grr)

Contracts are declarative

-   They are executed at the proper point in the chain no matter where
    they are called

Demo of an ArrayList full of contracts (Runtime validations)

There is a subtype that overrides Add and returns -1 which violates the
Add contract

Contracts get populated into subtypes

-   The tool takes care of contract injections

Probably don't want to put contracts out there in Release builds

-   If you still want them in Release there are other methods to use to
    put them into release builds
-   If you don't want them in Release the standard methods will exclude
    the contracts (faster)

Static Contract Checking

Analyzes all execution paths

Guides development

Not only explicit contracts

-   De-referencing null
-   indexing arrays
-   Arithmetic exceptions

What gets shipped?

Release assemblies + Contract Reference assemblies

-   Contract Reference Assemblies are all contracts, no code

Interface Contracts

-   ContractClass attribute
-   ContractClassFor attribute

Summary

Contract library class for all .NET languages

Contracts are being used in the BCL today

Same contracts used for

-   Runtime checking
-   Static checking
-   Documentation generation

PEX

Testing before Pex

-   Testing is tedious
-   too easy to miss cases
-   old tests get stale
-   too much legacy code - what does it do?

Tests for free: Demo

-   Using Pex Explorations you can see all the branches and all the
    values that execute those branches
-   Any Pex exploration can be saved as a unit test
-   Just right click in code -\> explore -\> get test cases for free

Demo: Using Pex to explore a class in NHibernate (Typename Parser)

-   Generates 31 different test cases
-   All MSTest cases
-   Pex gives you 100% Code Coverage
-   Once you start to understand code, you should start adding contracts
    and running more explorations to validate those contracts

Pex gives you high code coverage and generates automagically pretty good
test suites

Pex finds contract violations

Integrates with VS Team Test

can be used as Build Verification tests

-   Very targeted small tests

PexMethods

Parameterized Unit Test

-   A unit test method that takes parameters

Pex generates traditional Unit Tests in C\# which fix particular values

How to test this code? Demo

-   ResourceReader
-   It takes a stream
-   It gets down to reading bytes from a stream that can be ugly
    (includes magic numbers)
-   With parameterized tests you need to do some setup and create a
    viable scenario for testing
-   Everytime Pex finds a branch it creates a test case.
-   You can tell Pex what exceptions are acceptable and it will only
    flag un-expected exceptions as errors

Pex understands code

-   Pex does not guess
-   Pex does not enumerate all possible values
-   Pex does not make you write test input generators
-   Pex partitions inputs into equivalance classes
-   One equivalence class per branchin behavior
-   Test inputs computed by Z3, a constraint solver from MSR

[Pex](http://research.microsoft.com/Pex/) and Contracts are the shit. 
Seriously.  After watching this demo I'm all about it.  Downloading and
installing as soon as I get back home.

URL:
[http://research.microsoft.com/pex](http://research.microsoft.com/pex)
