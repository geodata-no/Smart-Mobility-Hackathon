# Smart Mobility Hackathon, Oslo, 16-18 September 2016
Her vil du finne informasjon og kodeeksempler på hvordan du kan komme i gang med å bruke tjenester og innhold fra [Geodata Online](http://geodata.no/hva-tilbyr-vi/innhold-og-tjenester/).

Geodata Online tilbyr en rekke kart og tjenester basert på norske data. Alle våre tjenester er skreddersydd for å brukes sammen med programvare fra Esri, men de kan også aksesseres fra andre klienter via standardiserte REST/JSON-grensesnitt. Det finnes blant annet ulike bakgrunnskart (tile-tjenester), søk- og geokoding (adresser, stedsnavn), ruteberegning, eiendomsdata (offisielle matrikkeldata), demografidata, risikodata (flom, skred etc.), forretningsdata (bedrifter, butikker, kjeder etc.), 3D-tjenester og mye mer. For en mer komplett liste, ta en titt på [denne oversikten](http://geodataonline.maps.arcgis.com/apps/MapAndAppGallery/index.html?appid=7c3bd2cafdc947779a6493a2e03504c9).

## Hvordan komme i gang
### Brukernavn og passord
Du vil (ved forespørsel) få utdelt brukernavn og passord til Geodata Online som gir deg gratis tilgang til mange av tjenestene i en begrenset periode. Alternativt er det mulig å opprette en bruker med 30-dagers fri prøveperiode [her](http://geodata.no/supportsenter/geodata-online-support/opprett-ny-konto/).

### URL'er til tjenester
Etter at du har fått tilgang til påloggingsinformasjon, trenger du URL'er til de ulike tjenestene. Tjenestene er gruppert etter hvor "tunge" der er; tile-tjenester ligger subdomenet "services", dynamiske- og enkle analysetjenester ligger på "services2", mens tyngre eksporttjenester ligger på "eksport". For en grov oversikt, [se her](http://geodata.no/supportsenter/geodata-online-support/gis-brukere/adresser-til-tjenester-fra-geodata-online/).

Alle tjenestene har et enkelt html-grensesnitt hvor du kan bla deg rundt for å se meta-data og prøve ut spørringer etc. For å se alle de ulike dynamiske karttjenestene kan du gå inn på URL'en under. Listen er tom inntil du logger inn (velg "Login" øverst til høyre på siden). 
[https://services2.geodataonline.no/arcgis/rest/services/Geomap_UTM33_EUREF89](https://services2.geodataonline.no/arcgis/rest/services/Geomap_UTM33_EUREF89).

For å finne arealet (og geometrien) på Slottsparken (Gårds- og bruksnummer 0301-209/25) vil spørringen se slik ut:
[http://services2.geodataonline.no/arcgis/rest/services/Geomap_UTM33_EUREF89/GeomapMatrikkel/MapServer/5/query?where=kommunenr%3D%270301%27+AND+gardsnr%3D209+AND+bruksnr%3D25&outFields=*&returnGeometry=true&f=html](http://services2.geodataonline.no/arcgis/rest/services/Geomap_UTM33_EUREF89/GeomapMatrikkel/MapServer/5/query?where=kommunenr%3D%270301%27+AND+gardsnr%3D209+AND+bruksnr%3D25&outFields=*&returnGeometry=true&f=html)

Skal du gjøre kallene via REST må man legge på et gyldig token (&token=XXX). I tillegg må man endre respons-formatet til json (&f=json).

### Token
Alle REST-kall krever et gyldig token. Dette kan enten lages manuelt på en webside (maks gyldighet 365 dager), eller man kan hente det programmatisk. Ideelt sett bør dette gjøres fra en backend-løsning. Mer informasjon om hvordan man lager token finnes [her](http://geodata.no/supportsenter/geodata-online-support/utviklere/tilgang-til-sikre-tjenester/).

### Dokumentasjon av REST-API
Når du navigerer rundt i html-grensesnittet til tjenesten (se over), kan du hele tiden trykke "API Reference" øverst til høyre på siden for å få opp dokumentasjon av den tjenesten/funksjonen du står på. En komplett oversikt over hele REST-grensesnittet finnes [her](http://services.geodataonline.no/arcgis/sdk/rest/index.html).

## JavaScript
Esri har et eget JavaScript API som inneholder masse ferdige GUI-komponenter og annet som gjør det enkelt å kommunisere med karttjenestene fra Geodata Online. Det finnes full dokumentasjon og en lang rekke kodeeksempler.
[https://developers.arcgis.com/javascript/](https://developers.arcgis.com/javascript/)
Siste hovedrelease (versjon 4.0) inneholder støtte for 3D-visning, men er enda ikke like komplett som "forrige" versjon (3.x).

Det er også fullt mulig å benytte tjenestene i andre rammeverk (Open Layers, Leaflet etc.), siden alt er basert på REST og JSON. For en del av rammeverkene er det også lagd hjelpemoduler for å forenkle jobben. Esri har blant annet lagd et sett med Leaflet plugins som finnes her:
[https://github.com/Esri/esri-leaflet](https://github.com/Esri/esri-leaflet)

## Native apps
I tillegg til et JavaScript API, har Esri SDK'er for de aller fleste plattformer og språk (iOS, Android, Xamarin, .Net, Qt etc.). Dokumentasjon, eksempler etc. finnes her:
[https://developers.arcgis.com/arcgis-runtime/](https://developers.arcgis.com/arcgis-runtime/).

## Demoer
Esri har en lang rekke kjørbare eksempler på sine utviklersider, f.eks. her:
[https://developers.arcgis.com/javascript/3/jssamples/](https://developers.arcgis.com/javascript/3/jssamples/)

I tillegg finnes det noen demo-applikasjoner på Geodata sine Labs-sider:
[http://labs.geodata.no](http://labs.geodata.no)
