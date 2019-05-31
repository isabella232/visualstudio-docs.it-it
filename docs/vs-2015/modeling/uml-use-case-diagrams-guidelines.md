---
title: 'Diagrammi caso di utilizzo UML: Linee guida | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cd0ba9030d658abb78605cf2e14b5afaa9678f78
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424311"
---
# <a name="uml-use-case-diagrams-guidelines"></a>Diagrammi caso di utilizzo UML: Indicazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, è possibile creare un *diagramma caso di utilizzo* per riepilogare chi usa l'applicazione o il sistema e ciò che è possibile eseguire. Per creare un diagramma caso di utilizzo UML nel **Architecture** menu, fare clic su **nuovo diagramma livello o UML**.  
  
 Per una dimostrazione video, vedere [organizzazione funzionalità nei casi d'uso](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/).  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Con l'aiuto di un diagramma caso di utilizzo, è possibile discutere e comunicare:  
  
- Gli scenari in cui il sistema o l'applicazione interagisce con persone, organizzazioni o sistemi esterni.  
  
- Gli obiettivi che gli attori sono aiutati a realizzare.  
  
- L'ambito del sistema.  
  
  Un diagramma caso di utilizzo non visualizza i dettagli dei casi di utilizzo: riepiloga solo alcune delle relazioni tra sistemi, attori e casi di utilizzo. In particolare, il diagramma non mostra l'ordine in cui vengono eseguiti i passaggi per realizzare gli obiettivi di ogni caso di utilizzo. È possibile descrivere tali dettagli in altri diagrammi e documenti, che è possibile collegare a ogni caso di utilizzo. Per altre informazioni, vedere [casi d'uso che descrive in dettaglio](#Details) in questo argomento.  
  
  Le descrizioni fornite per i casi di utilizzo useranno vari termini correlati al dominio in cui il sistema funziona, ad esempio vendita, menu, clienti e così via. È importante definire chiaramente questi termini e le relative relazioni ed è possibile farlo con l'aiuto di un diagramma classi UML. Per altre informazioni, vedere [Diagrammi classi UML: Linee guida](../modeling/uml-class-diagrams-guidelines.md).  
  
  I casi di utilizzo si occupano solo i requisiti funzionali per un sistema. Altri requisiti, ad esempio le regole di business, i requisiti di qualità del servizio e i vincoli di implementazione devono essere rappresentati separatamente. L'architettura e i dettagli interni devono anche essere descritti separatamente. Per altre informazioni su come definire i requisiti dell'utente, vedere [modellare i requisiti utente](../modeling/model-user-requirements.md).  
  
  Gli esempi usati in questo argomento si riferiscono a un sito Web in cui i clienti possono ordinare pasti dai ristoranti locali.  
  
  ![Gli elementi in un diagramma caso di utilizzo](../modeling/media/uml-ucovactor.png "UML_UCOvActor")  
  
- Un' *attore* (1) è una classe di persona, organizzazione, dispositivi o componenti software esterni che interagiscono con il sistema. Sono esempi di attori **cliente**, **ristorante**, **sensore di temperatura**, **Authorizer di carta di credito.**  
  
- Oggetto *caso d'uso* (2) rappresenta le azioni eseguite da uno o più attori per un obiettivo specifico. Sono esempi di casi d'uso **Ordinazione pasto**, **dal Menu di aggiornamento**, **elaborazione dei pagamenti**.  
  
   In un diagramma caso di utilizzo, i casi di utilizzo vengono associati (3) con gli attori che li eseguono.  
  
- I *sistema (4)* è l'elemento che sta sviluppando. Potrebbe essere un componente software di piccole dimensioni, in cui attori sono solo altri componenti software. Potrebbe essere un'applicazione completa oppure potrebbe essere un'ampia suite distribuita di applicazioni distribuite su molti computer e dispositivi. Sono esempi di sottosistemi **sito Web di Ordinazione pasto**, **azienda di consegna pasti**, **siti Web versione 2**.  
  
   Un diagramma caso di utilizzo è in grado di mostrare quali casi di utilizzo sono supportati dal sistema o dai relativi sottosistemi.  
  
## <a name="BasicSteps"></a> Passaggi di base per la creazione di diagrammi casi d'uso  
  
> [!NOTE]
> I passaggi dettagliati per la creazione dei diagrammi di modellazione sono descritte nel [modelli e diagrammi UML modifica](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-new-use-case-diagram"></a>Per creare un nuovo diagramma caso di utilizzo  
  
1. Nel **Architecture** menu, fare clic su **nuovo diagramma livello o UML**.  
  
2. Sotto **modelli**, fare clic su **diagramma caso di UMLUse**.  
  
3. Assegnare un nome al diagramma.  
  
4. Nelle **aggiungere al progetto di modellazione**, selezionare un progetto di modellazione esistente nella soluzione, o **creare un nuovo progetto di modellazione**, quindi fare clic su **OK**.  
  
#### <a name="to-draw-a-use-case-diagram"></a>Per creare un diagramma caso di utilizzo  
  
1. Trascinare **sottosistema** limiti dalla casella degli strumenti sul diagramma per rappresentare l'intero sistema o i relativi componenti principali.  
  
    - È possibile creare un diagramma caso di utilizzo senza limiti di sistema se non si vuole descrivere quali casi di utilizzo sono supportati dal sistema o dai relativi componenti.  
  
    - Trascinare l'angolo di un sistema per ingrandirlo, se necessario.  
  
    - Rinominarlo in modo appropriato.  
  
2. Trascinare **attori** dalla casella degli strumenti nel diagramma (posizionandoli all'esterno dei limiti del sistema).  
  
    - Gli attori rappresentano classi di utenti, organizzazioni e sistemi esterni che interagiscono con il sistema.  
  
    - Rinominarli. Ad esempio: **Agenzia di cliente, ristorante, carta di credito.**  
  
3. Trascinare **casi d'uso** dalla casella degli strumenti sui sistemi appropriati.  
  
    - I casi di utilizzo rappresentano le attività che gli attori eseguono con l'aiuto del sistema.  
  
    - Rinominarli usando titoli che gli attori stessi potrebbero comprendere. Non usare i titoli correlati al codice. Ad esempio: **Ordinare pasto, pagamento pasto, recapitare pasto**.  
  
    - Iniziare con le transazioni principali, ad esempio **Ordinazione pasto**, lasciando finché successive interazioni più piccole, ad esempio **voce di Menu selezionare**.  
  
    - Inserire ogni caso di utilizzo nel sistema o sottosistema principale che lo supporta (ignorando tutti gli aspetti o i componenti coinvolti unicamente nella connessione all'utente).  
  
    - È possibile creare un caso di utilizzo al di fuori del limite per mostrare che non è supportato dal sistema, ad esempio in una particolare versione del sistema.  
  
4. Fare clic su **Association** nella casella degli strumenti, quindi un caso d'uso e quindi un attore che fa parte del caso d'uso. Collegare ogni attore ai relativi casi di utilizzo in questo modo.  
  
5. Case struttura l'uso con il **inclusione**, **Estendi** e **generalizzazione** relazioni. Per creare ciascuno di questi collegamenti, fare clic sullo strumento, poi sul caso di utilizzo di origine e quindi sulla destinazione. Vedere la sezione seguente intitolata [strutturazione dei casi d'uso](#Structuring).  
  
6. Vengono descritti i casi di utilizzo in modo più dettagliato. Vedere la sezione seguente intitolata [casi d'uso che descrive in dettaglio](#Details).  
  
7. Creare diagrammi separati per concentrarsi su sottosistemi o gruppi diversi di casi di utilizzo correlati. Tutti i diagrammi in un progetto di modellazione sono viste dello stesso modello.  
  
## <a name="Actors"></a> Creazione di attori e casi d'uso  
 Lo scopo principale di un diagramma caso di utilizzo è mostrare che interagisce con il sistema e gli obiettivi principali raggiunti.  
  
- Creare **attori** per rappresentare le classi di persone, organizzazioni, altri sistemi, software o dispositivi che interagiscono con il sistema o sottosistema.  
  
    - Per informazioni su come creare attori e altri elementi, vedere [modelli e diagrammi UML modifica](../modeling/edit-uml-models-and-diagrams.md).  
  
    - Per ogni set distinto di obiettivi, identificare gli attori in base al tipo o al ruolo, anche se le persone fisiche o le entità potrebbero essere le stesse. Ad esempio, Ristorante e Cliente sono attori separati, anche se un dipendente del ristorante potrebbe talvolta essere un cliente.  
  
- Creare **casi d'uso** per ognuno degli obiettivi che ogni attore cerca di raggiungere con il sistema.  
  
    - Denominare e descrivere i casi di utilizzo con parole che l'attore è in grado di comprendere, anziché termini di implementazione.  
  
- Usare **associazioni** per collegare gli attori ai casi d'uso.  
  
### <a name="inheritance-between-actors"></a>Ereditarietà tra attori  
 ![Diagramma caso d'uso che mostra l'ereditarietà](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")  
  
 È possibile disegnare un **generalizzazione** collegamento tra gli attori. L'attore specializzato, come Cliente del club nell'esempio, eredita i casi di utilizzo dell'attore generalizzato, ad esempio Cliente. La freccia deve puntare all'attore più generale, ad esempio Cliente. Quando si crea il collegamento, puntare prima all'attore più specializzato.  
  
 L'attore specializzato può avere un proprio caso di utilizzo aggiuntivo che non è disponibile per gli altri.  
  
> [!CAUTION]
> È consigliabile non apportare cicli di relazioni di generalizzazione che comportano la generalizzazione di se stesso da parte di un attore. I cicli possono generare errori.  
  
### <a name="alternative-actor-icons"></a>Icone attore alternative  
 È possibile usare icone personalizzate per rappresentare un attore, anziché la figura stilizzata standard. Ad esempio, è possibile modificarla in modo che assomigli a un dispositivo, ristorante, banca e così via.  
  
##### <a name="to-change-the-appearance-of-an-actor"></a>Per modificare l'aspetto di un attore  
  
1. Fare doppio clic dell'attore e quindi fare clic su **proprietà**.  
  
     La finestra **Proprietà** verrà visualizzata.  
  
2. Impostare il **percorso dell'immagine** proprietà al percorso del file di immagine.  
  
    - È possibile usare uno dei diversi formati di immagine, tra cui gif, jpg e bmp.  
  
    - Usare un file incluso nel controllo del codice sorgente di una soluzione o un progetto in modo che sia ancora disponibile quando la soluzione viene spostata o copiata.  
  
3. Per replicare questa visualizzazione in altri diagrammi uso di utilizzo, copiare l'attore e incollarlo in un altro diagramma.  
  
    - La modifica dell'immagine viene applicata solo alla visualizzazione di un diagramma specifico. Non si applica all'elemento del modello sottostante. Se si trascina l'attore da Esplora modelli UML in un altro diagramma, verrà visualizzato come la figura stilizzata standard.  
  
### <a name="multiplicities-between-actors-and-use-cases"></a>Molteplicità tra attori e casi di utilizzo  
 L'associazione tra un attore e un caso d'uso può mostrare una *molteplicità* a ogni estremità.  
  
 ![Usare case uno-a-uno con attore](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")  
  
> [!NOTE]
> La molteplicità di un'associazione in un diagramma caso di utilizzo sono nascoste se sono entrambi **1**.  
  
 Per impostazione predefinita, ogni molteplicità è di tipo **1**. In un'interpretazione rigorosa del modello, una molteplicità pari a 1 significa che, ad esempio, un solo cliente è coinvolto nell'ordinazione di ogni pasto e che ogni cliente ordina un solo pasto alla volta.  
  
 È possibile modificare queste molteplicità.  
  
 Ad esempio:  
  
 ![Maiuscole e minuscole con molteplicità molti a molti](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")  
  
- Per dichiarare che diversi attori della stessa classe possono partecipare a una singola occorrenza di un caso d'uso, impostare la molteplicità alla fine dell'attore dell'associazione a **1...\\***.  
  
   Nell'illustrazione uno o più i ristoranti possono partecipare all'evasione della stessa ordinazione pasto.  
  
- Per mostrare che ogni attore può partecipare contemporaneamente a diverse occorrenze di un caso d'uso, impostare la molteplicità alla fine dell'associazione al case usare **\\***.  
  
   Nella figura ogni ristorante può cercare di soddisfare più ordini alla volta.  
  
##### <a name="to-set-multiplicities-on-an-association"></a>Per impostare le molteplicità in un'associazione  
  
1. Fare doppio clic sull'associazione e quindi fare clic su **proprietà**.  
  
2. Espandere la **primo ruolo** oppure **secondo ruolo**.  
  
    *Ruolo* significa che l'elemento a un'estremità dell'associazione.  
  
3. Impostare la proprietà Molteplicità scegliendo dall'elenco:  
  
   - **1** per indicare che solo un'istanza di questo ruolo fa parte di ogni collegamento.  
  
   - **1..\\** * per indicare che una o più istanze di questo ruolo fanno parte di ogni collegamento.  
  
   - **0..1** per indicare che la partecipazione è facoltativa.  
  
   - **\\** * per indicare che zero o più istanze di questo ruolo fanno parte del collegamento.  
  
> [!NOTE]
> Molti team non inseriscono informazioni sulla molteplicità nei diagrammi caso di utilizzo, lasciando le molteplicità impostate sul valore predefinito 1. Al contrario, forniscono informazioni in descrizioni separate dei casi di utilizzo. In questo caso, verranno nascoste tutte le molteplicità nei diagrammi caso di utilizzo.  
  
### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Uso di un attore o un caso di utilizzo in più diagrammi  
 È possibile visualizzare gli stessi attori e casi di utilizzo in diversi diagrammi. Ad esempio:  
  
- È possibile descrivere in diversi diagrammi caso di utilizzo diversi in cui un attore è coinvolto.  
  
- È possibile usare un diagramma per mostrare gli attori e i sottosistemi a cui è associato un caso di utilizzo e usare un altro diagramma per visualizzare la struttura del caso di utilizzo in casi di utilizzo inclusi ed estesi.  
  
##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>Per visualizzare lo stesso attore o caso di utilizzo in diagrammi diversi  
  
1. Creare l'attore o un caso di utilizzo in un diagramma.  
  
2. Creare un altro diagramma caso di utilizzo.  
  
3. Trascinare un attore o caso d'uso **Esplora modelli** nel nuovo diagramma.  
  
    > [!NOTE]
    > Se si inserisce nel nuovo diagramma un attore e un caso di utilizzo già associati, l'associazione tra di loro verrà visualizzata automaticamente nel nuovo diagramma.  
  
## <a name="Details"></a> Casi d'uso che descrive in dettaglio  
 Un caso di utilizzo rappresenta:  
  
- Un obiettivo di un attore nell'utilizzo del sistema, ad esempio **acquista un pasto**; e  
  
- Uno o più *scenari*, vale a dire le sequenze di passaggi eseguiti nel raggiungimento dell'obiettivo, ad esempio: {**Ordinazione pasto, pagamento, consegna**}. Oltre agli scenari di esito positivo, potrebbero esserci più eccezioni o scenari di errore, ad esempio **carta di credito rifiutata**.  
  
  È possibile descrivere un caso di utilizzo in diversi livelli di dettaglio. Nella fase iniziale di progettazione, è sufficiente solo il nome nel diagramma caso di utilizzo.  In un secondo momento è possibile scrivere descrizioni più dettagliate degli scenari.  
  
  In Visual Studio Ultimate è possibile descrivere un caso di utilizzo in diversi modi, che può essere usato insieme o separatamente:  
  
- Collegare il caso di utilizzo a un altro diagramma o ai diagrammi nel progetto.  
  
  - Un diagramma di attività consente di illustrare un processo più complesso se sono presenti cicli, diramazioni e thread paralleli. Inoltre è possibile visualizzare il flusso di dati tra le parti del processo. Per altre informazioni, vedere [diagrammi di attività UML: Linee guida](../modeling/uml-activity-diagrams-guidelines.md).  
  
  - Un diagramma di sequenza consente di illustrare una serie complessa di interazioni tra diversi attori. È possibile anche usarlo per mostrare cosa succede all'interno del sistema in risposta a ogni caso di utilizzo. Per altre informazioni, vedere [diagrammi di sequenza UML: Linee guida](../modeling/uml-sequence-diagrams-guidelines.md).  
  
- Collegare il caso di utilizzo a una pagina, una sezione o un paragrafo OneNote in cui viene descritto in dettaglio il caso di utilizzo.  
  
- Collegare il caso di utilizzo di un documento di Word, in cui si usano testo, schermate e così via per descrivere gli scenari del caso di utilizzo. Per altre informazioni, vedere [modellare i requisiti utente](../modeling/model-user-requirements.md).  
  
#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Per collegare un caso di utilizzo a un diagramma o a un file nella stessa soluzione  
  
1. Disegnare un diagramma, ad esempio un diagramma di sequenza o di attività, per illustrare uno scenario del caso di utilizzo.  
  
2. Tornare al diagramma caso di utilizzo.  
  
3. Trascinare il diagramma o il file da Esplora soluzioni in una parte vuota del diagramma caso di utilizzo.  
  
4. Collegamento dall'elemento per il caso di utilizzo usando una **dipendenza**.  
  
#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Per eseguire il collegamento a un file di soluzione, ad esempio un documento di Word o una presentazione di PowerPoint  
  
1. Scrivere un documento che usa testo, schermate e così via per descrivere lo scenario del caso di utilizzo.  
  
2. Aggiungere il documento alla soluzione.  
  
    1. Spostare il documento di Word nella stessa cartella di Windows della soluzione.  
  
    2. In Esplora soluzioni fare doppio clic la soluzione, scegliere **Add**, quindi fare clic su **elemento esistente**.  
  
    3. Passare al documento di Word e fare clic su **Add**.  
  
         Il documento di Word viene visualizzato in una cartella della soluzione in Esplora soluzioni.  
  
3. Trascinare il documento di Word da Esplora soluzioni in una parte vuota del diagramma caso di utilizzo.  
  
     Viene visualizzato un nuovo elemento.  
  
4. Collegamento dall'elemento per il caso di utilizzo usando una **dipendenza**.  
  
#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Per eseguire il collegamento a un documento condiviso, un elemento OneNote o una pagina Web  
  
1. Ottenere l'URL dell'elemento condiviso. Può trattarsi, ad esempio, un percorso che inizia file rete»\\\\', o una pagina web o URL di Sharepoint inizia con 'http://' o un collegamento a una sezione, pagina o paragrafo iniziale ' onenote:'.  
  
2. Nella casella degli strumenti, fare clic su **artefatto** e quindi fare clic nel diagramma caso di utilizzo.  
  
3. Con il nuovo elemento selezionato, digitare o incollare l'URL nel **Hyperlink** proprietà.  
  
> [!NOTE]
> Fare doppio clic su un elemento per aprire il diagramma o il documento a cui è collegato.  
  
### <a name="linking-use-cases-to-work-items"></a>Collegamento di casi di utilizzo a elementi di lavoro  
 Se il progetto usa [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] e aver [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], è possibile collegare ogni caso d'uso a un elemento di lavoro in [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Per informazioni su come creare questi collegamenti, vedere [collegare elementi di modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md).  
  
 In questo modo è possibile:  
  
- Descrivere il caso di utilizzo nell'elemento di lavoro collegato. In particolare, se il progetto usa il modello di processo formale di Visual Studio, è possibile collegarsi a un elemento di lavoro del caso di utilizzo. Questo tipo di elemento di lavoro fornisce campi per descrivere gli obiettivi e scenari del caso di utilizzo.  
  
- Collegare i test case al caso di utilizzo in modo che sia possibile ottenere report sulla misura in cui un codice in fase di sviluppo implementa il caso di utilizzo.  
  
- Collegare le attività al caso di utilizzo in modo da consentire il monitoraggio dell'avanzamento del lavoro di sviluppo.  
  
## <a name="Structuring"></a> Strutturazione di casi d'uso  
 È consigliabile provare a descrivere il comportamento del sistema con pochi casi di utilizzo principali. Ogni caso di utilizzo di grandi dimensioni definisce un obiettivo principale che un attore raggiunge, ad esempio l'acquisto di un prodotto oppure, dal punto di vista del fornitore, l'offerta di prodotti in vendita.  
  
 Dopo aver chiarito questi obiettivi, è possibile passare informazioni più dettagliate su come raggiungere ogni obiettivo e sulle variazioni negli obiettivi di base.  
  
 Evitare di scomporre i casi di utilizzo in troppi dettagli. I casi di utilizzo sono relativi all'esperienza degli utenti del sistema, invece che dei meccanismi interni. Risulterà in genere anche più produttivo creare versioni operative iniziali del codice, invece di impiegare tempo nella strutturazione di casi di utilizzo in particolari dettagliati.  
  
 È possibile riepilogare in un diagramma caso di utilizzo le relazioni tra i casi di utilizzo principali e più dettagliati. Le seguenti sezioni descrivono quanto segue:  
  
- [Visualizzazione dei dettagli di un caso d'uso con Includi](#Include)  
  
- [Condivisione degli obiettivi con generalizzazione](#Inheritance)  
  
- [Separazione di casi varianti con Estendi](#Extend)  
  
### <a name="Include"></a> Visualizzazione dei dettagli di un caso d'uso con Includi  
 Usare un **inclusione** relazione per mostrare che un caso di utilizzo descrive alcuni dettagli di un altro. Nell'illustrazione **ordinare un pasto** include **pagare**, **dal Menu scegliere**, e **scegliere voce di Menu**. Ognuno dei casi di utilizzo più dettagliati inclusi è un passaggio che l'attore o gli attori dovrebbero poter eseguire per raggiungere l'obiettivo complessivo del caso di utilizzo incluso. La freccia deve puntare al caso di utilizzo incluso più dettagliato.  
  
> [!CAUTION]
> È consigliabile non eseguire cicli di relazioni di inclusione che comportano l'inclusione di se stesso da parte di un caso di utilizzo. I cicli possono generare errori.  
  
 È possibile condividere casi di utilizzo inclusi. Nell'esempio, il **ordinare un pasto** e **sottoscrivere le revisioni** entrambi includono casi d'uso **pagare**.  
  
 ![Casi d'uso scomposti con Includi](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")  
  
 L'obiettivo e scenari di un caso di utilizzo incluso devono essere usati in modo indipendente in modo da poter essere inclusi in casi di utilizzo progettati in un secondo momento.  
  
 La separazione di casi di utilizzo in parti di inclusione e incluse è utile per realizzare gli obiettivi seguenti:  
  
- Strutturare le descrizioni dei casi di utilizzo in diversi livelli di dettaglio.  
  
- Evitare di ripetere scenari condivisi in diversi casi di utilizzo.  
  
#### <a name="Steps"></a> Definire l'ordine dei passaggi dettagliati  
 Il diagramma caso di utilizzo non indica l'ordine in cui è necessario eseguire i passaggi più dettagliati, né se ognuno di essi è sempre necessario.  
  
 Per rendere l'ordine di cancellare i passaggi, è possibile usare un **artefatto** per allegare un documento separato di, tra cui caso d'uso. Nell'esempio seguente viene riportato un diagramma di attività associato al caso di utilizzo di ordinazione di un pasto. In alternativa, è possibile usare un documento di testo contenente un elenco di passaggi o una sequenza di schermate. Per altre informazioni, vedere [casi d'uso che descrive in dettaglio](#Details).  
  
 Notare le convenzioni di denominazione quando si usa un diagramma di attività:  
  
- Il nome dell'intera attività corrisponde al caso di utilizzo di inclusione.  
  
- Le azioni nel diagramma di attività hanno nomi uguali a quelli dei casi di utilizzo inclusi.  
  
  Per altre informazioni, vedere [diagrammi di attività UML: Linee guida](../modeling/uml-activity-diagrams-guidelines.md).  
  
  ![Usare case passaggi illustrati nel diagramma di attività collegata](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")  
  
### <a name="Inheritance"></a> Condivisione degli obiettivi con generalizzazione  
 Usare una relazione generalizzazione per mostrare che un *specializzato* caso d'uso è un modo specifico per raggiungere gli obiettivi espressi da un altro *generali* caso d'uso. La freccia aperta deve puntare al caso di utilizzo più generale.  
  
 ![Utilizzare i case che mostra la relazione generalizzazione](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")  
  
 Ad esempio, **pagare** generalizza **pagare tramite carta di credito** e **pagamento in contanti**.  
  
> [!CAUTION]
> È consigliabile non apportare cicli di relazioni di generalizzazione che comportano la generalizzazione di se stesso da parte di un attore. I cicli possono generare errori.  
  
 Casi di utilizzo specializzati consentono di mostrare diverse modalità con cui il sistema può raggiungere lo stesso scopo.  
  
 Vengono considerati i casi di utilizzo specializzati che ereditano gli obiettivi e attori del caso di utilizzo generale. Il caso di utilizzo generale non deve necessariamente avere scenari specifici; le specializzazioni descrivono i diversi modi per raggiungere gli obiettivi.  
  
##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>Per effettuare il refactoring di obiettivi comuni da due o più casi di utilizzo  
  
1. Creare e denominare il caso di utilizzo generale.  
  
2. Creare un **generalizzazione** relazione con la freccia che punta al nuovo caso di utilizzo generale.  
  
    1. Fare clic su **generalizzazione** della casella degli strumenti.  
  
    2. Fare clic su un caso di utilizzo specializzato (**pagare tramite carta di credito** nell'esempio).  
  
    3. Fare clic sul caso di utilizzo generale (**pagare** nell'esempio).  
  
3. Se sono stati descritti gli obiettivi per i casi di utilizzo specializzati, spostare le parti comuni nella descrizione del caso di utilizzo generale.  
  
4. È possibile spostare gli attori condivisi tra i casi di utilizzo specializzati al caso di utilizzo generale.  
  
### <a name="Extend"></a> Separazione di casi varianti con Estendi  
 Usare e un collegamento Estendi per indicare che un caso di utilizzo può aggiungere funzionalità a un altro caso di utilizzo in determinate circostanze. La freccia deve puntare al caso di utilizzo esteso principale.  
  
 ![Un caso di utilizzo estende un altro](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")  
  
> [!CAUTION]
> È consigliabile non apportare cicli di relazioni di estensione che comportano la generalizzazione di se stesso da parte di un attore. I cicli possono generare errori.  
  
 Ad esempio, il **account di accesso** caso d'uso di un tipico sito Web può includere **Registra nuovo utente** - ma solo quando l'utente non possieda già un account.  
  
##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>Per separare un caso di utilizzo in parti principali e di estensione  
  
1. Creare e denominare il nuovo caso di utilizzo di estensione.  
  
2. Creare un **Estendi** relazione con la freccia rivolta al caso di utilizzo esteso.  
  
   1. Fare clic su **Estendi** della casella degli strumenti.  
  
   2. Fare clic sul caso di utilizzo di estensione (**Registra nuovo utente** nell'esempio).  
  
   3. Fare clic sul caso di utilizzo esteso (**account di accesso** nell'esempio).  
  
       > [!NOTE]
       > Evitare di creare un ciclo di relazioni Estendi nel diagramma. Non è corretto che un caso di utilizzo sia un'estensione di se stesso.  
  
3. Se sono già stati creati gli scenari per il caso di utilizzo esteso, spostare i relativi passaggi nello scenario dell'estensione.  
  
4. La descrizione dell'estensione (**Registra nuovo utente** nell'esempio) deve includere i dettagli del punto in cui nella finestra di scenari dei casi d'uso principale può verificarsi in seguito e in quali circostanze. Considerare questa operazione come una modifica della descrizione del caso principale.  
  
   Il caso di utilizzo di estensione rappresenta i passaggi dello scenario che altrimenti sarebbero parte degli scenari del caso di utilizzo principale. Lo scenario e l'obiettivo dell'estensione saranno sempre letti nel contesto del caso di utilizzo principale, di conseguenza non devono essere utili in modo indipendente.  
  
   La separazione delle estensioni può risultare utile per descrivere tali situazioni:  
  
- Sono presenti attori aggiuntivi che sono coinvolti solo nel caso di utilizzo di estensione. Ad esempio, un amministratore deve approvare una registrazione di un cliente sul sito Web.  
  
- Un sottosistema separato gestirà il caso di utilizzo di estensione.  
  
- Questa estensione sarà disponibile solo in versioni specifiche del sistema. È possibile visualizzare ogni versione come sottosistema separato nel diagramma caso di utilizzo.  
  
## <a name="Subsystems"></a> Usando i limiti del sottosistema  
 Usare un limite del sottosistema per mostrare quali casi di utilizzo sono compresi nell'ambito del sistema.  
  
#### <a name="to-draw-a-subsystem-boundary"></a>Per creare un limite del sottosistema  
  
1. Nella casella degli strumenti, fare clic su **sottosistema**, quindi fare clic sul diagramma.  
  
    Viene visualizzato un sottosistema nel diagramma.  
  
2. Trascinare gli angoli del sottosistema per modificarne le dimensioni.  
  
3. Trascinare i casi di utilizzo esistenti all'interno o all'esterno del sottosistema per modificarne il contenuto.  
  
   \- oppure -  
  
   Per creare un nuovo caso d'uso direttamente in un sottosistema, fare clic su **caso di utilizzo** nella casella degli strumenti, quindi fare clic all'interno del sottosistema.  
  
> [!NOTE]
> Il **soggetti** proprietà di un caso d'uso indica in quale sottosistema è contenuto all'interno.  
  
### <a name="use-cases-outside-the-system-scope"></a>Casi di utilizzo al di fuori dell'ambito del sistema  
 È spesso utile includere nel diagramma i casi di utilizzo che fanno parte dell'azienda, ma non sono gestiti dal sistema che si sta sviluppando. Ciò consente agli sviluppatori di comprendere il contesto del proprio lavoro. Ad esempio, Consegna pasto potrebbe essere visualizzato come un caso di utilizzo che include gli attori Ristorante e Cliente, ma fuori della responsabilità del Sito Web di ordinazione pasto.  
  
### <a name="multiple-subsystems"></a>Più sottosistemi  
 È possibile creare vari limiti del sottosistema per mostrare in che modo casi di utilizzo diversi vengono gestiti da componenti diversi del sistema. Ad esempio, **Aggiungi valutazione ristorante** può essere gestito in un sito Web forum separato. Un diagramma caso di utilizzo deve gestire gli elementi visibili all'utente. Se si desidera descrivere la divisione interna del lavoro nel sistema, è consigliabile usare un diagramma dei componenti.  
  
### <a name="system-versions"></a>Versioni del sistema  
 È possibile usare diversi limiti del sottosistema per illustrare diverse versioni del sistema. Ad esempio il caso di utilizzo Pagamento potrebbe essere incluso nella versione 2 del sito Web, ma non nella versione 1. Ciò implica che il sistema aiuta i clienti a effettuare gli ordini. Tuttavia, è necessario pagare direttamente il ristorante.  
  
 Uso **dipendenza** relazioni per collegare i sottosistemi che rappresentano diverse versioni o varianti.  
  
 ![I sottosistemi mostrano le diverse versioni di un sistema](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")  
  
## <a name="see-also"></a>Vedere anche  
 [Modellare i requisiti utente](../modeling/model-user-requirements.md)   
 [Diagrammi di sequenza UML: Linee guida](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrammi dei casi d'uso UML: Riferimento](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagrammi delle classi UML: Riferimento](../modeling/uml-class-diagrams-reference.md)   
 [Diagrammi dei componenti UML: Riferimento](../modeling/uml-component-diagrams-reference.md)   
 [Diagrammi di attività UML: Linee guida](../modeling/uml-activity-diagrams-guidelines.md)   
 [Video: Organizzare le funzionalità nei casi di utilizzo](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/)
