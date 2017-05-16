# Vue - code along - the-basics

Vi börjar med att hämta in vue via en cdn och jag tar här unpkg.com
```html
<script src="https://unpkg.com/vue"></script>
```

sen instansierar vi Vue-objektet:

```javascript
var app = new Vue({

})
```

Okej, detta är vår vue instans, vårt Vue-objekt.
Det första vi behöver göra är att ge vue ett element att jobba med
och detta kan vi göra med en css selector:

`div id="vue-container"`
`el: '#vue-container'` element-property

Nu vill vi lägga till vår variabel message, det gör vi genom en `data`-property

`data: {}` här kan vi stoppa in alla våra variabler

```javascript
data: {
    message: 'Hello World!'
}
```

Uppdatera och se om det funkar!


Yes, det funkar, nu har vi alltså initierat Vue korrekt och vi kan börja använda dess variabler.

## Styra HTML-attribut `v-bind`
Jag har sagt att man liksom **kryddar HTML** med Vue.
Vi kan binda html-attribut med vue js.


Så till exempel, om vi vill ha lite dynamiskt här nu så kan vi till en title på vår heading:
Säg att vi har en `span` och här skriver jag vad jag ska göra när jag kommer hem.

```html
<span>När jag kommer hem ska jag leka med min dotter</span>
```

`title="Test"`

Spara, håll musen över, se att det kommer upp.

Yes, det funkar, men title kanske inte är det man direkt tänker på
kan användas för detta. Men tänk då om vi dynamiskt vill kunna ange en klass.. Hm.. 

Vi har denna punkten, det jag tänkt göra när jag kommer hem.
Om jag ger den klassen `.completed` så ser det ut såhär.
Okej, hur kan vi göra detta lite mer dynamiskt..
Vi vill alltså kunna säga vilken class som ska vara aktiv.
Så om vi tar `v-bind:class="activeClass`
Skapa upp variabeln
`activeClass: '',`

Okeej.. och ändrar vi till `activeClass: 'completed'` så får vi tillbaka det.
Okej.. Så det är ganska kraftfullt..

Så det var `v-bind` vi kan alltså binda Vue till våra **html_attribut**


## Conditionals `v-if`
Men om vi ska fortsätta krydda vår html så kan vi krydda med `v-if=""`

Så om vi då lägger in en variabel här vi tar `v-if="showMe`
och vi lägger till variabeln i vues data propperty `showMe: false`
sparar och uppdaterar så försvinner vår heading helt.
Om vi tittar i devtools så ser vi att headingen är HELT borta!

Okej, så vi kan alltså sätta conditionals till våra html-element
om dom ska visas eller inte. Riktigt nice..

Okej, så nu har vi lite koll på `v-bind` som binder Vue-variabler
med html-attribut.
Och vi har `v-if` där vi villkorligt kan visa eller dölja html-element.

## Lista / loop `v-for`
Men säg att jag har mer saker som jag ska få gjort idag..
Jag har en liten att göra lista..
Vi gör om vår span till en `<li>`-tagg. och stoppar in i
en unordered list.
Och innan jag kan komma hem och mysa med min dotter så behöver vi
ju bli färdiga här:
```html
<li>Håll i workshop på YRGO</li>
<li>Mysa med min underbara dotter!</li>
```

Okej, så vi har alltså en att göra lista. Men såhär kommer vi ju
aldrig jobba med en att-göra-lista. Utan om vi har en att-göra-lista
så kommer det ju alltid först vara en array med list-objekt..

Så vi börjar med att skapa en array med några punkter.
Så skriv upp runt 5 punkter från din att-göra lista idag.
Så typ, gå upp, ät frukost

```javascript
todos: [
    {text: 'Vakna, snooza inte!'},
    {text: 'Käka en grym frukost, tänk på kalaspuffar så blir allt gott'},
    {text: 'Ta båten till Lindholmen'},
    {text: 'Håll i workshop på YRGO'},
    {text: 'Mys med familjen'},
]
```


## Vad har vi lärt oss hittills?

- initiera Vue instans
- property el: `el: '#vue-container'`
- Skriva variabler så som i Laravel: `{{ message }}`
- v-bind: `v-bind:class="activeClass"`
- v-if: `v-if="showMe"`
- v-for `v-for="todo in todos"`


------------

Okej, åter till vår att göra lista:
Vi har ju den där `.completed`-klassen. Så den ska vi ta
och använda tycker jag.

