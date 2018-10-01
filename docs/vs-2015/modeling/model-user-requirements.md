---
title: Modellare i requisiti dell'utente | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- requirements
- stories
- UML, modeling requirements
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 30
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1e7628db84a8f7515dfdf3ba9110ce1183751d8d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529720"
---
# <a name="model-user-requirements"></a>Modellare i requisiti utente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [modellare i requisiti utente](https://docs.microsoft.com/visualstudio/modeling/model-user-requirements).  
  
Visual Studio facilita la comprensione, la discussione e la comunicazione delle esigenze degli utenti mediante la creazione di diagrammi delle attività e del ruolo che il sistema svolge per il raggiungimento degli obiettivi. Un modello di requisiti è un set di tali diagrammi, ognuno dei quali è incentrato su un aspetto diverso delle esigenze degli utenti. Per una dimostrazione video, vedere: [Modellazione del dominio aziendale](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/).  
  
 Per vedere quali versioni di Visual Studio supportano ogni tipo di modello, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Un modello di requisiti consente di:  
  
-   Concentrarsi sul comportamento esterno del sistema, indipendentemente dalla progettazione interna.  
  
-   Descrivere le esigenze di utenti e parti interessate con molta meno ambiguità rispetto al linguaggio naturale.  
  
-   Definire un glossario di termini coerente che possa essere usato da utenti, sviluppatori e tester.  
  
-   Ridurre gap e incoerenze nei requisiti.  
  
-   Ridurre il lavoro necessario per rispondere alle modifiche dei requisiti.  
  
-   Pianificare l'ordine in cui verranno sviluppate le funzionalità.  
  
-   Usare i modelli come base per i test di sistema, evidenziando una chiara relazione tra test e requisiti. Quando i requisiti cambiano, questa relazione consente di aggiornare i test correttamente, garantendo in tal modo che il sistema soddisfi i nuovi requisiti.  
  
 Un modello di requisiti offre un vantaggio maggiore se viene usato per concentrare le discussioni con gli utenti o i relativi rappresentanti e se viene riesaminato all'inizio di ogni iterazione. Non è necessario completarlo in dettaglio prima di scrivere il codice. Un'applicazione parzialmente funzionante, anche se molto semplificata, crea in genere una base di discussione dei requisiti con gli utenti molto più stimolante. Il modello consente di riepilogare in modo efficace i risultati di tali discussioni. Per altre informazioni, vedere [usare i modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md).  
  
> [!NOTE]
>  In questi argomenti con "sistema" si intende il sistema o l'applicazione che si sta sviluppando. Potrebbe essere un'ampia raccolta di molti componenti software e hardware, una singola applicazione o un componente software all'interno di un sistema più grande. In ogni caso il modello di requisiti descrive il comportamento visibile dall'esterno del sistema, che sia tramite un'interfaccia utente o tramite un'API.  
  
## <a name="common-tasks"></a>Attività comuni  
 È possibile creare molte visualizzazioni diverse dei requisiti degli utenti.  Ogni visualizzazione fornisce un determinato tipo di informazioni.  Quando si creano queste visualizzazioni, è consigliabile spostarsi frequentemente dall'una all'altra. È possibile iniziare da qualsiasi visualizzazione.  
  
