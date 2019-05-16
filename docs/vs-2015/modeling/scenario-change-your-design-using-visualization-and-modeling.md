---
title: 'Scenario: Modificare la progettazione mediante visualizzazione e modellazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
ms.assetid: ccc80825-a4a0-44fa-a0bb-f95254785a3b
caps.latest.revision: 63
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dbb123b952287de0b519bfdd40b0d9a851a0b81f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686882"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scenario: Modificare la progettazione mediante gli strumenti di visualizzazione e modellazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per assicurarsi che il sistema software soddisfi le esigenze degli utenti, usare gli strumenti di visualizzazione e di modellazione in Visual Studio. Questi strumenti includono diagrammi UML (Unified Modeling Language), mappe codice, diagrammi livello e diagrammi classi per:  
  
 Per individuare le versioni di Visual Studio che supportano i singoli strumenti, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
- Definire le esigenze degli utenti e i processi aziendali.  
  
- Visualizzare ed esplorare il codice esistente.  
  
- Descrivere le modifiche a un sistema esistente.  
  
- Verificare che il sistema soddisfi i propri requisiti.  
  
- Mantenere la coerenza del codice con la progettazione.  
  
  Questa procedura dettagliata:  
  
- Descrive i possibili vantaggi di questi strumenti per un progetto software.  
  
- Illustra come usare questi strumenti, indipendentemente dall'approccio di sviluppo, con uno scenario di esempio.  
  
  Per altre informazioni su questi strumenti e sugli scenari supportati, vedere:  
  
- [Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)  
  
- [Visualizzare il codice](../modeling/visualize-code.md)  
  
