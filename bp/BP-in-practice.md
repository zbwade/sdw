# Spatial Data on the Web Best Practices in Practice 

- In progress - examples from best practices already, OGC Testbed 14 etc

## [Best Practice 1: Use globally unique persistent HTTP URIs for Spatial Things](https://www.w3.org/TR/sdw-bp/#bp-identifiers)

### Examples from Best Practices

#### EXAMPLE 4

>This URI identifies the Amsterdam Central train station:
>
>https://brt.basisregistraties.overheid.nl/top10nl/id/gebouw/102625209
>
>This URI was minted using the recommendations in the Dutch URI strategy. Although minted by the Kadaster, they chose to use the domain ‘basisregistraties.overheid.nl’ (which translates to ‘base registries . government . nl’) because this is expected to be a more persistent name than ‘kadaster.nl’. Even though the Kadaster is over a 100-years old, organization names are not considered persistent in general as organizations may merge or their names may change. ‘top10nl’ is the name of the dataset, and ‘gebouw’ means ‘building’ – giving the human reader of this URI a clue of what is being identified. The last part of the URI is the building number from the dataset.


### Other Examples

- TBD

## [Best Practice 2: Make your spatial data indexable by search engines](https://www.w3.org/TR/sdw-bp/#bp-indexable)

### Example from Best Practices

#### EXAMPLE 5

>In case of an address dataset, you could organize the Spatial Things (the addresses) by municipality, post code and street name to >support a human user to get to a building with a few clicks.

#### EXAMPLE 6

>Possible implementation approaches for addressing this best practice in the context of an existing SDI are discussed in more detail in >Best Practice 12: Expose spatial data through 'convenience APIs' for additional information. For example, by using a proxy tool like >ldproxy or by mapping the data in the SDI dynamically to crawlable resources on the Web using the [R2RML] standard and Linked Data >Publication tools. Both approaches generate crawlable data from Spatial Things in your spatial datasets at query time and allow to >enrich the data on the Web with additional information and links

#### EXAMPLE 7

>The Property Search in the City of Nanaimo, Canada provides a landing page and one page per property. The landing page offers a search capability and the option to browse by street. This data is indexed; a search for, for example, "2100 AARON WAY, NANAIMO, BC" in a popular search engine returns the Nanaimo data for this Spatial Thing as one of the first results.
>
>The Bathing Water Quality Explorer for England provides a landing page and one page per site. Sites can be searched, selected from a list or in a map.
>
>In both cases, the pages of the Spatial Things are generated from the underlying data at request time.
>
>The property Web-pages in Nanaimo also use [MICRODATA] annotations using [SCHEMA-ORG], which is discussed below.

#### EXAMPLE 8

>This code-snippet illustrates a [JSON-LD] annotation using a [SCHEMA-ORG] Dataset for an address dataset in the Netherlands that may be embedded in the HTML of the Web-page. It includes a name, a description, the spatial coverage using a bounding box, the URL of the Web-page, and a link to another dataset containing this dataset. The same annotation could also be provided using [MICRODATA], but we use [JSON-LD] here as this presents the structured data in a more human-readable way.
>
><pre>&lt;script type="application/ld+json">
>{
>  "@context" : {
>    "@vocab" : "http://schema.org/"
>  },
>  "@type" : "Dataset",
>  "@id" : "http://www.ldproxy.net/bag/inspireadressen/",
>  "name" : "Adressen",
>  "description" : "INSPIRE Adressen afkomstig uit de basisregistratie Adressen, beschikbaar voor heel Nederland",
>  "url" : "http://www.ldproxy.net/bag/inspireadressen/",
>  "isPartOf" : {
>    "@type" : "Dataset",
>    "url" : "http://www.ldproxy.net/bag/"
>  },
>  "keywords" : "Adressen",
>  "spatialCoverage" : {
>    "@type" : "Place",
>    "geo" : {
>      "@type" : "GeoShape",
>      "box" : "47.975,3.053 53.504,7.24"
>    }
>  }
>}
></script></pre>
>This code-snippet illustrates a [JSON-LD] annotation using a [SCHEMA-ORG] Place for the address of the "Anne Frank’s House" in that dataset. It includes the location, the URL of the Web-page, and the structured postal address information.
>
><pre>&lt;script type="application/ld+json">
>{
>  "@context" : {
>    "@vocab" : "http://schema.org/"
>  },
>  "@type" : "Place",
>  "@id" : "http://www.ldproxy.net/bag/inspireadressen/inspireadressen.3329155",
>  "url" : "http://www.ldproxy.net/bag/inspireadressen/inspireadressen.3329155",
>  "geo" : {
>    "@type" : "GeoCoordinates",
>    "longitude" : "4.88399",
>    "latitude" : "52.37520"
>  },
>  "name": "Anne Franks House",
>  "description": "Museum house where Anne Frank & her family hid from the Nazis in a secret annex, during WWII.",
>  "address" : {
>    "@type" : "PostalAddress",
>    "streetAddress" : "Prinsengracht 267",
>    "addressLocality" : "Amsterdam",
>    "postalCode" : "1016GV"
>  }
>}
></script></pre>

