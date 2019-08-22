---
layout: page
type: element
title: Metadata Identifier
---
#  Resource Default Locale ★★★★
*Most spatial resources contain some textual information written in particular languages. For users it is important that the language of the resource be shared. Default Locale provide a way to record the primary language of the metadata.*

**Path** - *MD_Metadata.identificationInfo>MD_DataIdentification.defaultLocale*
- **Governance** -  *Common ICSM*
- **Purpose -** *discovery, data management*
- **Audience -** 
  - machine resource - ⭑⭑
  - general - ⭑⭑⭑⭑⭑
  - data manager - ⭑⭑⭑
  - specialist - ⭑⭑⭑
- **Metadata type -** *descripive*
- *ICSM Level of Agreement* - ⭑⭑⭑

# Definition 
**Designation of the language used within the cited resource.**

## ISO Obligation 
- There may be only one [0..1] *defaultLocale* entries for the resource in the metadata  *[MD_DataIdentification](https://www.loomio.org/d/oqKd8GHM/class-md_dataidentification)* package. This must be of class *[PT_Locale](https://www.loomio.org/d/Y8IlUVRL/class-pt_locale)*.  

## ICSM Good Practice  
- The default language in our region is English and it is recommended to be used as the language in metadata records using the 3 letter code "eng".

### Recommended Sub-Elements   
- Follow the general guidance for *[class - PT_Locale](https://www.loomio.org/d/Y8IlUVRL/class-pt_locale)* 

### Recommended Sibling Elements   
- **otherLocale -** *[class - PT_Locale]* [0..\*] when a resource has information in additional languages
  - Follow the general guidance for [class - PT_Locale](https://www.loomio.org/d/Y8IlUVRL/class-pt_locale) 

# Discussion 
There may be only one default locale for a resource identified in a metadata record.
The element "otherLocale" can be use to provide information about alternatively used localised character strings

# Recommendations 

Therefore - In order to meet ICSM good practice, in metadata for data resources, one default language of the resource should be captured if the resource contains language elements, and its character set encoding in `MD_DataInformation.defaultLocale`. For the users in our region, English should be the default value for `language` using the ISO 639-2, 3-alphabetic digits code "eng" and the character encoding should be *UTF8*. If the resource contains multiple languages, capture the dominant one in `defaultLocale` and populate the sibling element `otherLocale` with  information describing these additional languages in the same manner.

## Crosswalk considerations

### ISO19139
MD_DataIdentification/language and MD_DataIdentification/characterSet moved to MD_DataIdentification/defaultLocale:PT_Locale - Make use of the newly added Language and character set localization package for defining local language and character set.

### Dublin core / CKAN / data.govt.nz
Maps to `language`
CKAN has one field for language that maps to both Metadata and Resource language fields. ISO 19115 recommends 639-2 3 letter codes. Data.gov.au recommends IETF RFC4646 2 letter codes as primary. See https://www.loc.gov/standards/iso639-2/faq.html#6 for discussion of the differences

### DCAT
Maps to `dct.language`.  
> Note BC 19-7: It iis unclear if DCAT makes a distinction between the metadata language and the resource language

### RIF-CS
No identified mapping

# Also Consider
- **MD_DataIdentification.otherLocale -**  *(codelist - PT_Locale)* [0..\*] alternate localised language(s) and character set (s) used within the resource
- **[Metadata Default Locale](https://www.loomio.org/d/HfkuWCaI/md_metadata-default-locale)** *(codelist - PT_Locale)* [0..1]  contains the  language and character set used in the metadata
- **MD_Metadata.otherLocale -** *(codelist - PT_Locale)* [0..\*] provides information about alternatively used localised character strings provides information about alternatively used localised character strings

# Examples

## XML -

```
<mdb:MD_Metadata>
....
   <mdb:identificationInfo>
      <mri:MD_DataIdentification>
      ....
          <mri:defaultLocale>
            <lan:PT_Locale>
               <lan:language>
                  <lan:LanguageCode codeList="http://www.loc.gov/standards/iso639-2/" codeListValue="eng"/>
               </lan:language>
               <lan:characterEncoding>
                  <lan:MD_CharacterSetCode codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO_19139_Schemas/resources/codelist/ML_gmxCodelists.xml#MD_CharacterSetCode"
                                           codeListValue="utf8"/>
               </lan:characterEncoding>
            </lan:PT_Locale>
         </mri:defaultLocale>
         ....
      </mri:MD_DataIdentification>
   </mdb:identificationInfo>
....
</mdb:MD_Metadata>

```

## UML diagrams
Recommended elements highlighted in Yellow
![resourceDefaultLocale](https://loomio-uploads.s3.amazonaws.com/documents/files/000/201/343/original/1560231295108)