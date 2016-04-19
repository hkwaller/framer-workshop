# Velkommen til Workshop

Idag skal vi prøve ut prototyping med FramerJS.

Hvis du ikke allerede har gjort det gå til [FramerJS.com](http://www.framerjs.com) for å laste ned Framers AutoCode.


## Kort om Framer

Det ble laget for å enkelt kunne gjøre prototyper der muligheten for bruk av kode fjerner mange av begrensningene man finner i mange av konkurrentene.

Forrige Tirsdag kom de med sin største oppdatering noen sinne da de plutselig ble en slags crossover mellom GUI og kode. Det er den som blir kalt AutoCode og som vi skal bruke i dag.


## Byggesteiner
Framer har mange forskjellige byggestener, men man kan si at de fire viktigste er:

1. Layers
2. States
3. Animasjoner
4. Events

### Layers

Et layer er akkurat som det høres ut et lag vi kan manipulere på mange forskjellige måter. Det kan være en enkel rektangel, det kan være en sirkel, en bild, en bakgrunn. Her er alternativene mange. Et layer er selve grunnsteinen i en prototype å vil være å finne i nesten enhver prototype.

### States

For å kunne manipulere et layer kan man gi det en eller flere tilstand/er. Når man går fra en tilstand til en annen kan vi se kraften i Framer som tar seg av animasjonen.

### Animasjoner

En viktig del av en prototype er selvfølgelig animasjoner. Det er de som gir liv til det vi skaper. Det finnes en del forskjellige måter å gjøre animasjoner i Framer. Vi kan bruke states, men også definere egne animasjoner.

### Events

For å få til interaksjon med brukeren settes events på f.eks. et layer. Det kan være et klikk, et tap eller en reaksjon på noe annet; f.eks. en annen animasjon som akkurat er blitt ferdig.


## Jobbe i AutoCode

Som tidligere nevnt er Framer blitt en crossover. Vi kan således velge selv hvis vi vil gjøre så mye som mulig i GUI eller om vi heller koder. Du må uansett kunne en del kode for å kunne gjøre noe litt mer avansert i Framer. Men her er det bare å finne sin egen måte å jobbe på.

Kode skriver med CoffeScript, hvis du ikke brukt det noe særlig eller er usikker på noe så gå til http://coffeescript.org/.


# Oppgaver

---

Hvis du sitter fast med en oppgave, spør meg eller noen andre. Eller så kan du åpne eksemplet i Framer for å se en måte å implementere løsningen på.

Framer har også god dokumentasjon som er gull verdt: http://framerjs.com/docs/
<br/><br/><br/>
### #1 - Lag et layer med animasjon

**Lag et Layer med valfrie attributter å legg til en animasjon**
<br />

Eksempel: https://share.framerjs.com/vf00q4mfxozd/
<iframe src="https://share.framerjs.com/vf00q4mfxozd/" height="400px" width="300px" ></iframe>


#### Hint:

Bruk pluss-menyen oppe til venstre for å lage et layer. Dette kan du så flytte rundt som du vil i kolonnen til høyre.

Animasjoner lages slik:

    new Animation
		layer: LayerSomSkalAnimeres
        properties:
        	x: 0
            y: 100
        time: 0.1

 Du må også starte en animasjon, f.eks. ved:

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

Du kan legge til states med pluss-ikonet oppe til venste. Flytt så rundt dit layer eller endre tilstand i midt-kolonnen.

For å gå mellom ulike states kan du enten velge:

    layer.states.next()

eller så kan du velge hvilken state du vil bytte til:

    layer.states.switch("navnPåState")

dette kan du enten gjøre med Events eller for eksempel en setInterval

	setInterval ->
    	layerA.states.next()
    , 1000

dette vil bytte til neste state hver sekund.
<br/><br/><br/>
>Hvis du syns animasjonene er litt triste på states så kan du legge til animationOptions:

	layer.states.animationOptions =
    	curve: "ease-in-out"
        time: 0.2
        delay: 0.1

<br/><br/>
### #3 - Vi tester events

Du kan fortsette på den forrige prototypen din hvis du vil.

Vi ska nå teste ut events. Disse finner du også på pluss-menyen, velg 'Events' å legg til en event for valfritt layer å få noe å skje.

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

Hvis du vil legge et layer i en container brukes:

    superLayer: navnPåContainer

Det legges til når du oppretter et layer.

<br/><br/>
<br/><br/>

> Teste gjerne ut litt forskjellige versjoner for å gjøre deg litt mer kjent med verktøyet.

<br/><br/>


### #5 - For-løkke

Eksempel: http://share.framerjs.com/3m6hhfxndbhs/
<iframe src="https://share.framerjs.com/3m6hhfxndbhs/" height="400px" width="300px" ></iframe>



Det er alltid leit å gjøre samme ting mange ganger. Prøv å populere en prototype med noen layers ved å ta i bruk en for-løkke.

For-løkker i CoffeScript lages slik:

	for index in [0...4]
    	layer = new Layer
        	...

Viktig å tenke på her er posisjonering. Kanskje det kunne være lurt å bruke en array som holder på posisjoner? Annars kan man også ta i bruk en Utility-funksjon for å plassere layers litt tilfeldig:

	Utils.randomNumber(maksGrense)


<br/>


### #6 - Drag

For å gjøre noe draggable i Framer kan vi si:

	layerName.draggable = true

Prøv ut dette å sjekk om du kan få layeret å returnere til sin ursprunglige posisjon når drag er over.

Eksempel: http://share.framerjs.com/1t3gmtvq60qk/
<iframe src="https://share.framerjs.com/1t3gmtvq60qk/" height="400px" width="300px" ></iframe>

<br/><br/>

#### Hint

Sjekk ut eventen

    layer.onDragEnd

<br/><br/>
### #7 - ScrollComponent

Mange prototyper har en Scrolllist. I Framer er dette relativt enkelt å implementere. Start et nytt prosjekt å legg inn dette bildet http://i.imgur.com/496Im0W.png i et layer. Her kan vi velge Image istedenfor Layer fra pluss-menyen.

Eksempel: http://share.framerjs.com/wgr8u3b505cx/
<iframe src="https://share.framerjs.com/wgr8u3b505cx/" height="400px" width="300px" ></iframe>


#### Hint

Du lager en ScrollComponent slik:

	scroll = new ScrollComponent
		height: Screen.height
		width: Screen.width
		backgroundColor: "#fff"

For å legge in et layer i et ScrollLayer kan vi bruke

	superLayer: navnPåScrollLayer.content

<br/><br/>
### #8 - PageComponent


Eksempel: http://share.framerjs.com/i8b0d45gyhhy/
<iframe src="https://share.framerjs.com/i8b0d45gyhhy/" height="400px" width="300px" ></iframe>


Presis som med scroll så er PageComponent viktig. Den brukes for alt fra en bildekarusell til onboarding. Også her finnes det en ferdig komponent i Framer å ta i bruk.

Det vi må tenke på her er at den må populeres med flere layers, vi kan ikke bare legge inn et bilde som vi gjorde i scroll-komponenten.

En horisontell pagekomponent som dekker hele skjermen lages eksempelvis slik:

	page = new PageComponent
		scrollVertical: false
		width: Screen.width
		height: 200

#### Hint

For å enkelt legge til layers i en PageComponent kan vi bruke en for løkke. Hvis du f.eks. har en PageComponent som går horisontellt kan man legge til layers å gange opp med index og bredden på et layer.

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

Som kan brukes å lytte på endringer.

<br/>
For å få tilgang til den aktuelle pagen kan vi så bruke

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

* Array som holder på id, x og y posisjon
* Container for å holde på bildene
* Legge til bilder, states og events i for-løkke


<br/>
### #2 Liten meny
---

Eksempel: http://share.framerjs.com/wxj5da9i6wzp/
<iframe src="https://share.framerjs.com/wxj5da9i6wzp/" height="400px" width="300px" ></iframe>


En prototype av en liten meny som gir tre valg når man trykker på den. Disse valgene kan så klikkes på for å ekspandere utover skjermen.

Forslag til løsning:

* Legg ut store knappen med de tre små under
* Legg til states for hvordan alla knappene skal animeres eller forflyttes
* Trenger click-events på alle knapper som skal bytte mellom ulike states


#### Hint

Skal et layer opp eller ned?

		if layer.states.current == "stateA"
			layer.states.switch("navnPåState")
