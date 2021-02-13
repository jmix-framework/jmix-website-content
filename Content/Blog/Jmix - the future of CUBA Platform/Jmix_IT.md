## Jmix - il futuro della Piattaforma CUBA

Jmix è il nuovo nome e la nuova release di CUBA Platform. Ora è in Anteprima e puntiamo a rilasciare la prima versione stabile nel secondo quadrimestre del 2021. Ecco le caratteristiche principali:
- Spring Boot come tecnologia di base
- Decomposizione in moduli componibili separati (dati, sicurezza, audit, ecc.) 
- Un nuovo approccio alla definizione del modello di dati
- Processo di aggiornamento del database basato su Liquibase
- Approccio di deploy utilizzando le funzionalità Spring Boot, che consente una migliore integrazione con gli ambienti cloud.

Lo sviluppo futuro dell'interfaccia utente sarà focalizzato sul framework ReactJS, ma manterremo l'attuale interfaccia basata su Vaadin come alternativa.

La piattaforma CUBA sarà supportata per un lungo periodo di tempo e stiamo fornendo un percorso di migrazione a Jmix tramite API di compatibilità.

Controlla il rilascio in anteprima di Jmix su [jmix.io](https://www.jmix.io/). Discutete la nuova release nell'apposita [categoria del forum](https://www.cuba-platform.com/discuss/c/jmix). 

<a href="http://jmix.io" class="button">Visita jmix.io</a> <a href="https://www.cuba-platform.com/discuss/c/jmix" class="button forum" style="background: #6c5ce7!important; margin-left:30px;">Lascia il tuo feedback</a>

## Introduzione

CUBA ha iniziato la sua strada nel 2008. Da allora ha attraversato alcune tappe molto importanti. All'inizio era un framework interno senza documentazione e ancor meno API. Era una soluzione interna che consentiva a Haulmont di sviluppare più velocemente le applicazioni aziendali. 

Nel 2015 CUBA è stato introdotto in tutto il mondo con una licenza proprietaria. Quell'anno abbiamo avuto solo pochi utenti - è stato imbarazzante. Divenne ovvio che la politica delle licenze doveva essere convertita all'open source. 

Il 2016 e il 2017 sono stati anni molto produttivi, in cui siamo riusciti ad attirare una comunità molto ampia. Questo è stato un grande cambiamento di mentalità, abbiamo scoperto cosa era giusto e cosa era sbagliato.

Nel 2018-2019 abbiamo iniziato a introdurre un livello API chiaro e ben documentato e abbiamo spostato CUBA Studio su IntelliJ. Tutto ciò ha significato una comunità ancora più grande con un feedback ancora maggiore. Ora ci troviamo al traguardo del prossimo importante aggiornamento. Adesso vediamo insieme cosa ci aspetterà nel 2021.

## Obiettivi della nuova versione

Questi erano gli obiettivi della prossima versione della piattaforma CUBA:

1. Rendere l'esperienza dello sviluppatore più vicina ai framework più popolari. CUBA Platform utilizza Spring, ma oggi Spring Boot ha quasi conquistato il mondo. Stanno emergendo nuovi framework - Micronaut e Quarkus. Hanno tutti principi simili al suo interno: semplice configurazione tramite file .properties o .yaml, uso estensivo delle annotazioni, e semplice connessione e configurazione dei componenti aggiuntivi. Quindi vogliamo che CUBA offra un'esperienza simile agli sviluppatori.

2. Non reinventare la ruota. Dal 2008 sono state sviluppate molte nuove librerie e strumenti. Ora sono mature e possono essere usate per applicazioni di livello enterprise. Così abbiamo voluto sostituire alcuni moduli personalizzati di CUBA con librerie collaudate sul campo. Ad esempio, il sistema di migrazione dei database.

3. Rendere le applicazioni CUBA più compatte. Quando si creano applicazioni con CUBA, non sempre sono necessarie tutte le caratteristiche come l'audit. Ma ha sempre fatto parte del core del framework, inquinando il database con tabelle inutili (per il vostro caso particolare) e avviando servizi extra sul vostro app server. Quindi, sarebbe bello avere la possibilità di escludere alcune funzionalità CUBA e includerle solo quando necessario.

4. E la cosa più importante: preservare la grande esperienza e la velocità di sviluppo delle applicazioni che ha caratterizzato il framework fino ad ora.
 
E la prima cosa da cui partiremo è il...

## Nome

"Cosa significa CUBA?" - È difficile contare quante volte ci è stata posta questa domanda. Sinceramente, era solo un nome non troppo lungo e non troppo corto per chiamare il primo pacchetto del nostro framework interno già nel 2008. Se si analizza il core di CUBA, si possono trovare anche i pacchetti "chile" e "bali". 

Nel 2021 rilasceremo una nuova versione principale - e il nome cambierà. "CUBA" diventa "Jmix". Questo nome è molto più semplice da spiegare: "J" per "Java" e "mix" per le tecnologie e i framework che si mescolano in un'unica applicazione. Meno domande, nessuna associazione né con la nota isola né con il noto cocktail alcolico. 

Effettivamente Jmix è la prossima versione principale di CUBA, con le sue API consolidate e il suo approccio allo sviluppo. Ed è ancora lo stesso insieme di strumenti e generatori di codice convenienti. 

Ma il cambio di nome, che è una parte importante, mostra anche un grande cambiamento nella...


## Tecnologia Core

In un certo senso, in CUBA stavamo copiando alcuni degli approcci di Spring Boot. Il nostro sistema di registrazione delle sessioni, il sottosistema di sicurezza, il sistema di autenticazione... e naturalmente il deployment. Inoltre, i componenti aggiuntivi CUBA sono stati introdotti come risposta agli "starters" di Boot con un proprio meccanismo di incapsulamento e autoconfigurazione.

Quando abbiamo iniziato lo sviluppo di CUBA nel 2008, abbiamo usato Spring "puro" nel core del framework. In Jmix useremo Spring Boot come tecnologia di base. 

L'utilizzo di Spring Boot ci offre i seguenti vantaggi:

1. Migliore esperienza di sviluppo. Oggigiorno quasi tutti gli sviluppatori Java hanno familiarità con Spring Boot. Con Jmix, l'esperienza di sviluppo di Spring Boot può essere sfruttata al massimo, non c'è bisogno di imparare un nuovo framework, solo nuovi starter.
2. Per quanto riguarda gli starter, il core basato su Spring Boot ci permette di utilizzare quasi tutti gli starter esistenti nel nostro framework. Quindi, possiamo contare su un'infrastruttura esistente con un enorme supporto da parte della comunità e un'enorme base di documentazione.
3. E un'altra cosa - Spring Boot ha grandi potenzialità per quanto riguarda il deploy, incluso un grande supporto per la containerizzazione, tutto pronto all'uso. 

Quando si parla di starter di Spring Boot, non possiamo dimenticare i componenti aggiuntivi CUBA. E questo ci porta alla...

![text]({{strapiUrl}}/uploads/c1a763a2f95443c1821b4275b7e4eea3.png)

## Modularizzazione

Di tanto in tanto riceviamo il feedback che un'applicazione CUBA "vuota" che non contiene una singola linea di logica di business ha troppe tabelle e molti componenti funzionali che non vengono mai utilizzati. 
Nella settima versione del framework, abbiamo iniziato ad estrarre le funzionalità di base in add-on separati. Fondamentalmente, CUBA è un insieme di API, e questo approccio ha fornito una flessibilità sufficiente per poter continuare il processo di modularizzazione. 

Partendo da Jmix, è possibile utilizzare le funzionalità del framework (ad es. audit, sicurezza) in modo separato e quasi indipendente. Tutte le funzionalità sono ora fornite come starter Spring Boot.  Per esempio, c'era una funzionalità di audit in CUBA, che ora è un modulo separato in Jmix. E questo modulo a sua volta è suddiviso in moduli Core e UI. Ciò significa che è possibile utilizzare il motore di audit come modulo completo o utilizzare solo il motore core e implementare la propria interfaccia utente personalizzata al posto di quella fornita.

Alcune funzionalità come lo healthcheck vengono sostituite con l'attuatore Spring Boot (vedere la sezione "Non reinventare la ruota").

Jmix fornisce più di 20 starter che possono essere utilizzati. Ecco alcuni starter e relative dipendenze:

<table>
<tbody>
<tr>
<td>
<p><strong>Funzionalità</strong></p>
</td>
<td>
<p><strong>Starter</strong></p>
</td>
<td>
<p><strong>Dipendenze</strong></p>
</td>
</tr>
<tr>
<td>
<p>Entity log</p>
</td>
<td>
<p>Audit</p>
</td>
<td>
<p>Data</p>
</td>
</tr>
<tr>
<td>
<p>File storage</p>
</td>
<td>
<p>Core</p>
</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>
<p>User settings</p>
</td>
<td>
<p>UI Persistence</p>
</td>
<td>
<p>Data</p>
</td>
</tr>
<tr>
<td>
<p>Table presentations</p>
</td>
<td>
<p>UI Persistence</p>
</td>
<td>
<p>Data</p>
</td>
</tr>
<tr>
<td>
<p>Entity log</p>
</td>
<td>
<p>Audit UI</p>
</td>
<td>
<p>Audit, UI</p>
</td>
</tr>
<tr>
<td>
<p>Config properties stored in DB</p>
</td>
<td>
<p>Core</p>
</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>
<p>Restore deleted entities</p>
</td>
<td>
<p>Data tools</p>
</td>
<td>
<p>Data, UI</p>
</td>
</tr>
<tr>
<td>
<p>User sessions</p>
</td>
<td>
<p>Core</p>
</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>
<p>Dynamic attributes</p>
</td>
<td>
<p>Dynamic attributes</p>
</td>
<td>
<p>Data, UI</p>
</td>
</tr>
<tr>
<td>
<p>Entity Snapshots</p>
</td>
<td>
<p>Audit</p>
</td>
<td>
<p>Data</p>
</td>
</tr>
<tr>
<td>
<p>Related entities</p>
</td>
<td>
<p>Advanced Data Operations</p>
</td>
<td>
<p>Data, UI</p>
</td>
</tr>
<tr>
<td>
<p>Bulk editor</p>
</td>
<td>
<p>Advanced Data Operations</p>
</td>
<td>
<p>Data, UI</p>
</td>
</tr>
</tbody>
</table>


Come si può vedere, lo starter "data" è utilizzato da quasi tutti i moduli Jmix. E non è una sorpresa, perché uno dei punti di forza della piattaforma CUBA è stato il suo...

## Livello di accesso ai dati

Qui introdurremo molti cambiamenti, mantenendo tutte le parti migliori di CUBA e introducendo nuove funzionalità che vi aiuteranno ad essere più produttivi.

Con tutti i vantaggi, il modello di dati di CUBA ha un difetto fondamentale: è piuttosto rigido. Per esempio, se si ha bisogno di una soft delete, si deve implementare un'interfaccia apposita (o ereditare la propria entità da `BaseEntity`) e introdurre colonne con nomi predefiniti nella tabella corrispondente. Tutte le chiavi primarie dovevano essere memorizzate nella colonna con il nome `id` se si usava la classe `StandardEntity`. 

Questo portava a limitazioni durante lo sviluppo di nuovi modelli di dati. E ha anche causato molti problemi quando gli sviluppatori hanno cercato di implementare applicazioni con CUBA utilizzando un modello di dati esistente. Questo è stato il caso ad esempio di applicazioni legacy migrate a CUBA per modernizzarle.

In Jmix, il modello Entity diventa più flessibile. Non è più necessario estendere la classe StandardEntity o implementare l'interfaccia Entity. Basta aggiungere l'annotazione `@JmixEntity` ad una classe per renderla accessibile al framework. 

Abbiamo deciso di deprecare le interfacce che specificano le funzionalità di un'entità. Esse vengono sostituite con annotazioni comuni. Per esempio, usiamo l'annotazione `@Version` di JPA e `@CreatedBy` di Spring Boot invece delle interfacce proprietarie `Versioned` e `Creatable`. 

Questo ci permette di rendere il codice più esplicito - si può riconoscere quali caratteristiche sono supportate dall'entità semplicemente guardando il suo codice. 

```
@JmixEntity
@Table(name = "CONTACT")
@Entity(name = "Contact")
public class Contact {

   @Id
   @GeneratedValue(strategy = GenerationType.IDENTITY)
   @Column(name = "ID", nullable = false)
   private Long id;

   @Version
   @Column(name = "VERSION", nullable = false)
   private Integer version;

   @InstanceName
   @NotNull
   @Column(name = "NAME", nullable = false, unique = true)
   private String name;

   @LastModifiedBy
   @Column(name = "LAST_MODIFIED_BY")
   private String lastModifiedBy;

   @Temporal(TemporalType.TIMESTAMP)
   @LastModifiedDate
   @Column(name = "LAST_MODIFIED_DATE")
   private Date lastModifiedDate;

```

Le "Viste di CUBA" sono ora "Fetch Plans". Il nuovo nome descrive molto meglio lo scopo di questi artefatti. 

Il livello di accesso ai dati di Jmix ora supporta il caricamento automatico dei riferimenti. Quindi, se si sceglie di non usare i Fetch Plans per filtrare gli attributi locali, non si otterrà più la famigerata "UnfetchedAttributeException".

Un'altra grande novità è il processo di generazione e aggiornamento del database. Abbiamo deciso di usare Liquibase al posto del motore personalizzato di aggiornamento del DB. Spring Boot è responsabile dell'esecuzione di questi script. Questo è un altro esempio di "non reinventare la ruota" - usando un motore ben noto con una buona documentazione. 

Liquibase può generare script di aggiornamento DB-agnostic, quindi se si sviluppa un prodotto o un add-on con Jmix, non sarà necessario generare script di creazione di database per tutti i possibili RDBMS. Liquibase utilizzerà il dialetto SQL appropriato a seconda del driver JDBC. Allo stesso tempo, permette la personalizzazione SQL specifica per il DB, se ne avete bisogno. 

E noi manteniamo la buona vecchia magia CUBA. Ogni volta che si cambia un'entità, Jmix Studio genera una voce di script Liquibase per riflettere le modifiche.

A cos'altro possiamo pensare quando parliamo di CUBA? Naturalmente, è il sistema avanzato di.. 

## Sicurezza

In Jmix la sicurezza è un modulo separato. Ora è possibile scegliere se si vuole o meno il motore di sicurezza CUBA o qualcos'altro. 

E abbiamo riprogettato il nostro motore di sicurezza, ora è strettamente integrato con la sicurezza di Spring. Per semplificare le cose agli sviluppatori e per reiterare il concetto "non reinventare la ruota", abbiamo sostituito il nostro motore personalizzato con il framework "standard" che ha molta documentazione e che è familiare agli sviluppatori. Il modello è cambiato di conseguenza - in Jmix usiamo classi di Spring Security come UserDetails e SessionRegistry, quindi potrebbe sembrare un po' insolito all'inizio. 

Anche i ruoli sono cambiati - abbiamo unito i ruoli e i gruppi di accesso per semplificare la gestione della sicurezza. In aggiunta a questo, abbiamo introdotto un "Ruolo di Aggregazione". Si tratta di un ruolo composto da altri ruoli - ci sono state molte richieste da parte degli utenti per questa funzione. 

La sicurezza di Spring non è la cosa più semplice da impostare, ma in Jmix abbiamo reso questo processo il più semplice possibile. Sarete in grado di impostare l'accesso alle entità, agli attributi, alle schermate, così come impostare la sicurezza basata sulle righe come avveniva in CUBA.

E come era in CUBA, tutto quello che dovete fare per implementare la sicurezza nella vostra applicazione è aggiungere una dipendenza al vostro progetto e Jmix farà la sua magia - avrete la sicurezza configurata così come l'interfaccia utente per la gestione degli utenti (se volete).

Oltre alla sicurezza, c'è un'altra cosa che è piaciuta a tutti di CUBA: la semplicità dello sviluppo della...

## Interfaccia utente

L'interfaccia utente del backoffice (anche nota come interfaccia utente generica) rimarrà intatta. L'interfaccia utente basata su componenti è stata una parte importante di CUBA e stiamo pianificando di supportarla in Jmix. Il supporto include generatori di schermo, editor di interfaccia utente nell'IDE, ecc. Abbiamo aggiunto nuovi componenti come un componente Pagination separato o ResponsiveGridLayout. L'unica differenza: ora è possibile escludere completamente Generic UI dall'applicazione grazie alla struttura modulare del framework Jmix. 

Si prega di notare che le applicazioni Jmix sono a un solo livello; non c'è più la separazione "core-web". Questo approccio è più semplice e si integra meglio nella nuova architettura. Se si desidera una separazione, è possibile ottenerla implementando due applicazioni Jmix e creando una REST API per la comunicazione. In questo caso, l'interfaccia utente non dipenderà dal modello dei dati e si passeranno i DTO per visualizzare i dati sul front-end o elaborarli sul back-end.

Quando stavamo pianificando la nuova versione del nostro framework, non potevamo ignorare l'ascesa dei framework JS UI. Così abbiamo iniziato a sviluppare i generatori client ReactJS (modulo front-end) in CUBA 7 e continueremo questo lavoro in Jmix. I framework JS hanno di solito una curva di apprendimento piuttosto ripida, quindi il nostro obiettivo è quello di rendere l'esperienza di sviluppo di ReactJS con Jmix più vicina allo sviluppo di Generic UI. 

Abbiamo introdotto TypeScript SDK e sviluppato una serie di componenti personalizzati di ReactJS che possono essere utilizzati per lo sviluppo dell'interfaccia utente. Il modulo front-end si basa sulla Generic REST API che è familiare agli sviluppatori CUBA. L'IDE supporta la generazione di interfacce utente di base con ReactJS. 

Per ora uno sviluppatore può generare una schermata di interfaccia utente "browser" e "editor" utilizzando i nostri componenti. In seguito abbiamo in programma di aggiungere altri componenti e semplificare lo sviluppo dell'interfaccia utente di ReactJS in Studio. 

E ora abbiamo discusso quasi tutti i principali cambiamenti in Jmix, ma sarebbe ingiusto non menzionare il...

![text]({{strapiUrl}}/uploads/9b0dd8c1ff404e01aa0d9e90b1729b2e.png)

## Deploy

CUBA ha due formati di distribuzione: WAR e UberJar e due opzioni: un deploy singolo  o di layer separati (core+web+...).
 
Jmix utilizzerà i plugin Spring Boot per il deploy delle applicazioni. Ciò significa che è possibile eseguire un'applicazione Jmix come un fat JAR eseguibile o un WAR deployable (può anche essere eseguito come applicazione standalone). 

Ma la novità migliore in questo caso è la containerizzazione. Ora non è necessario creare il proprio file Docker per creare un'immagine dell'applicazione, la sua generazione è supportata in automatico. Inoltre, è possibile creare JAR a più livelli per rendere più efficienti le immagini Docker. Oltre a questo, sono supportati i pacchetti di build pack nativi del cloud. 

Quindi le applicazioni Jmix utilizzeranno le tecnologie più all'avanguardia per la distribuzione in ambienti cloud moderni.

E con così tanti cambiamenti, che ne dite della...

## Migrazione da CUBA a Jmix

Prima cosa: non abbandoneremo CUBA. La versione 7.3 sarà una versione con  supporto a lungo termine, e sarà supportata per cinque anni. E dopo di ciò, ci sarà un supporto commerciale disponibile per i seguenti cinque anni. Quindi il framework CUBA vivrà per almeno i prossimi 10 anni.

Al momento Jmix è in fase di Anteprima, quindi lo stabilizzeremo per un po' di tempo prima di annunciare il rilascio stabile pronto per la produzione - tendenzialmente nel secondo trimestre del 2021. Ma se avete intenzione di iniziare a usare CUBA, date prima un'occhiata a Jmix. È abbastanza stabile per iniziare lo sviluppo di PoC. E ricordate che quasi tutto l'ecosistema Spring Boot è al vostro servizio. 

Ai fini della retro-compatibilità, abbiamo introdotto un modulo jmix-cuba. Questo modulo contiene la maggior parte delle API implementate in CUBA. Quindi, non avrete bisogno di cambiare molto il vostro codice per migrare alla prossima versione del framework. Il modulo di compatibilità sarà aggiunto automaticamente alla vostra applicazione durante la migrazione.

La maggior parte dei componenti aggiuntivi CUBA saranno gradualmente migrati alla piattaforma Jmix: reportistica, mappe, processi di business. Come abbiamo fatto con CUBA 7 in precedenza, potremmo deprecare alcuni moduli quando passiamo a Jmix perché c'è uno starter Spring Boot con le stesse funzionalità.

Il formato dei componenti aggiuntivi è cambiato, ma la funzionalità rimane la stessa. È possibile estendere entità e schermi usando la stessa tecnica usata in CUBA. Per quanto riguarda l'override dei servizi, sarà necessario utilizzare l'approccio Spring Boot - basta contrassegnare il servizio add-on con l'annotazione Primary e la funzionalità sarà sostituita. 

Come al solito, quando viene introdotta una major version  (fondamentalmente, Jmix è CUBA 8), potrebbero esserci alcune breaking changes. E queste modifiche, così come le possibili alternative, saranno descritte in dettaglio nella documentazione. 

E la parte più importante della migrazione è il nuovo Studio. Jmix Studio gioca un ruolo molto importante nell'ecosistema del framework. Sarà ancora possibile utilizzare tutti i designer a noi familiari (entità e interfaccia utente), le scorciatoie e le intentions dell'IDE. E Jmix Studio vi aiuterà nella creazione di applicazioni che utilizzano il framework. 

## Conclusioni

Jmix è il prossimo grande passo nell'evoluzione della piattaforma CUBA. Ora è possibile godere di quasi tutti gli starter Spring Boot e utilizzare le tecniche applicabili per il framework Java più popolare al mondo. Allo stesso tempo avete ancora tutte le comode e familiari API e le funzionalità fornite da Jmix - un discendente di CUBA così come una grande esperienza di sviluppo con il nuovo Studio.  

<a href="http://jmix.io" class="button">Visita jmix.io</a> <a href="https://www.cuba-platform.com/discuss/c/jmix" class="button forum" style="background: #6c5ce7!important; margin-left:30px;">Lascia il tuo feedback</a>
<style>.forum:hover, .forum:focus {box-shadow: 0 5px 20px 0 #6c5ce7;}</style>