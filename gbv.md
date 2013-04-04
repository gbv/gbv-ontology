% GBV Ontology
% Jakob Voß
% GIT_REVISION_DATE

# Introduction

This ontology defines some concepts used by the GBV library network.

# Namespaces and prefixes

~~~
@prefix daia: <http://purl.org/ontology/daia/> .
@prefix owl: <http://www.w3.org/2002/07/owl#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix terms: <http://purl.org/dc/terms/> .
@prefix void: <http://rdfs.org/ns/void#> .
@prefix cld: <http://purl.org/cld/terms/> .
~~~

~~~
@prefix : <http://purl.org/ontology/gbv/> .
@prefix gbv: <http://purl.org/ontology/gbv/> .


<http://purl.org/ontology/gbv/> a owl:Ontology ;
    dct:title "GBV Ontology" ;
    dct:description "This ontology defines some concepts used by the GBV library network."@en ;
    owl:versionInfo "Beta version 2011-07-01" .
~~~

# Object Properties

Object properties link resources to other resources.

## srubase

~~~
gbv:srubase a owl:ObjectProperty ;
	rdfs:isDefinedBy <http://purl.org/ontology/gbv/> ;
	rdfs:label "srubase"@en ;
	rdfs:comment "SRU interface of a database"@en ;
	rdfs:domain void:Dataset .
~~~

## oaibase

~~~
gbv:oaibase rdfs:comment "OAI-PMH base URL of a database"@en ;
	a owl:ObjectProperty ;
	rdfs:label "oaibase"@en ;
	rdfs:domain void:Dataset ;
	rdfs:isDefinedBy <http://purl.org/ontology/gbv/> .
~~~

## picabase

~~~
gbv:picabase rdfs:isDefinedBy <http://purl.org/ontology/gbv/> ;
	a owl:ObjectProperty ;
	rdfs:domain void:Dataset ;
	rdfs:label "picabase"@en ;
	rdfs:comment "PICA base URL of a database"@en .
~~~

## solrbase

~~~
gbv:solrbase rdfs:isDefinedBy <http://purl.org/ontology/gbv/> ;
	rdfs:comment "Solr base URL of a database"@en ;
	rdfs:label "solrbase"@en ;
	rdfs:domain void:Dataset ;
	a owl:ObjectProperty .
~~~

## opac

~~~
gbv:opac rdfs:seeAlso cld:catalogueOrIndex, <http://id.loc.gov/vocabulary/relators/own> ;
	a owl:ObjectProperty ;
	skos:scopeNote "the main catalog of a library usually contains records about its holdings, but the main catalog could also contain records that are not held by the institution."@en ;
	rdfs:label "opac"@en ;
	rdfs:range void:Dataset ;
	rdfs:domain daia:Institution ;
	rdfs:comment "main catalog of an institution"@en ;
	rdfs:isDefinedBy <http://purl.org/ontology/gbv/> .
~~~

# Data Properties

Data properties link resources to literal values.

## dbkey

~~~
gbv:dbkey rdfs:label "dbkey"@en ;
	rdfs:isDefinedBy <http://purl.org/ontology/gbv/> ;
	a owl:DatatypeProperty ;
	rdfs:subPropertyOf terms:identifier ;
	rdfs:comment "database key, used as prefix in unAPI and at other APIs within the GBV"@en ;
	skos:scopeNote "must comply to the regular expression ^[a-z][a-z0-9-]*[a-z0-9]$"@en .
~~~

## eln

~~~
gbv:eln rdfs:comment "external library number (ELN) as library identifier within the GBV"@en ;
	rdfs:subPropertyOf terms:identifier ;
	rdfs:label "eln"@en ;
	a owl:DatatypeProperty ;
	rdfs:isDefinedBy <http://purl.org/ontology/gbv/> .
~~~

## gvkppn

~~~
gbv:gvkppn rdfs:comment "PPN identifier within the GBV union catalog (GVK)"@en ;
	rdfs:subPropertyOf terms:identifier ;
	rdfs:isDefinedBy <http://purl.org/ontology/gbv/> ;
	skos:scopeNote "a PPN in general identifies a record in any PICA database. This property must only be used to identity records in GVK."@en ;
	a owl:DatatypeProperty ;
	rdfs:label "gvkppn"@en .
~~~

## iln

~~~
gbv:iln rdfs:isDefinedBy <http://purl.org/ontology/gbv/> ;
	a owl:DatatypeProperty ;
	rdfs:label "iln"@en ;
	rdfs:comment "internal library number (ILN) as library identifier within the GBV"@en ;
	rdfs:subPropertyOf terms:identifier .
~~~

# Datatypes

A [RDF datatype](http://www.w3.org/TR/rdf-concepts/#section-Datatypes-intro)
defines a set of Unicode strings which literal values of this datatype can take
(*literal space*), and a mapping from this set to the set of possible meanings
(*value space*). The datatype of a literal value must explicitely be expressed.

This ontology includes the following datatypes:

## ppn

A PPN in general identifies a record in a PICA database, but it does not
indicate which database it comes from.

~~~
gbv:ppn a rdfs:Datatype ;
    rdfs:comment "A PPN in general identifies a record in a PICA database, but it does not indicate which database it comes from."@en ;
    rdfs:isDefinedBy <> ;
    rdfs:label "PPN identifier"@en .
~~~
