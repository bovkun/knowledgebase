LUXRE XML Feed Development Guidelines
=====================================

__Version 1.0: Last Updated 1/10/14__


PREFACE
-------

This document defines the XML syntax required by LuxuryRealEstate.com for automatic submission of listings.

__Intended Audience__

This guide assumes that its readers:

+ Are experienced web or application developers 
+ Are familiar with XML
+ Have a background in the Real Estate industry

__Organization of this document__

This document is organized as follows:

+ Chapter 1 – Feed Development Guidelines Overview of the key aspects to consider before submitting your feed to LuxuryRealEstate.com.
+ Chapter 2 – Element Dictionary XML elements that are included within LuxuryRealEstate.com's data cycle.
+ Chapter 3 – Sample XML Feed Specification How a complete XML Listing Feed should look.
   
CHAPTER 1: Feed development guidelines
--------------------------------------

__Basic Guidelines__

+ To ensure rich, quality data, please fill out as many fields as possible for all listings. We calculate a completeness score for each listing, and the more complete the listing is, the better the chance it gets good visibility on LuxuryRealEstate.com and LuxuryRealEstate.com's social media channels. 
+ Element names are case sensitive. `<LivingArea>` will work, but `<livingarea>` will not.
+ Do not include quotations around values (for example `<ListingTitle>”Amazing city view”</ListingTitle>`) 
+ Include open and close tags for all nodes, and use proper indentation for parent/child tags. 
+ Do not include HTML tags and do not include line breaks in the fields. 

__Real Estate Standards Organization Syndication Format__

Syndication of listings to a wide variety of listing portals, such as Google, Yahoo!, Trulia, Three Wide, Point2, Zillow, and many others, is a priority for listing agents and brokers. To address this, the National Association of Realtors, the Real Estate Standards Organization (RESO) and a committee of diverse I.T. professionals, publishers and data processors has formed a syndication workgroup that have developed a standardized listing data and transport specification (RETS Syndication Format) that makes it easy for brokers to syndicate their listings to multiple sites.

The format that LuxuryRealEstate.com accepts adheres to the RETS Syndication Format (not to be confused with RETS data feeds or servers) however it is a strict subset of the RETS standard. This means that if you implement the full RESO standard, it is valid to submit to LuxuryRealEstate.com, however only the elements defined in this document will be imported.

For more information on the RETS Syndication standard please visit the syndication workgroup website.

