Advances in the .NET type system\
 (Code named: NPIA (No Primary Interop Assemblies))\
Type embedding and Type equivalence\
Loose type coupling and extensibility

Challenges:\
Deployment of PIAs\
Interop assemblies are large\
 1.2 Mb for excel

To get the PIAs you need to install the Office 2007 PIA Redistributable:
6.3 Mb

Implementing application extensiblity:\
COM Interop \
    Complex deployment\
Managed to Managed\
    Tight type-coupling\
    Versioning is still hard.

Type embedding\
    CLR 4.0 feature\
    Rutime dependency on Interop Assemblies can be eliminated at compile
time\
    Information required to call into COM objects is embedded into the
assembly

When running no Interop Assembly is ever loaded into memory since it has
been completely embedded into your executable\
Only imports the methods you use in your app.\
Anything that isnt used is skipped over by the type system (a
\_VtblGap\_ method is inserted instead)

There is a property on PIA references that allows you to tell the
compiler to embedde types

Rules:\
Only metadata is locally embedded\
    Interfaces (must have ComImport and Guid attributes)\
    delegates\
    structs\
    enums\
    no classes or static methods

 

Custom code emitted for new operator:

When you new up an object the compiler actually generates a call to
Activator.CreateInstance

Events are handled through a new ComHelper.Events API

Working with Multiple Assembies

> Helper libraries embed types
>
> Now types across multiple assemblies wouldn't be the same
>
> Framework handles this and the types will be equivalent.

Now we are looking into Managed Type Equivalence

Type Equivalence allows loose type coupling inside of .NET (which COM
allowed)

Type Embedding and Type Equivalence are CLR 4.0 features

Casts to an equivalent interface

> CLR Looks for TypeIdentifier attribute to be present on one of the
> interfaces

Calls through an equivalent interface

> COM objects: CLR intercepts the calls and routes them through COM
> interop (this is the old behavior)

Extensibility scenario for COM apps:

> Write add-in code against any verions of host PIA
>
> Embed local types using the /link compiler swtich
>
> Do not need to deploy the PIAs, just your user code
>
> Can compile against Office 2007 PIA and deploy against 2003 and it
> just works. 

Can be used for managed to managed code

Easy way to support interface versioning

 

How is this typesafe?

CLR manages it.  Casts to interface will succeed. Incompatible calls
will fail with System.MethodMissingException

Full trust required for embedding structs