|Diagramma o documento|Informazioni descritte in un modello di requisiti|Sezione|  
|-------------------------|-----------------------------------------------|-------------|  
|Diagramma caso di utilizzo|Utenti che usano il sistema e le relative attività svolte.|[Che descrive come viene usato il sistema](#UseCases)|  
|Diagramma classi concettuali|Glossario dei tipi usati per descrivere i requisiti, ovvero dei tipi visibili nell'interfaccia del sistema.|[Definizione dei termini usati per descrivere i requisiti](#RequirementsClasses)|  
|Diagramma di attività|Flusso di lavoro e informazioni tra le attività eseguite dagli utenti e dal sistema o dalle relative parti.|[Che mostra il flusso di lavoro tra gli utenti e il sistema](#Workflow)|  
|Diagramma sequenza|Sequenza di interazioni tra gli utenti e il sistema o le relative parti. Una visualizzazione alternativa al diagramma di attività.|[Visualizzazione delle interazioni tra utenti e del sistema](#Sequences)|  
|Documenti o elementi di lavoro aggiuntivi|Criteri di prestazioni, sicurezza, usabilità e affidabilità.|[Descrizione dei requisiti di qualità del servizio](#QoSRequirements)|  
|Documenti o elementi di lavoro aggiuntivi|Regole e vincoli non specifici di un particolare caso di utilizzo|[Visualizzazione delle regole di business](#BusinessRules)|  
  
 La maggior parte dei tipi di diagrammi può essere usata per altri scopi. Per una panoramica dei tipi di diagramma, vedere [creare modelli per l'app](../modeling/create-models-for-your-app.md). Per informazioni di base sulla creazione dei diagrammi, vedere [modelli e diagrammi UML modifica](../modeling/edit-uml-models-and-diagrams.md).  
  
##  <a name="UseCases"></a> Che descrive come viene usato il sistema  
 Creare diagrammi caso di utilizzo per descrivere chi usa il sistema e le relative attività svolte. Un caso di utilizzo rappresenta un obiettivo di un utente del sistema e la procedura eseguita per raggiungere l'obiettivo.  
  
 Si consideri ad esempio un sistema di vendita di pasti online che deve consentire ai clienti di scegliere elementi da un menu e ai ristoranti di aggiornare il menu. È possibile riepilogare questa condizione in un diagramma caso di utilizzo:  
  
 ![Casi d'uso per cliente e il ristorante](../modeling/media/uml-reqmuc1.png "UML_ReqmUC1")  
  
 È anche possibile illustrare come un caso di utilizzo sia costituito da casi più piccoli. Ad esempio, l'ordinazione di un pasto fa parte del processo di acquisto di un pasto, che comprende anche il pagamento e la consegna:  
  
 ![Il sistema partecipa al pagamento ma non al recapito. ](../modeling/media/uml-reqmuc2.png "UML_ReqmUC2")  
  
 È anche possibile illustrare i casi di utilizzo inclusi nell'ambito del sistema che si sta sviluppando. Ad esempio, il sistema raffigurato nell'illustrazione non fa parte del caso di utilizzo Consegna pasto. In questo modo è possibile impostare il contesto per il lavoro di sviluppo. In un diagramma caso di utilizzo i contenitori del sottosistema possono essere usati per rappresentare il sistema o i relativi componenti.  
  
 Consente inoltre al team di discutere su cosa includere nelle versioni successive. Ad esempio è possibile discutere se, nella versione iniziale del sistema, il pagamento pasto viene concluso direttamente tra il ristorante e il cliente invece di passare attraverso il sistema. In questo caso è possibile spostare il pagamento pasto all'esterno del rettangolo del Sistema Dinner Now per la versione iniziale.  
  
 Un diagramma caso di utilizzo fornisce solo un riepilogo dei casi di utilizzo. Per fornire descrizioni più dettagliate, si possono collegare i casi di utilizzo nel diagramma a documenti separati e ad altri diagrammi. Per informazioni su come eseguire questa operazione, vedere [collegare un caso d'uso a documenti e diagrammi](../modeling/link-a-use-case-to-documents-and-diagrams.md).  
  
 La creazione di un diagramma caso di utilizzo consente al team di:  
  
-   Concentrarsi sulle attività che gli utenti prevedono di eseguire con il sistema, senza farsi distrarre dai dettagli dell'implementazione.  
  
-   Discutere l'ambito del sistema o le particolari versioni del sistema.  
  
 Per altre informazioni, vedere gli argomenti seguenti:  
  
|Informazioni|Vedere|  
|--------------------|----------|  
|Informazioni più dettagliate su come creare casi di utilizzo|[Diagrammi casi d'uso UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Elementi in un diagramma caso di utilizzo|[Diagrammi casi d'uso UML: riferimento](../modeling/uml-use-case-diagrams-reference.md)|  
|Come sviluppare codice dai casi di utilizzo|[Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="RequirementsClasses"></a> Definizione dei termini usati per descrivere i requisiti  
 È possibile usare i diagrammi classi UML per sviluppare un vocabolario coerente dei concetti aziendali utilizzati per gli scopi seguenti:  
  
-   Dagli utenti stessi per presentare l'azienda in cui il sistema è in funzione.  
  
-   Per descrivere le esigenze degli utenti, ad esempio nelle descrizioni di casi di utilizzo, regole di business e storie degli utenti.  
  
-   I tipi di informazioni scambiate mediante l'API del sistema o l'interfaccia utente.  
  
-   Descrizioni di test di sistema o di accettazione.  
  
 Quando è usato per questo scopo, il contenuto di un diagramma classi UML viene denominato diagramma classi concettuali. È noto anche come *modello di dominio* o *modello di classe di analisi*.  
  
 In un diagramma classi concettuali vengono illustrate solo le classi richieste nelle descrizioni dei requisiti, senza illustrare alcun dettaglio della progettazione interna del sistema. Il diagramma non illustra alcun dettaglio della progettazione interna del sistema. Nelle classi concettuali non si rappresentano in genere operazioni o interfacce.  
  
 Provare ad esempio a creare le classi concettuali per il sistema Dinner Now:  
  
 ![Menu delle classi, ordine, voce di Menu, elemento ordine. ](../modeling/media/uml-reqmcd1.png "UML_ReqMCD1")  
  
 Un diagramma classi concettuali fornisce il vocabolario dei termini usati in tutto il modello dei requisiti. Ad esempio, nella descrizione dettagliata del caso di utilizzo Ordinazione pasto, è possibile scrivere:  
  
 Il cliente sceglie un *Menu* da cui creare un *Ordine*, quindi crea gli *Elementi ordine* nell' *Ordine* selezionando *Elementi menu* dal *Menu*.  
  
 Si noti che i termini utilizzati nella descrizione sono nomi di classi del modello. Il diagramma rimuove le ambiguità dalle relazioni tra le classi. Ad esempio, mostra chiaramente che a ogni Ordine è associato un solo Menu.  
  
 I malintesi sui requisiti degli utenti spesso possono essere attribuiti ai malintesi sui significati dettagliati delle parole. Ad esempio, la maggior parte dei ristoranti sarà d'accordo sul significato dei termini Menu e Ordine, ma la differenza tra un elemento di un Ordine e un elemento di un Menu potrebbe essere meno chiara. Quando i requisiti vengono discussi con le parti interessate dell'azienda, è importante esporre queste differenze. Il diagramma classi è uno strumento utile per chiarire i termini e le relative relazioni.  
  
 Il modello di classi concettuali può formare il vocabolario di base con cui può essere descritta la logica di business del sistema. Tuttavia, le classi nel software sono in genere molto più complesse del modello concettuale, perché l'implementazione deve considerare problemi quali prestazioni, distribuzione, flessibilità e altri fattori. Spesso in un unico sistema sono presenti diverse implementazioni di una classe concettuale.  
  
 Ad esempio, gli Ordini potrebbero essere rappresentati in XML, SQL, HTML e C# in diverse parti del sistema e in diverse interfacce tra le parti. L'associazione tra un Ordine e un Menu potrebbe essere rappresentata in molti modi diversi, ad esempio con riferimenti all'interno del codice C#, con relazioni in un database o con ID a riferimenti incrociati nel codice XML. Nonostante queste variazioni, il modello concettuale fornisce informazioni importanti che sono reali in ogni parte del software. Il diagramma classi nell'esempio indica che in ogni implementazione ci sarà solo un Menu associato a ogni Ordine.  
  
 La creazione di un diagramma classi dei requisiti consente al team di:  
  
-   Definire e standardizzare i termini di base usati nelle discussioni sulle esigenze degli utenti.  
  
-   Chiarire le relazioni tra questi termini.  
  
 Per altre informazioni, vedere gli argomenti seguenti:  
  
|Informazioni|Lettura|  
|--------------------|----------|  
|Altre informazioni su come trovare le classi di requisiti|[Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)|  
|Elementi in un diagramma classi concettuali|[Diagrammi classi UML: riferimento](../modeling/uml-class-diagrams-reference.md)|  
|Come sviluppare codice dalle classi concettuali|[Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)|  
  
 In un diagramma classi concettuali non è in genere utile posizionare le frecce sulle associazioni per rappresentare l'esplorabilità. Ciò è dovuto al fatto che il diagramma non rappresenta un'implementazione. Le associazioni rappresentano le relazioni tra oggetti reali. Quanto segue [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensione per rendere le frecce sono non direzionali il valore predefinito: [esempio: funzionalità modellazione di domini UML](http://go.microsoft.com/fwlink/?LinkId=213849).  
  
##  <a name="BusinessRules"></a> Showing Business Rules  
 Una regola di business è un requisito non associato a un particolare caso di utilizzo e deve essere osservata in tutto il sistema.  
  
 Molte regole di business sono vincoli sulle relazioni tra le classi concettuali. È possibile scrivere queste *statici * * le regole di business* come commenti associati alle relative classi di un diagramma classi concettuali. Ad esempio:  
  
 ![Regola nel commento associato alla classe Order. ](../modeling/media/uml-reqmcd2.png "UML_ReqmCD2")  
  
 Le*regole di business dinamiche* vincolano le sequenze di eventi consentite. È possibile ad esempio usare un diagramma di attività o di sequenza per mostrare che un utente deve accedere prima di eseguire altre operazioni nel sistema.  
  
 Tuttavia, molte regole dinamiche possono essere illustrate più efficacemente e genericamente sostituendole con regole statiche. Ad esempio è possibile aggiungere un attributo booleano "Connesso" in una classe del modello di classi concettuali. L'attributo Connesso viene aggiunto come postcondizione della registrazione nel caso di utilizzo e come precondizione della maggior parte degli altri casi di utilizzo. Questo approccio consente di evitare di definire tutte le combinazioni possibili di sequenze di eventi. È anche più flessibile quando è necessario aggiungere nuovi casi di utilizzo al modello.  
  
 Si noti che la scelta in questo caso riguarda la modalità di definizione dei requisiti ed è indipendente dal modo in cui vengono implementati i requisiti nel codice programma.  
  
 Per altre informazioni, vedere gli argomenti seguenti:  
  
|Informazioni|Lettura|  
|--------------------|----------|  
|Altre informazioni su come trovare e registrare regole di business statiche|[Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)|  
|Elementi in un diagramma classi concettuali|[Diagrammi classi UML: riferimento](../modeling/uml-class-diagrams-reference.md)|  
|Come sviluppare codice che soddisfi le regole di business|[Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="QoSRequirements"></a> Describing Quality of Service Requirements  
 Esistono diverse categorie di requisiti per la qualità del servizio. Di seguito vengono forniti alcuni esempi:  
  
-   Prestazioni  
  
-   Sicurezza  
  
-   Usabilità  
  
-   Affidabilità  
  
-   Efficienza  
  
 È possibile includere alcuni di questi requisiti nelle descrizioni di casi di utilizzo specifici. Gli altri requisiti non sono specifici dei casi di utilizzo e vengono scritti più efficacemente in un documento separato. Quando possibile, è utile rispettare il vocabolario definito dal modello di requisiti. Nell'esempio seguente le parole principali usate nel requisito sono i titoli di attori, casi di utilizzo e classi delle illustrazioni precedenti:  
  
 Se un Ristorante elimina un Elemento menu mentre un Cliente ordina un pasto, tutti gli Elementi ordine che fanno riferimento all'Elemento menu verranno visualizzati in rosso.  
  
 Per altre informazioni, vedere gli argomenti seguenti:  
  
|Informazioni|Lettura|  
|--------------------|----------|  
|Altre informazioni sulla registrazione dei requisiti di qualità del servizio|[Linee guida per la definizione dei requisiti di qualità del servizio](http://msdn.microsoft.com/en-us/9677a437-c2cb-4ac4-8c2d-4e3350005f06)|  
|Associazione di documenti aggiuntivi ai casi di utilizzo|[Collegare un caso d'uso a documenti e diagrammi](../modeling/link-a-use-case-to-documents-and-diagrams.md)|  
|Come sviluppare codice che soddisfi i requisiti di qualità del servizio|[Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Workflow"></a> Che mostra il flusso di lavoro tra gli utenti e il sistema  
 È possibile usare un diagramma di attività per mostrare il flusso di lavoro tra diversi casi di utilizzo. Spesso è utile iniziare un modello di requisiti creando un diagramma di attività che illustri le attività principali eseguite dagli utenti, sia con il sistema che all'esterno.  
  
 Ad esempio:  
  
 ![Attività con tre azioni e un ciclo. ](../modeling/media/uc-reqmwfact.png "UC_ReqmWFAct")  
  
 È possibile creare diagrammi caso di utilizzo e diagrammi di attività per mostrare visualizzazioni diverse delle stesse informazioni.  Il diagramma caso di utilizzo è più efficace perché mostra l'annidamento delle azioni più piccole all'interno dell'attività più grande, ma non mostra il flusso di lavoro. Ad esempio:  
  
 ![Casi d'uso per le azioni precedenti](../modeling/media/uml-reqmwfuc.png "UML_ReqmWFUC")  
  
 Si noti che è possibile usare i diagrammi di attività anche per rappresentare gli algoritmi all'interno del software, ma quando si usano i diagrammi per il processo aziendale, l'attenzione è incentrata sulle azioni visibili all'esterno del sistema.  
  
 Per altre informazioni, vedere gli argomenti seguenti:  
  
|Informazioni|Lettura|  
|--------------------|----------|  
|Altre informazioni sulla definizione di flussi di lavoro aziendali|[Diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md)|  
|Elementi in un diagramma di attività|[Diagrammi di attività UML: riferimento](../modeling/uml-activity-diagrams-reference.md)|  
|Come sviluppare codice dai diagrammi di attività|[Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Sequences"></a> Visualizzazione delle interazioni tra utenti e del sistema  
 È possibile usare un diagramma di sequenza per mostrare l'interscambio di messaggi tra il sistema e gli attori esterni o tra le parti del sistema. In questo modo vengono visualizzati i passaggi di un caso di utilizzo che mostra molto chiaramente la sequenza di interazioni. I diagrammi di sequenza sono particolarmente utili nelle situazioni in cui sono presenti molte parti che interagiscono tra di loro in un caso di utilizzo e anche quando nel sistema è disponibile un'API.  
  
 Ad esempio:  
  
 ![Diagramma di sequenza con sistema e attori. ](../modeling/media/uml-reqmseq.png "UML_ReqmSeq")  
  
 Un vantaggio dei diagrammi di sequenza è dato dal fatto che è facile vedere quali messaggi arrivano al sistema che si sta creando. Per progettare il sistema, è possibile sostituire la singola linea di vita del sistema con una linea di vita separata per ognuno dei componenti e quindi mostrare le interazioni tra di essi in risposta a ogni messaggio in arrivo.  
  
 Per altre informazioni, vedere gli argomenti seguenti:  
  
|Informazioni|Lettura|  
|--------------------|----------|  
|Altre informazioni sulla definizione delle interazioni|[Diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Elementi in un diagramma di sequenza|[Diagrammi di sequenza UML: riferimenti](../modeling/uml-sequence-diagrams-reference.md)|  
|Come sviluppare codice dai diagrammi di sequenza|[Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="using-a-model-to-reduce-inconsistencies"></a>Uso di un modello per ridurre le incoerenze  
 La creazione di un modello comporta generalmente una riduzione significativa di incoerenze e ambiguità nei requisiti degli utenti. Le diverse parti interessate danno in genere diverse interpretazioni dell'ambiente aziendale in cui viene usato il sistema. La prima attività consiste quindi nel risolvere queste differenze tra i clienti.  
  
 Molte domande sul dominio aziendale si presenteranno naturalmente durante la creazione di un modello. Ponendo agli utenti alcune domande specifiche, si ridurrà la necessità di modifiche in una fase successiva del progetto. Di seguito sono riportate alcune domande specifiche da porre innanzitutto a se stessi e quindi alle parti interessate all'interno dell'azienda se la risposta è poco chiara:  
  
-   Chiedere "Quale caso di utilizzo crea istanze di questa classe?" per ogni classe del modello di requisiti. Si potrebbe chiedere, ad esempio, "Quale caso di utilizzo crea istanze della classe Menu ristorante?" in un servizio di ordinazione pasti online. Questa domanda porta ad esaminare in che modo un nuovo ristorante si iscrive al servizio e fornisce il proprio menu. È possibile porre domande simili sugli elementi che creano o modificano gli attributi e le associazioni.  
  
-   Per ogni caso di utilizzo del modello di requisiti provare a descrivere il risultato o la postcondizione con le parole fornite dai diagrammi classi. Spesso è utile mostrare l'effetto di un caso di utilizzo delineando le istanze delle classi prima e dopo il verificarsi del caso di utilizzo. Se ad esempio la postcondizione del caso di utilizzo indica che "un elemento menu viene aggiunto all'ordine cliente", delineare istanze delle classi Ordine ed Elemento menu. Mostrare gli effetti del caso di utilizzo, ad esempio un nuovo collegamento o un nuovo oggetto, con un colore diverso o un nuovo disegno. Questi elementi avviano spesso discussioni sulle informazioni che è necessario includere nel modello. Anche se le classi di requisiti non riguardano direttamente l'implementazione, descrivono le informazioni che il sistema dovrà archiviare e trasmettere.  
  
-   Porre domande sui vincoli per attributi e associazioni, soprattutto per i vincoli che riguardano più attributi o associazioni.  
  
-   Porre domande sulle sequenze valide e non valide dei casi di utilizzo, creando diagrammi di sequenza o di attività per illustrarle.  
  
 Esaminando le relazioni tra le visualizzazioni fornite dai diversi diagrammi, è possibile comprendere rapidamente i concetti principali usati dagli utenti e aiutarli a comprendere ciò che hanno l'esigenza di ottenere dal sistema. È anche possibile ottenere una migliore comprensione dei requisiti di cui le parti interessate sono meno sicure. È possibile pianificare lo sviluppo di queste funzionalità, almeno in formato semplice nella fase iniziale del progetto, per permettere agli utenti di sperimentarle.  
  
## <a name="see-also"></a>Vedere anche  
 [Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Sviluppare test da un modello](../modeling/develop-tests-from-a-model.md)   
 [Usare i modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)   
 [Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)   
 [Estensione di Visual Studio di esempio: Le funzionalità modellazione di domini UML](http://go.microsoft.com/fwlink/?LinkId=213849)   
 [Estensione di Visual Studio di esempio: Colorazione di elementi UML per stereotipo](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [Estensione di Visual Studio di esempio: Collegamento di elementi UML a diagrammi, file e altri elementi](http://go.microsoft.com/fwlink/?LinkID=213813)   
 [Estensione di Visual Studio di esempio: Allineare le forme in un diagramma UML](http://go.microsoft.com/fwlink/?LinkID=213809)   
 [Video: Modellazione del dominio aziendale](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/)



