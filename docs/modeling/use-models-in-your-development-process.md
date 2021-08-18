---
title: Usare modelli nel processo di sviluppo
description: In questo Visual Studio è possibile usare un modello per comprendere e modificare un sistema, un'applicazione o un componente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, using models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 910aa4d25325ac6498e941bbba3a1a6d7ee2f957
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033993"
---
# <a name="use-models-in-your-development-process"></a>Usare modelli nel processo di sviluppo

In Visual Studio è possibile usare un modello che consenta di comprendere e modificare un sistema, un'applicazione o un componente. Un modello consente di visualizzare l'ambiente in cui opera il sistema, chiarire le esigenze degli utenti, definire l'architettura del sistema, analizzare il codice e assicurarsi che soddisfi i requisiti. Vedere [Channel 9 Video: Improve architecture through modeling (Video di Channel 9: migliorare l'architettura tramite la modellazione).](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)

Per vedere quali versioni di Visual Studio supportano ogni tipo di modello, vedere [Version support for architecture and modeling tools](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

I modelli possono essere di supporto all'utente in vari modi:

- La creazione dei diagrammi di modellazione consente di chiarire i concetti coinvolti nei requisiti, nell'architettura e nella progettazione di alto livello. Per altre informazioni, vedere [Modellare i requisiti utente.](../modeling/model-user-requirements.md)

- L'utilizzo di modelli consente di mettere in evidenza le incoerenze dei requisiti.

- La comunicazione con i modelli consente di comunicare concetti importanti in modo meno ambiguo rispetto al linguaggio naturale. Per altre informazioni, vedere [Modellare l'architettura dell'app.](../modeling/model-your-app-s-architecture.md)

- In alcuni casi, è possibile usare modelli per generare codice o altri elementi quali documenti o schemi di database. Ad esempio, i componenti di modellazione Visual Studio vengono generati da un modello. Per altre informazioni, vedere [Generare e configurare l'app dai modelli.](../modeling/generate-and-configure-your-app-from-models.md)

È possibile usare modelli in un'ampia gamma di processi da procedure estremamente agili a quelle più complesse.

## <a name="use-models-to-reduce-ambiguity"></a>Usare i modelli per ridurre l'ambiguità

Il linguaggio di modellazione è meno ambiguo del linguaggio naturale ed è progettato per esprimere idee in genere necessarie durante lo sviluppo di software.

Se per il progetto è disponibile un piccolo team che segue procedure agili, è possibile usare i modelli per chiarire le storie utente. Nelle discussioni con il cliente riguardo alle sue esigenze, la creazione di un modello può generare domande utili molto più rapidamente e in un'area più ampia del prodotto rispetto alla scrittura di codice di picco o di prototipi.

Se il progetto è grandi dimensioni e coinvolge team in diverse parti del mondo, è possibile usare i modelli per comunicare i requisiti e l'architettura in modo molto più efficace rispetto all'uso di testo normale.

In entrambi i casi la creazione di un modello quasi sempre comporta una riduzione significativa di incoerenze e ambiguità. Le diverse parti interessate frequentemente hanno percezioni diverse del mondo aziendale in cui funziona il sistema e sviluppatori diversi spesso hanno percezioni diverse della modalità di funzionamento del sistema. L'utilizzo di un modello come elemento attivo di una discussione generalmente rivela queste differenze. Per altre informazioni su come usare un modello per ridurre le incoerenze, vedere Modellare i [requisiti utente.](../modeling/model-user-requirements.md)

## <a name="use-models-with-other-artifacts"></a>Usare modelli con altri artefatti

Un modello non è da solo una specifica dei requisiti o un'architettura. È uno strumento per esprimere alcuni aspetti di questi elementi in modo più chiaro, ma non è possibile esprimere tutti i concetti necessari durante la progettazione del software. I modelli devono quindi essere usati insieme ad altri mezzi di comunicazione, ad esempio pagine o paragrafi di OneNote, documenti Microsoft Office, elementi di lavoro in Team Foundation o note sulla pareti della stanza del progetto. Tranne l'ultimo elemento, tutti i tipi di oggetto possono essere collegati alle parti di elementi del modello.

Di seguito sono riportati altri aspetti della specifica che in genere vengono usati con i modelli. A seconda della scala e dello stile del progetto, è possibile usare diversi di questi aspetti o non usarli affatto:

- Storie utente. Una storia utente è una breve descrizione, discussa con utenti e altre parti interessate, di un aspetto del comportamento del sistema che verrà recapitata in una delle iterazioni del progetto. Una storia utente tipica inizia "Il cliente sarà in grado di..." Una storia utente può introdurre un gruppo di casi d'uso o definire estensioni dei casi di utilizzo sviluppati in precedenza. La definizione o l'estensione di casi di utilizzo consente di rendere la storia utente più chiara.

- Richieste di modifica. Una richiesta di modifica in un progetto più formale è molto simile a una storia utente in un progetto agile. Nell'approccio agile tutti i requisiti vengono considerati modifiche a ciò che è stato sviluppato in iterazioni precedenti.

- Descrizione del caso di utilizzo. Un caso di utilizzo rappresenta uno dei modi in cui un utente interagisce con il sistema per raggiungere un obiettivo specifico. Una descrizione completa include l'obiettivo, sequenze principali e alternative di eventi e risultati eccezionali. Un diagramma caso di utilizzo consente di riepilogare e fornire una panoramica dei casi di utilizzo.

- Scenari. Uno scenario è una descrizione piuttosto dettagliata di una sequenza di eventi che mostrano come il sistema, gli utenti e altri sistemi funzionano insieme per fornire valore alle parti interessate. Potrebbe avere l'aspetto di una presentazione dell'interfaccia utente o di un prototipo dell'interfaccia utente. Può descrivere un caso di utilizzo o una sequenza di casi di utilizzo.

- Glossario. Il glossario dei requisiti del progetto descrivono le parole con cui i clienti discutono in merito al proprio mondo. I modelli di requisiti e interfaccia utente devono usare anche questi termini. Un diagramma classi può chiarire le relazioni tra la maggior parte di questi termini. La creazione dei diagrammi e del glossario non solo riduce malintesi tra utenti e sviluppatori, ma quasi sempre evidenzia anche malintesi tra le diverse parti aziendali interessate.

- Regole di business. Molte regole di business possono essere espresse come vincoli invariabili sulle associazioni e sugli attributi nel modello di classi di requisiti e come vincoli sui diagrammi di sequenza.

- Progettazione ad alto livello. Vengono descritte le parti principali e come interagiscono. I diagrammi dei componenti, di sequenza e interfaccia costituiscono una parte importante di un progetto di alto livello.

- Schemi progettuali. Vengono descritte le regole di progettazione che vengono condivise tra diverse parti del sistema.

- Specifiche di test. Gli script di test e le progettazioni per il codice di test possono avvalersi dei diagrammi di sequenza e di attività per descrivere le sequenze dei passi di test. I test di sistema devono essere espressi in termini di modello requisiti in modo che sia possibile modificarli facilmente quando cambiano i requisiti.

- Piano del progetto. Il piano del progetto o il backlog definisce quando verrà recapitata ogni funzionalità. È possibile definire ogni funzionalità dichiarando quali casi di utilizzo e regole di business vengono implementate o estese. È possibile fare riferimento ai casi di utilizzo e alle regole di business direttamente nel piano oppure è possibile definire un set di funzionalità in un documento separato e usare i titoli delle funzionalità nel piano.

## <a name="use-models-in-iteration-planning"></a>Usare i modelli nella pianificazione delle iterazioni

Anche se tutti i progetti sono diversi nella scala e nell'organizzazione, un progetto tipico è pianificato come una serie di iterazioni compresa tra due e sei settimane. È importante pianificare sufficienti iterazioni per consentire il feedback delle iterazioni precedenti da usare per regolare l'ambito e i piani per iterazioni successive.

I suggerimenti seguenti possono risultare utili per realizzare i vantaggi della modellazione in un progetto iterativo.

### <a name="sharpen-focus-as-each-iteration-approaches"></a>Affilare lo stato attivo con l'avvicinarsi di ogni iterazione

All'approcciarsi di ogni iterazione, è possibile usare modelli per definire cosa deve essere consegnato alla fine dell'iterazione.

- Non modellare tutto in dettaglio nelle prime iterazioni. Nella prima iterazione creare un diagramma classi per gli elementi principali nel glossario dell'utente, creare un diagramma dei casi di utilizzo principali e creare un diagramma dei componenti principali. Non descrivere nessuno di questi elementi dettagliatamente perché i dettagli verranno modificati in un secondo momento nel progetto. Usare i termini definiti in questo modello per creare un elenco di funzionalità o storie utente principali. Assegnare le funzionalità alle iterazioni in modo da bilanciare approssimativamente il carico di lavoro stimato nel corso del progetto. Queste assegnazioni verranno modificate in un secondo momento nel progetto.

- Provare a implementare versioni semplificate di tutti i casi di utilizzo più importanti in una prima iterazione. Estendere i casi di utilizzo in iterazioni successive. Questo approccio consente di ridurre il rischio di individuare un difetto nei requisiti o nell'architettura del progetto troppo tardi per poter fare qualcosa a riguardo.

- Verso la fine di ogni iterazione indire un workshop dei requisiti per definire in dettaglio i requisiti o le storie utente che verranno sviluppate nell'iterazione successiva. Invitare gli utenti e le parti interessate dell'azienda che sono in grado di decidere le priorità, nonché gli sviluppatori e i tester di sistema. Vengono consentite tre ore per definire i requisiti per un'iterazione di 2 settimane.

- Per ogni partecipante l'obiettivo del workshop è accettare ciò che verrà effettuato entro la fine dell'iterazione successiva. Usare i modelli come uno degli strumenti che consentono di chiarire i requisiti. L'output del workshop è un backlog di iterazione, ad esempio un elenco di attività di sviluppo in Team Foundation e gruppi di test in [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] .

- Nel workshop dei requisiti discutere la progettazione solo nella misura in cui è necessario determinare le stime per le attività di sviluppo. In caso contrario, discutere sul comportamento del sistema che gli utenti possono sperimentare direttamente. Mantenere il modello requisiti separato dal modello dell'architettura.

- Le parti interessate non tecniche in genere non hanno problemi a comprendere i diagrammi UML con alcune indicazioni da parte dell'utente.

### <a name="link-model-to-work-items"></a>Collegare il modello agli elementi di lavoro

Dopo il workshop di requisiti, elaborare i dettagli del modello requisiti e collegare il modello alle attività di sviluppo. È possibile eseguire questa operazione collegando gli elementi di lavoro in Team Foundation agli elementi del modello.

È possibile collegare qualsiasi elemento agli elementi di lavoro, ma quelli più utili sono i seguenti:

- Commenti che descrivono i requisiti delle regole di business o della qualità del servizio. Per altre informazioni, vedere [Modellare i requisiti utente.](../modeling/model-user-requirements.md)

### <a name="link-model-to-tests"></a>Collegare il modello ai test

Usare il modello requisiti per guidare la progettazione dei test di accettazione. Creare questi test contemporaneamente al lavoro di sviluppo.

Per altre informazioni su questa tecnica, vedere [Sviluppare test da un modello.](../modeling/develop-tests-from-a-model.md)

### <a name="estimate-remaining-work"></a>Stimare il lavoro rimanente

Un modello requisiti può agevolare la stima delle dimensioni totali del progetto rispetto alle dimensioni di ogni iterazione. La valutazione del numero e della complessità delle classi e dei casi di utilizzo agevolano la stima del lavoro di sviluppo che sarà necessario. Quando sono state completate le prime iterazioni, un confronto dei requisiti analizzati e di quelli ancora da analizzare può fornire un'indicazione approssimativa del costo e dell'ambito della parte restante del progetto.

Verso la fine di ogni iterazione, rivedere l'assegnazione dei requisiti per le iterazioni future. Può essere utile rappresentare lo stato del software alla fine di ogni iterazione come un sottosistema in un diagramma caso di utilizzo. Nelle discussioni è possibile spostare i casi di utilizzo e usare le estensioni da uno di questi sottosistemi a un altro.

## <a name="levels-of-abstraction"></a>Livelli di astrazione

I modelli dispongono di un intervallo di astrazione in relazione al software. I modelli più concreti rappresentano direttamente il codice di programma e quelli più astratti rappresentano i concetti di business che possono o non possono essere rappresentati nel codice.

È possibile visualizzare un modello tramite diversi tipi di diagrammi. Per informazioni sui modelli e i diagrammi, vedere [Creare modelli per l'app.](../modeling/create-models-for-your-app.md)

Diversi tipi di diagramma sono utili per descrivere la progettazione a diversi livelli di astrazione. Molti tipi di diagramma sono utili più livelli. Questa tabella mostra come usare ogni tipo di diagramma.

|Livello di progettazione|Tipi di diagramma|
|-|-|
|Processo aziendale<br /><br /> Le informazioni sul contesto in cui verrà usato il sistema consentono di comprendere quali sono le esigenze degli utenti.|- I diagrammi classi concettuali descrivono i concetti aziendali usati all'interno del processo aziendale.|
|Requisiti utente<br /><br /> La definizione di ciò che gli utenti richiedono al sistema.|- Le regole di business e i requisiti di qualità del servizio possono essere descritti in documenti separati.|
|Progettazione ad alto livello<br /><br /> La struttura generale del sistema: i componenti principali e la modalità con cui vengono accoppiati.|- I diagrammi delle dipendenze descrivono come il sistema è strutturato in parti interdipendenti. È possibile convalidare il codice del programma in base ai diagrammi delle dipendenze per assicurarsi che rispetti l'architettura.|
|Analisi codice<br /><br /> I diagrammi possono essere generati dal codice.|- I diagrammi delle dipendenze mostrano le dipendenze tra le classi. Il codice aggiornato può essere convalidato rispetto a un diagramma delle dipendenze.<br />- I diagrammi classi mostrano le classi nel codice.|

## <a name="external-resources"></a>Risorse esterne

|**Categoria**|**Collegamenti**|
|-|-|
|**Video**|![collegamento al video ](../data-tools/media/playvideo.gif) [MSDN How Do I Videos: How to Create and Use UML Models and Diagrams (How Do I Videos: How to Create and Use UML Models and Diagrams(](/previous-versions/visualstudio/visual-studio-2010/dd831853(v=vs.100)) Come creare e usare diagrammi e modelli UML Visual Studio 2010 Ultimate)<br /><br /> ![collegamento al video ](../data-tools/media/playvideo.gif) [Channel 9: UML con Visual Studio 2010](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-1-brainstorming-a-project)<br /><br /> ![collegamento al video ](../data-tools/media/playvideo.gif) [MSDN How Do I Series: UML Tools and Extensibility (Visual Studio 2010 Ultimate)](/previous-versions/visualstudio/visual-studio-2010/dd831853(v=vs.100))|
|**Forum**|- [Visual Studio Visualization and Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio Visualization and Modeling SDK (strumenti DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blog**|[Microsoft DevOps](https://devblogs.microsoft.com/devops/)|
|**Articoli e pubblicazioni tecniche**|[MSDN Architecture Center](/previous-versions/dn630665(v=msdn.10))|

## <a name="see-also"></a>Vedi anche

- [Usare i modelli nello sviluppo Agile](/previous-versions/ff398061(v=vs.140))
- [Creare modelli per l'app](../modeling/create-models-for-your-app.md)
- [Modellare i requisiti utente](../modeling/model-user-requirements.md)
- [Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)
- [Sviluppare test da un modello](../modeling/develop-tests-from-a-model.md)
- [Strutturare la soluzione di modellazione](../modeling/structure-your-modeling-solution.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]