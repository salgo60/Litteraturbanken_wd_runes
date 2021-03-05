# Litteraturbanken wikidata Runor
* Kanban boards [Bautil](https://github.com/salgo60/Litteraturbanken_wd_runes/projects/1) / [Misc](https://github.com/salgo60/Litteraturbanken_wd_runes/projects/2)
- [ ] skapa kopplingar Wikidata -> del av bok hos Litteraturbanken som beskriver runan se [karta](https://w.wiki/zKW) / [video](https://youtu.be/VvaZvkBmZcU)
  - exempel U 51 = [Wikidata Q18334422](https://www.wikidata.org/wiki/Q18334422?uselang=sv) som finns i 3 böcker hos Litteraturbanken men även Bautil [video](https://youtu.be/oq8XtxIfEwo)   
- [ ] koppla bilder i Wikicommons till den runa de avbildar [se video](https://youtu.be/qQ48Pqhfi1o?t=82) hur vi kopplar metadata i [Wikibase](https://wikiba.se/) på WIkicommons till Wikidata objekt som beskriver runan
   - se [video](https://youtu.be/qQ48Pqhfi1o), enklast vore om Evighetsrunor hade sina bilder med metadatadata i någon form exempel installera en egen [Wikibase](https://wikiba.se/) på samma sätt som [Wikicommons](https://commons.wikimedia.org/wiki/Commons:Structured_data) är en egen [Wikibase](https://wikiba.se/) 
- [ ] starta dialog med Evighetsrunor om dom har unika bildidn som kan vara en "auktoritet" för bilder i Wikipedia/Wikicommons dvs. konfirmera att bild x föreställer runa y  
- [ ] skapa nya Entity schemas så att datat vi bygger upp i Wikidata blir enkelt att återanvända av andra
  - [ ] för Runor som finns hos Litteraturbanken finns detta schema [EntitySchema:E290](https://www.wikidata.org/wiki/EntitySchema:E290)
  - [ ] för bilder på runor TBD 
    - tänker mig att bilder snart blir bra sökbara så genom att markera delar av bild och koppla dom till Wikidata kan vi navigera runstensbilder på nya sätt...
    - hur markeras att bild [Kulisteinen.jpg](https://commons.wikimedia.org/wiki/File:Kulisteinen.jpg) är en bild som avbildar en kopia av [N 449](https://www.wikidata.org/wiki/Q3367792)
      - förslag markerar ej koppling --> kopian skall inte finnas i Wikidata som ett eget objekt... 
    - markera när bilden av runstenen var tagen/ritat och ev. från vilken bok ex. [Nr 908 i Bautil](https://digital.ub.umu.se/resolve?urn=urn:17a_000068:0285) som   enligt bok Östergötlands runinskrifter [sid 61](https://litteraturbanken.se/forfattare/BrateE/titlar/%C3%96sterg%C3%B6tlandsRuninskrifter/sida/61/faksimil) är samma som Ög 62 samma som Wikidata [Q10727982](https://www.wikidata.org/wiki/Q10727982) som avbildas i bild [haswbstatement:P180=Q10727982](https://commons.wikimedia.org/w/index.php?search=haswbstatement%3AP180%3DQ10727982&title=Special%3ASearch&profile=advanced&fulltext=1&advancedSearch-current=%7B%7D&ns0=1&ns6=1&ns12=1&ns14=1&ns100=1&ns106=1)
* Worksheet ["Runestones in the Swedish Litteraturebank"](https://docs.google.com/spreadsheets/d/1TraXcbQwSsysCfsTK5i0zECVFIw2OoIjRZ0nv64GX-M/edit#gid=0)
  * [karta](https://w.wiki/zKW) med det som kopplats WD -> Litteraturbanken verk [lista](https://w.wiki/327T), [bilder](https://w.wiki/327V)
  * test [karta](https://w.wiki/32ts) där även icke Litteraturbanken visas ex. [Bautil](https://digital.ub.umu.se/node/249114?fulltext-query=)
    * enbart [Bautil](https://digital.ub.umu.se/node/249114?fulltext-query=) - [karta](https://w.wiki/32zE) / [lista](https://w.wiki/32zC) / [image Grid](https://w.wiki/32zL) - [Wikicommons Bautil](https://commons.wikimedia.org/wiki/Category:Bautil)
## SPARQL
* Bilder i Wikicommons föreställande Runor där vi kopplar dessa till Wikidata med [SDC](https://www.youtube.com/watch?v=lmWmMIuCJVM) verkar som WCQS inte är satt i produktion till 100% se EPIC [T260568](https://phabricator.wikimedia.org/T260568)
  *  [SPARQL federation Wikicommons](https://wcqs-beta.wmflabs.org/embed.html#%23%20runestones%0A%23defaultView%3AImageGrid%0ASELECT%20DISTINCT%20%3Fsignum%20%3Ffile%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fimage%20%3Fksam%20%3FEvighetsRunor%0AWITH%20%0A%7B%20SELECT%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fksam%20%3FEvighetsRunor%20%3Fsignum%20WHERE%0A%20%20%7B%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%0A%20%20%20%20%7B%3Fitem%20wdt%3AP1261%20%3Fsignum%3B%0A%20%20%20%20%20%20wdt%3AP1260%20%3Fksam.%0A%20%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%7D%0A%20%20%20%20%20%20FILTER%28CONTAINS%28%3Fksam%2C%22uu%2Fsrdb%2F%22%29%29%0A%20%20%20%20%20BIND%28URI%28CONCAT%28%22http%3A%2F%2Fkulturarvsdata.se%2F%22%2C%3Fksam%29%29%20AS%20%3FEvighetsRunor%29%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%20AS%20%25Wikidataitems%0A%0AWHERE%20%0A%7B%20%20INCLUDE%20%25Wikidataitems%20.%0A%20%20%3Ffile%20wdt%3AP180%20%3Fitem.%0A%20%20%3Ffile%20schema%3AcontentUrl%20%3Furl.%20%0A%20%20bind%28iri%28concat%28%22http%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FSpecial%3AFilePath%2F%22%2C%20wikibase%3AdecodeUri%28substr%28str%28%3Furl%29%2C53%29%29%29%29%20AS%20%3Fimage%29%0A%7D) / [lista](https://wcqs-beta.wmflabs.org/embed.html#SELECT%20DISTINCT%20%3Fsignum%20%3Ffile%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fimage%20%3Fksam%20%3FEvighetsRunor%0AWITH%20%0A%7B%20SELECT%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fksam%20%3FEvighetsRunor%20%3Fsignum%20WHERE%0A%20%20%7B%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%0A%20%20%20%20%7B%3Fitem%20wdt%3AP1261%20%3Fsignum%3B%0A%20%20%20%20%20%20wdt%3AP1260%20%3Fksam.%0A%20%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%7D%0A%20%20%20%20%20%20FILTER%28CONTAINS%28%3Fksam%2C%22uu%2Fsrdb%2F%22%29%29%0A%20%20%20%20%20BIND%28URI%28CONCAT%28%22http%3A%2F%2Fkulturarvsdata.se%2F%22%2C%3Fksam%29%29%20AS%20%3FEvighetsRunor%29%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%20AS%20%25Wikidataitems%0A%0AWHERE%20%0A%7B%20%20INCLUDE%20%25Wikidataitems%20.%0A%20%20%3Ffile%20wdt%3AP180%20%3Fitem.%0A%20%20%3Ffile%20schema%3AcontentUrl%20%3Furl.%20%0A%20%20bind%28iri%28concat%28%22http%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FSpecial%3AFilePath%2F%22%2C%20wikibase%3AdecodeUri%28substr%28str%28%3Furl%29%2C53%29%29%29%29%20AS%20%3Fimage%29%0A%7D) / [lista2](https://wcqs-beta.wmflabs.org/embed.html#SELECT%20DISTINCT%20%3Fsignum%20%3Ffile%20%3Fitem%20%3Fimage%20%3Fksam%0AWITH%20%0A%7B%20SELECT%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fksam%20%3FEvighetsRunor%20%3Fsignum%20WHERE%0A%20%20%7B%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%0A%20%20%20%20%7B%3Fitem%20wdt%3AP1261%20%3Fsignum%3B%0A%20%20%20%20%20%20wdt%3AP1260%20%3Fksam.%0A%20%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%7D%0A%20%20%20%20%20%20FILTER%28CONTAINS%28%3Fksam%2C%22uu%2Fsrdb%2F%22%29%29%0A%20%20%20%20%20BIND%28URI%28CONCAT%28%22http%3A%2F%2Fkulturarvsdata.se%2F%22%2C%3Fksam%29%29%20AS%20%3FEvighetsRunor%29%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%20AS%20%25Wikidataitems%0A%0AWHERE%20%0A%7B%20%20INCLUDE%20%25Wikidataitems%20.%0A%20%20%3Ffile%20wdt%3AP180%20%3Fitem.%0A%20%20%3Ffile%20schema%3AcontentUrl%20%3Furl.%20%0A%20%20bind%28iri%28concat%28%22http%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FSpecial%3AFilePath%2F%22%2C%20wikibase%3AdecodeUri%28substr%28str%28%3Furl%29%2C53%29%29%29%29%20AS%20%3Fimage%29%0A%7D) / [lista 3](https://wcqs-beta.wmflabs.org/embed.html#SELECT%20DISTINCT%20%3Fsignum%20%3Ffile%20%3Fitem%20%3Fksam%0AWITH%20%0A%7B%20SELECT%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fksam%20%3FEvighetsRunor%20%3Fsignum%20WHERE%0A%20%20%7B%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%0A%20%20%20%20%7B%3Fitem%20wdt%3AP1261%20%3Fsignum%3B%0A%20%20%20%20%20%20wdt%3AP1260%20%3Fksam.%0A%20%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%7D%0A%20%20%20%20%20%20FILTER%28CONTAINS%28%3Fksam%2C%22uu%2Fsrdb%2F%22%29%29%0A%20%20%20%20%20BIND%28URI%28CONCAT%28%22http%3A%2F%2Fkulturarvsdata.se%2F%22%2C%3Fksam%29%29%20AS%20%3FEvighetsRunor%29%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%20AS%20%25Wikidataitems%0A%0AWHERE%20%0A%7B%20%20INCLUDE%20%25Wikidataitems%20.%0A%20%20%3Ffile%20wdt%3AP180%20%3Fitem.%0A%20%20%3Ffile%20schema%3AcontentUrl%20%3Furl.%20%0A%20%20bind%28iri%28concat%28%22http%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FSpecial%3AFilePath%2F%22%2C%20wikibase%3AdecodeUri%28substr%28str%28%3Furl%29%2C53%29%29%29%29%20AS%20%3Fimage%29%0A%7D) / [karta med koordinat WD](https://wcqs-beta.wmflabs.org/embed.html#%23defaultView%3AMap%0ASELECT%20DISTINCT%20%3Fsignum%20%3Ffile%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fimage%20%3Fksam%20%3Fcoord%20%3FEvighetsRunor%0AWITH%20%0A%7B%20SELECT%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fksam%20%3FEvighetsRunor%20%3Fsignum%20%3Fcoord%20WHERE%0A%20%20%7B%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%0A%20%20%20%20%7B%3Fitem%20wdt%3AP1261%20%3Fsignum%3B%0A%20%20%20%20%20%20wdt%3AP1260%20%3Fksam%3B%0A%20%20%20%20%20%20wdt%3AP625%20%3Fcoord.%0A%20%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%7D%0A%20%20%20%20%20%20FILTER%28CONTAINS%28%3Fksam%2C%22uu%2Fsrdb%2F%22%29%29%0A%20%20%20%20%20BIND%28URI%28CONCAT%28%22http%3A%2F%2Fkulturarvsdata.se%2F%22%2C%3Fksam%29%29%20AS%20%3FEvighetsRunor%29%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%20AS%20%25Wikidataitems%0A%0AWHERE%20%0A%7B%20%20INCLUDE%20%25Wikidataitems%20.%0A%20%20%3Ffile%20wdt%3AP180%20%3Fitem.%0A%20%20%3Ffile%20schema%3AcontentUrl%20%3Furl.%20%0A%20%20bind%28iri%28concat%28%22http%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FSpecial%3AFilePath%2F%22%2C%20wikibase%3AdecodeUri%28substr%28str%28%3Furl%29%2C53%29%29%29%29%20AS%20%3Fimage%29%0A%7D) / [karta koordinat från bilden](https://wcqs-beta.wmflabs.org/embed.html#%23defaultView%3AMap%0ASELECT%20DISTINCT%20%3Fsignum%20%3Ffile%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fimage%20%3Fksam%20%3FEvighetsRunor%20%3Fpov_coords%0AWITH%20%0A%7B%20SELECT%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fksam%20%3FEvighetsRunor%20%3Fsignum%20WHERE%0A%20%20%7B%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%0A%20%20%20%20%7B%3Fitem%20wdt%3AP1261%20%3Fsignum%3B%0A%20%20%20%20%20%20wdt%3AP1260%20%3Fksam.%0A%20%20%20%20%20%20%23wdt%3AP625%20%3Fcoord.%0A%20%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%7D%0A%20%20%20%20%20%20FILTER%28CONTAINS%28%3Fksam%2C%22uu%2Fsrdb%2F%22%29%29%0A%20%20%20%20%20BIND%28URI%28CONCAT%28%22http%3A%2F%2Fkulturarvsdata.se%2F%22%2C%3Fksam%29%29%20AS%20%3FEvighetsRunor%29%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%20AS%20%25Wikidataitems%0A%0AWHERE%20%0A%7B%20%20INCLUDE%20%25Wikidataitems%20.%0A%20%20%3Ffile%20wdt%3AP180%20%3Fitem%3B%0A%20%20%20%20%20%20%20%20wdt%3AP625%7Cwdt%3AP1259%20%3Fpov_coords.%0A%0A%20%20%3Ffile%20schema%3AcontentUrl%20%3Furl.%20%0A%20%20bind%28iri%28concat%28%22http%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FSpecial%3AFilePath%2F%22%2C%20wikibase%3AdecodeUri%28substr%28str%28%3Furl%29%2C53%29%29%29%29%20AS%20%3Fimage%29%0A%7D) / [karta sten som saknar bild](https://wcqs-beta.wmflabs.org/embed.html#%23defaultView%3AMap%0ASELECT%20DISTINCT%20%3Fsignum%20%3Ffile%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fimage%20%3Fksam%20%3Fcoord%20%3FEvighetsRunor%0AWITH%20%0A%7B%20SELECT%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fksam%20%3FEvighetsRunor%20%3Fsignum%20%3Fcoord%20WHERE%0A%20%20%7B%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%0A%20%20%20%20%7B%3Fitem%20wdt%3AP1261%20%3Fsignum%3B%0A%20%20%20%20%20%20wdt%3AP1260%20%3Fksam%3B%0A%20%20%20%20%20%20wdt%3AP625%20%3Fcoord.%0A%20%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%7D%0A%20%20%20%20%20%20FILTER%28CONTAINS%28%3Fksam%2C%22uu%2Fsrdb%2F%22%29%29%0A%20%20%20%20%20BIND%28URI%28CONCAT%28%22http%3A%2F%2Fkulturarvsdata.se%2F%22%2C%3Fksam%29%29%20AS%20%3FEvighetsRunor%29%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%20AS%20%25Wikidataitems%0A%0AWHERE%20%0A%7B%20%20INCLUDE%20%25Wikidataitems%20.%0A%20%20minus%7B%3Ffile%20wdt%3AP180%20%3Fitem%7D%0A%7D) / [koordinater för en sten Sö 292](https://wcqs-beta.wmflabs.org/embed.html#%23defaultView%3AMap%0ASELECT%20DISTINCT%20%3Fsignum%20%3Ffile%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fimage%20%3Fksam%20%3FEvighetsRunor%20%3Fpov_coords%0AWITH%20%0A%7B%20SELECT%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fksam%20%3FEvighetsRunor%20%3Fsignum%20WHERE%0A%20%20%7B%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%0A%20%20%20%20%7B%3Fitem%20wdt%3AP1261%20%3Fsignum%3B%0A%20%20%20%20%20%20wdt%3AP1260%20%3Fksam.%0A%20%20%20%20%20%20%23wdt%3AP625%20%3Fcoord.%0A%20%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%7D%0A%20%20%20%20%20%20FILTER%28CONTAINS%28%3Fksam%2C%22uu%2Fsrdb%2F%22%29%29%0A%20%20%20%20%20BIND%28URI%28CONCAT%28%22http%3A%2F%2Fkulturarvsdata.se%2F%22%2C%3Fksam%29%29%20AS%20%3FEvighetsRunor%29%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%20AS%20%25Wikidataitems%0A%0AWHERE%20%0A%7B%20%20INCLUDE%20%25Wikidataitems%20.%0A%20%20%3Ffile%20wdt%3AP180%20%3Fitem%3B%0A%20%20%20%20%20%20%20%20wdt%3AP180%20wd%3AQ10688714%3B%0A%20%20%20%20%20%20%20%20wdt%3AP625%7Cwdt%3AP1259%20%3Fpov_coords.%0A%0A%20%20%3Ffile%20schema%3AcontentUrl%20%3Furl.%20%0A%20%20bind%28iri%28concat%28%22http%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FSpecial%3AFilePath%2F%22%2C%20wikibase%3AdecodeUri%28substr%28str%28%3Furl%29%2C53%29%29%29%29%20AS%20%3Fimage%29%0A%7D) <-> WD se [Evighetsrunor/issues/1#issuecomment-780541203](https://github.com/uppsala-university/Evighetsrunor/issues/1#issuecomment-780541203)
     * 126 records 2020-02-22 
     * 2020-03-02
       * 5188 mediafiles
       * [845 runes](https://wcqs-beta.wmflabs.org/embed.html#%23defaultView%3ABubbleChart%0ASELECT%20DISTINCT%20%3FitemLabel%20%3Fitem%28count%28%3Ffile%29%20AS%20%3FmediaFiles%29%0AWITH%20%0A%7B%20SELECT%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fksam%20%3FEvighetsRunor%20%3Fsignum%20WHERE%0A%20%20%7B%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%0A%20%20%20%20%7B%3Fitem%20wdt%3AP1261%20%3Fsignum%3B%0A%20%20%20%20%20%20wdt%3AP1260%20%3Fksam.%0A%20%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%7D%0A%20%20%20%20%20%20FILTER%28CONTAINS%28%3Fksam%2C%22uu%2Fsrdb%2F%22%29%29%0A%20%20%20%20%20BIND%28URI%28CONCAT%28%22http%3A%2F%2Fkulturarvsdata.se%2F%22%2C%3Fksam%29%29%20AS%20%3FEvighetsRunor%29%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%20AS%20%25Wikidataitems%0A%0AWHERE%20%0A%7B%20%20INCLUDE%20%25Wikidataitems%20.%0A%20%20%3Ffile%20wdt%3AP180%20%3Fitem.%0A%20%20%3Ffile%20schema%3AcontentUrl%20%3Furl.%20%0A%20%20bind%28iri%28concat%28%22http%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FSpecial%3AFilePath%2F%22%2C%20wikibase%3AdecodeUri%28substr%28str%28%3Furl%29%2C53%29%29%29%29%20AS%20%3Fimage%29%0A%7D%20group%20by%20%3Fitem%20%3FitemLabel%20%20order%20by%20desc%28%3FmediaFiles%29) / [list](https://wcqs-beta.wmflabs.org/embed.html?#SELECT%20%20%3FitemLabel%20%3Fitem%28count%28%3Ffile%29%20AS%20%3FmediaFiles%29%0AWITH%20%0A%7B%20SELECT%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fksam%20%3FEvighetsRunor%20%3Fsignum%20WHERE%0A%20%20%7B%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%0A%20%20%20%20%7B%3Fitem%20wdt%3AP1261%20%3Fsignum%3B%0A%20%20%20%20%20%20wdt%3AP1260%20%3Fksam.%0A%20%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%7D%0A%20%20%20%20%20%20FILTER%28CONTAINS%28%3Fksam%2C%22uu%2Fsrdb%2F%22%29%29%0A%20%20%20%20%20BIND%28URI%28CONCAT%28%22http%3A%2F%2Fkulturarvsdata.se%2F%22%2C%3Fksam%29%29%20AS%20%3FEvighetsRunor%29%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%20AS%20%25Wikidataitems%0A%0AWHERE%20%0A%7B%20%20INCLUDE%20%25Wikidataitems%20.%0A%20%20%3Ffile%20wdt%3AP180%20%3Fitem.%0A%20%20%3Ffile%20schema%3AcontentUrl%20%3Furl.%20%0A%20%20bind%28iri%28concat%28%22http%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FSpecial%3AFilePath%2F%22%2C%20wikibase%3AdecodeUri%28substr%28str%28%3Furl%29%2C53%29%29%29%29%20AS%20%3Fimage%29%0A%7D%20group%20by%20%3Fitem%20%3FitemLabel%20order%20by%20desc%28%3FmediaFiles%29)

![ss](https://github.com/salgo60/Litteraturbanken_wd_runes/blob/main/images/Runes.png?raw=true)
     * [karta](https://wcqs-beta.wmflabs.org/embed.html#%23defaultView%3AMap%0ASELECT%20DISTINCT%20%3Fsignum%20%3Ffile%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fimage%20%3Fksam%20%3FEvighetsRunor%20%3Fcoord%0AWITH%20%0A%7B%20SELECT%20%3Fitem%20%3FitemLabel%20%3FitemDescription%20%3Fksam%20%3FEvighetsRunor%20%3Fsignum%20%3Fcoord%20WHERE%0A%20%20%7B%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%0A%20%20%20%20%7B%3Fitem%20wdt%3AP1261%20%3Fsignum%3B%0A%20%20%20%20%20%20wdt%3AP1260%20%3Fksam%3B%0A%20%20%20%20%20%20wdt%3AP625%20%3Fcoord.%0A%20%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%7D%0A%20%20%20%20%20%20FILTER%28CONTAINS%28%3Fksam%2C%22uu%2Fsrdb%2F%22%29%29%0A%20%20%20%20%20BIND%28URI%28CONCAT%28%22http%3A%2F%2Fkulturarvsdata.se%2F%22%2C%3Fksam%29%29%20AS%20%3FEvighetsRunor%29%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%20AS%20%25Wikidataitems%0A%0AWHERE%20%0A%7B%20%20INCLUDE%20%25Wikidataitems%20.%0A%20%20%3Ffile%20wdt%3AP180%20%3Fitem.%0A%20%20%3Ffile%20schema%3AcontentUrl%20%3Furl.%20%0A%20%20bind%28iri%28concat%28%22http%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FSpecial%3AFilePath%2F%22%2C%20wikibase%3AdecodeUri%28substr%28str%28%3Furl%29%2C53%29%29%29%29%20AS%20%3Fimage%29%0A%7D) var bilder finns - hur koordinat sätts i Wikidata är nog lite inkonsekvent vi bör vara mer tydliga med försvunnen runa, nuvarande plats och tidigare plats ex. runorna på Skansen](https://w.wiki/33Yt)
      
## Litteraturkartan Plats ID ##
* Ny WD egenskap för en plats i [Litteraturkartan](https://litteraturbanken.se/litteraturkartan/) se Task [T273156](https://phabricator.wikimedia.org/T273156) och [Property P9213](https://www.wikidata.org/wiki/Property:P9213)
* Task för att populera egenskapen [T275700](https://phabricator.wikimedia.org/T275700)
  * Exempel Runsten Vg 152 = [plats 189](https://litteraturbanken.se/litteraturkartan/?id=189) = Wikidata [Q10717923](https://www.wikidata.org/wiki/Q10717923) =  [Evighetsrunor b31c2d13-07c0-44a1-85ee-03340e517ed2](https://app.raa.se/open/runor/inscription?id=b31c2d13-07c0-44a1-85ee-03340e517ed2) 
    * Wikidata saknar egenskap för Runinskription och bild hos Evighetsrunor idag se [Wikidata property proposal](https://www.wikidata.org/wiki/Wikidata:Property_proposal/Evighetsrunor) 
    * Mall [Litteraturkartan](https://sv.wikipedia.org/wiki/Mall:Litteraturkartan) används i [artiklar](https://sv.wikipedia.org/wiki/Special:L%C3%A4nkar_hit/Mall:Litteraturkartan)
* SPARQL [Litteraturkartan och Runor](https://w.wiki/32Tk)
* se även fler exempel [Container](https://github.com/spraakbanken/littb-frontend/issues/25): [Nils Holgersson](https://w.wiki/jEo), [Bellmans Stockholm](https://w.wiki/mMH) 
## Video
* [Video:Hur vi kopplar mot Litteraturbanken](https://www.youtube.com/watch?v=0Ac3oLSH7QU)
* [Video:;Hur bilder i Wikicommons kopplas med Wikibase till Wikidata](https://www.youtube.com/watch?v=QhZtGIJMEVQ&feature=youtu.be) dataroundtripping möjlighet dvs. [Semantisk interoperabilitet](https://en.wikipedia.org/wiki/Semantic_interoperability)
  * Evighetsrunor bör ha unika bildid i Wikicommons
  * Wikicommons bör ha i sitt metadata Evighetsrunors bildid för samma bild och där skulle Evighetsrunor vara en auktoritet för vad bilden föreställer 
* [Video:Wikidata runor Litteraturbanken data roundtrip](https://www.youtube.com/watch?v=qQ48Pqhfi1o&feature=youtu.be)