Vi lägger till en property för varje todo-item som heter `completed`

```javascript
todos: [
    {
        text: 'Vakna, snooza inte!',
        completed: true,
    },
    {
        text: 'Ät frukost, låtsas att det är kalaspuffar så blir allt godare',
        completed: true,
    },
    {
        text: 'Ta båten till Linholmen',
        completed: true,
    },
    {
        text: 'Håll i workshop på YRGO',
        completed: false,
    },
    {
        text: 'Mys med familjen',
        completed: false,
    },
],
```

Okej, då behöver vi alltså lägga till en v-bind:class här för
att vi ska kunna ange vår completed-klass
```
v-bind:class="todo.completed ? 'completed' : ''"
```

Nice, då har vi fått det att fungera..
Men vad händer då om vi vill kunna styra fler klasser dynamiskt?
Säg att vi har en klass som heter important som gör texten röd?

Jo, då finns det lite speciell syntax för just när vi binder classer

Vi kan då skicka in ett object:
Och då funkar det så att det property-namn som vi skickar in,
är den klass som kommer apliceras om värdet för propertyn är true.

Alltså, säg att vi hade haft en annan klass som hette "important"
som vi ville visa, men vi vill också visa "completed"

```
{important: true, completed: true}
...
{completed: todo.completed}
```

Se i devtools vad som händer.



## Event handling `v-on`
Nästa steg blir att vi vill kunna vara med och kontrollera
vilka todos som är completed och inte.
Vi vill kunna klicka på vårt list-item och då toggla `completed`

Då har vi en ny krydda: **v-on**, så då säger vi, `v-on:click=""`
Här kan vi antingen anropa en metod eller så kan vi ändra ett värde.
Så i vårt fall så `v-on:click="todo.completed = !todo.completed"`


## Computed Properties
Nu är det på tiden att vi snyggar till det iaf lite, vi sätter
classen "todo-list" på ul-taggen.

Nu så ska vi bättra på detta lite ytterligare.
När vi är färdiga med en uppgift vill vi inte att den ska ligga kvar
och vara i vägen utan vi vill att de items som inte är färdiga
ska ligga under "Att göra:" och de som redan är klara ska ligga
under "Färdiga:" istället.

Lägg till `<h3>Avslutade:</h3>` under listan.
Vi skapar en nu `<ul>` men vad ska vi göra nu..
Vi behöver filtrera bort och bara visa de som är klara..
Och det gäller för den första listan också..

Ja men om vi kan vår javascript så vet vi att `todos` är en array
och alla arrayer har ju en filter-metod vi kan anropa..
så vi borde kunna skriva:
```javascript
// inte färdiga
todos.filter(n => !n.completed)

// färdiga
todos.filter(n => !n.completed)
```

Men, detta blir lätt lite kladdigt.. Och vi vill ju inte heller
behöva ha för mycket logik i vår template.. Så vi vill istället
kunna skriva typ..

Till vår räddning kommer något som kallas **Computed Properties**
Computed properties används när vi har ett variabel som
vars data på något sätt behöver beräknas "on the fly". Alltså
om datan eventuellt behöver omvärderas så fort något värden
förändras av användaren.

En computed property är blir då en "live-variabel" som
hela tiden uppdateras.

Vi ska nu skapa två olika computed properties. Den ena ska heta
`uncompletedTodos`, `completedTodos`
och det är där vi sköter denna logik.
Computed properties i Vue anges i Vue.computed

Men, hur ska vi nå vår variabel todos?
Jo, Vue har lagt alla mina variabler från data, enkelt åtkomliga 
från `this.`, vue -instansens objekt.

```javascript
computed: {
    completedTodos () {
        return this.todos.filter(t => t.completed)
    },
    uncompletedTodos () {
        return this.todos.filter(t => !t.completed)
    }
}
```

Nu kan vi också skriva om "Avslutade" till:
`<h3>{{ completedTodos.length }} avslutade:</h3>`
för att ha koll på hur många todos som är avslutade.

## Snygga till det lite mer
Ja men när jag inte har några avslutade tasks, då vill jag inte
att det ska stå "0 avslutade", det ser kanske lite fult ut..

Så det känns som om vi behöver använda oss av `v-if`.
Men jag vill inte lägga det både på headern och på ul-listan.
Det blir lite för upprepande.. Jag vill hellre ha det i ett block..

Så jag skapar då ett block, jag tar en div, wrappar runt.
Sätter `<div v-if="completedTodos.length > 0">`