#### EXAMPLE 9

>At the time of writing, Google is indexing [KML] documents and supporting advanced searches that are restricted to KML documents. [GML] files are also indexed, but only like any other XML [XML11] documents. JSON [RFC7159], including GeoJSON [RFC7946], is currently not indexed.

### Other Examples

- TBD

## [Best Practice 3: Link resources together to create the Web of data](https://www.w3.org/TR/sdw-bp/#bp-linking)

### Examples from Best Practices

#### EXAMPLE 10: HTTP response Link header with IANA Link Relation types

>HTTP/1.1 200 OK
>Link: <http://www.gemeentegeschiedenis.nl/gemeentenaam/Amsterdam/2014>; rel="predecessor-version"
>Content-type: application/geo+json
>Connection: close
>
>{...}

### Other Examples

- TBD

## [Best Practice 4: Use spatial data encodings that match your target audience](https://www.w3.org/TR/sdw-bp/#bp-expressing-spatial)

### Examples from Best Practices

#### EXAMPLE 11

>Wikipedia includes web pages about many Spatial Things, for example Florence Cathedral. This page provides latitude and longitude coordinates for the cathedral, as well as linking to other pages about the city of Florence and the region of Tuscany. It would be better if typical Wikipedia pages about Spatial Things were explicit about the coordinate reference system used. However, a link is also provided to the 'Geohack' service which provides detailed location information, including the CRS.

#### EXAMPLE 12

>d3.js is a widely used JavaScript library for creating visualizations in web pages. This tutorial by Mike Bostock describes how to use D3 to work with geometrical data and display it in a web page.

#### EXAMPLE 13

>The Scottish Government makes a lot of statistical data available via their website Statistics.gov.scot. Every statistical data point is referred to a geographical area, identified by an HTTP URI, making it easy to compare different datasets about an area of interest. See for example this page about the City of Edinburgh Council Area.

#### EXAMPLE 14

>Statistics Netherlands (CBS) publishes their Neighborhoods statistics data as a [WFS] service. The capabilities of that service can be requested in the following way:
>
>https://geodata.nationaalgeoregister.nl/wijkenbuurten2016/wfs?request=GetCapabilities
>For example, the following request returns the data for neighborhoods within the specified bounding box. The bounding box is specified using EPSG:28992 ("Amersfoort / RD New") and indicates an areay of 100 square meters.
>
>https://geodata.nationaalgeoregister.nl/wijkenbuurten2016/wfs?request=GetFeature&typename=wijkenbuurten2016:cbs_wijken_2016&version=2.0.0&service=WFS&bbox=120000,480000,130000,490000

### Other Examples

#### LDProxy WFS 3.0 JSON Encoding

This example implementation of a WFS 3.0 provides a JSON-LD encoding using <code>@context</code> to provide semantics from schema.org

https://www.ldproxy.nrw.de/topographie/AX_Vegetationsmerkmal/DENWAT01D000BAoT/?f=jsonld

<pre>
{
  "@context" : {
    "@vocab" : "http://schema.org"
  },
  "@type" : "Place",
  "id" : "https://www.ldproxy.nrw.de/topographie/AX_Vegetationsmerkmal/DENWAT01D000BAoT",
  "url" : "https://www.ldproxy.nrw.de/topographie/AX_Vegetationsmerkmal/DENWAT01D000BAoT",
  "geo" : {
    "@type" : "GeoShape",
    "line" : "6.410075411601025,50.326107831017666 6.409635231068937,50.323045007336866"
  },
  "bewuchs" : "1100"
}
</pre>

