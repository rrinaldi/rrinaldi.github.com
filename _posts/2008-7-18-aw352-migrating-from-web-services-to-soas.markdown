---
layout: post
title: aw352-migrating-from-web-services-to-soas
---
Good morning! Walked the strip last night so I could see the Bellegaio. 
Very sweet hotel and casino.  I've never been to Vegas before so I'm
trying to get in all of the "tourist-y" things.

* * * * *

Presenter: Dan Wahlin (dwahlin at xmlforasp.net )
 
Evolution of Application Architectures:
- Structed Programming
- Object-Oriented
- Component Oriented
     - Componets exposed via contracts (interfaces...IDL)
     - Reduced code coupling
     - Hides implementation
- Web Services
     - Based upon standards (XML,SOAP, Schemas, WSDL)
     - Designed around loosely coupled messaging
     - Potentinal for Interoperablity across multiple platforms (when
designed properly)
 
What is SOA?
- focused on integrating distributed services through published
contracts
 
SOA Fundementals
- Core SOA Fundamentals
     - Design mehtodlogy
     - Leverages existing investments
     - loosely-coupled messaging
     - facilitates and encourages re0use
     - interoperability implied (based on standards)
- Hides implementation details
- Services defined using cntacts
- Handles distributed services
- Can have multiple players
     - Service Provider
     - Service Consumer
     - Service Broker
     - Service Agent
     - Service Bus
 
Web Service and SOA Differences
- SOAs represent a design methodology/architectural pattern for services
- Web Services provide a concrete means for implementing a SOA
     - Services discovered using UDDI
     - Contracts defined using WSDL
     - Messages defined using XSD Schemas
     - Messages exchanged using SOAP/XML
     - Various transport protocol options
- Web Services are only one potential way to realize SOAs
 
Aren't web services SOAs by Default?
- .NET Web Sercice can implement SOA principles but in many cases they
don't
     - Little thought given to input and output messages
     - PRC development
     - Rely on .NET's trnalation engine to generate message structure
     - Embed code directly in WebMethods
 
----
Not feeling this session so far.  Probably because I've spent the last
year working on trying to figure out how to do SOA and most of the
things that the presenter is telling me are things that I figured out on
my own months ago.  This is by no means a slam on the presenter or the
topic, I was just hoping to learn something I didn't know. :(
----
 
 
 
