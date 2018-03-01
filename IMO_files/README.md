# General Structure of EPOS-DCAT-AP web service XML

* ignore `eposap:Catalog`
* ignore `eposap:Project`
* ignore `eposap:Publication`
* ignore `eposap:Service`
* ignore `eposap:Equipment`
* ignore `eposap:Facility`
* fill in `eposap:Person`
* fill in `eposap:Organization`
* fill in `eposap:WebService`

## Common things

* `ORCID` = `http://orcid.org/0000-1111-2222-3333`
* `PIC:123456789` = PIC of organization

## eposap:Person

The filled values are just comments indicating what should be given there.

```xml
    <!-- EPOS Person -->
    <eposap:Person>
        <vcard:fn>LastName, GivenName</vcard:fn>
        <vcard:hasAddress>
            <vcard:Address>
                <vcard:street-address>Street Address</vcard:street-address>
                <vcard:locality>Locality</vcard:locality>
                <vcard:postal-code>Postal-code</vcard:postal-code>
                <vcard:country-name>Country-name</vcard:country-name>
            </vcard:Address>
        </vcard:hasAddress>
        <vcard:hasEmail>emailAddress</vcard:hasEmail>
        <vcard:hasTelephone>PhoneNumber</vcard:hasTelephone>
        <dct:identifier>ORCID</dct:identifier> 
        <eposap:affiliation>PIC:123456789</eposap:affiliation>
        <dct:language>
            <dct:LinguisticSystem>en</dct:LinguisticSystem>
        </dct:language>
        <schema:qualifications>Qualification</schema:qualifications>
        <vcard:hasURL>Website_CV</vcard:hasURL>
    </eposap:Person>
```

Typical `qualifications` are:
* Geochemist, Volcanologist, IT, Data Manager
* Lawyer, Financial Advisor
* Director of (some institute)
* Head of (some observatory)
* Engineer, Researcher, Professor
* PhD, HDR (French habilitation)
* Contractor

## eposap:Organisation

The filled values are just comments indicating what should be given there.

```xml
    <!-- EPOS Organisation -->
    <eposap:Organisation>
        <vcard:fn>Acronym: English name</vcard:fn>
        <vcard:organization-name xml:lang="is">Acronym: Native name</vcard:organization-name>
        <vcard:hasAddress>
            <vcard:Address>
                <vcard:street-address>Street Address</vcard:street-address>
                <vcard:locality>Locality</vcard:locality>
                <vcard:postal-code>Postal-code</vcard:postal-code>
                <vcard:country-name>Country-name</vcard:country-name>
            </vcard:Address>
        </vcard:hasAddress>
        <vcard:hasEmail>emailAddress</vcard:hasEmail>
        <vcard:hasURL>Website</vcard:hasURL>
        <vcard:hasLogo>http://test.org/logo.png</vcard:hasLogo>
        <dct:identifier>PIC:123456789</dct:identifier>
        <eposap:scientificContact>ORCID</eposap:scientificContact>
        <dct:spatial>
            <dct:Location>
                <locn:geometry>POINT(lon lat elevation)</locn:geometry>
            </dct:Location>
        </dct:spatial>
        <dct:type>Organisation Type</dct:type>
        <eposap:legalContact>ORCID</eposap:legalContact>
        <eposap:financialContact>ORCID</eposap:financialContact>
        <eposap:isPartOf>PIC:123456789</eposap:isPartOf>
        <eposap:associatedProjects>projectID01</eposap:associatedProjects>
    </eposap:Organisation>
```

Typical organisation types (`dct:type`) are:
* Scientific and technical establishment
* OUS - Observatory of Universe Sciences
* Research Institute
* Public Research Institute
* Governmental Research Institute
* Non-profit Organisation

## eposap:WebService



