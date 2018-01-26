_In the context of this post, immutability is the surface of the feature that stays the same, allowing it to be reused with reliability._

# It's not just Left-pad
It's left-pad; dependency, JAR or DLL hell; segfault, a conflict warning, a NoClassDefFoundError or unexpected behaviour; HTTP errors, marshalling errors and can even be unexpected timeouts, infinite loops and any other unexpected behaviour.

# What did SQL get right?
If you model an order system in SQL, you could  contract a SQL guru to do it in 2003 and years later it'd likely still work. I'd be suprised if the average Node app can last months without some form of npm dependency problem.

# Banks didn't trust us
Enterprise software industry was _**maybe**_ making progress on this: W3C (in the old days), JSRs, OMG and OASIS were making immutable standards with backwards compatibility.

But outside the "Enterprise" umbrella, the rest decided to shun strict xhtml, ebXML, SOAP, CORBA IDL and jumped into HTML5, REST, JSON and _**agile**_ moving targets that steer and depend on many _**open source software projects.**_

# Most businesses aren't going to have a business model that changes very much; so why does the software that supposedly represents it?
Microsoft's did do something good (never let me say that again), with relatively [immutable](https://www.youtube.com/watch?v=8WP7AkJo3OE) contracts in their API layers and they weren't the only ones, resulting in the famous acronym: [VRMF](https://www-01.ibm.com/support/docview.wss?uid=swg27008656).

Enterprise computing was dominated by some degree of immutable contracts from Oracle, Microsoft, IBM, Sun, Intel, etc and we still enjoy their efforts. Now, they weren't doing all of this for fun... [regulators liked interfaces](http://www.cptech.org/at/ibm/ibm1984ec.html).

# So what is relatively immutable?
Most of these...

* Instruction Sets
* Assembly
* POSIX
* Enterprise programming languages
* Enterprise Document Formats
* Network protocols
* Enterprise database interfaces
* Filesystem data structures
* Games console libraries

They share something in common. They are either used in regulated environments like for major industries' core business (banking systems, medical uses, etc) or governments, run on embedded systems that are hard to update or tied to hardware.

# And the rest ...

* Application code: but to be fair, this may not have any consumers except Human Beings
* Custom, internal integration services and models developed internally in companies. From startup to multinational, their internal services are only as good as the care dedicated to the project. Sometimes you're lucky to have a spec and other times that specification isn't as long lasting as you'd hoped.
* .., and I hate to say it, but if feels like most open source libraries and applications.

Open source projects seem to thrive on the ability to break users of their interfaces and those that don't often have strong relationships with Enterprise businesses... not always, sometimes ties to Enterprise don't help either.

# Hacking safety in
Some build systems (usually rather poorly) try to enforce immutable versions on top of a programming language and at runtime plugin systems can try to do the same. But it's not an easy process to work with. Both often require a lot of hand-holding to ensure that migration between immutable models, interfaces or services happens without disruption. If you're lucky, they'll warn you about problems and that is great... Maven would be a lot worse without Enforcer, but even in this case the tools aren't always there by default. They highlight the other problem of strange behaviours in that why would you ever allow multiple versions of a library to be imported at the same time: this isn't unique to Java or Maven, in fact they are probably a better pairing then most.

# Why programming languages are to blame?
Although the languages themselves are relatively Immutable (when did java.lang.String not have backwards compatibility) they encourage software development that isn't. The first mistake is to use text files for programming languages and depend on REST for build systems. Neither of which are immutable and yet both of which usually underpin the dependencies for a language, either the packaged library modules or the import/require statements use them, but if you imagine a language that only imported by torrent hashes, then breaking compatibility would be much harder, maybe impossible? Using a hash based database might work quite well, code might be unreadable:

    import sha512[23123213...]
    sha512[23123213...].apply(1))

But then you can map readability:

    identify sha512[23123213...] as listbuilder
    ...
    import listbuilder
    listbuilder.apply(1)
    
Other problems are programming languages encourage mutable design patterns with abstract classes, implicits, annotation preprocessors/dynamic dependency injection.

Things often get worse you start using a languages' custom DSL for XML or JSON: are you creating an XSD first?

Sometimes they embed auto serialization/deserialization to object formats, so code (that mutates) becomes the contract for middleware services, taking a problem at a language level and turning it into one that affects libraries and service layers alike.

# Fixing it

* Let's create immutable build dependencies and imports.
* Ban version conflicts
* Let's drop JSON and REST
* Code to interfaces, don't interface from code
* Ban inheritance of mutable features and implicits that can modify  the runtime behaviour unexpectedly
* Ban Javascript
* Simplify languages
* Aim for code to last 10 years for business domain logic, or maybe just ask the business more often about whether they realise the risks in the choices the development team is making.
