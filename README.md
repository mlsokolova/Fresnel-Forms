#Changes for Fresnel Forms
[Fresnel Form page](https://github.com/ABI-Team-30/Fresnel-Forms) 
Fresnel Forms (FForms) is a plugin for the Protégé ontology editor
Fresnel Forms provide following possibility:
- visualize Fresnel Lenses
- save ontology to Fresnel format. Ontology in Fresnel format can be opened in Protégé.
- save ontology to xml file that can be imported to Semantic MediaWiki
See [https://www.slideshare.net/Lloyd.Rutledge/smwcon-fall-2015-fforms](https://www.slideshare.net/Lloyd.Rutledge/smwcon-fall-2015-fforms) 

There is several changes for Fresnel Form:
- make form field label from semantic label instead from property name(nl.ou.fresnelforms.fresneltowiki.Fresnel2wiki.frmRow)
- add default Form for Category (nl.ou.fresnelforms.fresneltowiki.Fresnel2wiki.makeCategoryPage)
- add default form for Template (nl.ou.fresnelforms.fresneltowiki.Fresnel2wiki.makeTemplatePage)
- set autocomplection if Object Property have Range (nl.ou.fresnelforms.fresnel.PropertyBinding)
- "values from category=" instead of "autocomplete on category=". "autocomplete on category=" not working for MediaWiki 1.28.0 (nl.ou.fresnelforms.fresneltowiki.Fresnel2wiki.frmRow)
- "values from category=" instead of "autocomplete on category=". "autocomplete on category=" not working for MediaWiki 1.28.0 (nl.ou.fresnelforms.fresneltowikitest.FresnelToWikiTest.testFresnelToWiki)
- make Fresnel label from semantic label instead from property name (nl.ou.fresnelforms.jena.JenaFresnelModel.createFormatsFromLensProperties)

##Testing Configuration
Apache Maven 3.2.2
PHP 5.6.26
MariaDB 10.0.21
Apache Jena Fuseki 2.0.0
MediaWiki 1.28.0
Semantic MediaWiki 2.4.6
Page Forms 4.1
ParceFunctions 1.6.0
Character Escapes 0.9.1
Protégé 5.0.0-beta-17

##Architecture
####Semantic Web
It model based on guess that all phenomena world can be described by using three parts: subject, predicate, object:
...
"Contextual Search for Volkswagen and the Automotive Industry" "hasMember" "William Greenly"
"Contextual Search for Volkswagen and the Automotive Industry" "hasMember" "Charles Sandeman-Craik"
"Contextual Search for Volkswagen and the Automotive Industry" "used" "RDF"
"Contextual Search for Volkswagen and the Automotive Industry" "hasPlase" "UK"
...
(data from there: https://www.w3.org/2001/sw/sweo/public/UseCases/)
Phrase of three worlds &lt;subgect&gt; &lt;predicate&gt; &lt;object&gt; called "triple"

See ["Semantic Web for the Working Ontologist. Modeling in RDF, RDFS and OWL" on Gooble Books](https://books.google.ru/books?id=_qGKPOlB1DgC&printsec=frontcover&dq=%22Semantic+Web+for+the+Working+Ontologist%22&hl=ru&sa=X&ved=0ahUKEwjZwbKwsIHVAhXGFZoKHaXbA1IQ6AEIJjAA#v=onepage&q=%22Semantic%20Web%20for%20the%20Working%20Ontologist%22&f=false) 
Fundamental Conceps of Semantic Web and Ontology Modelling is:
- Class
- Propery(Data Property or Object Property)
- Individual
One of main parts of Semantic Web Application is а Triple Store
Semantic Web Vocabularies is: RDF, RDFS, RDFS+, OWL, Fresnel.
The next few triples:
...
"Contextual Search for Volkswagen and the Automotive Industry", "William Greenly", "RDF", "UK" is Individuals
...
"Project" rdf:type rdfs:Class
"Contextual Search for Volkswagen and the Automotive Industry" rdf:type "Project"
"hasMember" rdf:type owl:ObjectProperty
"hasMember" rdfs:domain "Project"
"Person" rdf:type rdfs:Class
"hasMember" rdfs:range "Person"
...

####About Semantic Mediawiki(SMW)
It's Wiki software 
Semantic MediaWiki(SMW) provides human-readable interface (Pages) and machine-readable interface (Semantic Web). Both use the same data.
See [https://www.semantic-mediawiki.org/wiki/Semantic_MediaWiki](https://www.semantic-mediawiki.org/wiki/Semantic_MediaWiki) 
All data created within SMW can easily be published via the Semantic Web.
Fundamental Concepts of SMW:
Category (helps to classify Pages)
Property (helps determine what sort of input will show up)
Template (assign a semantic property to some  of their fields)
Form (helps to create Wiki Pages using SMW Template) 
See [https://www.semantic-mediawiki.org/wiki/Extension:Page_Forms](https://www.semantic-mediawiki.org/wiki/Extension:Page_Forms) 
Any Page, including Category, Property, Template and Form can be exported to xml file.  Then this xml file can be imported to any other or to the same SMW.

####About Apache Jena Fuseki
[Apache Jena - Fuseki: serving RDF data over HTTP](https://jena.apache.org/documentation/fuseki2/) 
Fuseki is integrated with TDB triple store, see [https://jena.apache.org/documentation/tdb/index.html](https://jena.apache.org/documentation/tdb/index.html) 

####About Protégé
Protégé is a free, open-source ontology editor.
[https://protegewiki.stanford.edu/wiki/WebProtege](https://protegewiki.stanford.edu/wiki/WebProtege) 

####About Fresnel Vocabulary
[https://www.w3.org/2005/04/fresnel-info/manual/](https://www.w3.org/2005/04/fresnel-info/manual/) 
Fresnel is a simple, browser-independent vocabulary for specifying how to display RDF models in human-readable form.
Foundational concepts:
Lenses - define which properties of an RDF resource are displayed and how these properties are ordered
Formats - determine how the selected properties are rendered by specifying RDF-specific formatting attributes 
