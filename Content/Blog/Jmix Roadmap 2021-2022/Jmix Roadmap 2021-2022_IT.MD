### Jmix Roadmap 2021-2022

Prima di tutto, lasciatemi augurare a tutti voi un felice anno nuovo e congratulazioni per essere sopravvissuti al 2020! È stato un anno difficile per il mondo, e spero che il 2021 ci porti notizie più positive. 

In questo articolo vorrei ricapitolare i risultati del 2020 per il nostro team, e condividere alcuni piani per il prossimo 2021.

Abbiamo tenuto per lo più in silenzio i nostri piani nell'ultimo anno. Spero che ora, con il rilascio di [Jmix](https://www.cuba-platform.com/blog/jmix-the-future-of-cuba-platform/), possiate capire perché. La quantità di cambiamenti e il lavoro di ricerca e sviluppo hanno fatto sì che fosse troppo difficile fare promesse. Dovevamo essere flessibili e muoverci ad un ritmo confortevole. 
Ma anche se la maggior parte della squadra era concentrata su Jmix, abbiamo rilasciato alcune funzionalità interessanti anche per CUBA:
- Il supporto a Kotlin e i ruoli di sicurezza in fase di progettazione in [CUBA 7.2](https://www.cuba-platform.com/blog/cuba72-whats-new/) 
- Il nuovo tema [Helium](https://www.cuba-platform.com/blog/helium-announce/) con un editor di temi visivo
- Supporto per React Native nel frontend [generatore](https://www.cuba-platform.com/discuss/t/frontend-20-1-beta-published/12275/10) 
- [CUBA SDK](https://www.cuba-platform.com/blog/development-in-isolated-network/), che aiuta a sviluppare i vostri progetti in ambienti isolati
  
Naturalmente, ci sono stati centinaia di altri miglioramenti evolutivi in Studio, nel framework e nel generatore di frontend.

Sul fronte della comunità, abbiamo aggiunto le versioni italiana (https://www.cuba-platform.it/) e francese (https://www.cuba-platform.fr/) del sito web e del forum. Abbiamo anche introdotto un modulo semplificato per le richieste di licenza accademica, così [sempre più](https://www.cuba-platform.com/blog/cuba-platform-helping-it-education/) università stanno usando CUBA per i loro corsi di software aziendale! 
Diamo il benvenuto a nuovi grandi marchi tra i nostri clienti, tra cui Ingenico e Sber - la più grande banca dell'Europa orientale. Sber ha [firmato](https://www.sberbank.ru/en/press_center/all/article?newsID=1ffbb179-f30e-4a14-b230-c04d38123fe5&blockID=1539&regionID=77&lang=en&type=NEWS) un accordo su larga scala per adattare e utilizzare CUBA Studio per accelerare lo sviluppo di applicazioni per gli utenti interni di tutta la banca.

## Cosa c'è in programma nel 2021?

Il recente rilascio di Jmix ci fornisce una solida base, quindi guardiamo al futuro con fiducia. Abbiamo piani ambiziosi e attualmente stiamo scalando il team per supportarli. Ci aspettiamo che oltre 50 sviluppatori lavorino su Jmix entro la fine del prossimo anno!

La nostra prima priorità è naturalmente il rilascio di una versione stabile di Jmix. Questo include la documentazione completa, la migrazione degli addon rimanenti e i test approfonditi. Puntiamo al Q2 2020 per finire questo lavoro. 

Le nuove caratteristiche sono descritte di seguito. Tenete a mente che molte di esse richiedono ancora ricerca e sviluppo, quindi non chiedetemi dettagli sull'implementazione. Tuttavia, questo dovrebbe dare un indizio sufficiente della direzione che stiamo prendendo, e spero che vi piacerà!

### Frontend

Ora che il nostro backend CUBA è stato ricostruito su Spring Boot, la tecnologia lato server più usata per i progetti aziendali, è il momento di spostare l'attenzione sul frontend. Beh, ad essere onesti, il momento è arrivato un paio di anni fa, dato che Vaadin 8 è diventato obsoleto. Tuttavia, teniamo sempre in mente la sostenibilità a lungo termine e la compatibilità all'indietro. Sfortunatamente per noi, il mondo dei frameworks web sta cambiando così velocemente che era difficile fare una scommessa sicura. Anche il set di componenti Vaadin [è ancora attivamente in evoluzione] (https://www.cuba-platform.com/blog/vaadin-10-evaluation/) nelle ultime versioni. 
Così abbiamo dovuto mantenere Vaadin 8 UI che, con tutti i suoi limiti, "semplicemente funziona". Tuttavia, il team frontend stava esplorando nuovi approcci nel modulo portal e recentemente nell'SDK TypeScript e nel generatore di frontend React. Si possono già realizzare scaffold di client React e React Native, anche se è ancora un processo molto più complicato e manuale rispetto alla UI basata su Vaadin. È possibile integrare qualsiasi altro framework web con l'aiuto di Typescript SDK, naturalmente, ma è un processo ancora più manuale.

Comunque, la ricerca è finita. Crediamo che React sia "qui per restare" abbastanza a lungo. Quindi l'obiettivo principale per il 2021 è quello di spingere il client React UI allo stato in cui sarà produttivo e facile da usare come Vaadin. Naturalmente, questo presuppone il pieno supporto in Studio, compreso il visual designer con modelli di schermo, il ricaricamento a caldo, la tematizzazione, e una suite completa di componenti, almeno equivalente alle loro controparti Vaadin. Come al solito, cercheremo di astrarre (non isolare) gli sviluppatori dalle complessità dell'ecosistema JS nella maggior misura possibile. I benefici sono ovvi: UI più veloci e meglio scalabili con più ampie opzioni di personalizzazione e un massiccio supporto della comunità.
Tuttavia, c'è anche un prezzo da pagare. Sarà richiesta una comprensione di base di Typescript, HTML, CSS. Avrete anche bisogno dell'IntelliJ IDEA Ultimate commerciale per lavorare comodamente con Typescript. Abbiamo in programma di rilasciare una versione di Studio in bundle con esso. 

Cosa succede a Vaadin? Nessuna preoccupazione, anche la sua storia continua. Crediamo ancora che sia una grande scelta in molti scenari. È perfetto per gli sviluppatori backend che non hanno molto amore per le tematiche web. A meno che non vi aspettiate decine di migliaia di utenti o reti ad alta latenza, farà perfettamente il suo lavoro, e tali presupposti sono validi per la maggior parte delle applicazioni di back office. Continuiamo a monitorare i progressi della squadra di Vaadin nelle ultime versioni, e ci aspettiamo di essere in grado di passare dalla versione 8 a una di quelle moderne nel 2022. 

E le applicazioni mobili? Come detto sopra, stiamo già supportando la generazione di client React Native, così come le PWA nel client React. Inoltre, abbiamo iniziato un lavoro di ricerca e sviluppo su piccola scala intorno a [Flutter](https://flutter.dev/), una tecnologia UI molto promettente sostenuta da Google. L'obiettivo finale di Flutter è quello di fornire una singola tecnologia UI per tutte le piattaforme: mobile, web e anche desktop. Sarà anche molto più familiare agli sviluppatori backend, mentre la sua ideologia è simile a React: tutto è un componente (aka Widget) e l'UI è una funzione di stato.
Flutter sta guadagnando trazione velocemente ed è già la scelta più popolare per le app mobili cross platform, mentre il supporto web è in beta. Tuttavia, dobbiamo ancora vedere se diventerà mainstream. 

Il nostro principale caso d'uso - applicazioni "line of business" - presuppone la manipolazione con grafici di dati complessi. Quindi sia Flutter che React richiedono una comoda API lato server per questo scopo. Dopo alcuni esperimenti, abbiamo optato per GraphQL, che sembra essere un abbinamento molto naturale e che diventerà una parte condivisa per entrambi i clients.

Per concludere, Jmix supporterà più opzioni per fornire frontend di qualsiasi scala e complessità, sia per piattaforme web che mobili, e sia per coloro che amano o odiano JS :) 

### DevOps e Clouds

Per anni, abbiamo considerato il deployment "fuori dal nostro ambito" e ci siamo concentrati solo sul lato dello sviluppo dei progetti. Tuttavia, riceviamo sempre più richieste di semplificare anche questo aspetto del ciclo di vita delle applicazioni. Così abbiamo deciso di formare un team "DevOps" all'interno di Jmix per gestire questo aspetto. Il compito è in linea con il nostro approccio generale: astrarre (ma - lo sottolineo di nuovo - non isolare) lo sviluppatore dalle specifiche delle tecnologie sottostanti come Jenkins, Docker, Kubernetes, Terraform e fornire strumenti visuali semplici e convenienti per configurare i vostri ambienti e le pipeline CI/CD.

Cosa significa questo in pratica:
- Configurare, generare e pubblicare immagini Docker
- Configurazione di ambienti, ad esempio test e produzione
- Descrivere l'infrastruttura necessaria usando un designer visuale - basato su Kubernetes e Terraform
- Configurare le pipeline CI/CD
  
Stiamo progettando di affidarci all'infrastruttura dei cloud pubblici - AWS per cominciare - per una parte di queste funzionalità. Ma AWS (Azure, Alibaba, ecc.) offre così tanto di più del semplice hosting della vostra app, che sarebbe un crimine ignorare le sue capacità! Quindi vi daremo la possibilità di costruire applicazioni veramente cloud-native basate su servizi cloud tra cui database, archiviazione di file, autenticazione, ricerca full text, monitoraggio, logging, bilanciamento del carico, ecc. 

L'obiettivo finale è quello di fornirvi tutto il necessario per implementare ed eseguire le vostre applicazioni nel cloud con il minimo sforzo. Poiché questa è una direzione assolutamente nuova, è difficile indicare delle scadenze. Ma puntiamo a rilasciare una versione beta alla fine del 2021.  

### Strumenti

Il team di Studio sta gradualmente diventando il più grande di Jmix. Infatti, ogni direzione, sia essa cloud o frontend, presuppone un rilevante supporto di strumenti sul lato Studio. Inoltre, vogliamo introdurre alcuni importanti miglioramenti quest'anno:
- Nuovi designer visuali - per le query JPQL e GraphQL, stringhe di messaggi e semplici espressioni logiche. Spero che a tutti piacerà l'idea di non dover scrivere stringhe JPQL!
- Generazione di codice basata su modelli per azioni tipiche: aprire una schermata, salvare/caricare dati, mostrare un messaggio, invocare un servizio, avviare un processo aziendale.
- Configurazione dei report in fase di progettazione. 
- Configurazione dei processi BPM in fase di progettazione.

### Spostare le attività in fase di progettazione

Vorrei porre l'attenzione sulle ultime due funzionalità. Fino ad ora, entrambi gli addon Reporting e BProc supportavano solo la configurazione a runtime. Da un certo punto di vista, questo è fantastico: i report e i processi di business possono essere configurati da chi non è uno sviluppatore, senza la necessità di ricompilare l'applicazione. Tuttavia, questo ha una serie di effetti collaterali:
- Se il modello dei dati cambia, il tuo report o processo di business potrebbe smettere di funzionare, e non te ne accorgerai finché non lo eseguirai. 
- Le istanze dei report e dei processi di business potrebbero facilmente non essere sincronizzate tra diverse installazioni di un'applicazione. Mentre stai testando una nuova versione, allo stesso tempo qualcuno cambia qualcosa in produzione...
- Per i report complessi, uno sviluppatore deve usare scomodi editor di codice a runtime.
- Quando si configura un processo di business, uno sviluppatore deve passare avanti e indietro tra Studio e un'applicazione in esecuzione con frequenti riavvii per aggiungere nuovi moduli, servizi, ecc.  
  
Alla lunga, questo diventa un processo fragile e macchinoso, lasciando molto spazio agli errori. Considerando tutto questo, abbiamo deciso di implementare BPM e report designer in Studio. 
Anche l'opzione di costruire report e modificare i processi di business in fase di esecuzione sarà conservata. Si può notare che questo è in linea con il supporto al design time recentemente implementato per i gruppi di accesso e i ruoli di sicurezza.

Per i report, questo significa che un report diventerà una classe Java, configurata usando una procedura guidata di Studio. Questo permette la validazione al momento della compilazione, la capacità di testare e fare il debug dei report e migliori strumenti visuali. 

Per il BPM, l'idea è simile. L'editor di progettazione permetterà di testare e fare il debug delle definizioni di processo, così come di creare molte cose in linea: servizi, moduli, gestori e così via. Questo risulterà in un ambiente di sviluppo senza soluzione di continuità, abbastanza potente da competere con alcune soluzioni BPMS sul mercato.  

Come molte altre caratteristiche, puntiamo a rilasciare una versione beta di questi nuovi strumenti alla fine del 2021. 

### Timeline  

Ecco la timeline che riassume i rilasci previsti per vostra comodità:
- Q2 2021 - versione stabile di Jmix
- Q4 2021 - versione stabile del client React
- Q4 2021 - versioni beta di:
&nbsp;&nbsp;&nbsp;&nbsp;- strumenti DevOps e Cloud
&nbsp;&nbsp;&nbsp;&nbsp;- supporto alle applicazioni cloud native
&nbsp;&nbsp;&nbsp;&nbsp;- report visuali e configurazione dei processi di business in fase di progettazione
&nbsp;&nbsp;&nbsp;&nbsp;- altri strumenti in Studio
- Q2 2022 - versioni stabili di tutto quanto rilasciato nel Q4 2021

Questo è un programma impegnativo e alcune scadenze potrebbero slittare, ma siamo determinati a fare il possibile per rispettarlo.

### Il futuro

L'implementazione di tutto quanto descritto sopra significherà che Jmix diventerà una potente piattaforma per costruire moderne applicazioni aziendali, fornendo:
- UI scalabile per applicazioni mobili e web
- Capacità cloud native e automazione completa della distribuzione 
- Più strumenti visuali, facilitando lo sviluppo produttivo e un più facile onboarding
 
Infatti, Jmix dovrebbe diventare un forte concorrente sul fiorente mercato delle Low Code Application Platforms (LCAP). Con almeno lo stesso livello di produttività, Jmix affronta molte delle carenze delle LCAP, quindi speriamo che sia una ventata di freschezza in questo mercato controverso. 
Jmix è progettato per gli sviluppatori, e offre un ambiente di lavoro confortevole, mentre la maggior parte degli LCAP sono focalizzati sugli utenti business (alias gli sviluppatori "improvvisati") e quindi forniscono una scarsa esperienza ai veri sviluppatori. Jmix è anche abbastanza aperto e flessibile per costruire le applicazioni più complesse come gli ERP - questo fatto è stato dimostrato più volte dai progetti della nostra comunità. Infine, a differenza della maggior parte degli LCAP, è costruito intorno a un framework open source - il che significa che le vostre applicazioni sono veramente vostre. 

Speriamo che questa combinazione di caratteristiche di Jmix vi aiuti a realizzare applicazioni potenti ma belle in tempo record, e che attiri nuovi membri verso la nostra comunità. Come sempre, il vostro feedback è molto apprezzato - sentitevi liberi di lasciare i vostri commenti sul forum o contattateci direttamente. 