[http://www.reso.org/schemas-for-syndication](http://www.reso.org/schemas-for-syndication)

__Creating and Submitting an XML file__

Extensible Markup Language (XML) is a markup language that defines a set of rules for encoding and structuring data in a format that is both human-readable and machine-readable. The data format described in this document is an XML structured data format.

LuxuryRealEstate.com has the ability to process XML files that are stored on either a web server or an FTP server. After you have configured your system to generate an XML file, email the url link to websupport@luxre.com and we'll validate the file and set up the import to your LuxuryRealEstate.com account if validation passes. 

__Handling Illegal XML Characters__

When an XML element is parsed, all of the text within the XML tags is also parsed. This is done because it is possible, and highly likely, that the text will contain other XML elements. Because of this, there are certain characters that are deemed illegal since they will be misinterpreted by the XML parser. Entity Reference and CDATA Sections are two methods to avoid causing the XML parser to break.

<table width="100%">
  <tr>
    <th colspan="3">ENTITY REFERENCE<br />Replace the characters with their corresponding entity reference</th>
  </tr>
  <tr>
    <th>Illegal Character</th>
    <th>Entity Reference</th>
    <th>Description</th>
  </tr>
    <tr>
        <td>&lt;</td>
        <td>&amp;lt;</td>
        <td>Less Than</td>
    </tr>
    <tr>
        <td>&gt;</td>
        <td>&amp;gt;</td>
        <td>Greater Than</td>
    </tr>
    <tr>
        <td>&amp;</td>
        <td>&amp;amp;</td>
        <td>Ampersand</td>
    </tr>
    <tr>
        <td>&apos;</td>
        <td>&amp;apos;</td>
        <td>Apostrophe</td>
    </tr>
</table>

<table width="100%">
  <tr><th>CDATA SECTION<br />Enclose values in a CDATA section that starts with “&lt;![CDATA[“ and ends with “]]&gt;”</th></tr>
  <tr><td>
    <p>
      <strong>Without CDATA</strong><br />&lt;Example&gt;Brokers &amp;amp; Agents&lt;/Example&gt;
    </p>
    <p>
      <strong>With CDATA</strong><br />&lt;Example&gt;&lt;![CDATA[Brokers &amp;amp; Agents]]&gt;&lt;/Example&gt;
    </p>
  </td></tr>
</table>

CHAPTER 2: Element dictionary
-----------------------------

###&lt;Listings&gt;

Included exactly once following the XML declaration.

    <Listings xmlns="http://rets.org/xsd/Syndication/2012-03" xmlns:commons="http://rets.org/xsd/RETSCommons" xmlns:schemaLocation="http://rets.org/xsd/Syndication/2012-03/Syndication.xsd" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" listingsKey="2012-03-06T22:14:47" version="0.96" versionTimestamp="2012-02-07T03:00:00Z" xml:lang="en-us">
      <Listing>
        See documentation for Listing element.
      </Listing>
    </Listings>

###&lt;Listing&gt;

Contained once or many times by &lt;Listings&gt;, each time representing a Listing.

    <Listing>
      <Address>
        See documentation for Address element.
      </Address>
      <ListPrice commons:isgSecurityClass="Public" commons:currencyCode="USD" commons:currencyPeriod="Week">599000</ListPrice>
      <ListingURL>http://www.realestatesite.com/listings/123123</ListingURL>
      <ProviderName>Springfield Real Estate, Inc.</ProviderName>
      <ProviderURL>http://www.realestatesite.com</ProviderURL>
      <ProviderCategory>Broker</ProviderCategory>
      <LeadRoutingEmail>listingagent@realestatesite.com</LeadRoutingEmail>
      <Bedrooms>3</Bedrooms>
      <Bathrooms>2</Bathrooms>
      <PropertyType otherDescription="Residential">Residential</PropertyType>
      <PropertySubType otherDescription="Single Family Residence">Single Family Detached</PropertySubType>
      <MlsNumber>123456789</MlsNumber>
      <ListingKey>OURPREFIX-123456789</ListingKey>
      <ListingCategory>Purchase</ListingCategory>
      <ListingStatus>Active</ListingStatus>
      <MarketingInformation>
        See documentation for MarketingInformation element.
      </MarketingInformation>
      <Photos>
        See documentation for Photos element.
      </Photos>
      <ListingDescription>Gorgeous house. Must see. Tell all of your friends and relations in the market.</ListingDescription>
      <LivingArea commons:areaUnits="squareFoot">1260</LivingArea>
      <LotSize commons:areaUnits="acre">0.135</LotSize>
      <YearBuilt>1954</YearBuilt>
      <ListingDate>1989-12-17</ListingDate>
      <ListingTitle>Very Lovely Home</ListingTitle>
      <FullBathrooms>1</FullBathrooms>
      <HalfBathrooms>1</HalfBathrooms>
      <OneQuarterBathrooms>0</OneQuarterBathrooms>
      <PartialBathrooms>1</PartialBathrooms>
      <ListingParticipants>
        See documentation for ListingParticipants element.
      </ListingParticipants>
      <VirtualTours>
        See documentation for VirtualTours element.
      </VirtualTours>
      <Offices>
        See documentation for Offices element.
      </Offices>
      <Brokerage>
        See documentation for Brokerage element.
      </Brokerage>
      <Location>
        See documentation for Location element.
      </Location>
      <DetailedCharacteristics>
        See documentation for DetailedCharacteristics element.
      </DetailedCharacteristics>
      <ModificationTimestamp commons:isgSecurityClass="Public">2013-12-12T06:07:05+00:00</ModificationTimestamp>
      <Disclaimer commons:isgSecurityClass="Public">Copyright 2013 Springfield Real Estate, Inc. All rights reserved. All information provided by the listing agent/broker is deemed reliable but is not guaranteed and should be independently verified.</Disclaimer>
    </Listing>

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>ListPrice</td>
    <td>Integer</td>
    <td><p>Unformatted numerical list price for the property.</p><p>commons:currencyCode is used to state the currency used. Currency is a three letter currency code as defined by <a href="http://en.wikipedia.org/wiki/ISO_4217" target="_blank">ISO 4217</a>.</p><p>The currencyPeriod attribute is only expected for rental properites and contains either the value "Daily", "Weekly" or "Monthly" to indicate that a rental price is repeated at the frequency indicated. The abscence of the attribute indicates a one-time payment and the attribute is not expected for listings for sale.</p><p>If a rental currencyPeriod is set to "Monthly", it is considered a residential long term rental. If the listing is a rental and currencyPeriod is set to either "Daily" or "Weekly", it is considered a Vacation Rental.</p></td>
  </tr>
  <tr>
    <td>ListingURL</td>
    <td>String</td>
    <td>The URL for the original listing.</td>
  </tr>
  <tr>
    <td>ProviderName</td>
    <td>String</td>
    <td>The name of the entity that authorized the listing to be syndicated.</td>
  </tr>
  <tr>
    <td>ProviderURL</td>
    <td>String</td>
    <td>A URL for the entity that authorized the listing to be syndicated.</td>
  </tr>
  <tr>
    <td>ProviderCategory</td>
    <td>String</td>
    <td>The type of the entity that authorized the listing to be syndicated. Must contain one of these values:
      <ul>
        <li>Aggregator</li>
        <li>Broker</li>
        <li>Franchiser</li>	
        <li>HomeBuilder</li>
        <li>MLS</li>
        <li>Other</li>
        <li>Owner</li>
        <li>Publisher</li>
        <li>Unknown</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>LeadRoutingEmail</td>
    <td>String</td>
    <td>An email address leads will be sent to, in addition to the email addresses of any agent profiles that might be associated with the listing. See documentation for ListingParticipant for further instructions on listing agent inclusion and matching to agent profiles on LuxuryRealEstate.com.</td>
  </tr>
  <tr>
    <td>Bedrooms</td>
    <td>Integer</td>
    <td>The total number of bedrooms. For listings with no home on the property, such as a lot or land, this element should have the value of 0. When no information is available on Bathrooms, the value should be empty.</td>
  </tr>
  <tr>
    <td>Bathrooms</td>
    <td>Integer</td>
    <td>The total number of bathrooms. For listings with no home on the property, such as a lot or land, this element should have the value of 0. When no information is available on Bathrooms, the value should be empty.</td>
  </tr>
  <tr>
    <td>PropertyType</td>
    <td>String</td>
    <td>Primary type of the listed property. Must have one of these values:
      <ul>
        <li>Commercial</li>
        <li>Common Interest</li>	
        <li>Farm And Agriculture</li>	
        <li>Lots And Land</li>
        <li>MultiFamily</li>
        <li>Other</li>
        <li>Rental</li>
        <li>Residential</li>        
      </ul>
    </td>
  </tr>
  <tr>
    <td>PropertySubType</td>
    <td>String</td>
    <td>Secondary type of the listed property. Must have one of these values:
      <ul>
        <li>Apartment</li>
        <li>Boatslip</li>
        <li>Cabin</li>
        <li>Condominium</li>	
        <li>Deeded Parking</li>
        <li>Duplex</li>
        <li>Farm</li>
        <li>Manufactured Home</li>	
        <li>Mobile Home</li>
        <li>Other</li>
        <li>Own Your Own</li>	
        <li>Quadruplex</li>
        <li>Single Family Attached</li>
        <li>Single Family Detached</li>
        <li>Stock Cooperative</li>
        <li>Timeshare</li>
        <li>Townhouse</li>
        <li>Triplex</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>MlsNumber</td>
    <td>String</td>
    <td>In the US and Canada, it is the listing MLS number. In any other country or in markets witout an MLS, it is a unique listing identifier within the scope of the originating data source.</td>
  </tr>
  <tr>
    <td>ListingKey</td>
    <td>String</td>
    <td>Compound value made up from your unique LUXRE account token, a dash, and the value from MlsNumber. Inquire with websupport@luxre.com if you don't know what your unique LUXRE token is.</td>
  </tr>
  <tr>
    <td>ListingCategory</td>
    <td>String</td>
    <td>One of "Purchase", "Lease" and "Rent".</td>
  </tr>
  <tr>
    <td>ListingStatus</td>
    <td>String</td>
    <td>Must be one of:
      <ul>
        <li>Active</li>
        <li>Cancelled</li>
        <li>Closed</li>
        <li>Expired</li>
        <li>Pending</li>
        <li>Withdrawn</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>ListingDescription</td>
    <td>String</td>
    <td>Description of the listing.</td>
  </tr>
  <tr>
    <td>LivingArea</td>
    <td>Integer</td>
    <td>Unformatted number with total livable area of the listed property. Attribute areaUnit must be one of following values:
      <ul>
        <li>acre</li>
        <li>hectare</li>
        <li>squareCentimeter</li>
        <li>squareFoot</li>
        <li>squareMeter</li>
        <li>squareYard</li>
        <li>unknown</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>LotSize</td>
    <td>Integer</td>
    <td>Unformatted number with size of the lot of the listed property. Attribute areaUnit must be one of following values:
      <ul>
        <li>acre</li>
        <li>hectare</li>
        <li>squareCentimeter</li>
        <li>squareFoot</li>
        <li>squareMeter</li>
        <li>squareYard</li>
        <li>unknown</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>YearBuilt</td>
    <td>Integer</td>
    <td>Year the property was constructed.</td>
  </tr>
  <tr>
    <td>ListingDate</td>
    <td>Date</td>
    <td>Date the property was listed, formatted YYYY-MM-DD as specified in <a href="http://en.wikipedia.org/wiki/ISO_8601#Calendar_dates">ISO 8601</a>.</td>
  </tr>
  <tr>
    <td>ListingTitle</td>
    <td>String</td>
    <td>A short title for the listing.</td>
  </tr>
  <tr>
    <td>FullBathrooms</td>
    <td>Integer</td>
    <td>A total count for the full bathrooms on the property. Full bath generally includes sink, toilet, shower and bath, but may have other local definitions.</td>
  </tr>
  <tr>
    <td>HalfBathrooms</td>
    <td>Integer</td>
    <td>A total count of the half bathrooms on the property. Half bathrooms contain a sink and toilet.</td>
  </tr>
  <tr>
    <td>OneQuarterBathrooms</td>
    <td>Integer</td>
    <td>A total count of the one-quarter bathrooms on the property. One-quarter bathrooms contain a sink.</td>
  </tr>
  <tr>
    <td>PartialBathrooms</td>
    <td>Integer</td>
    <td>A total count for all the partial bathrooms on the property. This includes one quarter, one half, and three quarter baths.</td>
  </tr>
  <tr>
    <td>ModificationTimestamp</td>
    <td>Timestamp</td>
    <td>That most recent timestamp that information about this listing changed within the originating data source. This is used to determine if the information for a listing already present on LuxuryRealEstate.com needs updating.</td>
  </tr>
  <tr>
    <td>Disclaimer</td>
    <td>String</td>
    <td>Custom disclaimer.</td>
  </tr>
</table>


###&lt;DetailedCharacteristics&gt;

Contained exactly once by &lt;Listing&gt;.

    <DetailedCharacteristics>
      <Appliances>
        See documentation for Appliances element.
      </Appliances>
      <HasAttic>true</HasAttic>
      <HasBarbecueArea>true</HasBarbecueArea>
      <HasDeck>true</HasDeck>
      <HasDock>true</HasDock>
      <HasPatio>true</HasPatio>
      <HasSkylight>true</HasSkylight>
      <HasFireplace>true</HasFireplace>
      <HasHotTubSpa>true</HasHotTubSpa>
      <HasJettedBathTub>true</HasJettedBathTub>
      <HasPond>true</HasPond>
      <HasPool>true</HasPool>
      <HasSauna>true</HasSauna>
      <HasSportsCourt>true</HasSportsCourt>
      <HasWetBar>true</HasWetBar>
      <IsWaterfront>true</IsWaterfront>
      <ViewTypes>
        See documentation for ViewTypes
      </ViewTypes>
    </DetailedCharacteristics>

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>HasAttic</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has an attic.</td>
  </tr>
  <tr>
    <td>HasBarbecueArea</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has a barbecue area.</td>
  </tr>
  <tr>
    <td>HasDeck</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has one or more decks.</td>
  </tr>
  <tr>
    <td>HasDock</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has one or more docks.</td>
  </tr>
  <tr>
    <td>HasPatio</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has one or more patios.</td>
  </tr>
  <tr>
    <td>HasSkylight</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has  one or more skylights.</td>
  </tr>
  <tr>
    <td>HasFireplace</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has one or more fireplaces.</td>
  </tr>
  <tr>
    <td>HasHotTubSpa</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has one or more hot tubs or spas.</td>
  </tr>
  <tr>
    <td>HasJettedBathTub</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has one or more jetted bath tubs.</td>
  </tr>
  <tr>
    <td>HasPond</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has one or more ponds.</td>
  </tr>
  <tr>
    <td>HasPool</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has one or more pools.</td>
  </tr>
  <tr>
    <td>HasSauna</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has one or more saunas.</td>
  </tr>
  <tr>
    <td>HasSportsCourt</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has one or more sports courts.</td>
  </tr>
  <tr>
    <td>HasWetBar</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property has one or more wet bars.</td>
  </tr>
  <tr>
    <td>IsWaterfront</td>
    <td>Boolean</td>
    <td><code>true</code> or <code>false</code> to state if the property is on the waterfronts.</td>
  </tr>
</table>


###&lt;Appliances&gt;

Contained exactly once by &lt;DetailedCharacteristics&gt;.

    <Appliances>
      <Appliance>Coffee System</Appliance>
      <Appliance>Refrigerator</Appliance>
      <Appliance>Dishwasher</Appliance>
      <Appliance>Freezer</Appliance>
      <Appliance>Vacuum System</Appliance>
    </Appliances>

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td valign="top">Appliance</td>
    <td valign="top">String</td>
    <td valign="top">
      The Appliance element repeats and must contain one of following values:

      <ul>
        <li>Barbeque or Grill</li>
        <li>Coffee System</li>
        <li>Cooktop</li>
        <li>Dishwasher</li>
        <li>Dryer</li>
        <li>Freezer</li>
        <li>Garbage Disposer</li>
        <li>Ice Maker</li>
        <li>Microwave</li>
        <li>Oven</li>
        <li>Range</li>
        <li>Rangetop - Electric</li>
        <li>Refrigerator</li>
        <li>Trash Compactor</li>
        <li>Vacuum System</li>
        <li>Vent Hood</li>
        <li>Warming Drawer</li>
        <li>Washer</li>
        <li>Washer/Dryer Combo</li>
        <li>Water - Filter</li>
        <li>Water - Instant Hot</li>
        <li>Water - Softener</li>
      </ul>

    </td>
  </tr>
</table>

###&lt;Address&gt;

Contained exactly once by &lt;Listing&gt;, &lt;Brokerage&gt; and &lt;Office&gt;.

    <Address>
      <commons:preference-order>1</commons:preference-order>
      <commons:address-preference-order>1</commons:address-preference-order>
      <commons:FullStreetAddress>742 Evergreen Terrace</commons:FullStreetAddress>
      <commons:City>Springfield</commons:City>
      <commons:StateOrProvince>CA</commons:StateOrProvince>
      <commons:PostalCode>91401</commons:PostalCode>
      <commons:Country>US</commons:Country>
    </Address>

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>commons:preference-order</td>
    <td>Integer</td>
    <td>Value always 1.</td>
  </tr>
  <tr>
    <td>commons:address-preference-order</td>
    <td>Integer</td>
    <td>Value always 1.</td>
  </tr>
  <tr>
    <td>commons:FullStreetAddress</td>
    <td>String</td>
    <td>FullStreetAddress is a text representation of the address.</td>
  </tr>
  <tr>
    <td>commons:City</td>
    <td>String</td>
    <td>The city, township, municipality, etc. portion of an address.</td>
  </tr>
  <tr>
    <td>commons:StateOrProvince</td>
    <td>String</td>
    <td>For USA and Canada, the two letter state/province code. For other countries, the two letter subdivision code as defined by <a href="http://en.wikipedia.org/wiki/ISO_3166-2" target="_blank">ISO 3166-2</a>.</td>
  </tr>
  <tr>
    <td>commons:PostalCode</td>
    <td>String</td>
    <td>For USA, the five digit zip code. For other countries, a string representing the postal code for the address.</td>
  </tr>
  <tr>
    <td>commons:Country</td>
    <td>Integer</td>
    <td>Two digit country code as specified by <a href="http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2">ISO-3166-1 Alpha-2</td>.
  </tr>
</table>

###&lt;MarketingInformation&gt;

Contained exactly once by &lt;Listing&gt;.

    <MarketingInformation>
      <commons:VOWAddressDisplay commons:isgSecurityClass="Public">true</commons:VOWAddressDisplay>
      <commons:VOWAutomatedValuationDisplay commons:isgSecurityClass="Public">true</commons:VOWAutomatedValuationDisplay>
      <commons:VOWConsumerComment commons:isgSecurityClass="Public">true</commons:VOWConsumerComment>
    </MarketingInformation>

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>commons:VOWAddressDisplay</td>
    <td>String</td>
    <td>The string <code>true</code> or <code>false</code> to state whether it is allowed to show the address of the listing.</td>
  </tr>
  <tr>
    <td>commons:VOWAutomatedValuationDisplay</td>
    <td>String</td>
    <td>The string <code>true</code> or <code>false</code> to state whether it is allowed to show automatic valuation of the listing. Set this to <code>true</code> to enable display of mortgage calculator, and <code>false</code> to disable display of mortgage calculator.</td>
  </tr>
  <tr>
    <td>commons:VOWConsumerComment</td>
    <td>String</td>
    <td>The string <code>true</code> or <code>false</code> to state whether it is allowed for visitors to comment on the listing.</td>
  </tr>
</table>

###&lt;Photos&gt;

Contained exactly once by &lt;Listing&gt;.

    <Photos>
      <Photo>
        See documentation for Photo element.
      </Photo>
    </Photos>

###&lt;Photo&gt;

Contained one or many times by &lt;Photos&gt;.

    <Photo>
      <MediaModificationTimestamp commons:isgSecurityClass="Public">2013-08-27T09:06:50+00:00</MediaModificationTimestamp>
      <MediaURL>http://upload.wikimedia.org/wikipedia/en/c/ca/742_Evergreen_Terrace.png</MediaURL>
      <MediaCaption>Wine cellar fits 1,500 bottles.</MediaCaption>
      <MediaDescription>Wine Cellar</MediaCaption>
    </Photo>

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>MediaModificationTimestamp</td>
    <td>Timestamp</td>
    <td>Timestamp for when the photo was last updated. Update this value to force reimport of a new photo that has the same filename as the photo it replaces.</td>
  </tr>
  <tr>
    <td>MediaURL</td>
    <td>String</td>
    <td>The publicly accessible URL for the photo.</td>
  </tr>
  <tr>
    <td>MediaCaption</td>
    <td>String</td>
    <td>Short description of what is pictured.</td>
  </tr>
  <tr>
    <td>MediaDescription</td>
    <td>String</td>
    <td>LuxuryRealEstate.com uses MediaDescription to categorize what is pictured. It is optional, but if included must be one of these values:
      <ul>
        <li>Basement</li>
        <li>Bathroom</li>
        <li>Bedroom</li>
        <li>Closet</li>
        <li>Deck</li>
        <li>Dining Room</li>
        <li>Entry</li>
        <li>Exterior</li>
        <li>Family Room</li>
        <li>Floor Plan</li>
        <li>Garage</li>
        <li>Hall</li>
        <li>Home Gym</li>
        <li>Home Office</li>
        <li>Kids</li>
        <li>Kitchen</li>
        <li>Landscape</li>
        <li>Laundry Room</li>
        <li>Living Room</li>
        <li>Media Room</li>
        <li>Patio</li>
        <li>Pool</li>
        <li>Porch</li>
        <li>Powder Room</li>
        <li>Shed</li>
        <li>Staircase</li>
        <li>Wine Cellar</li>
      </ul>
    </td>
  </tr>
</table>

###&lt;VirtualTours&gt;

Contained exactly once by &lt;Listing&gt;.

    <VirtualTours>
      <VirtualTour>
        See documentation for VirtualTour element.
      </VirtualTour>
    </VirtualTours>

###&lt;VirtualTour&gt;

Contained one or many times by &lt;VirtualTours&gt;.

    <VirtualTour>
      <MediaModificationTimestamp commons:isgSecurityClass="Public">2013-08-27T09:06:50+00:00</MediaModificationTimestamp>
      <MediaURL>http://upload.wikimedia.org/wikipedia/en/c/ca/742_Evergreen_Terrace.png</MediaURL>
    </VirtualTour>

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>MediaModificationTimestamp</td>
    <td>Timestamp</td>
    <td>Timestamp for when the virtual tour was last updated. Update this value to force update of a new virtual that has the same URL as the virtual tour it replaces.</td>
  </tr>
  <tr>
    <td>MediaURL</td>
    <td>String</td>
    <td>The URL for the virtual tour.</td>
  </tr>
</table>

###&lt;ListingParticipants&gt;

Contained exactly once by &lt;Listing&gt;.

    <ListingParticipants>
      <Participant>
        See documentation for Participant element.
      </Participant>
    </ListingParticipants>

###&lt;Participant&gt;

Contained once or twice by &lt;ListingParticipants&gt;.

    <Participant>
      <ParticipantKey>OURPREFIX-AG123123</ParticipantKey>
      <ParticipantId>AG123123</ParticipantId>
      <FirstName>Gil</FirstName>
      <LastName>Gunderson</LastName>
      <Role>Listing</Role>
      <PrimaryContactPhone>5557891234</PrimaryContactPhone>
      <OfficePhone>5559875432</OfficePhone>
      <Email>gilgunderson@realestatesite.com.com</Email>
      <WebsiteURL>http://myownagentsite.com</WebsiteURL>
    </Participant>

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>ParticipantKey</td>
    <td>String</td>
    <td>Compound value made up from your unique LUXRE account token, a dash, and the value from ParticipantId. Inquire with websupport@luxre.com if you don't know what your unique LUXRE token is.</td>
  </tr>
  <tr>
    <td>ParticipantId</td>
    <td>String</td>
    <td>A value that uniquely identifies the listing agent within your LUXRE account. For US based listing agents, this is the agent's agent MLS ID. For other countries, it can be any unqiue string as long as it is consistenly used for the particular agent, and as long as it's used only for the particular agent. This value must also be assigned to the corresponding agent's LUXRE profile in the Luxury Lounge in order for the listing to get correctly associated with the agent profile on LuxuryRealEstate.com.</td>
  </tr>
  <tr>
    <td>FirstName</td>
    <td>String</td>
    <td>The listing agent's first name.</td>
  </tr>
  <tr>
    <td>LastName</td>
    <td>String</td>
    <td>The listing agent's last name.</td>
  </tr>
  <tr>
    <td>Role</td>
    <td>String</td>
    <td>Always contains the value <code>Listing</code> to signify listing agent.</td>
  </tr>
  <tr>
    <td>PrimaryContactPhone</td>
    <td>String</td>
    <td>Primary phone number for the participant, no format enforced.</td>
  </tr>
  <tr>
    <td>OfficePhone</td>
    <td>String</td>
    <td>The listing agent's office phone number, no format enforced.</td>
  </tr>
  <tr>
    <td>Email</td>
    <td>String</td>
    <td>Email address of the listing agent, no format enforced.</td>
  </tr>
  <tr>
    <td>WebsiteURL</td>
    <td>String</td>
    <td>URL for agent's website, no format enforced.</td>
  </tr>
</table>

###&lt;Offices&gt;

Contained exactly once by &lt;Listing&gt;.

    <Offices>
       <Office>
         See documentation for Office element.
       </Office>
     </Offices>

###&lt;Office&gt;

Contained exactly once by &lt;Offices&gt;.

     <Office>
       <OfficeKey>OURPREFIX-OF123123</OfficeKey>
       <OfficeId>OF123123</OfficeId>
       <Name>Springfield Real Estate, Inc.</Name>
       <CorporateName>Springfield Real Estate, Inc.</CorporateName>
       <BrokerId>BRID123123</BrokerId>
       <PhoneNumber>555-789-1234</PhoneNumber>
       <Fax>555-987-4321</Fax>
       <Address>
         See documentation for Address element.
       </Address>
       <OfficeEmail>info@realestatesite.com</OfficeEmail>
       <Website>http://www.realestatesite.com</Website>
    </Office>

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>OfficeKey</td>
    <td>String</td>
    <td>Compound value made up from your unique LUXRE account token, a dash, and the value from OfficeId. Inquire with websupport@luxre.com if you don't know what your unique LUXRE token is.</td>
  </tr>
  <tr>
    <td>OfficeId</td>
    <td>String</td>
    <td>A value that uniquely identifies the office within your LUXRE account. For US based companies, this is the office MLS ID. For other countries, it can be any unqiue string as long as it is consistenly used for the particular office, and as long as it's used only for the particular office. This value must also be assigned to the corresponding office's LUXRE profile in the Luxury Lounge in order for the listing to get correctly associated with the office profile on LuxuryRealEstate.com.</td>
  </tr>
  <tr>
    <td>Name</td>
    <td>String</td>
    <td>The name of the office.</td>
  </tr>
  <tr>
    <td>BrokerId</td>
    <td>String</td>
    <td>Identifier for the person who is the designated broker of the office. For US based offices, this is the broker's MLS ID. For other countries, it can be any unqiue string as long as it is consistenly used for the particular managing agent, and as long as it's used only for the particular person.</td>
  </tr>
  <tr>
    <td>PhoneNumber</td>
    <td>String</td>
    <td>Phone number of the office, no format enforced.</td>
  </tr>
  <tr>
    <td>Fax</td>
    <td>String</td>
    <td>Fax number of the office, no format enforced.</td>
  </tr>
  <tr>
    <td>OfficeEmail</td>
    <td>String</td>
    <td>Email address of the office, no format enforced.</td>
  </tr>
  <tr>
    <td>Website</td>
    <td>String</td>
    <td>Public website for the office.</td>
  </tr>
</table>

###&lt;Brokerage&gt;

Contained exactly once by &lt;Listing&gt;.

    <Brokerage>
      <Name>Springfield Real Estate, Inc.</Name>
      <Phone>555-789-1234</Phone>
      <Email>info@realestatesite.com</Email>
      <WebsiteURL>http://www.realestatesite.com</WebsiteURL>
      <LogoURL>http://www.realestatesite.com/images/logo.jpg</LogoURL>
    </Brokerage>

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Name</td>
    <td>String</td>
    <td>Name of the business that is a member of LuxuryRealEstate.com.</td>
  </tr>
  <tr>
    <td>Phone</td>
    <td>String</td>
    <td>Phone number as a string, no specific format enforced.</td>
  </tr>
  <tr>
    <td>Email</td>
    <td>String</td>
    <td>Email address as a string no specific format enforced.</td>
  </tr>
  <tr>
    <td>WebsiteURL</td>
    <td>String</td>
    <td>URL for the company website.</td>
  </tr>
  <tr>
    <td>LogoURL</td>
    <td>String</td>
    <td>Publicly accessible URL for the business logo.</td>
  </tr>
</table>

###&lt;Location&gt;

Contained exactly once by &lt;Listing&gt;.

    <Location>
      <County>Springfield</County>
      <Latitude>47.62001290</Latitude>
      <Longitude>-122.3491637</Longitude>
      <Neighborhoods>
        <Neighborhood>
          See documentation for Neighborhood element.
        </Neighborhood>
      </Neighborhoods>
    </Location>

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>County</td>
    <td>String</td>
    <td>The county that the property is located in.</td>
  </tr>
  <tr>
    <td>Latitude</td>
    <td>String</td>
    <td>Latitude of the property.</td>
  </tr>
  <tr>
    <td>Longitude</td>
    <td>String</td>
    <td>Longitude of the property.</td>
  </tr>
  <tr>
    <td>Neighborhoods</td>
    <td>String</td>
    <td>Container for a Neighborhood element. Maximum 1 is allowed.</td>
  </tr>
</table>

###&lt;Neighborhood&gt;

Contained exactly once by &lt;Listing&gt;.

    <Neighborhood>
      <Name>Evergreen Terrace</Name>
    </Neighborhood>

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Name</td>
    <td>String</td>
    <td>Name of the neighborhood the listings is in. This value can contain the name of an island, burrough or similar where the listing is located in a geographical area that doesn't fit to include elsewhere.</td>
  </tr>
</table>


###&lt;ViewTypes&gt;

Contained exactly once by &lt;DetailedCharacteristics&gt;.

    <ViewTypes>
      <ViewType>Water</ViewType>
      <ViewType>Ocean</ViewType>
      <ViewType>Golf Course</ViewType>
    </ViewTypes>

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td valign="top">ViewType</td>
    <td valign="top">String</td>
    <td valign="top">
      The ViewType element repeats and must contain one of following values:

      <ul>
        <li>Airport</li>
        <li>Average</li>
        <li>Bluff</li>
        <li>Bridge</li>
        <li>Canyon</li>
        <li>City</li>
        <li>Desert</li>
        <li>Forest</li>
        <li>Golf Course</li>	
        <li>Harbor</li>
        <li>Hills</li>
        <li>Lake</li>
        <li>Marina</li>
        <li>Mountain</li>
        <li>None</li>
        <li>Ocean</li>
        <li>Other</li>
        <li>Panorama</li>
        <li>Park</li>
        <li>Ravine</li>
        <li>River</li>
        <li>Territorial</li>	
        <li>Unknown</li>
        <li>Valley</li>
        <li>Vista</li>
        <li>Water</li>
      </ul>
            
    </td>
  </tr>
</table>



CHAPTER 3 – Sample XML Feed
---------------------------

    <?xml version="1.0"?>
    <Listings xmlns="http://rets.org/xsd/Syndication/2012-03" xmlns:commons="http://rets.org/xsd/RETSCommons" xmlns:schemaLocation="http://rets.org/xsd/Syndication/2012-03/Syndication.xsd" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" listingsKey="2012-03-06T22:14:47" version="0.96" versionTimestamp="2012-02-07T03:00:00Z" xml:lang="en-us">
      <Listing>
        <Address>
          <commons:preference-order>1</commons:preference-order>
          <commons:address-preference-order>1</commons:address-preference-order>
          <commons:FullStreetAddress>742 Evergreen Terrace</commons:FullStreetAddress>
          <commons:City>Springfield</commons:City>
          <commons:StateOrProvince>CA</commons:StateOrProvince>
          <commons:PostalCode>91401</commons:PostalCode>
          <commons:Country>US</commons:Country>
        </Address>
        <ListPrice commons:isgSecurityClass="Public" commons:currencyCode="USD">599000</ListPrice>
        <ListingURL>http://www.realestatesite.com/listings/123123</ListingURL>
        <ProviderName>Springfield Real Estate, Inc.</ProviderName>
        <ProviderURL>http://www.realestatesite.com</ProviderURL>
        <ProviderCategory>Broker</ProviderCategory>
        <LeadRoutingEmail>listingagent@realestatesite.com</LeadRoutingEmail>
        <Bedrooms>3</Bedrooms>
        <Bathrooms>2</Bathrooms>
        <PropertyType otherDescription="Residential">Residential</PropertyType>
        <PropertySubType otherDescription="Single Family Residence">Single Family Detached</PropertySubType>
        <ListingKey>OURPREFIX-123456789</ListingKey>
        <ListingCategory>Purchase</ListingCategory>
        <ListingStatus>Active</ListingStatus>
        <MarketingInformation>
          <commons:VOWAddressDisplay commons:isgSecurityClass="Public">true</commons:VOWAddressDisplay>
          <commons:VOWAutomatedValuationDisplay commons:isgSecurityClass="Public">true</commons:VOWAutomatedValuationDisplay>
          <commons:VOWConsumerComment commons:isgSecurityClass="Public">true</commons:VOWConsumerComment>
        </MarketingInformation>
        <Photos>
          <Photo>
            <MediaModificationTimestamp commons:isgSecurityClass="Public">2013-08-27T09:06:50+00:00</MediaModificationTimestamp>
            <MediaURL>http://upload.wikimedia.org/wikipedia/en/c/ca/742_Evergreen_Terrace.png</MediaURL>
            <MediaCaption>Exterior showing overview.</MediaCaption>
            <MediaDescription>Exterior</MediaCaption>
          </Photo>
          <Photo>
            <MediaModificationTimestamp commons:isgSecurityClass="Public">2013-08-27T09:06:50+00:00</MediaModificationTimestamp>
            <MediaURL>http://www.blogcdn.com/www.parentdish.co.uk/media/2011/05/parentdish-best-dads-homer-simpson-rex-590mt200511.jpg</MediaURL>
            <MediaCaption>Perfect couch for watching fottball.</MediaCaption>
            <MediaDescription>Living Room</MediaCaption>
          </Photo>
          <Photo>
            <MediaModificationTimestamp commons:isgSecurityClass="Public">2013-08-27T09:06:50+00:00</MediaModificationTimestamp>
            <MediaURL>http://i.dailymail.co.uk/i/pix/2013/12/21/article-2527254-1A3BFD0A00000578-904_634x377.jpg</MediaURL>
            <MediaCaption>Ideal space for family time.</MediaCaption>
            <MediaDescription>Living Room</MediaCaption>
          </Photo>
          <Photo>
            <MediaModificationTimestamp commons:isgSecurityClass="Public">2013-08-27T09:06:50+00:00</MediaModificationTimestamp>
            <MediaURL>http://stuffpoint.com/the-simpsons/image/312601-the-simpsons-simpsons-house-interior.jpg</MediaURL>
            <MediaCaption>Overview of floor plan.</MediaCaption>
            <MediaDescription>Floor Plan</MediaCaption>
          </Photo>
        </Photos>
        <DiscloseAddress>true</DiscloseAddress>
        <ListingDescription>Gorgeous house. Must see. Tell all of your friends and relations in the market.</ListingDescription>
        <MlsNumber>123456789</MlsNumber>
        <LivingArea commons:areaUnits="squareFoot">1260</LivingArea>
        <LotSize commons:areaUnits="acre">0.135</LotSize>
        <YearBuilt>1954</YearBuilt>
        <ListingDate>1989-12-17</ListingDate>
        <ListingTitle>Very Lovely Home</ListingTitle>
        <FullBathrooms>1</FullBathrooms>
        <HalfBathrooms>1</HalfBathrooms>
        <OneQuarterBathrooms>0</OneQuarterBathrooms>
        <PartialBathrooms>1</PartialBathrooms>
        <ListingParticipants>
          <Participant>
            <ParticipantKey>OURPREFIX-AG123123</ParticipantKey>
            <ParticipantId>AG123123</ParticipantId>
            <FirstName>Gil</FirstName>
            <LastName>Gunderson</LastName>
            <Role>Listing</Role>
            <PrimaryContactPhone>5557891234</PrimaryContactPhone>
            <OfficePhone>5559875432</OfficePhone>
            <Email>gilgunderson@realestatesite.com.com</Email>
            <WebsiteURL>http://myownagentsite.com</WebsiteURL>
          </Participant>
        </ListingParticipants>
        <VirtualTours>
          <VirtualTour>
            <MediaModificationTimestamp commons:isgSecurityClass="Public"/>
            <MediaURL>http://www.youtube.com/watch?v=IL2WHdRwlJ4</MediaURL>
          </VirtualTour>
        </VirtualTours>
        <Offices>
          <Office>
            <OfficeKey>OURPREFIX-OF123123</OfficeKey>
            <OfficeId>OF123123</OfficeId>
            <Name>Springfield Real Estate, Inc.</Name>
            <BrokerId>BRID123123</BrokerId>
            <PhoneNumber>555-789-1234</PhoneNumber>
            <Fax>555-987-4321</Fax>
            <Address>
              <commons:preference-order>1</commons:preference-order>
              <commons:address-preference-order>1</commons:address-preference-order>
              <commons:FullStreetAddress>123 NW Main St</commons:FullStreetAddress>
              <commons:UnitNumber>#100</commons:UnitNumber>
              <commons:City>Springfield</commons:City>
              <commons:StateOrProvince>CA</commons:StateOrProvince>
              <commons:PostalCode>91362</commons:PostalCode>
              <commons:Country>US</commons:Country>
            </Address>
            <OfficeEmail>info@realestatesite.com</OfficeEmail>
            <Website>http://www.realestatesite.com</Website>
          </Office>
        </Offices>
        <Brokerage>
          <Name>Springfield Real Estate, Inc.</Name>
          <Phone>555-789-1234</Phone>
          <Email>info@realestatesite.com</Email>
          <WebsiteURL>http://www.realestatesite.com</WebsiteURL>
          <LogoURL>http://www.realestatesite.com/images/logo.jpg</LogoURL>
          <Address>
            <commons:preference-order>1</commons:preference-order>
            <commons:address-preference-order>1</commons:address-preference-order>
            <commons:FullStreetAddress>123 NW Main St</commons:FullStreetAddress>
            <commons:UnitNumber>Suite 12</commons:UnitNumber>
            <commons:City>Springfield</commons:City>
            <commons:StateOrProvince>CA</commons:StateOrProvince>
            <commons:PostalCode>93065</commons:PostalCode>
            <commons:Country>US</commons:Country>
          </Address>
        </Brokerage>
        <Location>
          <County>Springfield</County>
          <Latitude>47.62001290</Latitude>
          <Longitude>-122.3491637</Longitude>
          <Neighborhoods>
            <Neighborhood>
              <Name>Evergreen Terrace</Name>
            </Neighborhood>
          </Neighborhoods>
        </Location>
        <DetailedCharacteristics>
          <Appliances>
            <Appliance>Dishwasher</Appliance>
            <Appliance>Washer</Appliance>
            <Appliance>Dryer</Appliance>
            <Appliance>Oven</Appliance>
            <Appliance>Range</Appliance>
          </Appliances>
          <HasAttic>true</HasAttic>
          <HasBarbecueArea>true</HasBarbecueArea>
          <HasDeck>true</HasDeck>
          <HasDock>true</HasDock>
          <HasPatio>true</HasPatio>
          <HasSkylight>true</HasSkylight>
          <ViewTypes>
            <ViewType>Water</ViewType>
            <ViewType>Ocean</ViewType>
            <ViewType>Golf Course</ViewType>
          </ViewTypes>
        </DetailedCharacteristics>
        <ModificationTimestamp commons:isgSecurityClass="Public">2013-12-12T06:07:05+00:00</ModificationTimestamp>
        <Disclaimer commons:isgSecurityClass="Public">Copyright 2013 Springfield Real Estate, Inc. All rights reserved. All information provided by the listing agent/broker is deemed reliable but is not guaranteed and should be independently verified.</Disclaimer>
      </Listing>
    </Listings>