## [Best Practice 5: Provide geometries on the Web in a usable way](https://www.w3.org/TR/sdw-bp/#geometry-and-crs)

### Examples from Best Practices

#### EXAMPLE 15: [GeoDCAT-AP] representation of dataset spatial coverage (bounding box) in multiple encodings
<pre>
@prefix dcat:      <http://www.w3.org/ns/dcat#> .
@prefix dcterms:   <http://purl.org/dc/terms/> .
@prefix geosparql: <http://www.opengis.net/ont/geosparql#> .
@prefix locn:      <http://www.w3.org/ns/locn#> .

<http://www.ldproxy.net/bag/inspireadressen/> a dcat:Dataset ;
  dcterms:title "Adressen"@nl ;
  dcterms:title "Addresses"@en ;
  dcterms:description "INSPIRE Adressen afkomstig uit de basisregistratie Adressen,
                   beschikbaar voor heel Nederland"@nl ;
  dcterms:description "INSPIRE addresses derived from the Addresses base registry,
                   available for the Netherlands"@en ;
  dcterms:isPartOf <http://www.ldproxy.net/bag/> ;
  dcat:theme <http://inspire.ec.europa.eu/theme/ad> ;
  dcterms:spatial [
    a dcterms:Location ;
    locn:geometry
# Bounding box in WKT
      "POLYGON((3.053 47.975,7.24 47.975,7.24 53.504,3.053 53.504,3.053 47.975))"^^geosparql:wktLiteral ,
# Bounding box in GML
      "<gml:Envelope srsName=\"http://www.opengis.net/def/crs/OGC/1.3/CRS84\">
         <gml:lowerCorner>3.053 47.975</gml:lowerCorner>
         <gml:upperCorner>7.24  53.504</gml:upperCorner>
       </gml:Envelope>"^^geosparql:gmlLiteral ,
# Bounding box in GeoJSON
      "{ \"type\":\"Polygon\",\"coordinates\":[[
           [3.053,47.975],[7.24,47.975],[7.24,53.504],[3.053,53.504],[3.053,47.975]
         ]] }"^^https://www.iana.org/assignments/media-types/application/geo+json
  ] .
</pre>
  
#### EXAMPLE 16: [GML] description of a building, with detailed geometry

>The [GML] representation of Anne Frank's house building (taken from the BAG WFS endpoint):
><pre>&lt;bagwfs:pand gml:id="pand.3323294">
  <bagwfs:identificatie>363100012169587</bagwfs:identificatie>
  <bagwfs:bouwjaar>1635</bagwfs:bouwjaar>
  <bagwfs:status>Pand in gebruik (niet ingemeten)</bagwfs:status>
  <bagwfs:gebruiksdoel>woonfunctie</bagwfs:gebruiksdoel>
  <bagwfs:oppervlakte_min>1</bagwfs:oppervlakte_min>
  <bagwfs:oppervlakte_max>21</bagwfs:oppervlakte_max>
  <bagwfs:aantal_verblijfsobjecten>20</bagwfs:aantal_verblijfsobjecten>
  <bagwfs:geometrie>
    <gml:MultiSurface srsDimension="2" axisLabels="east north"
                         srsName="urn:ogc:def:crs:EPSG::28992">
      <gml:surfaceMember>
        <gml:Polygon srsDimension="2">
          <gml:exterior>
            <gml:LinearRing>
              <gml:posList>
                120749.725 487589.422  120752.55  487594.375  120751.227 487595.129
                120732.539 487605.788  120723.505 487589.745  120721.387 487585.939
                120740.668 487575.07   120743.316 487573.589  120747.735 487581.337
                120751.564 487579.154  120755.411 487576.96   120750.935 487569.172
                120755.941 487566.288  120764.369 487581.066  120749.725 487589.422
                </gml:posList>
            </gml:LinearRing>
          </gml:exterior>
        </gml:Polygon>
      </gml:surfaceMember>
    </gml:MultiSurface>
  </bagwfs:geometrie>
