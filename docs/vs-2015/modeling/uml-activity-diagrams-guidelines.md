---
title: 'Diagrammi di attività UML: Linee guida | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
ms.assetid: fe5dbe96-79ab-483a-b9bc-44d0d1d3efc2
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 626be40ed9889ff7d16c07d511cbd060232412af
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105067"
---
# <a name="uml-activity-diagrams-guidelines"></a>Diagrammi di attività UML: Indicazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio è possibile tracciare un diagramma di attività per descrivere un processo aziendale o un algoritmo software come flusso di lavoro attraverso una serie di azioni. Queste azioni possono essere eseguite da persone, componenti software o dispositivi. Per una dimostrazione video, vedere: [Acquisire flussi di lavoro aziendali mediante diagrammi di attività](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-4-Capture-Business-Workflows/).  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Per creare un diagramma attività UML, scegliere il **Architecture** menu, fare clic su **nuovo diagramma livello o UML**.  
  
 È possibile usare un diagramma di attività per molti scopi:  
  
- Descrivere un processo aziendale o un flusso di lavoro tra gli utenti e il sistema. Per altre informazioni, vedere [modellare i requisiti utente](../modeling/model-user-requirements.md).  
  
- Descrivere i passaggi eseguiti in un caso di utilizzo. Per altre informazioni, vedere [diagrammi caso d'uso UML: Linee guida](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- Descrivere un metodo, una funzione o un'operazione nel software. Per altre informazioni, vedere [modellare l'architettura dell'applicazione](../modeling/model-your-app-s-architecture.md).  
  
  La creazione di un diagramma di attività può contribuire a migliorare un processo. Se il diagramma di un processo esistente si rivela molto complesso, è possibile valutare come semplificare tale processo.  
  
  Per informazioni di riferimento sugli elementi in diagrammi di attività, vedere [diagrammi di attività UML: informazioni di riferimento](../modeling/uml-activity-diagrams-reference.md).  
  
## <a name="Relationships"></a> Relazione con altri diagrammi  
 Se si traccia un diagramma di attività per descrivere un processo aziendale o il modo in cui gli utenti usano il sistema, è possibile scegliere un diagramma caso di utilizzo per mostrare una visualizzazione diversa delle stesse informazioni. Nel diagramma caso di utilizzo le azioni vengono tracciate come casi di utilizzo. Assegnare ai casi di utilizzo gli stessi nomi delle azioni corrispondenti. Ecco i vantaggi della visualizzazione dei casi di utilizzo, che permettono di:  
  
- Mostrare in un unico diagramma il modo in cui azioni/casi di utilizzo più grandi sono costituiti da elementi più piccoli, usando la relazione Include.  
  
- Connettere ogni azione/caso di utilizzo in modo esplicito agli utenti o ai sistemi esterni interessati dalla sua esecuzione.  
  
- Tracciare limiti attorno alle azioni e/o ai casi di utilizzo supportati dal sistema o da ogni componente principale.  
  
  È anche possibile tracciare un diagramma di attività per descrivere la progettazione dettagliata di un'operazione del software.  
  
  In un diagramma di attività è possibile mostrare il flusso di dati passati tra le azioni. Vedere la sezione sulla [descrizione del flusso di dati](#DataFlows). Un diagramma di attività non descrive la struttura dei dati. Per questo scopo, è possibile tracciare un diagramma classi UML. Per informazioni vedere [diagrammi classi UML: Linee guida](../modeling/uml-class-diagrams-guidelines.md).  
  
## <a name="BasicSteps"></a> Passaggi di base per la creazione di diagrammi di attività  
 I passaggi dettagliati per la creazione dei diagrammi di modellazione sono descritte nel [modelli e diagrammi UML modifica](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-draw-an-activity-diagram"></a>Per tracciare un diagramma di attività  
  
1. Nel **Architecture** menu, fare clic su **nuovo diagramma livello o UML**.  
  
2. Sotto **modelli**, fare clic su **diagramma attività UML**.  
  
3. Assegnare un nome al diagramma.  
  
4. Nelle **aggiungere al progetto di modellazione**, selezionare un progetto di modellazione esistente nella soluzione, o **creare un nuovo progetto di modellazione**.  
  
#### <a name="to-draw-elements-on-an-activity-diagram"></a>Per tracciare elementi in un diagramma attività  
  
1. Trascinare gli elementi dalla Casella degli strumenti nel diagramma.  
  
     Iniziare inserendo le attività principali nel diagramma, quindi connetterle e infine aggiungere i tocchi finali, come i nodi iniziali e finali.  
  
    > [!NOTE]
    >  Non è possibile trascinare elementi esistenti nel diagramma da Esplora modelli UML.  
  
2. Per collegare gli elementi, eseguire le operazioni seguenti:  
  
    1. Nel **diagramma di attività** della casella degli strumenti, fare clic su **connettore**.  
  
    2. Nel diagramma fare clic sull'elemento di origine.  
  
    3. Fare clic sull'elemento di destinazione.  
  
        > [!NOTE]
        >  Per usare uno strumento più volte, fare doppio clic sullo strumento nella Casella degli strumenti.  
  
#### <a name="to-move-an-activity-to-another-package"></a>Per spostare un'attività in un altro pacchetto  
  
- Nelle **Esplora modelli UML**, trascinare l'attività in un pacchetto.  
  
     \- oppure -  
  
- Nelle **Esplora modelli UML**, fare doppio clic su attività e fare clic su **Taglia**. Quindi fare doppio clic su pacchetto e fare clic su **Incolla**.  
  
    > [!NOTE]
    >  L'attività verrà visualizzata in Esplora modelli UML solo quando si aggiunge il primo elemento al diagramma.  
  
## <a name="SimpleControlFlow"></a> Descrizione del flusso di controllo  
 Un diagramma di attività descrive un processo aziendale o un algoritmo software come una serie di azioni. Le frecce del connettore mostrano il modo in cui il controllo viene passato in sequenza da un'azione alla successiva. In genere, un'azione può iniziare solo dopo che è stata completata quella precedente.  
  
 La figura seguente è un esempio di come è possibile mostrare una sequenza di azioni con azioni, connettori, rami e cicli. Ogni elemento viene descritto più dettagliatamente nelle sezioni seguenti.  
  
 ![Diagramma di attività semplice](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")  
  
 Diagrammi di attività usano **azioni** e **connettori** per descrivere il sistema o l'applicazione come una serie di azioni con il controllo che passa in sequenza da un'azione alla successiva.  
  
- Creare un **azione** (1) per ogni attività principale eseguita da un utente, il sistema o entrambi in collaborazione.  
  
  > [!NOTE]
  >  Provare a descrivere il processo o l'algoritmo con solo poche azioni. È possibile usare **azioni chiama comportamento** per definire ogni azione in modo più dettagliato in un diagramma separato, come descritto in [descrizione di sottoattività con azioni chiama comportamento](#Subactivities).  
  
- Assicurarsi che il titolo di ogni azione indichi chiaramente che cosa viene ottenuto in genere.  
  
- Collegare le azioni in sequenza con **connettori** (2).  
  
- Ogni azione termina prima che inizi quella successiva nel flusso di controllo. Se si vuole descrivere azioni che si sovrappongono, usare una **nodo Fork** come descritto nella sezione [flussi simultanei](#Concurrent).  
  
  Benché il diagramma descriva la sequenza di azioni, non descrive il modo in cui vengono eseguite le azioni o in cui viene passato il controllo da un'azione alla successiva. Se il diagramma viene usato per rappresentare un processo aziendale, il controllo può essere passato, ad esempio, quando una persona invia un messaggio di posta elettronica a un'altra. Se il diagramma viene usato per rappresentare una progettazione software, il controllo può essere passato tramite il normale flusso di esecuzione da un'istruzione alla successiva.  
  
### <a name="describing-decisions-and-loops"></a>Descrizione di decisioni e cicli  
  
- Usare un **nodo decisione** (3) per indicare un punto in cui il risultato di una decisione determina il passaggio successivo. È possibile tracciare tutti i percorsi di uscita desiderati.  
  
- Se il diagramma di attività viene usato per rappresentare parte di un'applicazione, è consigliabile definire guard (4) in modo che sia chiaro quando è necessario seguire un determinato percorso. Il pulsante destro del connettore, fare clic su **proprietà**e il **proprietà** finestra, digitare un valore per il **Guard** campo.  
  
- Non è sempre necessario definire guard. Ad esempio, se il diagramma di attività viene usato per descrivere un processo aziendale o un protocollo di interazione, un ramo definisce l'intervallo di opzioni aperte all'utente o ai componenti che interagiscono.  
  
- Usare un **nodo di tipo Merge** (5) per riunire due o più flussi alternativi che rami in corrispondenza di un **nodo decisione**.  
  
    > [!NOTE]
    >  È consigliabile usare un **nodo unione** per riunire flussi alternativi, invece di riunire flussi in corrispondenza di un'azione. Nell'esempio, non sarebbe corretto per la connessione dal nodo decisione direttamente nel **voce di Menu scegliere**. Il motivo è che un'azione non inizia fino a quando i thread di controllo non arrivano a tutti i connettori in ingresso. Di conseguenza, è consigliabile riunire solo i flussi simultanei in corrispondenza di un'azione. Per altre informazioni, vedere [flussi simultanei](#Concurrent).  
  
- Usare rami per descrivere i cicli, come mostrato nell'esempio.  
  
    > [!NOTE]
    >  Provare ad annidare i cicli in modo ben strutturato, come in un codice programma. Se si descrive un processo aziendale esistente, questo comportamento potrebbe offrire alcune opportunità per migliorarlo.  
  
### <a name="starting-the-activity"></a>Avvio dell'attività  
 Esistono due modi per indicare punti di ingresso in un'attività:  
  
- **Nodo iniziale**  
  
     Crearne uno **iniziale dei nodi** (6) per indicare la prima azione dell'attività.  
  
     Questo metodo è particolarmente utile quando si descrive una sottoattività o quando non è necessario dichiarare in modo esplicito che cosa avvia l'attività. Ad esempio, l'attività Ordinare un pasto inizia chiaramente quando un cliente ha fame.  
  
- **Nodo accetta evento**  
  
     Creare **nodi accetta evento**, come descritto nella sezione [flussi simultanei](#Concurrent), per indicare l'inizio di un thread che risponde a un evento specifico, ad esempio un input dell'utente. Non specificare un flusso in ingresso nel nodo. L'omissione di un flusso in ingresso indica che un thread verrà avviato ogni volta che si verifica l'evento.  
  
     Questo metodo è particolarmente utile per descrivere una risposta a un evento esterno specifico.  
  
### <a name="ending-the-activity"></a>Fine dell'attività  
 Usa un' **nodo finale attività** (7) per indicare la fine di un'attività.  
  
- Quando un thread di controllo raggiunge un' **nodo finale attività**, azioni simultanee dell'attività e le sottoattività terminano.  
  
- È possibile usare più di un nodo finale attività per ridurre la complessità causata da connettori aggiuntivi.  
  
### <a name="interrupting-the-activity"></a>Interruzione dell'attività  
 Per descrivere il modo in cui il flusso ordinario di un'attività può essere interrotto, ad esempio se l'utente decide di annullare il processo, è possibile creare un nodo accetta evento che attende l'evento. Per altre informazioni, vedere la sezione [flussi simultanei](#Concurrent). Creare un flusso di controllo da tale elemento a un nodo finale attività (7).  
  
### <a name="swimlanes"></a>Corsie  
 Talvolta può essere utile organizzare le azioni di un'attività in aree corrispondenti a oggetti o ruoli aziendali diversi che eseguono le azioni. Queste aree vengono tradizionalmente organizzate in colonne e vengono chiamate *corsie*.  
  
- Usare righe o rettangoli della **forme semplici** sezione della casella degli strumenti per tracciare corsie o altre aree.  
  
- Per etichettare ogni corsia, creare un commento e impostare relativi **Transparent** proprietà **True**.  
  
  Le forme semplici non fanno parte del modello UML e non vengono visualizzate in Esplora modelli UML.  
  
## <a name="DataFlows"></a> Descrizione del flusso di dati  
 È possibile descrivere i dati passati da e verso un'attività in due modi diversi:  
  
- Usa un' **nodo oggetto**. Si tratta del metodo più semplice per descrivere il flusso delle informazioni tra attività. Un nodo oggetto è come una variabile in un programma. Rappresenta un elemento che può contenere uno o più valori passati da un'azione a un'altra.  
  
- Usa un' **Pin di Output** e un **Pin di Input**. Questo metodo permette di descrivere separatamente gli output da un'azione e gli input a un'altra. I pin sono come i parametri in un programma. I pin rappresentano le porte in cui gli oggetti possono entrare e uscire da un'azione.  
  
    > [!NOTE]
    >  Per una panoramica degli elementi usati in questa sezione, vedere la sezione flussi di dati dell'argomento [diagrammi di attività UML: informazioni di riferimento](../modeling/uml-activity-diagrams-reference.md).  
  
### <a name="describing-data-flow-with-object-nodes"></a>Descrizione del flusso di dati con nodi oggetto  
 La maggior parte dei flussi contiene dati. Ad esempio, il flusso di output nell'azione "Il cliente fornisce i dettagli" contiene un riferimento all'indirizzo di consegna.  
  
 Se si vuole descrivere questi dati nel diagramma, è possibile sostituire un connettore con un nodo oggetto e due connettori, come mostrato nella figura seguente.  
  
 ![Nodi oggetto possono mostrare i dati passati tra le azioni](../modeling/media/uml-actguidedata.png "UML_ActGuideData")  
  
 Si noti che i rettangoli con angoli arrotondati, come Spedire le merci, rappresentano azioni, in cui avviene l'elaborazione. I rettangoli con angoli a punta, come Indirizzo di spedizione, rappresentano un flusso di oggetti da un'azione a un'altra.  
  
 Assegnare al nodo oggetto un nome che rifletta il ruolo del nodo come canale o buffer degli oggetti che si spostano tra le azioni.  
  
 È possibile impostare il **tipo** del nodo oggetto nella finestra Proprietà. Il tipo può essere un tipo primitivo, come Integer, o una classe, un'interfaccia o un'enumerazione definita in un diagramma classi. Ad esempio, è possibile creare una classe Indirizzo di spedizione, con gli attributi Via, Città e così via, insieme a un'associazione a un'altra classe denominata Cliente. Per altre informazioni, vedere [Diagrammi classi UML: Linee guida](../modeling/uml-class-diagrams-guidelines.md).  
  
> [!NOTE]
>  Se si digita il nome di un tipo che non è ancora stato definito, verrà aggiunto un elemento sotto **tipi non specificati** in Esplora modelli UML. Se successivamente si definisce un tipo con questo nome in un diagramma classi, è consigliabile reimpostare il tipo del nodo oggetto perché faccia riferimento al nuovo tipo.  
  
#### <a name="buffering-data-in-object-nodes"></a>Memorizzazione nel buffer dei dati dei nodi oggetto  
 Un nodo oggetto può fungere da buffer per più oggetti. Nella figura seguente il flusso di controllo indica che l'utente può eseguire il ciclo [scelta di altre voci] (1) più volte, mentre il nodo oggetto Voci di menu scelte (2) accumula le scelte dell'utente. Infine, quando l'utente ha completato la sua selezione, il controllo passa all'azione Confermare l'ordine (3), che accetta l'elenco completo di scelte dal buffer Voci di menu scelte.  
  
 ![Dati memorizzati nel buffer nei nodi oggetto](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")  
  
 È possibile specificare il modo in cui vengono archiviate le voci in un buffer impostando le proprietà del nodo oggetto:  
  
- Impostare il **Ordering** proprietà:  
  
    - **Non ordinata** per specificare un ordine casuale o non specificato. (impostazione predefinita).  
  
    - **Ordinati** per specificare un ordine in base a una chiave specifica.  
  
    - **FIFO** per specificare un ordine di first in, First-Out.  
  
    - **LIFO** per specificare un ordine last-in, First-Out.  
  
- Impostare il **limite superiore** proprietà per specificare il numero massimo di oggetti che possono essere contenuti nel buffer. Il valore predefinito è *, che significa che non esiste alcun limite.  
  
### <a name="describing-data-flow-with-input-and-output-pins"></a>Descrizione del flusso di dati con pin di input e di output  
 Usa un' **Pin di Output** e un **Pin di Input** per descrivere separatamente gli output da un'azione e gli input a un altro.  
  
 ![PIN di input e output sono parametri di azione](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")  
  
 Per creare un pin, fare clic su **Pin di Input** oppure **Pin di Output** della casella degli strumenti e quindi fare clic su un'azione. È quindi possibile spostare il pin intorno al perimetro dell'azione e modificarne il nome. È possibile creare un input e output pin su qualsiasi tipo di azione, tra cui **azioni chiama comportamento**, **azioni chiama operazione**, **azioni invia segnale**, e  **Accettare le azioni eventi**.  
  
 Un connettore tra due pin rappresenta un flusso oggetto, proprio come i flussi da e verso un nodo oggetto.  
  
 Assegnare a ogni pin un nome che indichi il ruolo degli oggetti che produce o accetta, ad esempio un nome di parametro.  
  
 È possibile impostare il tipo degli oggetti trasmessi usando la **tipo** proprietà. Il tipo deve essere già stato creato in un diagramma classi UML.  
  
 Gli oggetti che si spostano tra pin connessi devono essere compatibili in qualche modo. Il possibile motivo è che gli oggetti prodotti dal pin di output appartengono a un tipo derivato del tipo del pin di input.  
  
 In alternativa, è possibile specificare che il flusso oggetto includa una trasformazione che converte i dati tra il tipo del pin di output e il tipo del pin di input. La trasformazione più comune di questo genere estrae semplicemente la parte appropriata da un tipo più grande. L'esempio nella figura implica la presenza di una trasformazione che estrae l'indirizzo di spedizione dai dettagli dell'ordine.  
  
## <a name="Details"></a> Definizione di un'azione in modo più dettagliato  
 Oltre a usare il nome dell'azione per indicare in modo chiaro il risultato che deve essere generalmente ottenuto, ecco alcuni modi per aggiungere altri dettagli a un'azione:  
  
- Scrivere una descrizione più dettagliata nel **corpo** proprietà. Ad esempio, è possibile scrivere un frammento di codice programma o pseudo-codice oppure una descrizione completa dei risultati ottenuti.  
  
- Sostituire l'azione con un'azione chiama comportamento e descriverne il comportamento dettagliato in un diagramma di attività separato. Visualizzare [descrizione di sottoattività con azioni chiama comportamento](#Subactivities).  
  
- Impostare l'azione **Local Postconditions** e **Local Preconditions** le proprietà per descrivere il risultato più dettagliatamente. Per altre informazioni, vedere [definizione di postcondizioni e precondizioni](#Postcondition).  
  
### <a name="Subactivities"></a> Descrizione di sottoattività con azioni chiama comportamento  
 È possibile descrivere il comportamento dettagliato di un'azione usando un diagramma di attività separato. Un comportamento chiamato è un diagramma di attività rappresentato nel diagramma di attività principale tramite un'azione chiama comportamento. È anche possibile usare l'azione chiama comportamento per descrivere il comportamento condiviso tra attività diverse, in modo da non dover tracciare la sottoattività più volte.  
  
 Nella figura seguente il diagramma 1 mostra un'attività che include un'azione chiama comportamento, mentre il diagramma 2 mostra il diagramma della sottoattività che mostra il comportamento chiamato.  
  
 ![Un diagramma di attività distinto Mostra le azioni dettagliate](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")  
  
##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>Per descrivere una sottoattività con un'azione chiama comportamento  
  
1. Per creare il diagramma per la sottoattività, in **Esplora soluzioni**, fare doppio clic su un progetto di modellazione, scegliere **Add**, quindi fare clic su **nuovo elemento**.  
  
2. Nel **Aggiungi nuovo elemento** nella finestra di dialogo **modelli** fare clic su **diagramma di attività** e nel **nome** casella digitare il nome che si intende assegnare i **azione chiama comportamento**.  
  
3. Tracciare il flusso di lavoro dettagliato per la sottoattività. Si tratta del comportamento chiamato.  
  
    - Nel diagramma della sottoattività chiamata, il **iniziale dei nodi** indica dove inizia il controllo quando viene richiamato il comportamento chiamato. Il **nodo finale attività** illustra dove controllo deve tornare all'attività padre.  
  
4. Impostare il **comportamento** proprietà delle **azione chiama comportamento** per fare riferimento al diagramma del comportamento chiamato.  
  
    > [!NOTE]
    >  Diagramma della sottoattività deve contenere alcuni elementi su di esso o il diagramma non saranno disponibile nell'elenco a discesa per il **comportamento** proprietà. Inoltre, l'icona di tridente non verrà visualizzato nei **azione chiama comportamento** forma fino a quando non si imposta relativo **comportamento** proprietà.  
  
5. Impostare il **Is Synchronous** proprietà dell'azione per indicare se l'attività attende il completamento dell'attività chiamata.  
  
    - Se si imposta **Is Synchronous** su false, si indica che il flusso può continuare nell'azione successiva prima che venga completato l'attività chiamata. È consigliabile evitare di definire pin di output o flussi di dati in uscita dall'azione.  
  
### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Descrizione del flusso di dati da e verso sottoattività  
 È possibile descrivere il flusso di dati da e verso sottoattività allo stesso modo in cui si usano i parametri nel software.  
  
- Creare pin di input e di output (1) nell'azione chiama comportamento per ogni dato che si sposta da o verso l'azione. Assegnare il nome appropriato a ogni pin.  
  
- Nel diagramma della sottoattività, creare un **nodo parametro attività** (2) per ogni pin di input e output nell'azione chiamante. Assegnare a ogni nodo lo stesso nome del pin corrispondente.  
  
  > [!NOTE]
  >  Uno nodo parametro attività assomiglia a un nodo oggetto. Per verificare che il tipo di nodo che si sta analizzando, il pulsante destro del nodo e quindi fare clic su **proprietà**. Il tipo di nodo viene indicato nell'intestazione della finestra Proprietà.  
  
- Nel diagramma della sottoattività tracciare i connettori che mostrano il flusso di oggetti da e verso ogni nodo parametro attività.  
  
  ![Blocca sulla mappa azione chiama comportamento per i parametri di attività](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")  
  
### <a name="Postcondition"></a> Definizione di postcondizioni e precondizioni  
 È possibile usare la **Local Postconditions** e **Local Preconditions** le proprietà per specificare in modo dettagliato il risultato di un'azione. Queste proprietà descrivono l'effetto dell'azione senza indicare il modo in cui viene ottenuto.  
  
 Per impostare queste proprietà, fare doppio clic su azione e quindi fare clic su **proprietà**. Digitare i valori per le proprietà nella finestra Proprietà.  
  
#### <a name="local-postconditions"></a>Local Postconditions  
 Una postcondizione è una condizione che deve essere soddisfatta prima che l'azione possa essere considerata completata. Nell'azione di esempio Confermare l'ordine la postcondizione potrebbe essere:  
  
 Il cliente ha fornito dettagli validi e completi necessari per elaborare la sua carta di credito.  
  
 Una postcondizione può esprimere una relazione tra gli stati prima e dopo il verificarsi di un'azione. Ad esempio:  
  
 Il tasso di interesse è doppio rispetto a quello precedente.  
  
 È possibile scrivere postcondizioni in modo più formale, facendo riferimento ad attributi specifici dei dati gestiti nelle azioni. Ad esempio:  
  
 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`  
  
#### <a name="local-preconditions"></a>Local Preconditions  
 Una precondizione è una condizione che deve essere vera quando l'azione è pronta a iniziare. Ad esempio, l'azione Confermare l'ordine potrebbe avere questa precondizione:  
  
 Il cliente ha scelto almeno una voce dal menu.  
  
### <a name="describing-calls-to-operations"></a>Descrizione di chiamate a operazioni  
 In genere, un'azione descrive il lavoro eseguito da qualsiasi combinazione di persone, software o computer. Tuttavia, è possibile usare un'azione chiama operazione per descrivere una chiamata a una funzione o a un metodo specifico del software.  
  
- Impostare il nome dell'azione chiama operazione per indicare l'operazione chiamata e l'oggetto o il componente su cui viene chiamata.  
  
- Aggiungere pin di input e di output all'azione chiama operazione per descrivere i parametri e i valori restituiti.  
  
- È possibile impostare il **Is Synchronous** proprietà dell'azione per indicare se l'attività attende il completamento dell'operazione.  
  
    - Se si imposta **Is Synchronous** su false, si indica che il flusso può continuare nell'azione successiva prima del completamento dell'operazione chiamata. È consigliabile evitare di definire pin di output o flussi di dati in uscita dall'azione.  
  
## <a name="Concurrent"></a> Flussi simultanei  
 È possibile usare la **nodo Fork** e il **nodo Join** per descrivere due o più thread di attività che possono essere eseguite nello stesso momento.  
  
 ![I nodi fork e join mostrano flussi simultanei](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")  
  
 L'effetto del **nodo Fork** (1) consiste nel dividere il thread di controllo in due o più thread. Quando termina l'azione precedente, tutte le azioni sul lato di output del nodo fork possono iniziare.  
  
 Oggetto **nodo Join** (2) riunisce thread simultanei. L'azione dopo il **nodo Join** potrebbe non essere avviato finché tutte le azioni che portano il **nodo Join** sono state completate.  
  
### <a name="describing-signals-and-events"></a>Descrizione di segnali ed eventi  
 È possibile mostrare un passaggio in un processo che invia un segnale come azione invia segnale in un'attività. È possibile mostrare un passaggio che attende un segnale o un evento specifico prima di poter continuare come azione accetta evento.  
  
 Ad esempio, è possibile mostrare un passaggio che invia un ordine e quindi un altro passaggio che deve ricevere l'ordine prima di elaborarlo.  
  
#### <a name="sending-a-signal"></a>Invio di un segnale  
 Usare un'azione invia segnale (3) per indicare che un segnale o un messaggio di qualche tipo viene inviato ad altri processi o attività. Usare il nome dell'azione per indicare il tipo di messaggio inviato.  
  
- Controllare immediatamente i passaggi all'azione successiva nel flusso di controllo, se presente.  
  
- Non è possibile usare un'azione invia segnale per descrivere il modo in cui il processo risponde a qualsiasi informazione restituita. A questo scopo, usare invece un'azione accetta evento separata.  
  
- È possibile mostrare il flusso di dati in ingresso in un'azione invia segnale, per indicare quali dati possono essere inviati con il messaggio in uscita. Per altre informazioni, vedere [descrizione del flusso di dati](#DataFlows).  
  
#### <a name="waiting-for-a-signal-or-event"></a>Attesa di un segnale o un evento  
 Usare un'azione accetta evento (4) per indicare che questa attività attende un evento esterno o un messaggio in arrivo. Usare il nome dell'azione per indicare il tipo di evento atteso.  
  
- Per mostrare che l'attività attende un evento o un messaggio esterno in un punto specifico del suo flusso, tracciare un'azione accetta evento con un flusso in ingresso, nella posizione appropriata nell'attività.  
  
- Per mostrare che l'attività può rispondere a un evento o un messaggio esterno in qualsiasi momento, tracciare un'azione accetta evento senza alcun flusso in ingresso. Quando si verifica l'evento esterno denominato, inizierà un nuovo thread nell'attività, a partire dall'azione accetta evento.  
  
- Non è possibile usare un'azione accetta evento per descrivere qualsiasi valore restituito al mittente del segnale. Per questo scopo, usare un'azione invia segnale separata.  
  
- È possibile mostrare i flussi di dati in uscita dall'azione, per indicare il modo in cui l'attività elabora i dati ricevuti nel segnale. Se si desidera mostrare più di un flusso di output, è necessario impostare il **IsUnmarshall** proprietà dell'azione accetta evento, indicante che l'azione analizza il segnale in ingresso nei suoi componenti separati. Per altre informazioni, vedere [descrizione del flusso di dati](#DataFlows).  
  
### <a name="describing-multiple-data-flows"></a>Descrizione di più flussi di dati  
 È possibile tracciare più flussi di controllo o flussi oggetto provenienti da un'azione per indicare l'emergere di più thread al termine dell'azione. L'effetto assomiglia a quello di un nodo fork, ad eccezione del fatto che è possibile usare una combinazione di flussi di controllo e flussi oggetto.  
  
 L'esempio seguente mostra più flussi da e verso le azioni.  
  
 ![Flussi oggetto paralleli](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")  
  
 Al termine dell'operazione di "Cliente fornisce i dettagli", produce due oggetti: "Indirizzo di spedizione" e "dettagli della carta di credito". I due oggetti proseguono per l'elaborazione tramite azioni diverse.  
  
 Poiché prima di poter iniziare un'azione richiede che tutti gli input siano disponibili, l'ultima azione non inizia fino a quando tutte le azioni che vi conducono non sono complete.  
  
### <a name="streams"></a>Flussi  
 È possibile usare un diagramma di attività per descrivere una pipeline o una serie di azioni eseguite contemporaneamente e passare continuamente dati da un'azione a un'altra.  
  
 Lo scopo dell'esempio seguente è che ogni azione possa produrre oggetti e continuare a lavorare. Poiché non sono presenti flussi di controllo, ogni azione può iniziare non appena riceve il primo oggetto.  
  
 Si noti che i connettori nell'esempio sono flussi oggetto, perché hanno tutti almeno un'estremità in un nodo parametro attività, un nodo oggetto o un pin di input o di output.  
  
 ![Un flusso di dati](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")  
  
 1. L'esempio contiene tre nodi parametro attività, che ne rappresentano gli input e gli output.  
  
 2. I nodi oggetto, i pin di input e i pin di output possono rappresentare buffer. È possibile impostare la proprietà Upper Bound di un nodo oggetto in modo da indicare il numero di oggetti che possono essere contenuti nel buffer contemporaneamente.  
  
 3. È possibile usare nodi decisione per mostrare che un flusso viene diviso, inviando oggetti diversi lungo rami diversi. È possibile usare commenti o titoli dei nodi per descrivere il criterio di divisione.  
  
 4. È possibile usare nodi fork per mostrare la creazione di due o più copie di oggetti, inviate per l'elaborazione simultanea.  
  
 5. È possibile usare nodi join per mostrare che due flussi di elaborazione vengono riuniti in uno.  
  
### <a name="selection-and-transformation"></a>Selezione e trasformazione  
 È possibile specificare che gli oggetti in un flusso oggetto vengono trasformati o selezionati o sono soggetti a entrambe le operazioni. Un flusso oggetto è un flusso da o verso un pin o un nodo oggetto.  
  
- Una trasformazione descrive il modo in cui gli oggetti immessi in un flusso vengono convertiti in un altro tipo.  
  
- Una selezione descrive il modo in cui solo alcuni degli oggetti immessi in un flusso vengono trasmessi all'azione ricevente.  
  
  L'esempio mostra una trasformazione. La prima azione nel diagramma 1 produce un codice postale in un pin di output. Questo è connesso a un pin di input nella seconda azione. Tuttavia, la seconda azione richiede un indirizzo completo. La conversione da un tipo a un altro viene specificata in una seconda attività, Ricerca dell'indirizzo. A questa viene fatto riferimento dalla proprietà Transformation del flusso oggetto. L'attività Ricerca dell'indirizzo contiene un nodo parametro attività per il codice postale in ingresso e un altro per l'indirizzo completo in uscita.  
  
  ![Oggetto trasformazione definita in un altro diagramma](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")  
  
  È possibile specificare una trasformazione o una selezione in due modi:  
  
- Aggiungere un commento al pin di input o di output.  
  
  - Per distinguere questa descrizione da un commento generale, è possibile iniziare il commento con <\<**trasformazione**>> o <\<**selezione**>>.  
  
- Specificare la trasformazione o la selezione in modo dettagliato in un diagramma di attività separato.  
  
  - Se si usa questo metodo, aggiungere comunque un commento, per chiarire ai lettori che la trasformazione è stata definita.  
  
##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>Per specificare una trasformazione o una selezione in un diagramma di attività separato  
  
1. Creare un nuovo diagramma di attività in cui descrivere il flusso di trasformazione o selezione.  
  
   - Nel **Esplora soluzioni**, fare clic sul progetto, scegliere **Add**, fare clic su **nuovo elemento**, quindi fare clic su **diagramma di attività**. Assegnare al diagramma un nome appropriato per il flusso di trasformazione o selezione. Fare clic su **Aggiungi**.  
  
2. Nel nuovo diagramma:  
  
   1. Creare due nodi parametro attività, uno per il flusso di input e uno per il flusso di output.  
  
   2. Creare azioni interconnesse con flussi oggetto. In questo modo viene mostrato il funzionamento della trasformazione o della selezione.  
  
3. In qualsiasi diagramma in cui si vuole usare la trasformazione o la selezione eseguire le operazioni seguenti:  
  
   1. Creare un flusso oggetto, ovvero un connettore da o verso un pin di input o di output, un nodo oggetto o un nodo parametro attività.  
  
   2. Fare doppio clic su flusso oggetto e quindi fare clic su **proprietà**.  
  
   3. Nel **Transformation** oppure **selezione** proprietà, selezionare il diagramma in cui è stato specificato il flusso di trasformazione o selezione.  
  
   È anche possibile definire una selezione per un nodo oggetto e in singoli pin di input e di output. Definire un'attività di selezione come nella procedura precedente e quindi impostare il **selezione** proprietà del nodo oggetto, o un pin di input o output.  
  
## <a name="see-also"></a>Vedere anche  
 [Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrammi di sequenza UML: Riferimento](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagrammi dei componenti UML: Riferimento](../modeling/uml-component-diagrams-reference.md)   
 [Diagrammi dei casi d'uso UML: Riferimento](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagrammi delle classi UML: Riferimento](../modeling/uml-class-diagrams-reference.md)   
 [Diagrammi dei componenti UML: Riferimento](../modeling/uml-component-diagrams-reference.md)   
 [Video: Acquisire flussi di lavoro aziendali mediante diagrammi di attività](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-4-Capture-Business-Workflows/)
