# Litteraturbanken wikidata Runor
- [ ] skapa kopplingar Wikidata -> del av bok hos Litteraturbanken som beskriver runan se [karta](https://w.wiki/zKW) 
- [ ] koppla bilder i Wikicommons till den runa de avbildar video hur vi kopplar metadata i WIkibase på WIkicommons till Wikidata objekt som beskriver runan
- [ ] starta dialog med Evighetsrunor om dom har unika bildidn som kan vara en "auktoritet" för bilder i WIkipedia dvs. konfirmera att bild x föreståller runa y  
- [ ] skapa nya Entity schemas så att datat vi bygger upp i Wikidata blir enkelt att återanvända av andra
  - [ ] för Runor som finns hos Litteraturbanken finns detta schema [EntitySchema:E290](https://www.wikidata.org/wiki/EntitySchema:E290)
  - [ ] för bilder på runor TBD 
    - tänker mig att bilder snart blir bra sökbara så genom att markera delar av bild och koppla dom till Wikidata kan vi navigera runstensbilder på nya sätt...
    - hur markeras att bild [Kulisteinen.jpg](https://commons.wikimedia.org/wiki/File:Kulisteinen.jpg) är en bild som avbildar en kopia av [N 449](https://www.wikidata.org/wiki/Q3367792)
      - förslag markerar ej koppling --> kopian skall inte finnas i Wikidata som ett eget objekt... 
* Worksheet ["Runestones in the Swedish Litteraturebank"](https://docs.google.com/spreadsheets/d/1TraXcbQwSsysCfsTK5i0zECVFIw2OoIjRZ0nv64GX-M/edit#gid=0)
  * [karta](https://w.wiki/zKW) med det som kopplats WD -> Litteraturbanken verk [lista](https://w.wiki/327T), [bilder](https://w.wiki/327V)
## SPARQL
* Bilder i Wikicommons föreställande Runor där vi kopplar dessa till WIkidata med [SDC](https://www.youtube.com/watch?v=lmWmMIuCJVM)
  *  [SPARQL federation WIkicommons](https://wcqs-beta.wmflabs.org/embed.html#%23%20runestones%0A%23defaultView%3AImageGrid%0ASELECT%20DISTINCT%20%3Fsignum%20%3Ffile%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fimage%20%3Fksam%20%3FEvighetsRunor%0AWITH%20%0A%7B%20SELECT%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fksam%20%3FEvighetsRunor%20%3Fsignum%20WHERE%0A%20%20%7B%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%0A%20%20%20%20%7B%3Fitem%20wdt%3AP1261%20%3Fsignum%3B%0A%20%20%20%20%20%20wdt%3AP17%20wd%3AQ34%3B%0A%20%20%20%20%20%20wdt%3AP1260%20%3Fksam.%0A%20%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%7D%0A%20%20%20%20%20%20FILTER%28CONTAINS%28%3Fksam%2C%22uu%2Fsrdb%2F%22%29%29%0A%20%20%20%20%20BIND%28URI%28CONCAT%28%22http%3A%2F%2Fkulturarvsdata.se%2F%22%2C%3Fksam%29%29%20AS%20%3FEvighetsRunor%29%0A%23%20uu%2Fsrdb%2Fd2a4ed30-a765-4d8c-82ad-57fe4b293d21%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%20AS%20%25Wikidataitems%0A%0AWHERE%20%0A%7B%20%20INCLUDE%20%25Wikidataitems%20.%0A%20%20%3Ffile%20wdt%3AP180%20%3Fitem.%0A%20%20%23%20This%20is%20a%20hack%20to%20make%20ImageGrid%20work%0A%20%20%3Ffile%20schema%3AcontentUrl%20%3Furl.%20%0A%20%20bind%28iri%28concat%28%22http%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FSpecial%3AFilePath%2F%22%2C%20wikibase%3AdecodeUri%28substr%28str%28%3Furl%29%2C53%29%29%29%29%20AS%20%3Fimage%29%0A%7D%0ALIMIT%201000) <-> WD se [Evighetsrunor/issues/1#issuecomment-780541203](https://github.com/uppsala-university/Evighetsrunor/issues/1#issuecomment-780541203)
     * 47 records 2020-02-22 

## Litteraturbanken Place ID ##
* Ny WD egenskap för en plats i [Litteratur kartan](https://litteraturbanken.se/litteraturkartan/) se Task [T273156](https://phabricator.wikimedia.org/T273156) och [Property P9213](https://www.wikidata.org/wiki/Property:P9213)
* Task för att populera egenskapen [T275700](https://phabricator.wikimedia.org/T275700)
  * Exempel Runsten Vg 152 = [plats 189](https://litteraturbanken.se/litteraturkartan/?id=189) = Wikidata 
## Video
* [Video:Hur vi kopplar mot Litteraturbanken](https://www.youtube.com/watch?v=0Ac3oLSH7QU)
* [Video:;Hur bilder i Wikicommons kopplas med Wikibase till Wikidata](https://www.youtube.com/watch?v=QhZtGIJMEVQ&feature=youtu.be) dataroundtripping möjlighet dvs. [Semantisk interoperabilitet](https://en.wikipedia.org/wiki/Semantic_interoperability)
  * Evighetsrunor bör ha unika bildid i Wikicommons
  * Wikicommons bör ha i sitt metadata Evighetsrunors bildid för samma bild och där skulle Evighetsrunor vara en auktoritet för vad bilden föreställer 
