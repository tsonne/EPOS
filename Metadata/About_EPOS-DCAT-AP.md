# Metadata and EPOS-DCAT-AP

* Author: Tim Sonnemann (tim@vedur.is)
* Created: 2018-02-13

## Purpose of this document

* Explain EPOS-DCAT-AP.

## Summary

* __EPOS-DCAT-AP__ is an extension of __DCAT-AP__ is an extension of __DCAT__.
* These are all __metadata vocabularies__ to describe (web)resources/things/contacts.
* __[DCAT](https://www.w3.org/TR/vocab-dcat/)__ is recommended by the [W3C](http://www.w3.org/) for global use to enable linking basic types of datasets.
* __[DCAT-AP](https://joinup.ec.europa.eu/solution/dcat-application-profile-data-portals-europe/about)__ was developed for data portals in Europe to improve discoverability.
* __[EPOS-DCAT-AP](https://github.com/epos-eu/EPOS-DCAT-AP)__ was developed as extension for Solid Earth data in the [EPOS](http://www.epos-ip.org/) project.

## About Metadata

Mostly taken from Tim Berners-Lee's article about [Metadata Architecture](https://www.w3.org/DesignIssues/Metadata):

* Information about information is generally known as __Metadata__.
* Definition: Metadata is __machine understandable__ information about web resources or other things.
* Metadata is data.
* Metadata about one document can occur within the document, or within a separate document, or it may be transferred accompanying the document.
* Metadata can describe metadata.
* Metadata consists of __assertions__ about data (e.g. name="report_01.doc").
* Data have __attributes__ (e.g. a file can have a *name*, which is one of its attributes).
* Attributes specific to one type of data can be defined in a dedicated __name space__.
* Vocabulary name spaces can be defined/stored at a specific URL.

## DCAT Summary

* [DCAT](https://www.w3.org/TR/vocab-dcat/) is a [W3C](http://www.w3.org/) __vocabulary recommendation for metadata__ to describe datasets in data catalogs across different websites and allow their general interoperability and discoverability on the web.
    - [W3C](http://www.w3.org/) (__World Wide Web Consortium__) is the main international standards organization for the World Wide Web.
    - A __DCAT profile__ is a specification for data catalogs that __extends DCAT__.
* DCAT is an [RDF](https://www.w3.org/2001/sw/wiki/RDF) vocabulary suited to representing government data catalogs.
    - The __Resource Description Framework__ (RDF) is a language for representing information about resources in the World Wide Web.
* It's currently one of the most widely used Semantic Web vocabularies for describing datasets and data catalogues.
* What is defined in DCAT?
    - DCAT is basically a database schema with attributes defined by various name spaces.
    - There are 7 linked classes (tables) total.
    - Each class (table) and attribute (field) has naming pattern `<namespace>:<property>`
    - DCAT uses already existing name spaces for most properties:
        - [dct](http://purl.org/dc/terms/) = [Dublin Core](http://dublincore.org/) terms
        - [dctype](http://purl.org/dc/dcmitype/) = Dublin Core object types
        - [foaf](http://xmlns.com/foaf/spec/) = "Friend of a Friend" dictionary for human relations
        - [rdf](http://www.w3.org/1999/02/22-rdf-syntax-ns#) = RDF vocabulary terms
        - [rdfs](http://www.w3.org/2000/01/rdf-schema#) = RDF Schema vocabulary
        - [skos](http://www.w3.org/2004/02/skos/core#) = Simple Knowledge Organization System
        - [vcard](http://www.w3.org/2006/vcard/ns#) = contact info (virtual business card)
        - [xsd](http://www.w3.org/2001/XMLSchema#) = XML schema definition
    - The [dcat](http://www.w3.org/ns/dcat#) vocabulary specific to DCAT has 4 classes
        - `dcat:Catalog`
        - `dcat:CatalogRecord`
        - `dcat:Dataset` describes common info about a collection of resources
        - `dcat:Distribution` describes a specific resource (file)
    - Other classes used are:
        - `skos:ConceptScheme`
        - `skos:Concept`
        - `foaf:Agent` (can be `foaf:Person` or `foaf:Organization`)

## DCAT-AP Summary

* [DCAT-AP](https://joinup.ec.europa.eu/solution/dcat-application-profile-data-portals-europe/about): __DCAT Application profile for data portals in Europe__
* DCAT-AP is a DCAT profile (i.e. extension) for European applications.
    - Metadata profile based on and compliant with DCAT of W3C.
* __Purpose:__ Define a common interchange metadata format for data portals of the EU and of EU Member States.
* Developed in the framework of the EU Programme *[Interoperability Solutions for European Public Administrations](http://ec.europa.eu/isa/)* (ISA)
* Specification: [DCAT-AP v1.1](https://joinup.ec.europa.eu/system/files/project/dcat-ap_version_1.1.pdf) (Oct 2015)
    - UML diagram on page 8
    - 1-page reference for all classes and properties on page 26
* __Differences__ with DCAT:
    - DCAT-AP adds 15 classes and various properties to DCAT.
        - language, keywords, referenced standards, checksum, location, etc.
    - DCAT-AP also specifies the requirement type for every class/property:
        - mandatory, recommended, optional

## EPOS-DCAT-AP Summary

* [EPOS-DCAT-AP](https://github.com/epos-eu/EPOS-DCAT-AP) is a DCAT-AP extension for Solid Earth data.
* Developed in context of European Plate Observing System ([EPOS](http://www.epos-ip.org/)) project
* [UML diagram](https://github.com/epos-eu/EPOS-DCAT-AP/blob/master/docs/EPOS-DCAT-AP_UML_schema.jpg) shows added classes and links around original DCAT-AP
    - WARNING: The diagram is not up to date and is missing some properties!
* New classes are used to describe:
    - Publication (abstract, issued, title, issn, ...)
    - Organisation (isPartOf, associatedProjects, scientific/legal/financial contact)
    - Person (language, affiliation, qualification)
    - Software (software application schema, model code)
    - Service (terms of use, service type, schema)
    - Webservice (EPOS domain, parameters, contact, created, ...)
    - Equipment (description, type, manufacturer, dynamic range, ...)
    - Facility (theme, type, description, foaf:page, ...)
    - Dataset (character encoding, subject, type, domain, subdomain, ...)
* Mandatory properties describe the minimum set of information needed by the Integrated Core Service (ICS) to automatically categorize, query and expose a dataset/service.
* The required information classes with mandatory/optional properties for EPOS TCS-ICS integration are listed and described in an Excel file: [EPOS_DCAT-AP_Vocabulary_and_Specification.xlsx](https://github.com/epos-eu/EPOS-DCAT-AP/blob/master/docs/EPOS_DCAT-AP_Vocabulary_and_Specification.xlsx)
