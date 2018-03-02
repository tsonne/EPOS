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

## Common Things

* `ORCID` = `http://orcid.org/0000-1111-2222-3333`
* `PIC:123456789` = PIC of organization

## eposap:Person

### Specific Parameters

Typical `qualifications` are:
* Geochemist, Volcanologist, IT, Data Manager
* Lawyer, Financial Advisor
* Director of (some institute)
* Head of (some observatory)
* Engineer, Researcher, Professor
* PhD, HDR (French habilitation)
* Contractor

### XML

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


## eposap:Organisation

### Specific Parameters

Typical organisation types (`dct:type`) are:
* Scientific and technical establishment
* OUS - Observatory of Universe Sciences
* Research Institute
* Public Research Institute
* Governmental Research Institute
* Non-profit Organisation

### XML

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


## eposap:WebService

### Specific Parameters

License:
* see [list](http://publications.europa.eu/mdr/resource/authority/licence/html/licences-eng.html)
* maybe assume Creative Commons type licenses for gov/public data/services
* use URL to where the license is defined
* common examples:
    - http://www.fsf.org/licensing/licenses/agpl-3.0.html
    - https://creativecommons.org/licenses/by/4.0/
    - https://creativecommons.org/licenses/by-nc_sa/3.0/
    - http://creativecommons.org/licenses/by-nc/4.0/
    - TBD <-- inappropriate

Rights statement:
* see [list](http://publications.europa.eu/mdr/resource/authority/access-right/html/access-right-eng.html)
* basically these:
    - PUBLIC
    - RESTRICTED
    - others wrote lots of extra stuff, but probably does not conform here

Parameter `dct:conformsTo` is spatial reference:
* use URL to a coordinate reference system
* base: http://www.opengis.net/def/crs

Redundant? `foaf:page.foaf:primaryTopic` and `dct:identifier`
* yes for most examples

`eposap:domain`: Geology, anthropogenic hazards, Geomagnetism, Geoelectromagnetism, Satellite-Observations, Volcanology, Volcano-Observations, Geodesy, Geohazards, Near Fault Observations, Seismology
* probably `Volcanology`, current examples are somewhat inconsistent

`eposap:subDomain`: Episodes, coal mining, reservoir impoundment, conventional hydrocarbon extraction, geothermal energy production, 3D/4D models, Borehole data, Geological Data, salt solution mining, hard rock mining, Global Magnetic Model, Magnetic Field, InSAR, Volcanological Data, Geochemical-Data, Seismic stations, Seismic waveforms, GNSS Products Portal, Crustal velocity parameters, waveform quality, Seismic Hazard products, Historical earthquakes, Earthquake parameters
* seems like a catch-all parameter without consistent vocabulary

`eposap:operation`: Fill in "TBD" for now
* common examples from others are: TBD, execute, download, visualize, getmap, metadata

`eposap:parameter`: Only query parameters allowed, no path parameters!!!
* can give parameter label, i.e. description for users
* should specify type, e.g. string, integer, numeric...
* can limit numeric range (min/max values)
* can specify allowed set of values, e.g. 'on', 'off' if applicable

Bounding box: `<dct:spatial><dct:Location><locn:geometry>`
* Must be one polygon like: `POLYGON(lon1 lat1, lon2 lat2,...)`
* examples seem to be 5 clockwise points, first == last point, rectangle

`</dct:spatial><adms:representationTechnique> `:
* (base URI: https://www.iana.org/assignments/media-types/text/)
* not well explained what this is
* only useful if returned data have a specific georeferenced format?
* probably leave empty for now...

### XML

The filled values are just comments indicating what should be given there.

```xml
    <!-- EPOS WebService -->
    <eposap:WebService>
        <dct:title>Descriptive_Title_for_Service</dct:title>
        <dct:description>More verbose description text...</dct:description>
        <dct:issued>2018-03-10T12:00:00</dct:issued><!-- When WS was started -->
        <dct:modified>2018-12-31T12:00:00</dct:modified>
        <dct:license>license_link...</dct:license>
        <foaf:page>
            <foaf:primaryTopic>web endpoint URL...</foaf:primaryTopic>
        </foaf:page>
        <dct:format>
            <dct:MediaTypeOrExtent>service MIMEtype...</dct:MediaTypeOrExtent>
        </dct:format>
        <dct:rights>
            <dct:RightsStatement>PUBLIC</dct:RightsStatement>
        </dct:rights>
        <dct:conformsTo>http://www.opengis.net/def/crs/EPSG/0/4326</dct:conformsTo>
        <dct:identifier>web endpoint URL...</dct:identifier>
        <dct:created>2001-12-31T12:00:00</dct:created>
        <eposap:domain>EPOS topic...</eposap:domain>
        <eposap:subDomain>EPOS domain's subcategory...</eposap:subDomain>
        <dcat:keyword>comma, separated, keywords...</dcat:keyword>
        <eposap:operation>TBD</eposap:operation>
        <dct:hasVersion>0.1</dct:hasVersion>
        <eposap:parameter>
            <http:paramName>query parameter name...</http:paramName>
            <rdf:label>description...</rdf:label>
            <dct:type>value type, e.g. string, integer...</dct:type>
            <schema:minValue>numeric min value...</schema:minValue> 
            <schema:maxValue>numeric max value...</schema:maxValue>
        </eposap:parameter>
        <eposap:parameter>
            <http:paramName>query parameter name...</http:paramName>
            <rdf:label>description...</rdf:label>
            <dct:type>value type, e.g. string, integer...</dct:type>
            <http:paramValue>allowed valueX...</http:paramValue>
            <http:paramValue>allowed valueY...</http:paramValue>    
            <owl:versionInfo>version number of parameter...</owl:versionInfo>
        </eposap:parameter>
        <schema:documentation>URL of service manual...</schema:documentation>
        <dcat:contactPoint>ORCID of already mentioned person...</dcat:contactPoint>
        <eposap:publisher>PIC of already mentioned org</eposap:publisher>
        <dct:spatial>
            <dct:Location>
                <locn:geometry>
                    POLYGON(-25 66.7,-13 66.7,-13 63.1,-25 63.1, -25 66.7)
                </locn:geometry>
            </dct:Location>
        </dct:spatial>
        <adms:representationTechnique>xml</adms:representationTechnique>
        <dct:temporal>
            <dct:PeriodOfTime>
                <schema:startDate>2001-12-31T12:00:00</schema:startDate>
                <schema:endDate>2018-12-31T12:00:00</schema:endDate>
            </dct:PeriodOfTime>
        </dct:temporal>
        <eposap:DDSS-ID>WPXX-DDSS-ID</eposap:DDSS-ID>
            <eposap:actions>download,visualise,etc</eposap:actions>
    </eposap:WebService>
```