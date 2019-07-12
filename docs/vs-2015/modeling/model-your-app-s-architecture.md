---
title: Modellare l'applicazione&#39;architettura s | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
ms.assetid: aedce746-9df5-49e1-9662-67eb1b83d313
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c9e5de52fbe15049f4acb3dacf236bfe9f4ecc92
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823271"
---
# <a name="model-your-app39s-architecture"></a>Modellare l'applicazione&#39;architettura s
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per garantire che il sistema software o l'applicazione soddisfi degli utenti esigenze, è possibile creare modelli in Visual Studio come parte del comportamento dell'applicazione o sistema software e la descrizione della struttura complessiva. Usando gli schemi è anche possibile descrivere modelli usati durante la progettazione. Questi modelli consentono di comprendere l'architettura esistente, discutere le modifiche e comunicare chiaramente le intenzioni.  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Lo scopo di un modello è ridurre l'ambiguità che si verifica nelle descrizioni in linguaggio naturale e consentono all'utente e ai colleghi di visualizzare la progettazione e discutere le progettazioni alternative. Un modello deve essere usato insieme ad altri documenti o discussioni. Un modello di per sé non rappresenta una specifica completa dell'architettura.  
  
> [!NOTE]
> In questo argomento, il termine "sistema" indica il software che si sta sviluppando. Potrebbe essere un'ampia raccolta di molti componenti hardware e software oppure una singola applicazione o una parte di un'applicazione.  
  
 L'architettura di un sistema può essere suddivisa in due aree:  
  