</bagwfs:pand></pre>

>The corresponding RDF representation is provided in the following [TURTLE] snippet (taken from the BAG Linked Data service). NB: The RDF representation below has been complemented with additional properties (marked with # Added) for demonstration purposes.

#### EXAMPLE 17: [RDF] description of a building, with detailed geometry
<pre>
@prefix bag:       <http://bag.basisregistraties.overheid.nl/def/bag#> .
@prefix dcterms:   <http://purl.org/dc/terms/> .
@prefix geosparql: <http://www.opengis.net/ont/geosparql#> .
@prefix gml-ont:   <http://www.opengis.net/ont/gml#> .
@prefix locn:      <http://www.w3.org/ns/locn#> .
@prefix pdok:      <http://data.pdok.nl/def/pdok#> .
@prefix rdfs:      <http://www.w3.org/2000/01/rdf-schema#> .
@prefix schema:    <http://schema.org/> .
@prefix w3cgeo:    <http://www.w3.org/2003/01/geo/wgs84_pos#> .

<http://bag.basisregistraties.overheid.nl/bag/id/pand/0363100012169587> 
  a geosparql:Feature, bag:Pand ;
  rdfs:label "Pand 0363100012169587"@nl;
  rdfs:isDefinedBy <http://bag.basisregistraties.overheid.nl/bag/doc/2016083000000000/pand/0363100012169587> ;
  bag:identificatiecode "0363100012169587"^^xsd:string;
# Added
  dcterms:identifier "363100012169587"^^xsd:string ;
  bag:status <http://bag.basisregistraties.overheid.nl/id/begrip/PandInGebruik_nietIngemeten> ;
  bag:oorspronkelijkBouwjaar "1635"^^xsd:gYear;
# Added
  dcterms:created "1635"^^xsd:gYear ;
# Added
  locn:address <http://www.ldproxy.net/bag/inspireadressen/inspireadressen.3329155> ;
  geosparql:hasGeometry <http://bag.basisregistraties.overheid.nl/bag/id/geometry/5C1F8F11324717378B437B2CD12871FF> ;
  bag:geometriePand <http://bag.basisregistraties.overheid.nl/bag/id/geometry/5C1F8F11324717378B437B2CD12871FF>
.

<http://bag.basisregistraties.overheid.nl/bag/id/geometry/5C1F8F11324717378B437B2CD12871FF> 
  a geosparql:Geometry, gml-ont:Surface ;
  geosparql:asWKT 
    "POLYGON ((
      4.8842353  52.375108 , 4.884276 52.375153 , 
      4.8842567  52.375159 , 4.883981 52.375254 , 
      4.8838502  52.375109 , 4.883819 52.375075 , 
      4.8841037  52.374979 , 4.884143 52.374965 , 
      4.8842069  52.375035 , 4.884263 52.375016 , 
      4.8843200  52.374996 , 4.884255 52.374926 , 
      4.8843289  52.374901 , 4.884451 52.375034 , 
      4.8842353  52.375108
    ))"^^geosparql:wktLiteral ;
  pdok:asWKT-RD 
    "POLYGON ((
      120749.725 487589.422 , 120752.55 487594.375  ,   
      120751.227 487595.129 , 120732.539 487605.788 ,
      120723.505 487589.745 , 120721.387 487585.939 , 
      120740.668 487575.07  , 120743.316 487573.589 , 
      120747.735 487581.337 , 120751.564 487579.154 , 
      120755.411 487576.96  , 120750.935 487569.172 , 
      120755.941 487566.288 , 120764.369 487581.066 , 
      120749.725 487589.422
    ))"^^xsd:string ;
# Added
  geosparql:asWKT 
    "<http://www.opengis.net/def/crs/EPSG/0/28992> POLYGON ((
      120749.725 487589.422 , 120752.55 487594.375  ,   
      120751.227 487595.129 , 120732.539 487605.788 ,
      120723.505 487589.745 , 120721.387 487585.939 , 
      120740.668 487575.07  , 120743.316 487573.589 , 
      120747.735 487581.337 , 120751.564 487579.154 , 
      120755.411 487576.96  , 120750.935 487569.172 , 
      120755.941 487566.288 , 120764.369 487581.066 , 
      120749.725 487589.422
    ))"^^geosparql:wktLiteral