- [Creare modelli per l'app](../modeling/create-models-for-your-app.md)  
  
## <a name="ScenarioOverview"></a> Panoramica dello scenario  
 Questo scenario descrive alcuni episodi dei cicli di vita di sviluppo software di due società fittizie: Dinner Now e Lucerne Publishing. Dinner Now fornisce un servizio di consegna pasti basato sul Web per l'area di Milano. I clienti possono ordinare i pasti ed effettuare il pagamento sul sito Web di Dinner Now. Gli ordini vengono quindi inviati al ristorante locale di pertinenza per la consegna. Lucerne Publishing, una società con sede a Roma, gestisce varie attività offline e sul Web. Ad esempio, gestisce un sito Web in cui i clienti possono inserire recensioni di ristoranti.  
  
 Lucerne ha recentemente acquisito Dinner Now e vuole apportare le modifiche seguenti:  
  
- Integrare i siti Web delle due società aggiungendo funzionalità di recensione dei ristoranti a Dinner Now.  
  
- Sostituire il sistema di pagamento di Dinner Now con il sistema di Lucerne.  
  
- Espandere il servizio di Dinner Now nell'area.  
  
  Dinner Now usa le metodologie SCRUM e eXtreme Programming. Dispone di un code coverage dei test molto elevato e di una quantità estremamente ridotta di codice non supportato. Per ridurre al minimo i rischi, crea versioni ridotte ma funzionali di un sistema, aggiungendo quindi le funzionalità in modo incrementale. Lo sviluppo del codice avviene sulla base di iterazioni brevi e frequenti. Ciò consente all'azienda di gestire le modifiche nella massima sicurezza, di effettuare spesso il refactoring del codice ed evitare un eccessivo impegno iniziale di scrittura del codice.  
  
  Lucerne gestisce un insieme di sistemi molto più ampio e complesso, alcuni dei quali risalenti a oltre 40 anni fa. Le modifiche vengono apportate con estrema cautela a causa della complessità e dell'ambito del codice legacy. Segue un processo di sviluppo più rigoroso, in cui si preferisce progettare soluzioni dettagliate e documentare la progettazione e le modifiche apportate durante lo sviluppo.  
  
  Entrambi i team usano i diagrammi di modellazione in Visual Studio per sviluppare sistemi che soddisfino le esigenze degli utenti. Usano Team Foundation Server insieme ad altri strumenti per pianificare, organizzare e gestire il lavoro.  
  
  Per altre informazioni su Team Foundation Server, vedere:  
  
- [Pianificazione e traccia del lavoro](#PlanningTracking)  
  
- [Test, convalida e archiviazione del codice aggiornato](#TestValidateCheckInCode)  
  
## <a name="ModelingDiagramsTools"></a> Ruoli dei diagrammi dell'architettura e della modellazione nello sviluppo del software  
 La tabella seguente descrive i ruoli che questi strumenti possono svolgere in diverse fasi del ciclo di vita dello sviluppo del software.  
  
||**Modellazione dei requisiti utente**|**Modellazione dei processi aziendali**|**Architettura e progettazione di sistemi**|**Visualizzazione ed esplorazione del codice**|**Verifica**|  
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|  
|Diagramma caso di utilizzo (UML)|√|√|||√|  
|Diagramma di attività (UML)|√|√|√||√|  
|Diagramma classi (UML)|√|√|√||√|  
|Diagramma dei componenti (UML)|√|√|√||√|  
|Diagramma di sequenza (UML)|√|√|√||√|  
|Diagramma DSL (Domain-Specific Language)|√|√|√|||  
|Diagramma livello, convalida dei livelli|||√|√|√|  
|Mappa codice|||√|√|√|  
|Progettazione classi (basata su codice)||||√||  
  
 Per creare diagrammi UML e diagrammi livello, è necessario creare un progetto di modellazione come parte di una soluzione esistente o di una nuova soluzione. Questi diagrammi devono essere creati nel progetto di modellazione. Gli elementi dei diagrammi UML fanno parte di un modello comune e i diagrammi UML sono viste di tale modello. Gli elementi dei diagrammi livello si trovano nel progetto di modello, ma non vengono archiviati nel modello comune. Mappe codice e diagrammi classi .NET creati dal codice esistono al di fuori del progetto di modellazione.  
  
 Vedere:  
  
- [Creare diagrammi e progetti di modellazione UML](../modeling/create-uml-modeling-projects-and-diagrams.md)  
  
- [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)  
  
- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)  
  
- [Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
- [SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  
  
  Per mostrare visualizzazioni alternative dell'architettura, è possibile riutilizzare determinati elementi dello stesso modello in più diagrammi dello stesso tipo o di tipo diverso. Ad esempio, è possibile trascinare un componente in un altro diagramma dei componenti o in un diagramma di sequenza per usarlo come attore. Visualizzare [modelli e diagrammi UML modifica](../modeling/edit-uml-models-and-diagrams.md).  
  
  Entrambi i team usano anche la convalida dei livelli per assicurarsi che il codice in fase di sviluppo rimanga coerente con la progettazione.  
  
  Vedere:  
  
- [Coerenza del codice con la progettazione](#ValidatingCode)  
  
- [Descrivere l'architettura logica: Diagrammi livello](#DescribeLayers)  
  
- [Convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md)  
  
  > [!NOTE]
  > Alcune versioni di Visual Studio supportano la convalida dei livelli e le versioni di sola lettura di mappe codice e diagrammi UML per la visualizzazione e la modellazione. Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="UnderstandingCommunicating"></a> Comprensione e comunicazione delle informazioni relative al sistema  
 Non è necessario usare i diagrammi di modellazione di Visual Studio in base a un ordine stabilito; possono essere usati in base alle proprie esigenze o all'approccio preferito. In genere i team rivedono i propri modelli in modo frequente e iterativo nel corso di un progetto. Ogni diagramma offre specifici punti di forza che consentono di comprendere, descrivere e comunicare i diversi aspetti del sistema in fase di sviluppo.  
  
 Dinner Now e Lucerne comunicano tra di loro e con gli stakeholder del progetto usando i diagrammi come linguaggio comune. Ad esempio, Dinner Now usa i diagrammi per eseguire queste attività:  
  
- Visualizzare il codice esistente.  
  
- Comunicare con Lucerne riguardo a storie utente nuove o aggiornate.  
  
- Identificare le modifiche necessarie per supportare le storie utente nuove o aggiornate.  
  
  Lucerne usa i diagrammi per eseguire queste attività:  
  
- Acquisire informazioni sui processi aziendali di Dinner Now.  
  
- Comprendere la progettazione del sistema.  
  
- Comunicare con Dinner Now riguardo a requisiti utente nuovi o aggiornati.  
  
- Documentare gli aggiornamenti di sistema.  
  
  I diagrammi sono integrati con Team Foundation Server per consentire ai team di pianificare, gestire e tenere traccia del proprio lavoro più facilmente. Ad esempio, i team usano i modelli per identificare test case e attività di sviluppo e per stimare il lavoro. Lucerne collega gli elementi di lavoro di Team Foundation Server a elementi del modello in modo da poter monitorare lo stato di avanzamento e assicurarsi che il sistema soddisfi i requisiti degli utenti. Ad esempio, collega i casi d'uso agli elementi di lavoro dei test case in modo da poter verificare che i casi d'uso siano soddisfatti quando tutti i test vengono superati.  
  
  Prima di archiviare le modifiche, i team convalidano il codice in base ai test e alla progettazione eseguendo compilazioni che includono la convalida dei livelli e test automatizzati. Questo garantisce che il codice aggiornato non sia in conflitto con la progettazione e non interferisca con funzionalità precedentemente funzionanti.  
  
  Vedere:  
  
- [Informazioni sul ruolo del sistema nel processo di business](#UnderstandingBPMandSystemDesign)  
  
- [Descrizione dei requisiti utente nuovi o aggiornati](#DescribingURM)  
  
- [Creazione di test da modelli](#CreatingTests)  
  
- [Identificazione di modifiche apportate al sistema esistente](#DeterminingChanges)  
  
- [Keeping code consistent with the design](#ValidatingCode)  
  
- [Suggerimenti generali per la creazione e l'uso di modelli](#GeneralTips)  
  
- [Pianificazione e traccia del lavoro](#PlanningTracking)  
  
- [Test, convalida e archiviazione del codice aggiornato](#TestValidateCheckInCode)  
  
### <a name="UnderstandingBPMandSystemDesign"></a> Informazioni sul ruolo del sistema nel processo di Business  
 Lucerne vuole acquisire altre informazioni sui processi aziendali di Dinner Now. Crea i diagrammi seguenti per chiarire più facilmente l'accordo con Dinner Now:  
  
|**Diagramma**|**Oggetto della descrizione**|  
|-----------------|-------------------|  
|*Diagramma caso di utilizzo (UML)*<br /><br /> Vedere:<br /><br /> -   [Diagrammi caso di utilizzo UML: Riferimento](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagrammi caso di utilizzo UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md)|-Le attività che supporta il sistema di Dinner Now<br />-Le persone e sistemi esterni che eseguono le attività.<br />-I componenti principali del sistema che supportano ciascuna attività<br />-Le parti del processo di business che non rientrano nell'ambito del sistema corrente, ad esempio, consegna di cibo|  
|*Diagramma di attività (UML)*<br /><br /> Vedere:<br /><br /> -   [Diagrammi di attività UML: Riferimento](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md)|Il flusso dei passaggi eseguiti quando un cliente crea un ordine|  
|*Diagramma di classi (UML)*<br /><br /> Vedere:<br /><br /> -   [Diagrammi classi UML: Riferimento](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)|Le entità aziendali e i termini usati nella discussione e nelle relazioni tra tali entità. Ad esempio, fanno parte di questo scenario i termini "ordine" e "voce di menu".|  
  
 Ad esempio, Lucerne crea il diagramma caso di utilizzo seguente per comprendere le attività che vengono eseguite nel sito Web di Dinner Now e i relativi autori:  
  
 ![Diagramma caso di utilizzo UML](../modeling/media/uml-usecase.png "UML_UseCase")  
  
 **Diagramma caso d'uso UML**  
  
 Il diagramma di attività seguente descrive il flusso dei passaggi relativi a un ordine effettuato da un cliente sul sito Web di Dinner Now. In questa versione, gli elementi di commento identificano i ruoli e le linee creano *corsie*che organizzano i passaggi per ruolo:  
  
 ![Diagramma attività UML](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")  
  
 **Diagramma attività UML**  
  
 Il diagramma classi seguente descrive le entità che partecipano al processo di ordine:  
  
 ![Diagramma classi UML](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")  
  
 **UML Class Diagram**  
  
### <a name="DescribingURM"></a> Descrizione dei requisiti utente nuovi o aggiornati  
 Lucerne vuole aggiungere funzionalità al sistema di Dinner Now affinché i clienti possono leggere e inviare recensioni sui ristoranti. L'azienda aggiorna i diagrammi seguenti in modo da poter descrivere e illustrare questo nuovo requisito a Dinner Now:  
  
|**Diagramma**|**Oggetto della descrizione**|  
|-----------------|-------------------|  
|*Diagramma caso di utilizzo (UML)*<br /><br /> Vedere:<br /><br /> -   [Diagrammi caso di utilizzo UML: Riferimento](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagrammi caso di utilizzo UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md)|Un nuovo caso d'uso per "Recensione di un ristorante"|  
|*Diagramma di attività (UML)*<br /><br /> Vedere:<br /><br /> -   [Diagrammi di attività UML: Riferimento](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md)|I passaggi eseguiti quando un cliente vuole scrivere una recensione di un ristorante|  
|*Diagramma di classi (UML)*<br /><br /> Vedere:<br /><br /> -   [Diagrammi classi UML: Riferimento](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)|I dati necessari per archiviare una recensione|  
  
 Il diagramma caso di utilizzo seguente, ad esempio, include un nuovo caso d'uso di "Recensione di un ristorante" per rappresentare il nuovo requisito. È evidenziato in arancione nel diagramma per renderne più semplice l'identificazione:  
  
 ![Diagramma caso di utilizzo UML](../modeling/media/uml-writerev.png "UML_WriteRev")  
  
 **Diagramma caso di utilizzo UML**  
  
 Il diagramma di attività seguente include nuovi elementi in arancione per descrivere il flusso dei passaggi del nuovo caso d'uso:  
  
 ![Diagramma attività UML](../modeling/media/uml-writereview.png "UML_WriteReview")  
  
 **Diagramma attività UML**  
  
 Il diagramma classi seguente include una nuova classe Recensione e le relative relazioni con altre classi, affinché i team possano discuterne i dettagli. Si noti che un cliente e un ristorante possono avere più recensioni:  
  
 ![Diagramma classi UML](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")  
  
 **Diagramma classi UML**  
  
### <a name="CreatingTests"></a> Creazione di test da modelli  
 Entrambi i team concordano sulla necessità di un set completo di test per il sistema e i relativi componenti prima di apportare qualsiasi modifica. Lucerne ha un team specializzato che esegue i test a livello di sistema e di componente. L'azienda riutilizza i test creati da Dinner Now e li struttura usando i diagrammi UML:  
  
- Ogni caso d'uso è rappresentato da uno o più test. Gli elementi del diagramma caso di utilizzo sono collegati agli elementi di lavoro del test case in Team Foundation Server.  
  
- Ogni flusso in un diagramma di attività o in un diagramma di sequenza a livello di sistema è collegato ad almeno un test. Il team di test si assicura sistematicamente di testare ogni possibile percorso nel diagramma di attività.  
  
- I termini usati per descrivere i test sono basati su termini definiti dai diagrammi caso di utilizzo, classi e di attività.  
  
  Man mano che i requisiti cambiano e i diagrammi vengono aggiornati per riflettere tali modifiche, vengono aggiornati anche i test. Un requisito è considerato soddisfatto solo quando i test vengono superati. Quando è possibile o fattibile, i test vengono definiti e basati sui diagrammi UML prima dell'inizio dell'implementazione.  
  
  Vedere:  
  
- [Sviluppare test da un modello](../modeling/develop-tests-from-a-model.md)  
  
- [Eseguire la convalida di un modello UML](../modeling/validate-your-uml-model.md)  
  
### <a name="DeterminingChanges"></a> Identifying Changes to the Existing System  
 Dinner Now deve stimare i costi da sostenere per soddisfare il nuovo requisito. Il costo dipende in parte dall'impatto che tale modifica avrà su altre parti del sistema. Per facilitare il compito, uno degli sviluppatori di Dinner Now crea queste mappe e questi diagrammi dal codice esistente:  
  
|**Mappa o diagramma**|**Mostra**|  
|------------------------|---------------|  
|*Mappa codice*<br /><br /> Vedere:<br /><br /> -   [Mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Cercare e ridisporre le mappe codice](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Dipendenze e altre relazioni nel codice.<br /><br /> Ad esempio, Dinner Now potrebbe iniziare esaminando le mappe codice assembly per avere una panoramica degli assembly e delle relative dipendenze. Può analizzare in dettaglio le mappe per esplorare gli spazi dei nomi e le classi in tali assembly.<br /><br /> Dinner Now può anche creare mappe per esplorare aree specifiche e altri tipi di relazioni nel codice. Usa Esplora soluzioni per trovare e selezionare le aree e le relazioni di suo interesse.|  
|*Diagramma classi basato su codice*<br /><br /> Vedere [Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Classi presenti nel codice|  
  
 Ad esempio, lo sviluppatore crea una mappa codice. Modifica l'ambito per concentrarsi sulle aree che saranno interessate dal nuovo scenario. Queste aree sono selezionate ed evidenziate nella mappa:  
  
 ![Grafico delle dipendenze Namespace](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")  
  
 **Mappa codice degli spazi dei nomi**  
  
 Lo sviluppatore espande gli spazi dei nomi selezionati per visualizzarne le classi, i metodi e le relazioni:  
  
 ![Grafico dipendenze spazio dei nomi espanso](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")  
  
 **Mappa codice degli spazi dei nomi espansi con i collegamenti tra gruppi visibili**  
  
 Lo sviluppatore esamina il codice per trovare le classi e i metodi interessati. Per visualizzare gli effetti di ogni modifica nel momento stesso in cui viene effettuata, rigenerare le mappe codice dopo ogni modifica. Visualizzare [visualizzare il codice](../modeling/visualize-code.md).  
  
 Per descrivere le modifiche ad altre parti del sistema, ad esempio componenti o interazioni, il team potrebbe disegnare questi elementi su una lavagna. Potrebbe anche creare i diagrammi seguenti in Visual Studio affinché i dettagli possano essere acquisiti, gestiti e riconosciuti da entrambi i team:  
  
|**Diagrammi**|**Oggetto della descrizione**|  
|------------------|-------------------|  
|*Diagramma di attività (UML)*<br /><br /> Vedere:<br /><br /> -   [Diagrammi di attività UML: Riferimento](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md)|Il flusso dei passaggi eseguiti quando il sistema rileva che un cliente effettua un nuovo ordine presso un ristorante già usato in precedenza e gli propone pertanto di scriverne la recensione.|  
|*Diagramma di classi (UML)*<br /><br /> Vedere:<br /><br /> -   [Diagrammi classi UML: Riferimento](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)|Classi logiche e relative relazioni. Ad esempio, viene aggiunta una nuova classe per descrivere una **Recensione** e le sue  relazioni con altre entità come **Ristorante**, **Menu**e **Cliente**.<br /><br /> Per associare le recensioni a un cliente, il sistema deve archiviare i dati relativi al cliente. Un diagramma classi UML può essere utile per chiarire quei dati.|  
|*Diagramma classi basato su codice*<br /><br /> Vedere [Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Classi presenti nel codice.|  
|*Diagramma dei componenti (UML)*<br /><br /> Vedere:<br /><br /> -   [Diagrammi dei componenti UML: Riferimento](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagrammi dei componenti UML: linee guida](../modeling/uml-component-diagrams-guidelines.md)|Parti generali del sistema, ad esempio il sito Web di Dinner Now e le relative interfacce. Queste interfacce definiscono la modalità di interazione reciproca dei componenti tramite i metodi o i servizi da essi forniti e utilizzati.|  
|*Diagramma di sequenza (UML)*<br /><br /> Vedere:<br /><br /> -   [Diagrammi di sequenza UML: Riferimento](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md)|Sequenza di interazioni tra le istanze.|  
  
 Ad esempio, il diagramma dei componenti seguente illustra il nuovo componente, che fa parte del componente del sito Web di Dinner Now. Il componente ElaborazioneRecensioni gestisce la funzionalità di creazione di recensioni ed è evidenziato in arancione:  
  
 ![Diagramma dei componenti UML](../modeling/media/uml-internal.png "UML_Internal")  
  
 **Diagramma dei componenti UML**  
  
 Il diagramma di sequenza seguente illustra la sequenza delle interazioni che si verificano quando il sito Web di Dinner Now controlla se il cliente ha già effettuato un ordine presso un ristorante. Se il risultato è true, viene chiesto al cliente di scrivere una recensione, che viene inviata al ristorante e pubblicata sul sito Web:  
  
 ![Diagramma di sequenza UML](../modeling/media/uml-revsystem.png "UML_RevSystem")  
  
 **Diagramma di sequenza UML**  
  
### <a name="ValidatingCode"></a> Coerenza del codice con la progettazione  
 Dinner Now deve assicurarsi che il codice aggiornato rimanga coerente con la progettazione. L'azienda crea diagrammi livello che descrivono i livelli di funzionalità nel sistema, specificano le dipendenze consentite tra gli elementi della soluzione e associano tali elementi ai livelli.  
  
|**Diagramma**|**Oggetto della descrizione**|  
|-----------------|-------------------|  
|*Diagramma livello*<br /><br /> Vedere:<br /><br /> -   [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammi livello: Riferimento](../modeling/layer-diagrams-reference.md)<br />-   [Diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md)<br />-   [Convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md)|L'architettura logica del codice.<br /><br /> Un diagramma livello organizza e mappa gli elementi di una soluzione [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per astrarre gruppi denominati *livelli*. Questi livelli identificano i ruoli, le attività o le funzioni che questi elementi eseguono nel sistema.<br /><br /> I diagrammi livello sono utili per descrivere la progettazione desiderata del sistema e convalidare il codice dinamico in base a questa progettazione.<br /><br /> Per creare livelli, trascinare elementi da Esplora soluzioni, mappe codice, Visualizzazione classi e Visualizzatore oggetti. Per disegnare nuovi livelli, usare la casella degli strumenti o fare clic con il pulsante destro del mouse sulla superficie del diagramma.<br /><br /> Per visualizzare le dipendenze esistenti, fare clic con il pulsante destro del mouse sulla superficie del diagramma livello e scegliere **Genera dipendenze**. Per specificare le dipendenze desiderate, disegnare nuove dipendenze.|  
  
 Il diagramma livello seguente, ad esempio, descrive le dipendenze tra i livelli e il numero di elementi associati a ogni livello:  
  
 ![Diagramma di livello di sistema di pagamenti integrato](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagramma livello**  
  
 Per assicurarsi che non si verifichino conflitti con la progettazione durante lo sviluppo del codice, i team usano la convalida dei livelli su compilazioni che vengono eseguite in Team Foundation Build. Creano anche un'attività di MSBuild personalizzata per richiedere la convalida dei livelli nelle operazioni di archiviazione. Per raccogliere gli errori di convalida, usano report di compilazione.  
  
 Vedere:  
  
- [Definire il processo di compilazione](https://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)  
  
- [Utilizzare un processo di compilazione di archiviazione gestita per convalidare le modifiche](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)  
  
- [Personalizzare il modello del processo di compilazione](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
### <a name="GeneralTips"></a> General Tips for Creating and Using Models  
  
- La maggior parte dei diagrammi è costituita da nodi connessi tramite linee. Per ogni tipo di diagramma, nella casella degli strumenti sono disponibili nodi e linee di vario tipo.  
  
   Per aprire la casella degli strumenti, fare clic su **Casella degli strumenti** nel menu **Visualizza**.  
  
- Per creare un nodo, trascinarlo dalla casella degli strumenti nel diagramma. Alcuni tipi di nodi devono essere trascinati nei nodi esistenti. Ad esempio, in un diagramma dei componenti è necessario aggiungere una nuova porta a un componente esistente.  
  
- Per creare una linea o una connessione, fare clic sullo strumento appropriato nella casella degli strumenti, quindi sul nodo di origine e infine sul nodo di destinazione. Alcune linee possono essere create solo tra determinati tipi di nodi. Quando si sposta il puntatore su una possibile origine o destinazione, il puntatore indica se è possibile creare una connessione.  
  
- La creazione di elementi nei diagrammi UML comporta anche l'aggiunta di questi elementi a un modello comune. I diagrammi UML in un progetto di modello rappresentano visualizzazioni del modello stesso. Gli elementi di un diagramma livello fanno parte del progetto di modello, anche se non sono archiviati nel modello comune.  
  
   Per visualizzare il modello, scegliere **Finestre** dal menu  **Architettura**, quindi fare clic su **Esplora modelli UML**.  
  
- In alcuni casi è possibile trascinare alcuni elementi da **Esplora modelli UML** in un diagramma UML. Alcuni elementi dello stesso modello possono essere usati in più diagrammi dello stesso tipo o di tipo diverso per mostrare visualizzazioni alternative dell'architettura. Ad esempio, è possibile trascinare un componente in un altro diagramma dei componenti o in un diagramma di sequenza per usarlo come attore.  
  
- Visual Studio supporta UML 2.1.2. In questa panoramica sono descritte solo le funzionalità principali dei diagrammi UML nella versione corrente; per un approfondimento su UML e sul relativo uso, sono disponibili numerose pubblicazioni.  
  
  Visualizzare [creare modelli per l'app](../modeling/create-models-for-your-app.md).  
  
### <a name="PlanningTracking"></a> Planning and Tracking Work  
 I diagrammi di modellazione di Visual Studio sono integrati con Team Foundation Server per consentire di pianificare, gestire e tenere traccia del proprio lavoro più facilmente. Entrambi i team usano i modelli per identificare test case e attività di sviluppo e per stimare il lavoro. Lucerne crea e collega gli elementi di lavoro di Team Foundation Server agli elementi del modello, come casi d'uso o componenti. In questo modo è in grado di monitorare lo stato di avanzamento e di tenere traccia del lavoro tenendo conto dei requisiti degli utenti. Ciò consente di verificare che le modifiche continuino a soddisfare tali requisiti.  
  
 Durante il lavoro, i team aggiornano gli elementi di lavoro in modo da riflettere il tempo dedicato alle varie attività. Inoltre, monitorano e segnalano lo stato del lavoro usando le funzionalità di Team Foundation Server seguenti:  
  
- *Rapporti burn-down* giornalieri che mostrano se il lavoro pianificato verrà completato nei tempi previsti. Altri rapporti analoghi vengono generati da Team Foundation Server per tenere traccia dello stato di avanzamento dei bug.  
  
- Un *foglio di lavoro delle iterazioni* che usa Microsoft Excel per consentire al team di monitorare e bilanciare il carico di lavoro tra i membri. Questo foglio di lavoro è collegato a Team Foundation Server e fornisce contenuti sui quali incentrare la discussione durante le riunioni periodiche sullo stato di avanzamento.  
  
- Un *dashboard di sviluppo* che usa Office Project per consentire al team di tenersi al corrente sulle informazioni importanti del progetto.  
  
  Vedere:  
  
- [Tenere traccia del lavoro tramite Visual Studio Online o Team Foundation Server](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)  
  
- [Collegare elementi di modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md)  
  
- [Grafici, dashboard e report per Visual Studio ALM](https://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)  
  
- [Creare il backlog e le attività tramite Project](https://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)  
  
### <a name="TestValidateCheckInCode"></a> Test, convalida e archiviazione del codice  
 Quando i team completano ogni attività, archiviano il codice in Controllo della versione di Team Foundation e, qualora se ne dimenticassero, ricevono un promemoria da Team Foundation Server. Prima che Team Foundation Server accetti le archiviazioni, i team devono eseguire gli unit test e la convalida dei livelli per verificare il codice in base ai test case e alla progettazione. Usano Team Foundation Server per eseguire periodicamente le compilazioni, unit test automatizzati e la convalida dei livelli. Questo permette di verificare che il codice soddisfi i criteri seguenti:  
  
- Viene eseguito correttamente.  
  
- Non impedisce l'esecuzione di codice precedentemente funzionante.  
  
- Non è in conflitto con la progettazione.  
  
  Dinner Now dispone di un'ampia raccolta di test automatizzati, che possono essere riutilizzati da Lucerne in quanto ancora applicabili ai nuovi scenari. Lucerne può inoltre estendere questi test e aggiungerne altri per analizzare nuove funzionalità. Entrambi i team usano Visual Studio per eseguire i test manuali.  
  
  Per assicurarsi che il codice sia conforme alla progettazione, i team configurano le compilazioni in Team Foundation Build per includere la convalida dei livelli. In caso di conflitti, viene generato un report con i dettagli.  
  
  Vedere:  
  
- [Test dell'applicazione](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)  
  
- [Convalidare il sistema durante lo sviluppo](../modeling/validate-your-system-during-development.md)  
  
- [Utilizzare il controllo della versione](http://go.microsoft.com/fwlink/?LinkID=525605)  
  
- [Compilare l'applicazione](https://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
## <a name="UpdatingSystem"></a> Updating the System Using Visualization and Modeling  
 Lucerne e Dinner Now devono integrare i propri sistemi di pagamento. Le sezioni seguenti mostrano i diagrammi di modellazione in Visual Studio per eseguire questa attività:  
  
- [Comprendere i requisiti dell'utente: Diagrammi caso d'uso](#UnderstandUseCases)  
  
- [Comprendere il processo di Business: Diagrammi di attività](#UnderstandActivities)  
  
- [Descrivere la struttura di sistema: Diagrammi dei componenti](#DescribeComponents)  
  
- [Vengono descritte le interazioni: Diagrammi di sequenza](#DescribeSequence)  
  
- [Visualizzare il codice esistente: Mappe codice](#VisualizeCode)  
  
- [Definire un glossario dei tipi: Diagrammi classi](#DefineClasses)  
  
- [Descrivere l'architettura logica: Diagrammi livello](#DescribeLayers)  
  
  Vedere:  
  
- [Creare modelli per l'app](../modeling/create-models-for-your-app.md)  
  
- [Visualizzare il codice](../modeling/visualize-code.md)  
  
- [Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)  
  
- [Modellare i requisiti utente](../modeling/model-user-requirements.md)  
  
- [Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)  
  
### <a name="UnderstandUseCases"></a> Comprendere i requisiti dell'utente: Diagrammi caso d'uso  
 I diagrammi caso di utilizzo riepilogano le attività supportate ed eseguite da un sistema. Lucerne usa un diagramma caso di utilizzo per ottenere le seguenti informazioni sul sistema di Dinner Now:  
  
- I clienti creano gli ordini.  
  
- I ristoranti ricevono gli ordini.  
  
- Il gateway esterno per l'elaborazione dei pagamenti, usato dal sistema di Dinner Now per convalidare i pagamenti, non rientra nell'ambito del sito Web.  
  
  Il diagramma mostra anche la divisibilità di alcuni dei principali casi d'uso in casi d'uso più piccoli. Lucerne vuole usare il proprio sistema di pagamento. Evidenzia pertanto il caso d'uso Elaborazione dei pagamenti con un colore diverso per indicare che sono richieste modifiche:  
  
  ![L'evidenziazione di elaborazione dei pagamenti in un diagramma caso di utilizzo](../modeling/media/uml-processpay.png "UML_ProcessPay")  
  
  **L'evidenziazione di elaborazione dei pagamenti nel diagramma caso di utilizzo**  
  
  Se il tempo a disposizione per lo sviluppo è scarso, il team potrebbe valutare la possibilità di consentire ai clienti di effettuare i pagamenti direttamente ai ristoranti. Per mostrare questo approccio, sostituirà il caso d'uso Elaborazione dei pagamenti con un altro esterno ai limiti del sistema di Dinner Now. Quindi, collegherà Cliente direttamente a Ristorante, indicando così che Dinner Now si limiterà all'elaborazione degli ordini:  
  
  ![Modifica dell'ambito di pagamento ristorante nel diagramma caso di utilizzo](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")  
  
  **Modifica dell'ambito di pagamento ristorante nel diagramma caso di utilizzo**  
  
  Vedere:  
  
- [Diagrammi dei casi d'uso UML: riferimenti](../modeling/uml-use-case-diagrams-reference.md)  
  
- [Diagrammi dei casi d'uso UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md)  
  
#### <a name="drawing-a-use-case-diagram"></a>Creazione di un diagramma caso d'uso  
 Le caratteristiche principali di un diagramma caso di utilizzo sono le seguenti:  
  
- *Attori* : rappresentano ruoli svolti da persone, organizzazioni, computer o sistemi software. Esempi di attori sono Cliente, Ristorante e il sistema di pagamento di Dinner Now.  
  
- *Casi d'uso* : rappresentano le interazioni tra gli attori e il sistema in corso di sviluppo.  Possono rappresentare interazioni di qualsiasi entità, da un semplice clic del mouse o messaggio a una transazione che si estende su più giorni.  
  
- *Associazioni* : collegano gli attori ai casi d'uso.  
  
- Un caso d'uso più ampio può *includere* casi d'uso più piccoli; ad esempio, Creazione dell'ordine include Selezione del ristorante. È possibile *estendere* un caso d'uso aggiungendo obiettivi e passaggi, per indicare che il caso d'uso si verifica solo a determinate condizioni. I casi d'uso possono anche ereditare l'uno dall'altro.  
  
- *Sottosistema* : rappresenta il sistema software in corso di sviluppo o uno dei suoi componenti. È rappresentato da una casella di grandi dimensioni che contiene i casi d'uso. Un diagramma caso di utilizzo definisce gli elementi interni o esterni ai limiti del sottosistema. Per indicare che l'utente deve portare a termine determinati obiettivi in altri modi, tracciare quei casi d'uso all'esterno dei limiti del sottosistema.  
  
- *Elementi* :  collegano gli elementi del diagramma ad altri diagrammi o documenti.  
  
  Vedere:  
  
- [Diagrammi dei casi d'uso UML: riferimenti](../modeling/uml-use-case-diagrams-reference.md)  
  
- [Diagrammi dei casi d'uso UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-use-case-diagrams"></a>Riepilogo: Vantaggi dei diagrammi casi d'uso  
 I diagrammi caso di utilizzo consentono di visualizzare:  
  
- Le attività supportate o meno da un sistema  
  
- Le persone e i sistemi esterni che eseguono quelle attività  
  
- I componenti principali del sistema che supportano ciascuna attività e che è possibile rappresentare come sottosistemi annidati nel sistema padre  
  
- La divisibilità di un caso d'uso in casi d'uso più piccoli o varianti.  
  
#### <a name="relationship-to-other-diagrams"></a>Relazione con altri diagrammi  
  
|**Diagramma**|**Oggetto della descrizione**|  
|-----------------|-------------------|  
|Diagramma di attività|Il flusso dei passaggi in un caso d'uso e le persone che li eseguono.<br /><br /> I nomi dei casi d'uso rispecchiano spesso i passaggi di un diagramma di attività. I diagrammi di attività supportano elementi quali le decisioni, le unioni, gli input e gli output, i flussi simultanei e così via.<br /><br /> Vedere:<br /><br /> -   [Diagrammi di attività UML: Riferimento](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md)|  
|Diagramma sequenza|La sequenza delle interazioni tra i partecipanti in un caso d'uso.<br /><br /> Vedere:<br /><br /> -   [Diagrammi di sequenza UML: Riferimento](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Diagramma classi (UML)|Le entità o i tipi che partecipano al caso d'uso.<br /><br /> Vedere:<br /><br /> -   [Diagrammi classi UML: Riferimento](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)|  
  
### <a name="UnderstandActivities"></a> Comprendere il processo di Business: Diagrammi di attività  
 I diagrammi di attività descrivono il flusso dei passaggi di un processo aziendale e offrono un modo semplice per comunicare un flusso di lavoro. Un progetto di sviluppo può avere più diagrammi di attività. In genere, un'attività include tutte le azioni risultanti da un'azione esterna, ad esempio l'ordinazione di un pasto, l'aggiornamento di un menu o l'aggiunta di un nuovo ristorante all'attività commerciale. Un'attività potrebbe anche descrivere i dettagli di un'azione complessa.  
  
 Lucerne aggiorna il diagramma di attività seguente per mostrare che la società elabora il pagamento e paga il ristorante. Il sistema di pagamento di Dinner Now viene sostituito con quello di Lucerne, come evidenziato:  
  
 ![Sistema di pagamento di Lucerne nel diagramma di attività](../modeling/media/uml-lucerne.png "UML_Lucerne")  
  
 **Sostituire il sistema di Dinner Now nel diagramma di attività**  
  
 Il diagramma aggiornato consente a Lucerne e Dinner Now di verificare in quale fase del processo aziendale interviene il sistema di pagamento di Lucerne. In questa versione, i commenti vengono usati per identificare i ruoli che eseguono i passaggi. Le linee vengono usate per creare *corsie*, che consentono di organizzare i passaggi in base al ruolo.  
  
 I team potrebbero anche prendere in considerazione una storia alternativa, in cui il cliente paga il ristorante dopo la consegna dell'ordine. Questa modifica produrrebbe una variazione dei requisiti per il sistema software.  
  
 In precedenza, il team di Dinner Now disegnava questi diagrammi su una lavagna o in PowerPoint. Adesso si avvale anche di Visual Studio per effettuare questa operazione, in modo che entrambi i team possano acquisire, comprendere e gestire i dettagli.  
  
 Vedere:  
  
- [Diagrammi di attività UML: riferimenti](../modeling/uml-activity-diagrams-reference.md)  
  
- [Diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md)  
  
#### <a name="drawing-an-activity-diagram"></a>Creazione di un diagramma di attività  
 Le caratteristiche principali di un diagramma di attività sono le seguenti:  
  
- *Nodo iniziale* : indica la prima azione dell'attività.  
  
   Il diagramma deve avere sempre uno di questi nodi.  
  
- *Azioni* : descrivono i passaggi in cui l'utente o il software esegue un'attività.  
  
- *Flussi di controllo* : mostrano il flusso tra le azioni.  
  
- *Nodi decisione* : rappresenta rami condizionali del flusso.  
  
- *Nodi fork* : suddividono i singoli flussi in flussi simultanei.  
  
- *Nodi finali attività* : mostrano le estremità dell'attività.  
  
   Sebbene questi nodi siano facoltativi, è utile includerli nel diagramma per mostrare dove termina l'attività.  
  
  Vedere:  
  
- [Diagrammi di attività UML: riferimenti](../modeling/uml-activity-diagrams-reference.md)  
  
- [Diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-activity-diagrams"></a>Riepilogo: Vantaggi dei diagrammi di attività  
 I diagrammi di attività consentono di visualizzare e descrivere il flusso di controllo e delle informazioni tra le azioni di un'azienda, di un sistema o di un programma. Rappresentano uno strumento semplice e utile per descrivere il flusso di lavoro quando si comunica con altre persone.  
  
#### <a name="relationship-to-other-diagrams"></a>Relazione con altri diagrammi  
  
|**Diagramma**|**Descrizione**|  
|-----------------|---------------------|  
|Diagramma caso di utilizzo|Riepilogo delle attività eseguite da ciascun attore.<br /><br /> Vedere:<br /><br /> -   [Diagrammi caso di utilizzo UML: Riferimento](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagrammi caso di utilizzo UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Diagramma dei componenti|Visualizzazione del sistema come raccolta di parti riutilizzabili che forniscono o usano il comportamento tramite un set ben definito di interfacce.<br /><br /> Vedere:<br /><br /> -   [Diagrammi dei componenti UML: Riferimento](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagrammi dei componenti UML: linee guida](../modeling/uml-component-diagrams-guidelines.md)|  
  
### <a name="DescribeComponents"></a> Descrivere la struttura di sistema: Diagrammi dei componenti  
 I diagrammi dei componenti descrivono un sistema come una raccolta di parti separabili che forniscono o usano il comportamento tramite un set ben definito di interfacce. Le parti possono essere di qualsiasi dimensione e connettersi in qualsiasi modo.  
  
 Per aiutare Lucerne e Dinner Now a visualizzare e discutere i componenti del sistema e le relative interfacce, i team creano i diagrammi dei componenti seguenti:  
  
 ![Componenti esterni del sistema di pagamento](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")  
  
 **Componenti di sistema di pagamento di Dinner Now**  
  
 Questo diagramma mostra diversi tipi di componente e le relative *dipendenze*. Ad esempio, per convalidare i pagamenti, sia il sito Web di Dinner Now che il sistema di pagamenti di Lucerne necessitano del gateway esterno per l'elaborazione dei pagamenti. Le frecce tra i componenti rappresentano le dipendenze che indicano quali componenti richiedono la funzionalità di altri componenti.  
  
 Per usare il sistema di pagamento di Lucerne, è necessario aggiornare il sito Web di Dinner Now in modo che usi le interfacce ApprovazionePagamenti e InserimentoCrediti nel sistema di pagamento di Lucerne.  
  
 Il seguente diagramma mostra una specifica configurazione di componenti per il sito Web Dinner Now. Questa configurazione indica che qualsiasi istanza del sito Web è costituita da quattro *parti*:  
  
- ElaborazioneClienti  
  
- ElaborazioneOrdini  
  
- ElaborazioneRecensioni  
  
- ElaborazionePagamenti  
  
  Queste parti sono istanze dei tipi di componente specificati e sono connesse come segue:  
  
  ![I componenti all'interno del sito Web di Dinner Now](../modeling/media/uml-dinnernow.png "UML_DinnerNow")  
  
  **Sito Web i componenti all'interno di Dinner Now**  
  
  Il sito Web di Dinner Now delega il comportamento a queste parti, che ne gestiscono le funzioni. Le frecce che connettono il componente padre e i relativi componenti membro mostrano le *deleghe* , che indicano quali parti gestiscono i messaggi che il padre riceve o invia tramite le relative interfacce.  
  
  In questa configurazione, il componente ElaborazionePagamenti elabora i pagamenti dei clienti. Pertanto, deve essere aggiornato per integrarsi con il sistema di pagamento di Lucerne. In altri scenari potrebbero esistere più istanze di un tipo di componente nello stesso componente padre.  
  
  Vedere:  
  
- [Diagrammi dei componenti UML: riferimenti](../modeling/uml-component-diagrams-reference.md)  
  
- [Diagrammi dei componenti UML: linee guida](../modeling/uml-component-diagrams-guidelines.md)  
  
#### <a name="drawing-a-component-diagram"></a>Creazione di un diagramma dei componenti  
 Le caratteristiche principali di un diagramma dei componenti sono le seguenti:  
  
- *Componenti* : rappresentano porzioni separabili di funzionalità del sistema.  
  
- *Porte dell'interfaccia fornite* : rappresentano gruppi di messaggi o chiamate implementate dai componenti e usate da altri componenti o sistemi esterni.  
  
- *Porte dell'interfaccia richieste* : rappresentano gruppi di messaggi o di chiamate inviate dai componenti ad altri componenti o a sistemi esterni. Questo tipo di porta descrive le operazioni minime previste per un componente da parte di altri componenti o sistemi esterni.  
  
- *Parti* : membri di componenti e in genere istanze di altri componenti. Una parte è una porzione della progettazione interna del componente padre.  
  
- *Dipendenze* : indicano componenti che richiedono le funzionalità di altri componenti.  
  
- *Deleghe* : indicano le parti di un componente che gestiscono i messaggi inviati o ricevuti dal componente padre.  
  
  Vedere:  
  
- [Diagrammi dei componenti UML: riferimenti](../modeling/uml-component-diagrams-reference.md)  
  
- [Diagrammi dei componenti UML: linee guida](../modeling/uml-component-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-component-diagrams"></a>Riepilogo: Vantaggi dei diagrammi dei componenti  
 I diagrammi dei componenti consentono di visualizzare:  
  
- Il sistema come una raccolta di parti separabili indipendentemente dal linguaggio o dallo stile di implementazione.  
  
- Componenti con interfacce ben definite, che rendono la progettazione più facile da comprendere e da aggiornare in caso di variazione dei requisiti.  
  
#### <a name="relationship-to-other-diagrams"></a>Relazione con altri diagrammi  
  
|**Diagramma**|**Descrizione**|  
|-----------------|---------------------|  
|Mappa codice|Visualizzazione dell'organizzazione e delle relazioni nel codice esistente.<br /><br /> Per identificare i candidati per i componenti, creare una mappa codice e raggruppare gli elementi in base alla funzione che svolgono nel sistema.<br /><br /> Vedere:<br /><br /> -   [Mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)|  
|Diagramma sequenza|Visualizzazione della sequenza delle interazioni tra i componenti o le parti all'interno di un componente.<br /><br /> Per creare una linea di vita in un diagramma di sequenza da un componente, fare clic il pulsante destro del mouse sul componente e quindi scegliere **Crea linea di vita**.<br /><br /> Vedere:<br /><br /> -   [Diagrammi di sequenza UML: Riferimento](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Diagramma classi (UML)|Definizione delle interfacce sulle porte fornite o richieste e delle classi che implementano le funzionalità dei componenti.<br /><br /> Vedere:<br /><br /> -   [Diagrammi classi UML: Riferimento](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagramma livello|Descrizione dell'architettura logica del sistema in relazione ai componenti. Usare la convalida dei livelli per assicurare la coerenza del codice con la progettazione.<br /><br /> Vedere:<br /><br /> -   [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammi livello: Riferimento](../modeling/layer-diagrams-reference.md)<br />-   [Diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md)<br />-   [Convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md)|  
|Diagramma di attività|Visualizzazione dell'elaborazione interna eseguita dai componenti in risposta ai messaggi in arrivo.<br /><br /> Vedere:<br /><br /> -   [Diagrammi di attività UML: Riferimento](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md)|  
  
### <a name="VisualizeCode"></a> Visualizzare il codice esistente: Mappe codice  
 Le mappe codice mostrano l'organizzazione e le relazioni correnti nel codice. Gli elementi sono rappresentati da *nodi* sulla mappa e le relazioni sono rappresentate da *collegamenti*. Le mappe codice consentono di effettuare i tipi di attività seguenti:  
  
- Esplorare codice con cui si ha poca familiarità.  
  
- Comprendere dove e in che modo una modifica proposta potrebbe influire sul codice esistente.  
  
- Trovare aree di complessità, livelli o modelli naturali o altre aree suscettibili di miglioramento.  
  
  Ad esempio, si supponga che Dinner Now debba stimare il costo dell'aggiornamento del componente ElaborazionePagamenti. Il costo dipende in parte dall'impatto che tale modifica avrà su altre parti del sistema. Per facilitare il compito, uno degli sviluppatori di Dinner Now genera le mappe codice dal codice e ne modifica l'ambito limitandolo alle aree che potrebbero essere interessate dalla modifica.  
  
  Il seguente grafico mostra le dipendenze tra la classe ElaborazionePagamenti e le altre parti del sistema di Dinner Now, che appaiono selezionate:  
  
  ![Grafico delle dipendenze per il sistema di pagamento di Dinner Now](../modeling/media/dep-dnpayment.png "Dep_DNPayment")  
  
  **Mappa codice per il sistema di pagamento di Dinner Now**  
  
  Lo sviluppatore esplora la mappa espandendo la classe ElaborazionePagamenti e selezionandone i membri per visualizzare le aree potenzialmente interessate:  
  
  ![Metodi interni a ElaborazionePagamenti e dipendenze](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")  
  
  **Metodi interni alla classe ElaborazionePagamenti e relative dipendenze**  
  
  Viene generata la mappa seguente per consentire il controllo delle classi, dei metodi e delle dipendenze del sistema di pagamento di Lucerne. Il team si rende conto che potrebbe essere necessario apportare modifiche anche al sistema di Lucerne, per consentirne l'interazione con le altre parti di Dinner Now:  
  
  ![Grafico delle dipendenze per il sistema di pagamento di Lucerne](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")  
  
  **Mappa codice per il sistema di pagamento di Lucerne**  
  
  Entrambi i team collaborano per determinare le modifiche necessarie per integrare i due sistemi e decidono di effettuare il refactoring di parte del codice per facilitarne l'aggiornamento. La classe RespApprovazionePagamenti verrà spostata nello spazio dei nomi DinnerNow.Business e richiederà alcuni nuovi metodi. Le classi di Dinner Now che gestiscono le transazioni avranno uno spazio dei nomi distinto. I team creano e usano elementi di lavoro per pianificare, organizzare e tenere traccia del lavoro. Ove sia utile, collegano gli elementi di lavoro agli elementi del modello.  
  
  Dopo avere riorganizzato il codice, i team generano una nuova mappa codice per visualizzare la struttura aggiornata e le relazioni:  
  
  ![Grafico delle dipendenze con codice riorganizzato](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")  
  
  **Mappa codice con codice riorganizzato**  
  
  Questa mappa mostra che la classe RespApprovazionePagamenti ora si trova nello spazio dei nomi DinnerNow.Business e ha alcuni nuovi metodi. Le classi di transazione di Dinner Now ora hanno uno spazio dei nomi SistemaPagamento distinto, che semplificherà in seguito la gestione del codice.  
  
#### <a name="creating-a-code-map"></a>Creazione di una mappa codice  
  
- Per una rapida panoramica del codice sorgente, seguire questa procedura per generare una mappa codice:  
  
     Nel menu **Architettura** fare clic su **Genera mappa codici per la soluzione**.  
  
     Per una rapida panoramica del codice compilato, creare una mappa codice vuota, quindi trascinare file di assembly o file binari sulla superficie della mappa.  
  
- Per esplorare elementi specifici del codice o della soluzione, usare Esplora soluzioni per selezionare gli elementi e le relazioni da visualizzare. È possibile quindi generare una nuova mappa o aggiungere gli elementi selezionati a una mappa esistente. Vedere [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).  
  
- Per esplorare agevolmente la mappa, ridisporre il layout in base ai tipi di attività da eseguire.  
  
     Ad esempio, per visualizzare i livelli nel codice, selezionare un layout con una struttura ad albero. Visualizzare [cercare e ridisporre le mappe codice](../modeling/browse-and-rearrange-code-maps.md).  
  
#### <a name="summary-strengths-of-code-maps"></a>Riepilogo: Vantaggi delle mappe codice  
 Le mappe codice consentono di:  
  
- Ottenere informazioni sull'organizzazione e sulle relazioni nel codice esistente.  
  
- Identificare le aree sulle quali potrebbe influire una modifica proposta.  
  
- Trovare aree di complessità, modelli, livelli o altre aree suscettibili di miglioramento, per rendere il codice più facile da gestire, modificare e riutilizzare.  
  
#### <a name="relationship-to-other-diagrams"></a>Relazione con altri diagrammi  
  
|**Diagramma**|**Oggetto della descrizione**|  
|-----------------|-------------------|  
|Diagramma livello|L'architettura logica del sistema. Usare la convalida dei livelli per assicurare la coerenza del codice con la progettazione.<br /><br /> Per identificare più facilmente i livelli esistenti o previsti, creare una mappa codice e raggruppare gli elementi correlati. Per creare un diagramma livello, vedere:<br /><br /> -   [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md)|  
|Diagramma dei componenti|I componenti e le relative interfacce e relazioni.<br /><br /> Per identificare più facilmente i componenti, creare una mappa codice e raggruppare gli elementi in base alla funzione che svolgono nel sistema.<br /><br /> Vedere:<br /><br /> -   [Diagrammi dei componenti UML: Riferimento](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagrammi dei componenti UML: linee guida](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagramma classi (UML)|Le classi e i relativi attributi, operazioni e relazioni.<br /><br /> Per identificare più facilmente questi elementi, creare un diagramma classi UML in cui siano visualizzati.<br /><br /> Vedere:<br /><br /> -   [Diagrammi classi UML: Riferimento](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagramma classi (basato su codice)|Classi presenti nel codice per un progetto specifico.<br /><br /> Per visualizzare e modificare una classe esistente nel codice, usare Progettazione classi.<br /><br /> Vedere [Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|  
  
### <a name="DescribeSequence"></a> Vengono descritte le interazioni: Diagrammi di sequenza  
 I diagrammi di sequenza descrivono una serie di interazioni tra le parti di un sistema. Le parti possono essere di qualsiasi dimensione, da singoli oggetti di un programma a grandi sottosistemi o attori esterni. Le interazioni possono essere di qualsiasi entità e tipo, da singoli messaggi a transazioni estese, e possono essere chiamate di funzione o messaggi del servizio Web.  
  
 Per aiutare Lucerne e Dinner Now a descrivere e discutere i passaggi del caso d'uso Elaborazione dei pagamenti, dal diagramma dei componenti viene creato il seguente diagramma di sequenza. Le linee di vita rispecchiano il componente del sito Web di Dinner Now e le relative parti. I messaggi visualizzati tra le linee di vita seguono le connessioni sui diagrammi dei componenti:  
  
 ![Caso d'uso di diagramma di sequenza per l'elaborazione dei pagamenti](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")  
  
 **Diagramma di sequenza per l'elaborazione dei pagamenti caso d'uso**  
  
 Il seguente diagramma di sequenza mostra che il sito Web di Dinner Now chiama ElaboraOrdine su un'istanza di ElaborazioneOrdini quando il cliente crea un ordine. Quindi, ElaborazioneOrdini chiama ElaboraPagamento su ElaborazionePagamenti. Il processo continua finché il gateway esterno per l'elaborazione dei pagamenti non convalida il pagamento. Solo a quel punto il controllo torna al sito Web Dinner Now.  
  
 Lucerne deve stimare il costo di aggiornamento del sistema di pagamento per l'integrazione con il sistema di Dinner Now. Per facilitare il compito, potrebbe anche creare codice mappe per visualizzare le interazioni esistenti.  
  
 Vedere:  
  
- [Diagrammi di sequenza UML: riferimenti](../modeling/uml-sequence-diagrams-reference.md)  
  
- [Diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md)  
  
- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)  
  
#### <a name="drawing-a-sequence-diagram"></a>Creazione di un diagramma di sequenza  
 Le caratteristiche principali di un diagramma di sequenza sono le seguenti:  
  
- *Linee di vita* verticali, che rappresentano attori o istanze di oggetti del software.  
  
   Per aggiungere un simbolo Attore, che indica un partecipante esterno al sistema in corso di sviluppo, fare clic sulla linea di vita. Nella finestra **Proprietà** impostare **Attore** su **True**. Se la finestra **Proprietà** non viene visualizzata, premere **F4**.  
  
- *Messaggi* orizzontali, che rappresentano chiamate ai metodi, messaggi del servizio Web o altre comunicazioni. Le*occorrenze dell'esecuzione* sono rettangoli ombreggiati verticali che vengono visualizzati sulle linee di vita e rappresentano i periodi durante i quali gli oggetti riceventi elaborano le chiamate.  
  
- Durante una *sincrona* messaggio, l'oggetto mittente attende dal controllo <\<restituire >> come una normale chiamata di funzione. Durante un messaggio *asincrono* , il mittente può continuare immediatamente.  
  
- Usare <\<creare >> messaggi per indicare la costruzione di oggetti da altri oggetti. Deve essere il primo messaggio inviato all'oggetto.  
  
  Vedere:  
  
- [Diagrammi di sequenza UML: riferimenti](../modeling/uml-sequence-diagrams-reference.md)  
  
- [Diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-sequence-diagrams"></a>Riepilogo: Vantaggi dei diagrammi di sequenza  
 I diagrammi di sequenza consentono di visualizzare:  
  
- Il flusso di controllo trasferito tra attori o oggetti durante l'esecuzione di un caso d'uso.  
  
- L'implementazione di una chiamata di metodo o di un messaggio.  
  
#### <a name="relationship-to-other-diagrams"></a>Relazione con altri diagrammi  
  
|**Diagramma**|**Descrizione**|  
|-----------------|---------------------|  
|Diagramma classi (UML)|Le classi rappresentate dalle linee di vita e i parametri e i valori restituiti usati in messaggi inviati tra le linee di vita.<br /><br /> Per creare una classe da una linea di vita, fare clic il pulsante destro del mouse sulla linea di vita, quindi scegliere **Crea classe** o **Crea interfaccia**. Per creare una linea di vita in un diagramma classi da un tipo, fare clic il pulsante destro del mouse sul tipo e quindi scegliere **Crea linea di vita**.<br /><br /> Vedere:<br /><br /> -   [Diagrammi classi UML: Riferimento](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagramma dei componenti|I componenti rappresentati dalle linee di vita e le interfacce che forniscono e usano il comportamento rappresentato dai messaggi.<br /><br /> Per creare una linea di vita da un diagramma dei componenti, fare clic con il pulsante destro del mouse sul componente e scegliere **Crea linea di vita**.<br /><br /> Vedere:<br /><br /> -   [Diagrammi dei componenti UML: Riferimento](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagrammi dei componenti UML: linee guida](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagramma caso di utilizzo|Un riepilogo delle interazioni tra utenti e componenti in un diagramma di sequenza sotto forma di caso d'uso, che rappresenta l'obiettivo di un utente.<br /><br /> Vedere:<br /><br /> -   [Diagrammi caso di utilizzo UML: Riferimento](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagrammi caso di utilizzo UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md)|  
  
### <a name="DefineClasses"></a> Definire un glossario dei tipi: Diagrammi classi  
 I diagrammi classi definiscono le entità, i termini o i concetti che fanno parte del sistema e le reciproche relazioni. Ad esempio, è possibile usare questi diagrammi durante lo sviluppo per descrivere gli attributi e le operazioni per ogni classe, indipendentemente dal linguaggio o stile di implementazione.  
  
 Per aiutare Lucerne a descrivere e discutere le entità che partecipano al caso d'uso Elaborazione dei pagamenti, viene creato il diagramma classi seguente:  
  
 ![Entità Elabora pagamento nel diagramma classi](../modeling/media/uml-payentities.png "UML_PayEntities")  
  
 **Entità di Elaborazione dei pagamenti in un diagramma classi**  
  
 Questo diagramma mostra che a un cliente possono essere associati più ordini e modalità di pagamento differenti. ContoBancario e CartaDiCredito ereditano da Pagamento.  
  
 Durante lo sviluppo, Lucerne usa il seguente diagramma classi per descrivere e discutere i dettagli di ogni classe:  
  
 ![Elaborare i dettagli di pagamento di entità in un diagramma classi](../modeling/media/uml-payment.png "UML_Payment")  
  
 **Dettagli di Elaborazione dei pagamenti nel diagramma classi**  
  
 Vedere:  
  
- [Diagrammi delle classi UML: riferimenti](../modeling/uml-class-diagrams-reference.md)  
  
- [Diagrammi delle classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)  
  
#### <a name="drawing-a-class-diagram"></a>Creazione di un diagramma classi  
 Le caratteristiche principali di un diagramma classi sono le seguenti:  
  
- Tipi quali classi, interfacce ed enumerazioni:  
  
  - *Classe* : la definizione di oggetti che condividono caratteristiche strutturali o comportamentali specifiche.  
  
  - *Interfaccia* : la definizione di una parte del comportamento esternamente visibile di un oggetto.  
  
  - *Enumerazione* : un classificatore che contiene un elenco di valori letterali.  
  
- *Attributi* : valori di un determinato tipo che descrivono ogni istanza di un *classificatore*. Un classificatore è un nome generale per tipi, componenti, casi d'uso e persino attori.  
  
- *Operazioni* : metodi o funzioni che possono essere eseguite dalle istanze di un classificatore.  
  
- *Associazione* : indica un tipo di relazione tra due classificatori.  
  
  - *Aggregazione* : un'associazione che indica una proprietà condivisa tra classificatori.  
  
  - *Composizione* : un'associazione che indica una relazione di una parte con il tutto tra classificatori.  
  
    Per mostrare aggregazioni o composizioni, impostare la proprietà **Aggregazione** su un'associazione. **Condiviso** mostra le aggregazioni e **Composito** mostra le composizioni  
  
- *Dipendenza* : indica che la modifica della definizione di un classificatore potrebbe comportare la modifica della definizione di un altro classificatore.  
  
- *Generalizzazione* : indica che uno specifico classificatore eredita parte della definizione da un classificatore generale. *Realizzazione* : indica che una classe implementa le operazioni e gli attributi offerti da un'interfaccia.  
  
   Per creare le relazioni, usare lo strumento **Ereditarietà** . In alternativa, una realizzazione può essere rappresentata come *simbolo*.  
  
- *Pacchetti* : gruppi di classificatori, associazioni, linee di vita, componenti e altri pacchetti. *Importazione* : relazioni indicanti che un pacchetto include tutte le definizioni di un altro pacchetto.  
  
  Come punto di partenza per esplorare e discutere le classi esistenti, è possibile usare Progettazione classi per creare diagrammi classi dal codice.  
  
  Vedere:  
  
- [Diagrammi delle classi UML: riferimenti](../modeling/uml-class-diagrams-reference.md)  
  
- [Diagrammi delle classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)  
  
- [Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
#### <a name="summary-strengths-of-class-diagrams"></a>Riepilogo: Vantaggi dei diagrammi classi  
 I diagrammi classi consentono di definire:  
  
- Un glossario comune di termini da usare quando si discutono le esigenze degli utenti e le entità che partecipano al sistema. Visualizzare [modellare i requisiti utente](../modeling/model-user-requirements.md).  
  
- Tipi usati da parti del sistema, come i componenti, indipendentemente dalla relativa implementazione. Visualizzare [modellare l'architettura dell'applicazione](../modeling/model-your-app-s-architecture.md).  
  
- Le relazioni tra tipi, quali le dipendenze. Ad esempio, è possibile mostrare che un tipo può essere associato a più istanze di un altro tipo.  
  
#### <a name="relationship-to-other-diagrams"></a>Relazione con altri diagrammi  
  
|**Diagramma**|**Descrizione**|  
|-----------------|---------------------|  
|Diagramma caso di utilizzo|Definizione dei tipi usati per descrivere gli obiettivi e i passaggi nei casi d'uso.<br /><br /> Vedere:<br /><br /> -   [Diagrammi caso di utilizzo UML: Riferimento](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagrammi caso di utilizzo UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Diagramma di attività|Definizione dei tipi di dati che passano attraverso nodi oggetto, pin di input, pin di output e nodi parametro attività.<br /><br /> Vedere:<br /><br /> -   [Diagrammi di attività UML: Riferimento](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md)|  
|Diagramma dei componenti|Descrizione dei componenti e delle relative interfacce e relazioni. Una classe potrebbe anche descrivere un componente completo.<br /><br /> Vedere:<br /><br /> -   [Diagrammi dei componenti UML: Riferimento](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagrammi dei componenti UML: linee guida](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagramma livello|Definizione dell'architettura logica del sistema in relazione alle classi.<br /><br /> Usare la convalida dei livelli per assicurare la coerenza del codice con la progettazione.<br /><br /> Vedere:<br /><br /> -   [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammi livello: Riferimento](../modeling/layer-diagrams-reference.md)<br />-   [Diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md)<br />-   [Convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md)|  
|Diagramma sequenza|Definizione dei tipi di linee di vita e delle operazioni, dei parametri e dei valori restituiti per tutti i messaggi che la linea di vita può ricevere.<br /><br /> Per creare una linea di vita in un diagramma classi da un tipo, fare clic il pulsante destro del mouse sul tipo e quindi scegliere **Crea linea di vita**.<br /><br /> Vedere:<br /><br /> -   [Diagrammi di sequenza UML: Riferimento](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Mappa codice|Visualizzazione dell'organizzazione e delle relazioni nel codice esistente.<br /><br /> Per identificare le classi e le relative relazioni e metodi, creare una mappa codice che mostra quegli elementi.<br /><br /> Vedere:<br /><br /> -   [Mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)|  
  
### <a name="DescribeLayers"></a> Descrivere l'architettura logica: Diagrammi livello  
 I diagrammi livello descrivono l'architettura logica di un sistema organizzando gli elementi della soluzione in gruppi astratti o *livelli*. Gli elementi possono essere di vario tipo, ad esempio spazi dei nomi, progetti, classi, metodi e così via. I livelli rappresentano i ruoli o le attività svolte nel sistema da tali elementi. È anche possibile includere la convalida dei livelli nelle operazioni di compilazione e archiviazione per assicurare la coerenza del codice con la progettazione.  
  
 Per mantenere la coerenza del codice con la progettazione, Dinner Now e Lucerne usano il diagramma livello seguente per convalidare il codice di volta in volta modificato:  
  
 ![Diagramma di livello di sistema di pagamenti integrato](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagramma livello di Dinner Now integrato con Lucerne**  
  
 I livelli di questo diagramma sono collegati ai corrispondenti elementi delle soluzioni di Dinner Now e Lucerne. Ad esempio, il livello Business è collegato allo spazio dei nomi DinnerNow.Business e ai relativi membri, che ora includono la classe RespApprovazionePagamenti. Il livello Accesso risorse è collegato allo spazio dei nomi DinnerNow.Dati. Le frecce, o *dipendenze*, specificano che solo il livello Business può usare le funzionalità del livello Accesso risorse. Man mano che aggiornano il codice, i team eseguono regolarmente la convalida dei livelli per intercettare i conflitti che si verificano e risolverli prontamente.  
  
 I team collaborano per integrare e testare in modo incrementale i due sistemi. Prima di occuparsi di ElaborazionePagamenti, verificano il corretto funzionamento di RespApprovazionePagamenti con gli altri componenti di Dinner Now.  
  
 La mappa codice seguente mostra le nuove chiamate tra Dinner Now e RespApprovazionePagamenti:  
  
 ![Grafico delle dipendenze aggiornato con il sistema integrato](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")  
  
 **Mappa codice con le chiamate di metodo aggiornate**  
  
 Dopo aver verificato che il sistema funziona come previsto, Dinner Now imposta come commento il codice di ElaborazionePagamenti. I report di convalida dei livelli non segnalano problemi e la mappa codice risultante mostra che non esistono altre dipendenze di ElaborazionePagamenti:  
  
 ![Grafico delle dipendenze senza ElaborazionePagamenti](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")  
  
 **Codice mappa senza ElaborazionePagamenti**  
  
#### <a name="drawing-a-layer-diagram"></a>Creazione di un diagramma livello  
 Le caratteristiche principali di un diagramma livello sono le seguenti:  
  
- *Livelli* : descrivono gruppi logici di elementi.  
  
- *Collegamento* : un'associazione tra un livello e un elemento.  
  
   Per creare livelli dagli elementi, trascinare gli elementi da Esplora soluzioni, da mappe codice, da Visualizzazione classi o da Visualizzatore oggetti. Per disegnare nuovi livelli e collegarli agli elementi, usare la casella degli strumenti o fare clic con il pulsante destro del mouse sulla superficie del diagramma per creare i livelli, quindi trascinare gli elementi su tali livelli.  
  
   Il numero specificato su un livello indica il numero di elementi a esso collegati. Questi elementi possono essere spazi dei nomi, progetti, classi, metodi e così via. Quando si interpreta il numero di elementi in un livello, tenere presente quanto segue:  
  
  - Se un livello è collegato a un elemento contenente altri elementi, ma non è collegato direttamente ad altri elementi, il numero include solo l'elemento collegato. Tuttavia, gli altri elementi vengono inclusi per l'analisi durante la convalida dei livelli.  
  
     Ad esempio, se un livello è collegato a un solo spazio dei nomi, il numero degli elementi collegati sarà 1, anche se lo spazio dei nomi contiene classi. Se il livello è collegato anche a ciascuna classe dello spazio dei nomi, il numero includerà le classi collegate.  
  
  - Se un livello contiene altri livelli collegati a elementi, anche il livello contenitore sarà collegato a tali elementi nonostante il numero raffigurato sul livello contenitore non includa quegli elementi.  
  
    Per visualizzare gli elementi collegati a un livello, fare clic con il pulsante destro del mouse su un livello, quindi scegliere **Visualizza collegamenti** per aprire **Esplora livello**.  
  
- *Dipendenza* : indica che un livello può usare le funzionalità di un altro livello, ma non viceversa. *Dipendenza bidirezionale* : indica che un livello può usare le funzionalità di un altro livello e viceversa.  
  
   Per visualizzare le dipendenze esistenti nel diagramma livello, fare clic con il pulsante destro del mouse sulla superficie del diagramma e scegliere **Genera dipendenze**. Per descrivere le dipendenze previste, disegnarne altre.  
  
  Vedere:  
  
- [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)  
  
- [Diagrammi dei livelli: riferimenti](../modeling/layer-diagrams-reference.md)  
  
- [Diagrammi dei livelli: linee guida](../modeling/layer-diagrams-guidelines.md)  
  
- [Convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md)  
  
#### <a name="summary-strengths-of-layer-diagrams"></a>Riepilogo: Vantaggi dei diagrammi livello  
 I diagrammi livello consentono di:  
  
- Descrivere l'architettura logica di un sistema in base alle funzionalità degli elementi.  
  
- Assicurarsi che il codice in corso di sviluppo sia conforme alla progettazione specificata.  
  
#### <a name="relationship-to-other-diagrams"></a>Relazione con altri diagrammi  
  
|**Diagramma**|**Descrizione**|  
|-----------------|---------------------|  
|Mappa codice|Visualizzazione dell'organizzazione e delle relazioni nel codice esistente.<br /><br /> Per creare livelli, generare una mappa codice e quindi raggruppare gli elementi della mappa come potenziali livelli. Trascinare i gruppi dalla mappa nel diagramma livello.<br /><br /> Vedere:<br /><br /> -   [Mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Cercare e ridisporre le mappe codice](../modeling/browse-and-rearrange-code-maps.md)|  
|Diagramma dei componenti|Descrizione dei componenti e delle relative interfacce e relazioni.<br /><br /> Per visualizzare i livelli, creare un diagramma dei componenti che descrive le funzionalità dei vari componenti del sistema.<br /><br /> Vedere:<br /><br /> -   [Diagrammi dei componenti UML: Riferimento](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagrammi dei componenti UML: linee guida](../modeling/uml-component-diagrams-guidelines.md)|  
  
## <a name="external-resources"></a>Risorse esterne  
  
|**Categoria**|**Links**|  
|------------------|---------------|  
|**Forum**|-   [Visual Studio Visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization and Modeling SDK (strumenti DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare il codice](../modeling/visualize-code.md)   
 [Creare modelli per l'app](../modeling/create-models-for-your-app.md)   
 [Usare i modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)   
 [Usare i modelli nello sviluppo Agile](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)   
 [Convalidare il sistema durante lo sviluppo](../modeling/validate-your-system-during-development.md)   
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)
