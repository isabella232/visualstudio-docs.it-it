---
title: 'Diagrammi dei componenti UML: Linee guida | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: aa08a132c752b5bdde7ba2b497a6bd206e8f2972
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843847"
---
# <a name="uml-component-diagrams-guidelines"></a>Diagrammi dei componenti UML: linee guida
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, è possibile creare un *diagramma dei componenti* per mostrare la struttura di un sistema software. Per una dimostrazione video, vedere [progettazione della struttura fisica tramite i diagrammi componente](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/).  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Per creare un diagramma dei componenti UML, nelle **Architecture** menu, fare clic su **nuovo diagramma livello o UML**.  
  
 Un componente è un'unità modulare sostituibile all'interno dell'ambiente. Gli elementi interni sono nascosti, ma ne ha uno o più ben definiti *interfacce fornite* tramite cui le funzioni sono accessibili. Un componente può anche contenere *interfacce necessarie*. Un'interfaccia richiesta definisce le funzioni o i servizi necessari presenti in altri componenti. Connettendo le interfacce fornite e richieste di diversi componenti, è possibile costruire un componente più grande. Un sistema software completo può essere considerato come un componente.  
  
 La creazione dei diagrammi dei componenti comporta diversi vantaggi:  
  
- Il concetto di progettazione in relazione ai blocchi principali consente al team di sviluppo di comprendere una progettazione esistente e di crearne una nuova.  
  
- Considerando il sistema come una raccolta di componenti con interfacce fornite e richieste ben definite, è possibile migliorare la separazione tra i componenti. Questa operazione consente a sua volta di comprendere la progettazione più facilmente e di modificarla qualora vengano modificati i requisiti.  
  
  È possibile usare un diagramma dei componenti per rappresentare la progettazione indipendentemente dalla lingua o dalla piattaforma usata.  
  
##  <a name="OtherDiagrams"></a> Relazione con altri diagrammi  
 È possibile utilizzare un diagramma dei componenti insieme ad altri diagrammi.  
  
|Altro diagramma|Discussione e comunicazione dei seguenti aspetti della progettazione|  
|-------------------|--------------------------------------------------------------------|  
|Diagramma di sequenza UML|-Le interazioni tra componenti del sistema<br />-Le interazioni tra le parti all'interno di un componente.<br /><br /> Per altre informazioni, vedere [diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md).|  
|Diagramma classi UML|-Le interfacce di un componente. Il diagramma classi consente di descrivere in dettaglio i metodi di interfaccia.<br />-I dati inviati nei parametri attraverso le interfacce dei componenti.<br /><br /> Per altre informazioni, vedere [diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md).|  
|Diagrammi di attività|-L'elaborazione interna eseguita da un componente in risposta ai messaggi in arrivo.<br /><br /> Per altre informazioni, vedere [diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md).|  
|Diagrammi livello|-Livelli architetturali logici per i componenti.<br /><br /> Per altre informazioni, vedere [diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md).|  
  
##  <a name="Basics"></a> Passaggi di base per la creazione di diagrammi componente  
 Per informazioni di riferimento sugli elementi nei diagrammi dei componenti, vedere [diagrammi dei componenti UML: riferimento](../modeling/uml-component-diagrams-reference.md).  
  
 Per altre informazioni su come usare i diagrammi dei componenti nel processo di progettazione, vedere [modellare l'architettura dell'applicazione](../modeling/model-your-app-s-architecture.md).  
  