```xml
    <!-- EPOS WebService -->
    <eposap:WebService>
        <!-- the title must have a maximum length of 250 chars and that acronyms (e.g. GFZ) 
            as well as too generic service names (e.g. 'Data service') should be avoided 
        -->
        <dct:title>GFZ Data Services</dct:title> <!-- title -->
        <!-- abstract -->
        <dct:description>Since 2004, the GFZ German Research Centre for Geosciences assigns Digital Object Identifiers (DOI) to datasets. These datasets are archived by and published through GFZ Data Services and cover all geoscientific disciplines. They range from large dynamic datasets deriving from data intensive global monitoring networks with real-time data acquisition to the full suite of highly variable datasets collected by individual researchers or small teams. These highly variable data (‘long-tail data’) are small in size, but represent an important part of the total scientific output.</dct:description>
        <dct:issued>2001-12-31T12:00:00</dct:issued><!-- When WS was started -->
        <dct:modified>2016-12-31T12:00:00</dct:modified><!-- Last change or revision of the WS -->
        <!--
            Whenever possible, you should use URIs for licences.
            A register of standard licences is available at:
            http://publications.europa.eu/mdr/resource/authority/licence/html/licences-eng.html
        -->
        <dct:license>Creative Commons for data, Open Source licences for software </dct:license> <!-- Access and Use Restrictions -->
        <foaf:page> <!-- URL -->
            <foaf:primaryTopic>http://dataservices.gfz-potsdam.de/igets/showshort.php?</foaf:primaryTopic>
        </foaf:page>
        <dct:format><!-- distribution format. 
            The base URI of the controlled vocabulary is: https://www.iana.org/assignments/media-types/application/
                 (e.g., zip) -->
            <dct:MediaTypeOrExtent>zip</dct:MediaTypeOrExtent>
        </dct:format>
        <!-- public access limitations:
            There a codelist for this, so you can check if it is suitable to you.
            The description is here:
            http://publications.europa.eu/mdr/resource/authority/access-right/html/access-right-eng.html

            The base URI is:
            http://publications.europa.eu/resource/authority/access-right/
        -->
        <dct:rights>
            <dct:RightsStatement>open data</dct:RightsStatement>
        </dct:rights>
        <!--
            Spatial Reference System
            the CRS should be specified with the relevant URI.
            The base URI is:
            http://www.opengis.net/def/crs/ -->
        <dct:conformsTo>EPSG:4326</dct:conformsTo> <!-- Spatial Reference System -->
        <dct:identifier>http://dataservices.gfz-potsdam.de</dct:identifier> <!-- Unique Resource Identifier: this is the entry point of the service -->
        <dct:created>2001-12-31T12:00:00</dct:created> <!-- When WS was started -->
        <eposap:domain> <!-- This property refers to the domain of resource (e.g. Seismology, Geodesy, 
        Satellite data, Geomagnetic data, Geology, Geohazards, Georesources, Transnational access) -->
            Seismology
        </eposap:domain>
        <eposap:subDomain> <!-- This property refers to the subdomain of resource (to be defined, TBD...) -->
            TBD
        </eposap:subDomain>
        
        <!-- Keywords, annotation. Simple and free (web annotation ontology in the future). List of comma-separated values. -->
        <dcat:keyword>Laboratories, rocks</dcat:keyword> <!-- Keywords -->
        <eposap:operation>TBD</eposap:operation> <!-- still pending, please fill in with TBD (to be defined)-->
        <dct:hasVersion>0.1</dct:hasVersion>

        <!-- List of Parameters:
            this section is needed in order to describe the parameters of the service.
            E.g. in the case of a RESTful service, we may have "domain" as parameter,
            with type "string" and a list of allowed value terms specified by the value tag,
            e.g. 'seism','gps'  (i.e. namespace)-->
        <eposap:parameter>
            <http:paramName>id</http:paramName>
            <rdf:label>id</rdf:label>
            <dct:type> <!-- This property refers to parameter type (e.g., string, integer, float, boolean) -->
                integer
            </dct:type>
            <!-- These properties refer to range value of the parameter -->
            <schema:minValue>0</schema:minValue> 
            <schema:maxValue>100</schema:maxValue>
        </eposap:parameter>
        <eposap:parameter>
            <http:paramName>statType</http:paramName>
            <rdf:label>stationType</rdf:label>
            <dct:type> <!-- This property refers to parameter type (e.g., string, integer, float, boolean, date) -->
                string
            </dct:type>
            <!-- allowed vocabulary terms, optional tag -->
            <http:paramValue>mobile</http:paramValue>
            <http:paramValue>static</http:paramValue>    
            <owl:versionInfo>1.5</owl:versionInfo> <!-- version of parameter -->
        </eposap:parameter>
        <!-- The document is meant to be human readable (e.g. PDF, doc, and so on). 
            This will help a user who, for instance, does not understand something from the hints/label of the parameters. -->
        <schema:documentation>URL pointing to the specification</schema:documentation>
        <dcat:contactPoint>personID01</dcat:contactPoint> <!-- internal link to contact point (vcard:Individual) described in the same file in <eposap:Person> -->
        <eposap:publisher>organisationID01</eposap:publisher> <!-- internal link to responsibleParty (vcard:Organisation) described in the same file in <eposap:Organisation> -->
        <dct:spatial> <!-- Geographic location/spatial extent /bounding box. A single polygon will be supported. -->
            <dct:Location>
                <!-- POLYGON(lon1 lat1, lon2 lat2,...) -->
                <locn:geometry>POLYGON(-10.58 70.09,34.59 70.09,34.59 34.56,-10.58 34.56, -10.58 70.09)</locn:geometry>
            </dct:Location>
        </dct:spatial>
        <!-- Spatial representation type. 
            The base URI is: https://www.iana.org/assignments/media-types/text/
             (e.g., xml) -->
        <adms:representationTechnique> 
            xml
        </adms:representationTechnique>
        <dct:temporal> <!-- temporal extent -->
            <dct:PeriodOfTime>
                <schema:startDate>2001-12-31T12:00:00</schema:startDate>
                <schema:endDate>2016-12-31T12:00:00</schema:endDate>
            </dct:PeriodOfTime>
        </dct:temporal>
        <eposap:DDSS-ID>WPXX-DDSS-ID</eposap:DDSS-ID>
            <eposap:actions>download,visualise,etc</eposap:actions>
    </eposap:WebService>
```