.</pre>

>The different WKT encodings in the example show alternative ways of specifying the coordinate reference system used.

#### EXAMPLE 18: HTTP URIs for geometries

>As shown in Example 4, the following URI:
>
>https://brt.basisregistraties.overheid.nl/top10nl/id/gebouw/102625209
>
>denotes Amsterdam Central train station. However, its geometry is provided as a separate, standalone resource, denoted by the following URI:
>
>https://brt.basisregistraties.overheid.nl/top10nl/id/geometry/2525562935f2c33152e98f65f9d8d6ff
>
>A similar approach is used by Ordnance Survey. For instance, North Devon is denoted by the following URI:
>
>http://data.ordnancesurvey.co.uk/id/7000000000022933
>
>whereas its geometry is denoted by:
>
>http://data.ordnancesurvey.co.uk/id/geometry/22933-4
>
>An additional example is the API of the GADM-RDF project, providing access to spatial linked data concerning administrative areas. For instance, the following URI http://gadm.geovocab.org/id/0/60 returns a description of administrative area "Germany", which links to the geometry of Germany's boundaries, provided via a separate URI: http://gadm.geovocab.org/id/0/60/geometry.
>
>Dereferencing the geometry URIs operated by the GADM-RDF API returns different geometry representations / encodings (SVG included), that can be accessed via HTTP content negotiation or by appending the format extension to the URI. For instance, URI http://gadm.geovocab.org/id/0/60/geometry.geojson returns the GeoJSON [RFC7946] representation of the geometry. Direct links to the supported geometry representations / encodings are specified in the RDF and HTML representations of the geometry.

### Other Examples

- TBD

## [Best Practice 6: Provide geometries at the right level of accuracy, precision, and size](https://www.w3.org/TR/sdw-bp/#geometry-and-crs)

### Examples from Best Practices

#### EXAMPLE 19

>The point coordinates of the address of Anne Frank's House (see Example 8) can be encoded with Geohash as u173zns7thy (corresponding to the following WGS 84 lat/long coordinates: 52.37520 4.88399).

#### EXAMPLE 20

>The GADM-RDF project provides access to geometries of administrative areas at a resolution of 100m, 1km, 10km, and 100km. Each of these variants is associated with a different HTTP URI, and geometry data are made available in different formats. For instance, the geometry of Germany at 100m resolution is denoted by the following URI http://gadm.geovocab.org/id/0/60/geometry_100m, whereas the variant at 100km resolution is available from the following URI: http://gadm.geovocab.org/id/0/60/geometry_100km (see also Example 18: HTTP URIs for geometries).

#### EXAMPLE 21

>In the following [TURTLE] snippet, [W3C-BASIC-GEO] and [GeoRSS] are used to specify, respectively, the centroid (w3cgeo:lat and w3cgeo:long) and bounding box (georss:box) of the 2-dimensional footprint of the building hosting Anne Frank's Museum (see Example 17: [RDF] description of a building, with detailed geometry).
<pre>
@prefix bag:       <http://bag.basisregistraties.overheid.nl/def/bag#> .
@prefix georss:    <http://www.georss.org/georss/> .
@prefix geosparql: <http://www.opengis.net/ont/geosparql#> .
@prefix rdfs:      <http://www.w3.org/2000/01/rdf-schema#> .
@prefix w3cgeo:    <http://www.w3.org/2003/01/geo/wgs84_pos#> .

<http://bag.basisregistraties.overheid.nl/bag/id/pand/0363100012169587> 
  a geosparql:Feature, bag:Pand ;
  rdfs:label "Pand 0363100012169587"@nl;
  
# Detailed geometry  
  
  geosparql:hasGeometry <http://bag.basisregistraties.overheid.nl/bag/id/geometry/5C1F8F11324717378B437B2CD12871FF> ;
  bag:geometriePand     <http://bag.basisregistraties.overheid.nl/bag/id/geometry/5C1F8F11324717378B437B2CD12871FF> ;
  
# Centroid

  w3cgeo:lat  "52.37509"^^xsd:float ;
  w3cgeo:long "4.88412"^^xsd:float ;
  