> [!NOTE]
>  I passaggi dettagliati per la creazione dei diagrammi di modellazione sono descritte nel [modelli e diagrammi UML modifica](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-component-diagram"></a>Per creare un diagramma dei componenti  
  
1.  Nel **Architecture** menu, fare clic su **nuovo diagramma livello o UML**.  
  
2.  Sotto **modelli**, fare clic su **diagramma componente UML**.  
  
3.  Assegnare un nome al diagramma.  
  
4.  Nelle **aggiungere al progetto di modellazione**, selezionare un progetto di modellazione esistente nella soluzione, o **creare un nuovo progetto di modellazione**, quindi fare clic su **OK**...  
  
     Viene visualizzato un nuovo diagramma componente con il modello UML **diagramma dei componenti** della casella degli strumenti. La casella degli strumenti contiene le relazioni e gli elementi necessari.  
  
### <a name="drawing-components"></a>Creazione dei componenti  
 ![Componenti con interfacce](../modeling/media/uml-compdrawing.png "UML_CompDrawing")  
  
 Creare un *componente* (1) per ogni unità funzionale principale nel sistema o nell'applicazione.  
  
 Gli esempi includono un'applicazione, un dispositivo hardware, un servizio Web, un assembly .NET, una classe o un gruppo di classi di programma oppure qualsiasi segmento separabile di un programma.  
  
##### <a name="to-create-components"></a>Per creare i componenti  
  
1.  Fare clic su **componente** della casella degli strumenti, quindi fare clic su una parte vuota del diagramma.  
  
     \- oppure -  
  
     Copiare e incollare un componente esistente.  
  
    1.  Trovare un componente esistente in un diagramma o nel **Esplora modelli UML**.  
  
    2.  Fare clic sul componente e quindi fare clic su **copia**.  
  
    3.  Aprire il diagramma in cui si desidera che venga visualizzato il componente copiato.  
  
    4.  Fare doppio clic su una parte vuota del diagramma e quindi fare clic su **Incolla**.  
  
         Verrà visualizzata una copia del componente con un nuovo nome.  
  
2.  Fare clic sul nome del componente per modificarlo.  
  
3.  Fare clic sulla freccia di espansione (5) se si desidera visualizzare solo l'intestazione del componente.  
  
### <a name="showing-the-ports-of-a-component"></a>Visualizzazione delle porte di un componente  
 Oggetto *porta* (2, 3) rappresenta un gruppo di messaggi o chiamate di operazioni che passano all'interno o all'esterno di un componente. Il gruppo viene descritto da un'interfaccia che definisce il tipo della porta. Una porta può fornire o richiedere un'interfaccia.  
  
 Una porta con un *interfaccia fornita* (2) fornisce le operazioni che vengono implementate dal componente e che può essere utilizzato da altri componenti.  
  
 Alcuni esempi sono un'interfaccia utente, un servizio Web, un'interfaccia .NET o una raccolta di funzioni in qualsiasi linguaggio di programmazione.  
  
 Una porta con un *interfaccia richiesta* (3) rappresenta il requisito di un componente per un gruppo di operazioni o servizi devono essere fornite da altri componenti o sistemi esterni.  
  
 Ad esempio, un Web browser richiede server Web o un componente aggiuntivo dell'applicazione richiede i servizi dall'applicazione.  
  
 Un componente può contenere un qualsiasi numero di porte.  
  
##### <a name="to-add-ports-to-a-component"></a>Per aggiungere le porte a un componente  
  
1. Nella casella degli strumenti, fare clic su **interfaccia fornita** oppure **interfaccia richiesta**.  
  
2. Fare clic sul componente a cui si desidera aggiungere la porta.  
  
    Una porta verrà visualizzata sul limite del componente.  
  
    Una nuova interfaccia verrà creata come tipo della porta. Questa interfaccia viene visualizzata **Esplora modelli UML**.  
  
3. Trascinare la porta sul limite del componente per posizionarla nel punto desiderato.  
  
4. Trascinare l'etichetta della porta per regolarne la posizione.  
  
5. Fare clic sull'etichetta per modificarla. L'etichetta mostra il nome dell'interfaccia. Se si modifica l'etichetta, si modificherà il nome dell'interfaccia.  
  
   Se si desidera elencare gli attributi e le operazioni dell'interfaccia, è possibile aggiungerli all'interfaccia in Esplora modelli UML. In alternativa, è possibile trascinare l'interfaccia da Esplora modelli UML in un diagramma classi e aggiungere le operazioni e gli attributi in tale posizione.  
  
### <a name="linking-between-components"></a>Collegamento tra componenti  
 Usare una dipendenza (4) per mostrare che il requisito di un componente può essere soddisfatto dalle operazioni o dai servizi forniti da un altro componente.  
  
##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>Per mostrare che un'interfaccia fornita può soddisfare un'interfaccia richiesta  
  
1. Nella casella degli strumenti, fare clic su **dipendenza**.  
  
2. Fare clic sulla porta con l'interfaccia richiesta in un componente, quindi fare clic sulla porta con l'interfaccia fornita in un altro componente.  
  
   È consigliabile evitare di progettare cicli di dipendenza in cui ogni componente di un gruppo dipende da tutti gli altri componenti.  
  
##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>Per aggiungere una porta di un'interfaccia esistente a un componente  
  
-   Trovare l'interfaccia **Esplora modelli UML** e quindi trascinarla sul componente.  
  
     oppure  
  
-   Copiare e incollare un riferimento a un'interfaccia da un diagramma.  
  
    1.  In un diagramma classi o un diagramma dei componenti, fare doppio clic dell'interfaccia e quindi fare clic su **copia**.  
  
    2.  Nel diagramma dei componenti, fare clic sul componente e quindi fare clic su **Incolla riferimento**.  
  
         Un'interfaccia fornita verrà visualizzata nel componente e accanto viene visualizzato un tag azioni.  
  
        > [!NOTE]
        >  Se si usa **Incolla** invece di **Incolla riferimento**, verrà creata una nuova interfaccia con un nuovo nome.  
  
    3.  Se si vuole creare un'interfaccia richiesta, fare clic sul tag azioni e quindi fare clic su **Converti in interfaccia richiesta**.  
  
##  <a name="Parts"></a> Visualizzazione delle parti interne di un componente  
 ![Diagramma dei componenti che mostra le parti interne](../modeling/media/uml-compshowing.png "UML_CompShowing")  
  
 È possibile posizionare le parti (3) di un componente (1) in modo da mostrare come sia costituito da componenti più piccoli che interagiscono tra di loro.  
  
 Il diagramma nell'illustrazione indica che ogni istanza del tipo Dinner Now Web Service contiene un'istanza di Customer Server e un'istanza di Kitchen Server.  
  
 Una parte è una proprietà del componente padre, molto simile a un attributo appartenente a una classe ordinaria. Una parte dispone di un proprio tipo che generalmente è anche un componente. L'etichetta della parte ha lo stesso formato di un attributo ordinario:  
  
 `+ partName : TypeName`  
  
 Nel componente padre ogni parte mostra le interfacce fornite e richieste definite per il tipo (4, 5). Le operazioni o i servizi richiesti da una parte possono essere forniti da un'altra parte. È possibile usare **Assembly parti** connettori per illustrare come le parti sono connesse tra loro (6).  
  
 È inoltre possibile illustrare che un'interfaccia del componente padre è in effetti fornita o richiesta da una delle relative parti. È possibile connettere una porta dell'elemento padre a una porta di una parte interna usando un **delega** relazione (9). Le due porte devono essere dello stesso tipo (fornito o richiesto) e i tipi di interfaccia devono essere compatibili.  
  
 È possibile creare una nuova parte con un nuovo tipo o da un tipo esistente.  
  
#### <a name="to-add-parts-to-a-component"></a>Per aggiungere le parti a un componente  
  
1.  Creare una parte per ogni unità funzionale principale che si considera parte del componente padre.  
  
    1.  Fare clic su **componente** nella casella degli strumenti e quindi fare clic su nel componente padre (1).  
  
         Una nuova parte (3) verrà visualizzata nel componente padre.  
  
         Viene creato un nuovo componente nel **Esplora modelli UML**. Si tratta del tipo della nuova parte.  
  
         \- oppure -  
  
         Trascinare un componente esistente da Esplora modelli UML nel componente padre.  
  
         Una nuova parte (3) verrà visualizzata nel componente padre. Il tipo è il componente trascinato da Esplora modelli UML.  
  
         \- oppure -  
  
         Fare doppio clic su un componente in un diagramma o in Esplora modelli UML e quindi fare clic su **copia**.  
  
         Fare clic sul componente padre e quindi fare clic su **Incolla riferimento**.  
  
         Una nuova parte (3) verrà visualizzata nel componente padre. Il tipo è il componente copiato.  
  
    2.  Fare clic sul nome della nuova parte per modificarlo. Non è possibile modificarne il tipo.  
  
    3.  È possibile aggiungere alla nuova parte le interfacce fornite e richieste (4, 5). Fare clic sui **interfaccia fornita** oppure **interfaccia richiesta** dello strumento e quindi fare clic su nella parte.  
  
         \- oppure -  
  
         Trascinare un'interfaccia esistente da **Esplora modelli UML** sulla parte.  
  
         Le interfacce verranno aggiunte al tipo della parte e verranno visualizzate nella parte stessa. Se necessario, il componente padre modifica la dimensione.  
  
2.  Connettere le parti tra loro.  
  
    -   Usare la **dipendenza** dello strumento per connettere le porte di parti diverse (6).  
  
3.  Connettere le parti alle porte del componente padre:  
  
    1.  Creare uno o più porte (7) nel componente padre. Fare clic su **interfaccia richiesta** oppure **interfaccia fornita** della casella degli strumenti, quindi fare clic sul componente padre.  
  
    2.  Delegare (9) la porta a una o più parti. Scegliere il **delega** strumento, quindi una porta nel componente padre e quindi una porta in una parte. È possibile connettere le porte che forniscono o richiedono le interfacce allo stesso modo.  
  
### <a name="showing-the-parts-of-a-part"></a>Visualizzazione delle parti di una parte  
 Dopo avere scomposto un componente in parti, è possibile scomporre ogni tipo della parte nelle relative parti interne.  
  
 È più facile eseguire ogni livello di scomposizione in un diagramma dei componenti separato. È necessario innanzitutto individuare il tipo della parte. Ad esempio, nell'illustrazione una delle parti è denominata `DNCustomerServer` e il relativo tipo è un componente denominato `CustomerServer`. È possibile trovare il tipo in Esplora modelli UML e posizionarlo in un altro diagramma. È possibile quindi creare le relative parti interne.  
  
##### <a name="to-place-a-parts-type-on-a-diagram"></a>Per posizionare il tipo di una parte in un diagramma  
  
1.  Determinare il nome completo del tipo della parte.  
  
     Fare doppio clic la parte e quindi fare clic su **proprietà**.  
  
     Il nome del tipo viene visualizzato nei **tipo** campo della finestra Proprietà.  
  
2.  Individuare il tipo della parte nelle **Esplora modelli UML**.  
  
     Fare clic su **View**, scegliere **Other Windows**, quindi fare clic su **Esplora modelli UML**.  
  
     Espandere il progetto e se necessario il pacchetto a cui appartiene il tipo.  
  
     Il tipo verrà elencato come un **componente**.  
  
     Se si desidera, è possibile modificarne il nome.  
  
3.  Aprire o creare un altro diagramma dei componenti.  
  
4.  Trascinare dal tipo in Esplora modelli UML nel diagramma.  
  
     Una visualizzazione del tipo apparirà come componente nel diagramma.  
  
     Avrà le stesse interfacce definite per la parte.  
  
     È ora possibile aggiungervi le parti.  
  
##  <a name="Designing"></a> Progettazione del componente  
  
### <a name="describing-how-the-parts-collaborate"></a>Descrizione del modo in cui collaborano le parti  
 È possibile creare un diagramma di sequenza per illustrare il modo in cui le parti collaborano in risposta a un messaggio che arriva nel componente padre.  
  
 È possibile usare questi diagrammi sia per illustrare un componente esistente che per progettare un nuovo componente.  
  
 Se il componente è ancora in fase di progettazione, è possibile creare i diagrammi di sequenza prima di decidere le parti che conterrà. È possibile usare i diagrammi di sequenza per sperimentare parti diverse, interfacce richieste e sequenze di messaggi. Creare i diagrammi di sequenza per i messaggi in arrivo più frequenti e più importanti. È possibile creare quindi le parti nel componente che corrispondono alle linee di vita scelte.  
  
 Usare i diagrammi di sequenza per valutare il modo in cui il lavoro del sistema viene distribuito tra i diversi componenti.  
  
- Se su una parte viene caricato troppo lavoro, probabilmente sarà più difficile aggiornare l'applicazione, rispetto a una condizione in cui il carico di lavoro viene distribuito in modo uniforme.  
  
- Se invece il carico lavoro viene distribuito alleggerendo in maniera eccessiva le parti con molte interazioni, il sistema potrebbe venire eseguito in modo non corretto e la comprensione potrebbe risultare più complessa.  
  
  ![Diagramma con collaborazione parti di sequenza](../modeling/media/uml-compdescparts.png "UML_CompDescParts")  
  
##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>Per creare un diagramma di sequenza che illustri la collaborazione tra le parti  
  
1.  Creare un nuovo diagramma di sequenza.  
  
     Per altre informazioni, vedere [diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md).  
  
2.  Creare una linea di vita per un componente esterno, un utente, un dispositivo o un altro attore (1) che invia messaggi a questo componente.  
  
     È possibile impostare il **attore** proprietà di questa linea di vita su true per indicare che è esterno al componente in fase di analisi. Sopra la linea di vita viene visualizzata una figura stilizzata.  
  
3.  Creare una linea di vita per l'interfaccia fornita (2) di questo componente a cui l'attore scelto invia i messaggi.  
  
4.  Creare una linea di vita per ogni parte (3) del componente.  
  
5.  Creare una linea di vita per ogni interfaccia richiesta (4) del componente.  
  
6.  Creare i messaggi dall'attore esterno (5). Mostrare come il messaggio viene passato alle parti e come esse collaborano per rispondere al messaggio.  
  
7.  Se necessario, mostrare i messaggi inviati in un'interfaccia richiesta (6). Non mostrare alcun dettaglio all'interno dell'esecuzione del messaggio.  
  
### <a name="is-the-component-more-than-its-parts"></a>Il componente vale più delle relative parti?  
 In alcuni casi, un componente rappresenta solo un nome assegnato a una raccolta di parti. Tutto il lavoro viene svolto dalle parti e in fase di esecuzione non è presente un codice né un altro artefatto che rappresenti il componente.  
  
 È possibile indicarlo nel modello impostando il **Is Indirectly Instantiated** proprietà del componente. In questo caso, tutte le interfacce del componente devono trovarsi sulle porte, con deleghe alle parti interne.  
  
### <a name="describing-the-process-inside-each-part"></a>Descrizione del processo all'interno di ogni parte  
 È possibile usare i diagrammi di attività per illustrare come un componente elabori ogni messaggio in arrivo. Per altre informazioni, vedere [diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Diagramma di attività con buffer di dati](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")  
  
 Usare la proprietà Accept Event Action (1) per indicare che un messaggio in arrivo avvia un nuovo thread.  
  
 Usare i nodi dell'oggetto e i pin di input/output per mostrare il flusso di informazioni e dove vengono archiviate le informazioni. Nell'esempio un nodo dell'oggetto (2) viene usato per mostrare gli elementi memorizzati nel buffer tra un thread e l'altro.  
  
### <a name="defining-data-and-classes"></a>Definizione di dati e classi  
 È possibile usare un diagramma classi UML per descrivere il contenuto dettagliato di:  
  
-   Interfacce dei componenti. Quando si aggiunge una richiesta o si fornisce una porta a un componente, in Esplora modelli UML viene visualizzata un'interfaccia. È possibile trascinare o copiare tale interfaccia in un diagramma classi UML per visualizzarne attributi, operazioni e relazioni con altre interfacce.  
  
-   Dati passati nei parametri delle operazioni delle interfacce.  
  
-   Dati archiviati nei componenti, ad esempio come illustrato nei flussi dell'oggetto dei diagrammi di attività.  
  
### <a name="general-dependencies-between-components"></a>Dipendenze generali tra componenti  
 È possibile usare un diagramma dei componenti solo per illustrare le parti principali della progettazione e le relative interdipendenze.  
  
 ![Una dipendenza tra i componenti](../modeling/media/uml-compdepend.png "UML_CompDepend")  
  
 Usare la **dipendenza** dello strumento per creare una dipendenza. In questo modo viene indicato che la progettazione di un componente si basa su un altro componente.  
  
 Tra i comuni tipi di dipendenza sono inclusi i seguenti:  
  
- Un componente chiama il codice all'interno di un altro componente.  
  
- Un componente crea un'istanza di una classe definita all'interno di un'altra classe.  
  
- Un componente usa le informazioni create da un altro componente.  
  
  È possibile usare il nome della freccia di dipendenza per indicare un particolare tipo di utilizzo. Per impostare il nome, fare doppio clic sulla freccia, quindi fare clic su **delle proprietà**e impostare le **nome** campo nella finestra Proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrammi dei componenti UML: riferimento](../modeling/uml-component-diagrams-reference.md)   
 [Diagrammi di sequenza UML: riferimento](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagrammi caso di utilizzo UML: riferimento](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagrammi classi UML: riferimento](../modeling/uml-class-diagrams-reference.md)   
 [Diagrammi dei componenti UML: riferimento](../modeling/uml-component-diagrams-reference.md)   
 [Video: Progettazione della struttura fisica tramite i diagrammi componente](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/)



