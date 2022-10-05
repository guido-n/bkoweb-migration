# bkoweb-migration

Roadmap per la migrazione di bkoweb-web-1.3.6 verso tecnologie Spring Boot 2.x e Spring Framework 5.x.

## Functional slicing

Inizialmente l'approccio prevede di isolare le funzionalita' dell'applicazione di backoffice e di fare deployment + (breve) testing delle singole funzionalita', mantenendo lo stack tecnologico originale.

* Le "fette" funzionali (*functional slice*) dovranno essere il piu' snelle possibile.
* I test saranno *integration tests* usando Junit/Spring-test/Hamcrest e possibilmente anche *full-e2e tests* usando Selenium. Non e' necessario che i test coprano tutti gli aspetti della funzionalita' in questione, l'importante e' che si verifichi il corretto deployment e funzionamento base dall'esterno.

L'idea e' quella di arrivare ad una migrazione  di tutto lo stack tecnologico il prima possibile, e di usare la migrazione di una singola funzionalita' come esempio per le successive, che verranno poi migrate una ad una, fino ad arrivare alla migrazione completa dell'applicazione. Un approccio diverso, basato sulla divisione dell'applicazione nei vari *layer* tecnologici e sulla migrazione a compartimenti dei suddetti, rischia di minare la possibilita' di concludere fasi intermedie ed ottenere risultati parziali in maniera soddisfacente.

Laddove i componenti/funzionalita' del'applicazione sono originariamente separati in maniera netta anche dal punto di vista tecnologico, si puo' direttamente pensare a creare dei microservizi apposta. Ottimi candidati sono la parte di *Exporter*, il componente realizzato con *Spring Batch* ed il componente di integrazione realizzato con *Apache Camel*.

## Component migration

Una volta fatto il deployment e testing di una *functional slice*, si procede alla migrazione. Di seguito una lista indicativa degli aspetti tecnologici coinvolti

* creazione e gestione di repository Git.
* passaggio da *Ant* verso *Maven*.
* utilizzo di Spring Boot nativo, senza piu' avere a che fare direttamente con Tomcat.
* migrazione del codice XML e Java del *domain layer* (ovvero *entity & DAO layers*) verso *Spring DATA JPA*.
* il codice scritto utilizzando le *Criteria API* ([specifica](https://jakarta.ee/specifications/persistence/3.1/jakarta-persistence-spec-3.1.html#a6925) e [implementazione](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/)) puo' essere mantenuto tale quale e migrato nelle nuove classi *JPA repository* ([tutorial](https://www.baeldung.com/spring-data-criteria-queries)).
* il codice dovra' essere organizzato in moduli Maven o addirittura progetti Maven separati, in modo da massimizzarne il riutilizzo. [Qui](https://www.baeldung.com/spring-boot-multiple-modules) e [qui](https://spring.io/guides/gs/multi-module/) si trovano tutorial su come strutturare una applicazione *Spring Boot* su piu' moduli sfruttando il meccanismo delle dipendenze Maven.
* Un ottimo candidato per un modulo a se stante e' il *domain layer*, ovvero in sostanza raccogliere tutte le classi *entity* e *JPA repository* in un modulo Maven su cui si puo' dichiarare una dipendenza esplicita (che di solito viene chiamato con l'estensione *-domain*, in questo caso *bkoweb-domain*).
* Altri ottimi candidati per moduli Maven a se stanti sono i clientper servizi soap. Ovvero dei Moduli maven che cotengano WSDL, codice autogenerato JAXB e JAX-WS ([Qui](https://cxf.apache.org/docs/maven-cxf-codegen-plugin-wsdl-to-java.html) la documentazione di come auto-generare il codice per client SOAP con Maven e Apache CXF).
* NOTA questa sezione potra' essere aggiornata con una *struttura dei moduli Maven consigliata* esplicitamente definita, una volta effettuata la prima migrazione di *functional slice* con successo.
* la logica di business dovrebbe essere estratta dalle classi del *domain layer* e concentrata in classi *services* nel modulo Maven contenente la *Spring Boot app* vera e propria.
* la parte di UI puo' essere migrata mantenedo l'utilizzo di *Spring WEB FLOW* e *JSP*, eventualmente anche usando *Javascript* e frontend toolkit come *Bootstrap*.

Infine, una volta completata la migrazione, l'obiettivo e' di poter lanciare gli stessi test scritti per il deployment con lo stack tecnologico originale, nei confronti delle funzionalita' deployate con lo stack tecnologico nuovo. Nel corso della migrazione potranno presentarsi delle modifiche, le quali verranno discusse a loro tempo in caso necessario.

NOTA dal codice e' possibile argomentare che l'utilizzo di *Spring Batch* in questo progetto sia *overkill*. E' possibile realizzare le stesse funzionalita' con Spring Boot nativo, in particolare in relazione alla parte di *scheduling* con *Quartz*. Un approfondimaneto sara' necessario a riguardo e questa sezione potra' essere aggiornata.