# Bounding box

  georss:box "52.3749,4.8838 52.3753,4.8845"^^xsd:string .
.
</pre>
### Other Examples

- TBD

## [Best Practice 7: Choose coordinate reference systems to suit your user's applications](https://www.w3.org/TR/sdw-bp/#geometry-and-crs)

### Examples from Best Practices

None.

### Other Examples

- TBD

## [Best Practice 8: State how coordinate values are encoded](https://www.w3.org/TR/sdw-bp/#geometry-and-crs)

### Examples from Best Practices

#### EXAMPLE 22: Coordinate reference system stated in [GeoDCAT-AP] (TTL encoding)

>There are four common ways that this information can be provided:
>
>Describe the coordinate reference system in the dataset metadata.
><pre>

@prefix ex:      <http://data.example.org/datasets/> .
@prefix dcat:    <http://www.w3.org/ns/dcat#> .
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix skos:    <http://www.w3.org/2004/02/skos/core#> .

ex:ExampleDataset 
  a dcat:Dataset ;
  dcterms:conformsTo <http://www.opengis.net/def/crs/EPSG/0/32630> .

<http://www.opengis.net/def/crs/EPSG/0/32630> 
  a dcterms:Standard, skos:Concept ;
  dcterms:type <http://inspire.ec.europa.eu/glossary/SpatialReferenceSystem> ;
  dcterms:identifier "http://www.opengis.net/def/crs/EPSG/0/32630"^^xsd:anyURI ;
  skos:prefLabel "WGS 84 / UTM zone 30N"@en ;
  skos:inScheme <http://www.opengis.net/def/crs/EPSG/0/> .</pre>
>The example above illustrates how to describe the coordinate reference system used for a dataset within [GeoDCAT-AP] metadata. The conformsTo property from [DCTERMS] is used to assert the relationship between dataset and CRS in the same way that conformance with a standard is expressed in [VOCAB-DQV].
>
>Dataset metadata for spatial data should always provide details of the CRS used. For more information about dataset metadata, please refer to Best Practice 13: Include spatial metadata in dataset metadata.

#### EXAMPLE 23: Coordinate position provided using [W3C-BASIC-GEO]

>Provide each coordinate value with explicit labels and provide metadata to indicate what each label means.
<pre>
@prefix w3cgeo: <http://www.w3.org/2003/01/geo/wgs84_pos#> .
@prefix dcterms: <http://purl.org/dc/terms/> .

:myPointOfInterest a w3cgeo:SpatialThing ;
    dcterms:description "Anne Frank's House, Amsterdam."
    w3cgeo:lat "52.37514"^^xsd:float ;
    w3cgeo:long "4.88412"^^xsd:float ;
    .</pre>
>The labels (or terms) w3cgeo:lat and w3cgeo:long are provided by the [W3C-BASIC-GEO] vocabulary which states that it is:
>
>A vocabulary for representing latitude, longitude and altitude information in the WGS 84 geodetic reference datum.
>
>The terms themselves (plus w3cgeo:alt) are defined with all the necessary information as follows:
>
>lat: The WGS 84 latitude of a Spatial Thing (decimal degrees).
>long: The WGS 84 longitude of a Spatial Thing (decimal degrees).
>alt: The WGS 84 altitude of a Spatial Thing (decimal meters above the local reference ellipsoid).

#### EXAMPLE 24: Coordinate position provided using [JSON-LD] and [SCHEMA-ORG]

<pre>&lt;script type="application/ld+json">
{
  "@context" : {
    "@vocab" : "http://schema.org/"
  },
  "myPointOfInterest" : {
    "@type" : "Place",
    "geo" : {
      "@type": "GeoCoordinates",
      "latitude": "52.37514",
      "longitude": "4.88412"
    }
  }
}
</script></pre>
>In the example above, the labels latitude and longitude are defined in [SCHEMA-ORG], as indicated by the [JSON-LD] key @vocab. The >associated definitions in [SCHEMA-ORG] are:
>
>latitude: The latitude of a location. For example 37.42242 (WGS 84).
>longitude: The longitude of a location. For example -122.08585 (WGS 84).

#### EXAMPLE 25: Coordinate position provided using column in tabular data