## `v-if` eller `v-show`
Nice, där har vi det. Så låt oss inspektera detta i devtools..
Vår div raderas helt ur domen då villkoret inte stämmer.
Detta är väldigt bra, det gör att användare som tar upp sin devtools
och försöker leta efter exploits osv inte kan hitta det som döljs
bakom en v-if. Det är mer säkert.

Men, varje gång man raderar och lägger till ett object i vår DOM,
detta blir då som sagt lite säkrare men det kan också vara
problematiskt ur perfomance-perspektiv. Säg att vi använder har
en todo-lista med flera hundra kanske tusen avklarade uppgifter,
ja, om vi då hade haft en knapp som säger "visa alla avslutade"
så skulle det blivit onödigt mycket load att skapa alla de tusen 
html-elementen och sen ta bort alla om man inte längre vill 
visa alla avslutade.. Så när det finns stor möjlighet att 
den data man har inuti sin `v-if` kommer togglas fram och tillbaka,
då bör man vara lite försiktig. Och för att lösa detta så finns det
ännu en annan vue-krydda passar perfekt här:
`v-show`.

Det v-show gör är att bara sätta css-propertyn 'display:none' på
det object som inte ska visas. Detta gör att inget 
object raderas eller skapas på nytt.

Titta i inspektor.

Och på samma sätt, när det inte finns några uppgifter som ska göras
vill vi visa användaren det på ett snyggare sätt.
```html
<li class="empty-placeholder" v-if="uncompletedTodos.length == 0">
    Det finns inga uppgifter att göra!<br>
    <small>Njut så länge det varar...</small>
</li>
```

## Lägga till ny todo `v-model`
Sådär.. Då har vi ett ganska så sjyst gränssnitt för hur
det ser ut när vi togglar mellan completed / uncompleted..

Då ska vi se till så att vi kan lägga till en ny todo!

Nu kommer vi komma i kontakt med vues **two way data binding**, den är
väldigt lik så som angular har _two way data binding_.

Vi börjar med att lägga till en input:
```html
<li>
    <input type="text" placeholder="Lägg till din nya uppgift här...">
</li>
```

Och för att vi nu ska få denna input att bindas till en variabel
så anger vi `v-model` vilken data model som ska bindas.
Så i vårt fall så kör vi `v-model="newTodo"`
Och nu har vi då bundit vår input till variabeln newTodo.
Men vi måste nu också då bara skapa newTodo för annars skriker 
consollen och säker att vi inte har den variabeln..

```javascript
newTodo: 'Köp bananaer!',
```

bara för att visa här nu då så kan vi printa vår variabel `newTodo`
bredvid får rubrik här: 

```html
<h1 v-if="showMe">{{ message }} {{ newTodo }}</h1>
```

Och skriv sedan i inputen och se two way data binding.

Och om ni har brottats med JavaScript innan så förstår ni 
hur mycket jobb det skulle ligga bakom bara denna funktion
att live-uppdatera samma text som man själv skriver någon annan
stans. Kul! :)

Okej, så nu vet vi att vår variabel `newTodo` fungerar.

## Lägg till ny todo! `methods`

Då ska vi fixa en knapp som lägger till vår nya todo också.

```html
<button>+ Lägg till</button>
```

och vad ska vi göra nu då?
Jo nu ska vi krydda vår html och binda lite logik till vår HTML.
vi lägger till en `v-on:click=""`
När vi använde `v-on:click=""` förra gången så utförde vi vår logik
direkt här. Men nu ska vi peka på en method.
`v-on:click="addTodo"`

Och nu ska vi lägga till ytterligare en property i vår Vue-instans:
`methods: {}`

```javascript
addTodo(){
    // steg 3
    let todoText = this.newTodo.trim()
    if(!todoText) return

    this.todos.push({
        text: todoText,
        completed: false
    })

    // ta denna i steg 2
    this.newTodo = ''
}
```

Nästa steg är att vi vill kunna trycka enter för att lägga till,
inte behöva trycka på knappen!

`v-on:keyup.enter="addTodo"``

Och om man trycker på `Esc` så kanske man skall avbryta och 
tömma input:
`v-on:keyup.esc="newTodo = ''"`

Och så snyggar vi till det genom att ta bort knappen som nu inte 
behövs och lägger till klassen:
`<li class="add-todo">`

Sådär, nu har vi en skapligt fungerande uppgift!
