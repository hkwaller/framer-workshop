# Velkommen til Workshop

Idag skal vi prøve ut prototyping med FramerJS.

Hvis du ikke allerede har gjort det gå til [FramerJS.com](http://www.framerjs.com) for å laste ned Framers AutoCode.


## Start av lokal server

Hvis du heller vil starte en lokal server for å se denne guiden - noe som også gir deg alle eksempler inline:

    git clone git@github.com:hkwaller/framer-workshop.git

cd inn i repo

    npm i
    npm start

Ett vindu vil da åpne seg med alle eksemplene.


## Kort om Framer

Det ble laget for å enkelt kunne gjøre prototyper der muligheten for bruk av kode fjerner mange av begrensningene man finner i mange av konkurrentene. For å gjøre kodingen litt enklere for eksempelvis designere er CoffeScript tatt i bruk da dette har en noe 'snillere' syntaks enn vanlig JavaScript.

Forrige Tirsdag kom Framer med sin største oppdatering noensinne da de plutselig ble en slags crossover mellom GUI og kode. Det er den som blir kalt AutoCode og som vi skal bruke i dag.


## Byggesteiner

Framer har mange forskjellige byggestener, men man kan si at de fire mest grunnleggende er:

1. Layers
2. States
3. Animasjoner
4. Events

### Layers

Ett `layer` er akkurat som det høres ut et lag vi kan manipulere på forskjellige måter. Det kan være en enkel boks, det kan være en sirkel, et bilde, en bakgrunn. Ett `layer` er selve grunnsteinen å vil være å finne i nesten enhver prototype.

### States

For å kunne manipulere et layer kan man gi det en eller flere tilstand/er. Når man går fra en tilstand til en annen kan vi se styrken i Framer som tar seg av animasjonen uten at vi trenger å tenke så altfor mye på det.

### Animasjoner

En viktig del av en prototype er selvfølgelig animasjoner. Det er de som gir liv til det vi skaper. Det finnes en del forskjellige måter å gjøre animasjoner i Framer. Vi kan bruke states, men også definere egne animasjoner. Så å si alt kan animeres å det er bare oss selv som stopper oss.

### Events

For å få til interaksjon med brukeren brukes events på f.eks. et `layer`. Det kan være et klikk eller en swipe. Men det kan også være en reaksjon på noe annet; f.eks. på en animasjon som akkurat er blitt ferdig kan vi bruke events for å gjøre noe annet når det skjer.


## Jobbe i AutoCode

Som tidligere nevnt har Framer blitt noe av en crossover. Vi kan således velge selv hvis vi vil gjøre så mye som mulig i GUI eller om vi heller koder. Du må uansett kunne en del kode for å kunne gjøre noe litt mer avansert i Framer. Men her er det bare å finne sin egen måte å jobbe på.

Her er ett screenshot fra appen:

![Framer AutoCode](http://i.imgur.com/eNdI2VG.png "Framer AutoCode")

Kode skriver vi altså med CoffeScript, har du ikke brukt dette noe særlig eller er usikker på noe så gå til http://coffeescript.org/.


# Oppgaver

---

Hvis du sitter fast med en oppgave, spør meg eller noen andre. Eller så kan du åpne eksemplet i Framer for å se ett forslag på hvordan du kan implementere løsningen.

Framer har også god dokumentasjon som er gull verdt: http://framerjs.com/docs/
<br/><br/><br/>
### #1 - Lag et layer med animasjon

**Lag et Layer med valfrie attributter å legg til en animasjon**
<br />

Eksempel: https://share.framerjs.com/vf00q4mfxozd/
<iframe src="https://share.framerjs.com/vf00q4mfxozd/" height="400px" width="300px" ></iframe>


#### Hint:

Bruk pluss-menyen oppe til venstre eller bruk taste kombinasjon `CMD+SHIFT+N `for å lage et `layer`. Dette kan du så flytte rundt i kolonnen til høyre.

Animasjoner lages slik:

    new Animation
		layer: NavnPåLayerSomSkalAnimeres
        properties:
        	x: 0
            y: 100
        time: 0.1

 Du må også starte en animasjon, f.eks. ved å bruke:

    animation.start()

<br />
<br/><br/>
### #2 - Legge til å bytte mellom states

**Legg til et eller flere states å animer mellom disse**
<br/>

Eksempel: http://share.framerjs.com/sbggjcm6v3pz/
<iframe src="https://share.framerjs.com/sbggjcm6v3pz/" height="400px" width="300px" ></iframe>


<br/>
#### Hint:

Du kan legge til states med pluss-ikonet oppe til venstre. Flytt så rundt ditt `layer` eller endre tilstand i den midterste kolonnen.

For å gå mellom ulike `states` kan du enten velge:

    layer.states.next()

eller så kan du velge hvilken `state` du vil bytte til:

    layer.states.switch("navnPåState")

dette kan du enten gjøre med `Events` eller for eksempel en `setInterval`

	setInterval ->
    	layerA.states.next()
    , 1000

Da vil vi bytte til neste state hver sekund. Vert å notere er at første tilstanden også byttes til når vi velger `.next()`.
<br/><br/><br/>
>Hvis du syns animasjonene er litt triste på states så kan du legge til animationOptions:

	layer.states.animationOptions =
    	curve: "ease-in-out"
        time: 0.2
        delay: 0.1

>Hvis du heller vil endre alle animasjoner i prototypen samtidig bruk:

    Framer.Defaults.Animation =
        curve: "ease-in-out"
        time: 0.2
        delay: 0.1

<br/><br/>
### #3 - Vi tester events

Du kan fortsette på den forrige prototypen din hvis du vil.

Vi ska nå teste ut `events`. Disse finner du også på pluss-menyen, velg `Events` å legg til en event for valgfritt `layer` å få noe til å skje.

Eksempel: http://share.framerjs.com/6gasty0th5hi/
<iframe src="https://share.framerjs.com/6gasty0th5hi/" height="400px" width="300px" ></iframe>


#### Hint:

Her kan vi for eksempel gjøre

    layerA.onClick ->
    	layerA.states.next()


<br/><br/><br/>
### #4 - Container

Eksempel: http://share.framerjs.com/jgpdnbiunlly/
<iframe src="https://share.framerjs.com/jgpdnbiunlly/" height="400px" width="300px" ></iframe>


For å enklere plassere mange elementer kan det være en god idé å bruke en container på samme måte som vi gjør mange andre steder.

Hvis du vil legge et layer i en `container` brukes:

    superLayer: navnPåContainer

Det legges til når du oppretter et `layer`.

<br/><br/>
<br/><br/>

> Teste gjerne ut litt forskjellige versjoner for å gjøre deg litt mer kjent med verktøyet.

<br/><br/>


### #5 - For-løkke

Eksempel: http://share.framerjs.com/3m6hhfxndbhs/
<iframe src="https://share.framerjs.com/3m6hhfxndbhs/" height="400px" width="300px" ></iframe>



Det er alltid litt trist å gjøre samme ting mange ganger. Prøv å populere en prototype med noen layers ved å ta i bruk en `for`-løkke.

`For`-løkker i CoffeScript lages slik:

	for index in [0...4]
    	layer = new Layer
        	...

Viktig å tenke på her er posisjonering. Kanskje det kunne være lurt å bruke en `array` som holder på posisjoner? Ellers kan man også ta i bruk en `Utility`-funksjon for å plassere `layers` tilfeldig:

	Utils.randomNumber(maksGrense)


<br/>


### #6 - Drag

For å gjøre noe flyttbart i Framer kan vi bruke:

	layerName.draggable = true

Prøv ut dette, å sjekk om du kan få `layeret` å returnere til sin opprinnelige posisjon når forflyttningen avsluttes.

Eksempel: http://share.framerjs.com/1t3gmtvq60qk/
<iframe src="https://share.framerjs.com/1t3gmtvq60qk/" height="400px" width="300px" ></iframe>

<br/><br/>

#### Hint

Sjekk ut eventen

    layer.onDragEnd


### #6b

Gå tilbake til oppgave 5 å se om du kan kombinere den med oppgave 6 for å få de individuelle `layerene` å animeres på avsluttet `drag`.

Eksempel: http://share.framerjs.com/lr0ctjaw2531/
<iframe src="https://share.framerjs.com/lr0ctjaw2531/" height="400px" width="300px" ></iframe>



<br/><br/>
### #7 - ScrollComponent

Mange prototyper har en `Scrollist`. I Framer er dette relativt enkelt å implementere. Start et nytt prosjekt å legg inn dette bildet http://i.imgur.com/496Im0W.png i et `layer`. Her kan vi for eksempel velge `Image` istedenfor `Layer` fra pluss-menyen.

Eksempel: http://share.framerjs.com/wgr8u3b505cx/
<iframe src="https://share.framerjs.com/wgr8u3b505cx/" height="400px" width="300px" ></iframe>


#### Hint

Du lager en `ScrollComponent` slik:

	scroll = new ScrollComponent
		height: Screen.height
		width: Screen.width
		backgroundColor: "#fff"

For å legge inn ett `layer` i ett `ScrollLayer` kan vi bruke

	superLayer: navnPåScrollLayer.content

<br/><br/>
### #8 - PageComponent


Eksempel: http://share.framerjs.com/i8b0d45gyhhy/
<iframe src="https://share.framerjs.com/i8b0d45gyhhy/" height="400px" width="300px" ></iframe>


Akkurat som med scroll så er `PageComponent` viktig. Den brukes for alt fra en bildekarusell til onboarding. Også her finnes det en ferdig komponent i Framer å ta i bruk.

Det vi må tenke på her er at den må populeres med flere layers, vi kan ikke bare legge inn et bilde som vi gjorde i scrollkomponenten.

En horisontell pagekomponent som dekker hele skjermen lages eksempelvis slik:

	page = new PageComponent
		scrollVertical: false
		width: Screen.width
		height: 200

#### Hint

For å enkelt legge til `layers` i en `PageComponent` kan vi bruke en `for`-løkke. Hvis du f.eks. har en `PageComponent` som går horisontellt kan man legge til `layers` for å  så gange opp med index sammen med bredden på ett `layer`.

	for index in [0...10]
      layer = new Layer
          width: 200
          height: 200
          superLayer: page.content
          x: 205 * index

<br />
### #8b - Animere PageComponent

Eksempel: http://share.framerjs.com/6r63i6h45y9l/
<iframe src="https://share.framerjs.com/6r63i6h45y9l/" height="400px" width="300px" ></iframe>


For å videreutvikle vår pagekomponent kan vi ved hjelp av eventer få animasjoner å skje når vi navigerer rundt i den.

Her har vi blant annet:

	pageComponent.on "change:currentPage", ->

Som kan brukes til å lytte på endringer.

<br/>
For å få tilgang til det aktuelle `layeret` kan vi da bruke

	pageComponent.currentPage


# Litt mer avansert
<br/>
### #1 Favourite animal app
---
Start et nytt prosjekt å last ned bildene: http://www.filedropper.com/animals

Eksempel: http://share.framerjs.com/qq36gxnu5rzw/
<iframe src="https://share.framerjs.com/qq36gxnu5rzw/" height="400px" width="300px" ></iframe>


Bildene skal legges i griden lengst nede. Størrelsen på et bilde er 187.5x200. Fordel de i en grid som i eksemplet.

Hvert bilde skal ha en state for å flytte den opp over der det står "Nothing here". Trykker man på et bilde igjen skal det legges ned igjen.

Forslag til løsning:

* Array som holder på id, x- og y-posisjon
* Container for å holde på bildene
* Legge til bilder, states og events i for-løkke


<br/>
### #2 Liten meny
---

Eksempel: http://share.framerjs.com/wxj5da9i6wzp/
<iframe src="https://share.framerjs.com/wxj5da9i6wzp/" height="400px" width="300px" ></iframe>


En prototype av en liten meny som animerer ut tre valg når man trykker på den. Disse valgene kan så klikkes på for å ekspanderes utover skjermen.

Forslag til løsning:

* Legg ut store knappen med de tre små under
* Legg til states for hvordan alla knappene skal animeres eller forflyttes
* Trenger `click-events` på alle knapper som skal bytte mellom ulike `states`


#### Hint

Skal et `layer` opp eller ned?

		if layer.states.current == "stateA"
			layer.states.switch("navnPåState")
<br/><br/>
### #3 Egne moduler
---

En bra ting kan være å kunne skrive egne moduler. Framer legger fint tilrette for dette.

Hvert prosjekt du starter med Framer AutoCode lager en mappe i filstrukturen som heter `modules`. Det er her vi kan legge til våre egne moduler.

Åpne opp en prosjektmappe i valfri editor og åpne filen `myModule.coffe`.

Øverst i filen står det forklart hvordan du kan bruke moduler.
<br/><br/><br/>
Men hva om vi vil gjøre noe litt mer spennende?

Eksempel: http://share.framerjs.com/5oojc14b3px2/ (klikk i inputfeltet)
<iframe src="https://share.framerjs.com/5oojc14b3px2/" height="400px" width="300px" ></iframe>

For å kunne lage denne kommer du trenge ett bilde på ett tastatur, for eksempel dette: http://i.imgur.com/jB5hf12.png

Denne modulen er en `class` som extender `layer`. Den tar inn en Y-verdi for å posisjonere tastaturet og har en `event` for å åpne og lukke tastaturet.

For at den ska fungere trenger vi noen ting:
* Sette inn bildet
* Størrelsen på skjermen
* Hente inn hvor på skjermen tastaturet ska vises (det som blir y:0 for tastaturet)
* `Event`for klikk

Husk at modulen må eksporteres!


## Ferdig?

Sjekk ut http://frameco.de for litt inspirasjon og prøv å lage noe selv.

>Visste du at du også kan importere fra Sketch? Pass på å legge dine layers i egne grupper da det er disse du vil referere i Framer.