- [Progettazione di alto livello](#Structure). Descrive i componenti principali e la loro modalità di interazione per soddisfare ogni requisito. Se il sistema è di grandi dimensioni, ogni componente può disporre del proprio progetto di alto livello che mostra come è costituito da componenti più piccoli.  
  
- [Schemi progettuali](#Patterns) e le convenzioni usate in tutte le progettazioni dei componenti. Un modello descrive un particolare approccio per realizzare un obiettivo di programmazione. Usando gli stessi schemi in tutta una progettazione, il team può ridurre il costo delle modifiche e dello sviluppo di nuovo software.  
  
## <a name="Structure"></a> Progettazione di alto livello  
 Un progetto di alto livello descrive i componenti principali del sistema e il modo in cui interagiscono tra loro per raggiungere gli obiettivi della progettazione. Le attività nell'elenco seguente sono coinvolte nello sviluppo della progettazione di alto livello, anche se non necessariamente in una determinata sequenza.  
  
 Se si sta aggiornando il codice esistente, è possibile iniziare descrivendo i componenti principali. Verificare di comprendere le modifiche ai requisiti dell'utente e quindi aggiungere o modificare le interazioni tra i componenti. Se si sta sviluppando un nuovo sistema, iniziare individuando le funzionalità principali di esigenze degli utenti. È possibile esplorare le sequenze di interazioni per i casi di utilizzo principali e quindi consolidare le sequenze in una progettazione del componente.  
  
 In ogni caso, è utile per sviluppare le diverse attività in parallelo e sviluppare il codice e i test in una fase iniziale. Evitare di tentare di completare uno di questi aspetti prima di avviarne un altro. In genere, i requisiti e la comprensione del modo migliore per progettare il sistema verrà modificato durante la scrittura e il test del codice. Di conseguenza, è necessario iniziare a individuare e codificare le funzionalità principali dei requisiti e della progettazione. Inserire i dettagli nelle iterazioni successive del progetto.  
  
- [Informazioni sui requisiti](#Requirements). Il punto di partenza di qualsiasi progettazione è una chiara comprensione delle esigenze degli utenti.  
  
- [Modelli architettonici](#BigDecisions). Le scelte effettuate sulle tecnologie principali e gli elementi architettonici del sistema.  
  
- [Componenti e relative interfacce](#Components). È possibile creare diagrammi dei componenti per mostrare le parti principali del sistema e le interfacce tramite cui interagiscono tra loro. Le interfacce di ogni componente includono tutti i messaggi identificati nei diagrammi di sequenza.  
  
- [Interazioni tra componenti](#Interactions). Per ogni caso di utilizzo, evento o messaggio in arrivo, è possibile creare un diagramma di sequenza che mostra il modo in cui interagiscono i componenti principali del sistema per ottenere la risposta richiesta.  
  
- [Modello di dati di componenti e interfacce](#Data). È possibile creare diagrammi classi per descrivere le informazioni passate tra componenti e archiviate all'interno dei componenti.  
  
## <a name="Requirements"></a> Informazioni sui requisiti  
 La progettazione di alto livello di un'applicazione completa viene sviluppata più efficacemente con un modello requisiti o altra descrizione delle esigenze degli utenti. Per altre informazioni sui modelli di requisiti, vedere [modellare i requisiti utente](../modeling/model-user-requirements.md).  
  
 Se il sistema che si sta sviluppando è un componente in un sistema più grande, parte o tutti i requisiti potrebbero essere incorporati nelle interfacce di programmazione.  
  
 Il modello requisiti fornisce queste informazioni essenziali:  
  
- Interfacce fornite. Un'interfaccia fornita fornisce un elenco dei servizi o operazioni che il sistema o il componente deve fornire ai propri utenti, che siano utenti o altri componenti software.  
  
- Interfacce necessarie. Un'interfaccia richiesta fornisce un elenco di servizi o operazioni che possono essere usate dal sistema o dal componente. In alcuni casi, sarà possibile progettare tutti questi servizi come parte del proprio sistema. In altri casi, specialmente se si sta sviluppando un componente che può essere combinato con altri componenti in molte configurazioni, l'interfaccia richiesta verrà impostata da considerazioni esterne.  
  
- Requisiti di qualità del servizio. Le prestazioni, la sicurezza, l'affidabilità e altri obiettivi e vincoli che il sistema deve soddisfare.  
  
  Il modello requisiti viene scritto dal punto di vista degli utenti del sistema, siano essi persone o altri componenti software. Questi non conoscono i meccanismi interni del sistema. Al contrario, l'obiettivo in un modello architettonico è descrivere i meccanismi interni e mostrare come soddisfano le esigenze degli utenti.  
  
  Se si mantengono i requisiti e modelli architettonici separati, diventa più semplice illustrare i requisiti con gli utenti. In tal modo vengono agevolati anche il refactoring di progettazione e la considerazione di architetture alternative mentre i requisiti restano invariati.  
  
  È possibile separare i requisiti e modelli architettonici in due modi diversi:  
  
- È possibile mantenerli nella stessa soluzione ma in progetti diversi. Verranno visualizzati come modelli separati in Esplora modelli UML. Diversi membri del team possono operare in parallelo sui modelli. È possibile creare tipi limitati di traccia tra i modelli.  
  
- Inserirli nello stesso modello UML, ma in pacchetti diversi. In questo modo è più semplice tracciare le dipendenze tra i modelli, ma si impedisce a più persone alla volta l'uso del modello. Inoltre, un modello molto grande richiederà più tempo per il caricamento in Visual Studio. Questo approccio è pertanto meno adatto per progetti di grandi dimensioni.  
  
  La quantità di dettagli che devono essere inseriti in un modello di requisiti o architettonico dipende dalla scala del progetto e dalle dimensioni e dalla distribuzione del team. Un piccolo team su un progetto breve non po' andare oltre il disegno di un diagramma classi dei concetti aziendali e alcuni schemi progettuali; un progetto di grandi dimensioni distribuito su più aree ha bisogno di più dettagli.  
  
## <a name="BigDecisions"></a> Modelli di architettura  
 Nelle prime fasi di sviluppo è necessario scegliere le principali tecnologie e gli elementi da cui dipende la progettazione. Le aree in cui devono essere apportate queste scelte includono quanto segue:  
  
- Scelte di tecnologia di base, ad esempio la scelta tra un database e un file system e la scelta tra un'applicazione di rete e un client Web e così via.  
  
- Scelte di framework, ad esempio una scelta tra Windows Workflow Foundation o ADO.NET Entity Framework.  
  
- Scelte dei metodi di integrazione, ad esempio tra un bus di servizio aziendale o un canale Point to Point.  
  
  Queste scelte vengono frequentemente determinate dai requisiti di qualità del servizio, ad esempio la scala e la flessibilità e possono essere effettuate prima che siano noti i requisiti dettagliati. In un sistema di grandi dimensioni, la configurazione di hardware e software sono fortemente correlati.  
  
  Le selezioni effettuate influiscono sulla modalità di utilizzo e di interpretazione del modello architettonico. Ad esempio, in un sistema che usa un database, le associazioni in un diagramma classi potrebbero rappresentare relazioni o chiavi esterne nel database, mentre in un sistema basato su file XML, le associazioni potrebbero indicare riferimenti incrociati che usano XPath. In un sistema distribuito i messaggi in un diagramma di sequenza possono rappresentare messaggi su una connessione; in un'applicazione indipendente, possono rappresentare chiamate di funzione.  
  
## <a name="Components"></a> Componenti e relative interfacce  
 Le indicazioni principali di questa sezione sono le seguenti:  
  
- Creare diagrammi dei componenti per mostrare le parti principali del sistema.  
  
- Disegnare le dipendenze tra i componenti o le interfacce per mostrare la struttura del sistema.  
  
- Usare interfacce sui componenti per visualizzare i servizi che ciascun componente fornisce o richiede.  
  
- In una progettazione di grandi dimensioni, è possibile creare diagrammi separati per scomporre ogni componente in parti più piccole.  
  
  Questi concetti sono approfonditi nelle sezioni seguenti.  
  
### <a name="components"></a>Componenti  
 Le viste centrali di un modello dell'architettura sono i diagrammi dei componenti che mostrano le parti principali del sistema e le modalità di dipendenza tra loro. Per altre informazioni sui diagrammi dei componenti, vedere [diagrammi dei componenti UML: informazioni di riferimento](../modeling/uml-component-diagrams-reference.md).  
  
 ![Diagramma dei componenti UML con parti](../modeling/media/uml-barecomponent.png "UML_BareComponent")  
  
 Un diagramma dei componenti tipico per un sistema di grandi dimensioni può includere componenti come i seguenti:  
  
- Presentazione. Il componente che fornisce l'accesso all'utente, in genere in esecuzione in un Web browser.  
  
- Componenti del servizio Web. Fornisce la connessione tra client e server.  
  
- Controller del caso di utilizzo. Eseguire i passaggi di ogni scenario utente.  
  
- Attività principali dell'azienda. Contiene classi che si basano su classi nel modello dei requisiti, implementa le operazioni principali e impone i vincoli aziendali.  
  
- Database. Archivia gli oggetti business.  
  
- Registrazione e gestione degli errori dei componenti.  
  
### <a name="dependencies-between-components"></a>Dipendenze tra componenti  
 Oltre ai componenti, è possibile visualizzare le reciproche dipendenze. Una freccia di dipendenza tra due componenti mostra che le modifiche nella progettazione di uno influisce sulla progettazione dell'altro. Ciò accade solitamente perché un componente usa direttamente o indirettamente i servizi o le funzioni fornite da un altro componente.  
  
 Un'architettura ben strutturata dispone di una disposizione chiara delle dipendenze, in cui tali condizioni sono vere:  
  
- In una mappa codice non sono presenti cicli.  
  
- I componenti possono essere disposti in livelli in cui ogni dipendenza va da un componente di un livello a quello del livello successivo. Tutte le dipendenze tra due livelli qualsiasi vanno nella stessa direzione.  
  
  È possibile visualizzare direttamente le dipendenze tra componenti oppure è possibile visualizzare le dipendenze tra le interfacce richieste e fornite associate ai componenti. Tramite le interfacce è possibile definire le operazioni che vengono usate in ogni dipendenza. In genere, le dipendenze vengono visualizzate tra i componenti quando i diagrammi vengono creati per la prima volta e quindi sostituiti dalle dipendenze tra interfacce durante l'aggiunta di altre informazioni. Entrambe le versioni sono descrizioni corrette del software, ma la versione con interfacce offre informazioni più dettagliate rispetto alle versioni precedenti.  
  
  La gestione delle dipendenze è molto importante per la produzione di software gestibile. I diagrammi dei componenti devono riflettere tutte le dipendenze nel codice. Se il codice esiste già, verificare che tutte le dipendenze vengono visualizzate nei diagrammi. Se il codice è in fase di sviluppo, verificare che non includa le dipendenze che non sono previsti nel diagramma dei componenti. Per consentire l'individuazione delle dipendenze nel codice, è possibile generare diagrammi livello. Per garantire che siano soddisfatti i vincoli di dipendenza pianificati, è possibile convalidare il codice rispetto ai diagrammi livello. Per altre informazioni, vedere [diagrammi livello: informazioni di riferimento](../modeling/layer-diagrams-reference.md).  
  
### <a name="interfaces"></a>Interfacce  
 Posizionando le interfacce sui componenti, è possibile separare e denominare i gruppi principali di operazioni fornite da ogni componente. I componenti di un sistema di vendite basato su Web, ad esempio, potrebbero disporre di un'interfaccia mediante la quale i clienti acquistano beni, un'interfaccia mediante la quale i fornitori aggiornano i cataloghi e una terza interfaccia mediante la quale viene gestito il sistema.  
  
 Un componente può contenere un numero qualsiasi di interfacce fornite e richieste. Le interfacce fornite mostrano i servizi forniti dal componente per essere usate da altri componenti. Le interfacce richieste mostrano i servizi che il componente usa in altri componenti.  
  
 Se si definiscono entrambi le interfacce fornite e richieste, è possibile separare chiaramente il componente dal resto della progettazione, in modo da poter usare le tecniche seguenti:  
  
- Posizionare il componente in un test harness in cui i componenti circostanti sono simulati dal test harness.  
  
- Sviluppare il componente indipendentemente da altri componenti.  
  
- Riutilizzare il componente in altri contesti accoppiando le interfacce a componenti diversi.  
  
  Quando si vuole definire l'elenco delle operazioni in un'interfaccia, è possibile creare un'altra visualizzazione dell'interfaccia in un diagramma classi UML. A tale scopo, individuare l'interfaccia in Esplora modelli UML e trascinarla in un diagramma classi. È quindi possibile aggiungere operazioni all'interfaccia.  
  
  Un'operazione in un'interfaccia UML può rappresentare qualsiasi modalità in cui può essere richiamato un comportamento di un componente. Potrebbe rappresentare una richiesta di servizio Web, un segnale o un'interazione di un altro tipo o una chiamata di funzione di un programma normale.  
  
  Per determinare le operazioni da aggiungere, creare diagrammi di sequenza per mostrare il modo in cui i componenti interagiscono tra loro. Visualizzare [interazioni tra componenti](#Interactions). Ognuno di questi diagrammi di sequenza visualizza le interazioni che si verificano in un caso di utilizzo diversi. In questo modo, è possibile eseguire gradualmente aggiunte all'elenco di operazioni in ogni interfaccia di componente, esplorando i casi di utilizzo.  
  
### <a name="decomposing-a-component-into-parts"></a>Scomposizione di un componente in parti  
 È possibile applicare la procedura descritta nelle sezioni precedenti per ogni componente.  
  
 All'interno di ogni componente è possibile visualizzare i sottocomponenti come parti. Una parte è in modo efficace un attributo del componente padre, ovvero un tipo di classe. Ogni parte dispone di un proprio tipo che può essere un componente. È possibile posizionare questo componente in un diagramma e mostrarne le parti. Per altre informazioni, vedere [diagrammi dei componenti UML: Linee guida](../modeling/uml-component-diagrams-guidelines.md).  
  
 È utile applicare questa tecnica all'intero sistema. Crearlo come singolo componente e visualizzare i componenti principali come parti. Consente di identificare chiaramente le interfacce del sistema con il mondo esterno.  
  
 Quando la progettazione di un componente usa un altro componente, spesso è possibile scegliere se rappresentarlo come una parte o un componente separato cui si accede tramite un'interfaccia richiesta.  
  
 Nelle situazioni elencate usare le parti:  
  
- La progettazione del componente padre deve sempre usare il tipo componente della parte. Di conseguenza, la progettazione della parte è fondamentale per la progettazione del componente padre.  
  
- Il componente padre non dispone di alcun esistenza concreta in proprio. È possibile ad esempio disporre di un componente concettuale chiamato livello di presentazione che rappresenta una raccolta di componenti reali che gestiscono le interazioni e le visualizzazioni dell'utente.  
  
  Usare componenti separati accessibili tramite le interfacce richieste in queste situazioni:  
  
- Il componente richiedente può essere accoppiato tramite le relative interfacce a diversi componenti di fornitura in fase di esecuzione.  
  
- La progettazione è tale per cui sarebbe facile sostituire un provider con un altro.  
  
  L'utilizzo di interfacce richieste è preferibile all'utilizzo delle parti. Sebbene la progettazione può richiedere più tempo, il sistema risultante è più flessibile. È anche più semplice testare separatamente i componenti. In questo modo sono possibili meno accoppiamenti nei piani di sviluppo.  
  
## <a name="Interactions"></a> Interazioni tra componenti  
 Le indicazioni principali di questa sezione sono le seguenti:  
  
- Identificare i casi di utilizzo del sistema.  
  
- Per ogni caso di utilizzo creare uno o più diagrammi per mostrare come i componenti del sistema ottengono il risultato richiesto collaborando tra loro e con gli utenti. In genere, si tratta di diagrammi di sequenza o diagrammi attività.  
  
- Usare le interfacce per specificare i messaggi ricevuti da ogni componente.  
  
- Vengono descritti gli effetti delle operazioni nelle interfacce.  
  
- Ripetere la procedura per ogni componente, che mostra come interagiscono le parti.  
  
  In un sistema di vendite basato sul Web, ad esempio, il modello requisiti potrebbe definire un acquisto del cliente come un caso di utilizzo. È possibile creare un diagramma di sequenza per mostrare le interazioni del cliente con i componenti nel livello di presentazione e per mostrare le interazioni con il warehouse e i componenti di contabilità.  
  
### <a name="identifying-the-initiating-events"></a>Identificazione degli eventi di inizializzazione  
 Le operazioni eseguite dalla maggior parte dei sistemi software possono essere divise in modo semplice in base alle risposte fornite a input o eventi diversi. L'evento di inizializzazione potrebbe essere uno dei seguenti:  
  
- La prima azione in un caso di utilizzo. Può essere nel modello requisiti un passaggio in un caso di utilizzo o un'azione in un diagramma di attività. Per altre informazioni, [diagrammi caso d'uso UML: Linee guida](../modeling/uml-use-case-diagrams-guidelines.md) e [diagrammi di attività UML: Linee guida](../modeling/uml-activity-diagrams-guidelines.md).  
  
- Un messaggio a un'interfaccia programmatica. Se il sistema che si sta sviluppando è un componente in un sistema più grande, deve essere descritto come un'operazione in una delle interfacce del componente. Visualizzare [componenti e relative interfacce](#Components).  
  
- Una determinata condizione che viene monitorata dal sistema o un evento normale, ad esempio un'ora del giorno.  
  
### <a name="describe-the-computations"></a>Descrivere i calcoli  
 Creare diagrammi di sequenza per mostrare come i componenti rispondono all'evento iniziale.  
  
 Creare una linea di vita per ogni istanza del componente che fa parte di una sequenza tipica. In alcuni casi, potrebbero essere presenti più istanze di ogni tipo. Se l'intero sistema è stato descritto come singolo componente, deve essere presente una linea di vita per ogni parte in esso contenuta.  
  
 Per altre informazioni, vedere [diagrammi di sequenza UML: Linee guida](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 I diagrammi di attività sono anche utili in alcuni casi. Se ad esempio i componenti dispongono di un flusso continuo di dati, è possibile descriverlo come un flusso oggetto. Se il componente dispone di un algoritmo complesso, è possibile descriverlo come un flusso di controllo. Verificare di esprimere chiaramente quale componente esegue ogni azione, ad esempio i commenti. Per altre informazioni, vedere [diagrammi di attività UML: Linee guida](../modeling/uml-activity-diagrams-guidelines.md).  
  
### <a name="specify-the-operations"></a>Specificare le operazioni  
 I diagrammi mostrano le operazioni eseguite da ogni componente, rappresentate come messaggi in un diagramma di sequenza o azioni in un diagramma di attività.  
  
 Raccogliere insieme queste operazioni per ogni componente. Creare le interfacce fornite sul componente e aggiungere le operazioni alle interfacce. Viene usata in genere un'interfaccia separata per ogni tipo di client. Le operazioni vengono aggiunte più facilmente alle interfacce nello **Esplora modelli UML**. Raccogliere allo stesso modo le operazioni che ogni componente usa da altri componenti e li inserisce nelle interfacce richieste associate al componente.  
  
 È utile aggiungere commenti a diagrammi di attività o di sequenza, per prendere nota del risultato ottenuto dopo ogni operazione. È anche possibile scrivere l'effetto di ogni operazione nel relativo **postcondizione locale** proprietà.  
  
### <a name="Data"></a> Modello di dati di componenti e interfacce  
 Definire i parametri e restituire valori di ogni operazione nelle interfacce del componente. Laddove le operazioni rappresentano chiamate come ad esempio richieste di servizio Web, i parametri sono quelle informazioni che vengono inviate come parte della richiesta. Se vengono restituiti valori diversi da un'operazione, è possibile usare parametri con il **direzione** impostata su **Out**.  
  
 Ogni parametro e il valore restituito dispongono di un tipo. È possibile definire questi tipi mediante Diagrammi classi UML. Non è necessario rappresentare il dettaglio di implementazione in questi diagrammi. Se, ad esempio, si descrivono i dati trasmessi come XML, è possibile usare un'associazione per rappresentare qualsiasi tipo di riferimento incrociato tra nodi XML e usare classi per rappresentare i nodi.  
  
 Usare i commenti per descrivere i vincoli aziendali sulle associazioni e sugli attributi. Se, ad esempio, tutti gli elementi nell'ordine del cliente devono provenire dallo stesso fornitore, è possibile descrivere tale situazione mediante il riferimento alle associazioni tra gli articoli dell'ordine e gli elementi nel catalogo dei prodotti e tra l'elemento del catalogo e il fornitore.  
  
## <a name="Patterns"></a> Modelli di progettazione  
 Uno schema progettuale è una struttura sulla modalità di progettazione di un particolare aspetto del software, specialmente uno che ricorre in parti diverse del sistema. Adottando un approccio uniforme nel progetto, è possibile ridurre il costo di progettazione, garantire la coerenza nell'interfaccia utente e ridurre i costi di comprensione e modifica del codice.  
  
 Alcuni schemi progettuali generali, ad esempio Observer sono ben conosciuti e ampiamente applicabili. Sono anche disponibili modelli che possono essere applicati solo al progetto. Ad esempio, in un sistema di vendite Web, saranno disponibili diverse operazioni nel codice dove vengono apportate modifiche all'ordine del cliente. Per assicurarsi che lo stato dell'ordine venga visualizzato in modo accurato in ogni fase, tutte queste operazioni devono seguire un particolare protocollo per aggiornare il database.  
  
 Parte del lavoro dell'architettura software consiste nel determinare quali schemi devono essere adottati nella progettazione. In genere si tratta di un'attività in corso, poiché i nuovi modelli e miglioramenti a modelli esistenti verranno individuati nel corso del progetto. È utile organizzare il piano di sviluppo in modo da esercitarsi con ognuno degli schemi progettuali principali in una fase iniziale.  
  
 La maggior parte degli schemi progettuali può essere parzialmente incorporata nel codice del framework. Parte del modello può essere ridotto per richiedere agli sviluppatori di usare particolari classi o componenti, ad esempio un livello di accesso ai database che assicura che il database venga gestito correttamente.  
  
 Uno schema progettuale viene descritto in un documento e in genere include le seguenti parti:ne viene descritto in un documento e in genere include le seguenti parti:  
  
- Nome.  
  
- Descrizione del contesto in cui è applicabile. In base a quali criteri uno sviluppatore deve pensare di applicare questo modello?  
  
- Breve spiegazione del problema da risolvere.  
  
- Modello delle parti principali e relative relazioni. Potrebbe trattarsi di classi o componenti e interfacce, con associazioni e dipendenze tra di loro. Gli elementi in genere rientrano in due categorie:  
  
  - Elementi che lo sviluppatore deve replicare in ogni parte del codice in cui viene usato il modello. È possibile usare i tipi di modello per descriverli. Per altre informazioni, vedere [diagrammi caso d'uso UML: informazioni di riferimento](../modeling/uml-use-case-diagrams-reference.md).  

  - Elementi che descrivono le classi di framework che lo sviluppatore deve usare.  
  
- Modello delle interazioni tra le parti, usando i diagrammi di sequenza o di attività.  
  
- Convenzioni di denominazione.  
  
- Descrizione di come il modello risolve il problema.  
  
- Descrizione delle variazioni che gli sviluppatori potrebbero essere in grado di adottare.  
  
## <a name="see-also"></a>Vedere anche  
 [Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Visualizzare il codice](../modeling/visualize-code.md)   
 [Modellare i requisiti utente](../modeling/model-user-requirements.md)   
 [Sviluppare test da un modello](../modeling/develop-tests-from-a-model.md)   
 [Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)