<pre>
GID,On Street,Long,Lat,Species,Trim Cycle,Diameter at Breast Ht,Inventory Date,Comments,Protected
1,ADDISON AV,-122.15649,37.44096,Celtis australis,Large Tree Routine Prune,11,10/18/2010,,
2,EMERSON ST,-122.15675,37.44096,Liquidambar styraciflua,Large Tree Routine Prune,11,6/2/2010,,
6,ADDISON AV,-122.15630,37.44115,Robinia pseudoacacia,Large Tree Routine Prune,29,6/1/2010,cavity or decay; trunk decay; codominant leaders; included bark; large leader or limb decay; previous failure root damage; root decay;  beware of BEES,YES
</pre>
>
>In this example (adapted from the City of Palo Alto tree operations database and published as tabular data and as an interactive map) the coordinate position of each tree is specified using separate columns (Long and Lat).

#### EXAMPLE 26: Abridged tabular metadata providing column meanings

<pre>
{
  "@context": ["http://www.w3.org/ns/csvw", {"@language": "en"}],
  "@id": "http://example.org/tree-ops-db",
  "url": "tree-ops-db.csv",
  "dcterms:title": "Tree Operations",
  ...
  "tableSchema": {
    "columns": [{
      "name": "GID",
      "titles": [
        "GID",
        "Generic Identifier"
      ],
      "dcterms:description": "An identifier for the operation on a tree.",
      "datatype": "string",
      "required": true, 
      "suppressOutput": true
    }, {
      "name": "on_street",
      "titles": "On Street",
      "dcterms:description": "The street that the tree is on.",
      "datatype": "string"
    }, {
      "name": "Long",
      "titles": "Longitude",
      "dcterms:description": "The WGS 84 longitude of the tree (decimal degrees).",
      "propertyUrl": "http://www.w3.org/2003/01/geo/wgs84_pos#long"
      "datatype": {
        "base": "number",
        "minimum": "-180",
        "maximum": "180"
      }
    }, {
      "name": "Lat",
      "titles": "Latitude",
      "propertyUrl": "http://www.w3.org/2003/01/geo/wgs84_pos#lat"
      "dcterms:description": "The WGS 84 latitude of the tree (decimal degrees).",
      "datatype": {
        "base": "number",
        "minimum": "-90",
        "maximum": "90"
      }
    },
    ...
    "primaryKey": "GID",
    "aboutUrl": "http://example.org/tree-ops-ext#gid-{GID}"
  }
}</pre>

#### EXAMPLE 27: Coordinates encoded using GeoJSON [RFC7946] in HTTP response

<pre>
HTTP/1.1 200 OK
Date: Sun, 05 Mar 2017 17:12:35 GMT
Content-length: 543
Connection: close
Content-type: application/geo+json

{
  "type": "Feature",
  "geometry": {
    "type": "Polygon",
    "coordinates": [
      [ [4.884235, 52.375108], [4.884276, 52.375153], 
        [4.884257, 52.375159], [4.883981, 52.375254], 
        [4.883850, 52.375109], [4.883819, 52.375075], 
        [4.884104, 52.374979], [4.884143, 52.374965], 
        [4.884207, 52.375035], [4.884263, 52.375016], 
        [4.884320, 52.374996], [4.884255, 52.374926], 
        [4.884329, 52.374901], [4.884451, 52.375034], 
        [4.884235, 52.375108] ]
      ]
  },
  "properties": {
    "name": "Anne Frank's House"
  }
}
</pre>

### Other Examples

- TBD

## Best Practice 9: Describe relative positioning

### Examples from Best Practices

- TBD

### Other Examples

- TBD

## Best Practice 10: Use appropriate relation types to link Spatial Things

### Examples from Best Practices

- TBD

### Other Examples

- TBD

## Best Practice 11: Provide information on the changing nature of spatial things

### Examples from Best Practices

- TBD

### Other Examples

- TBD

## Best Practice 12: Expose spatial data through 'convenience APIs'

### Example from Best Practices

- TBD

### Other Examples

- TBD

## Best Practice 13: Include spatial metadata in dataset metadata

### Examples from Best Practices

- TBD

### Other Examples

- TBD

## Best Practice 14: Describe the positional accuracy of spatial data

### Examples from Best Practices

- TBD

### Other Examples

- TBD