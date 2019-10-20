---
title: Creare diagrammi e progetti di modellazione UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.addnewdiagramdialog
- vs.teamarch.createnewmodelingprojectdialog
helpviewer_keywords:
- projects [Visual Studio ALM], modeling
- diagrams - modeling, modeling
- modeling diagrams
- projects, UML
- UML, deleting diagrams
- UML
- UML diagrams, adding
- UML, projects
- Visual Studio ALM, modeling projects
- modeling projects
- UML diagrams
- projects, modeling
ms.assetid: c178b04b-4fd2-4bed-97e3-d793dae8649c
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e65f2f33d9c7b034da6b58f32280c95a96bacd7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651248"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Creare diagrammi e progetti di modellazione UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I modelli UML semplificano la comprensione, l'esame e la progettazione di sistemi software. Visual Studio fornisce i modelli per cinque dei diagrammi UML usati più frequentemente: attività, classi, componenti, sequenza e caso di utilizzo. È anche possibile creare diagrammi livello, che semplificano la definizione della struttura del sistema.

 I diagrammi di modellazione UML e i diagrammi livello possono essere usati solo all'interno di un progetto di modello. Ogni progetto di modello include un modello UML condiviso e alcuni diagrammi UML. Ogni diagramma è una visualizzazione parziale del modello. Il modello UML include tutti gli elementi dei diagrammi UML e può essere visualizzato tramite Esplora modelli UML. Per informazioni sui modelli e sulle rispettive relazioni con i diagrammi, vedere [modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md). Per informazioni sui progetti di modellazione nel controllo della versione, vedere [gestire modelli e diagrammi nel controllo della versione](../modeling/manage-models-and-diagrams-under-version-control.md) e [strutturare la soluzione di modellazione](../modeling/structure-your-modeling-solution.md)

> [!NOTE]
> Esiste un altro tipo di diagramma, il diagramma classi .NET, usato per visualizzare il codice programma. Per ulteriori informazioni, vedere [progettazione e visualizzazione di classi e tipi](http://go.microsoft.com/fwlink/?LinkId=142231).

## <a name="CreatingModelingDiagrams"></a>Creazione di un diagramma in un progetto di modello
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Per creare un diagramma e aggiungerlo a un progetto

1. Scegliere **nuovo diagramma livello o UML**dal menu **architettura** .

2. Nella finestra di dialogo **Aggiungi nuovo diagramma** fare clic sul tipo di diagramma di modellazione desiderato.

    ![Finestra di dialogo Aggiungi nuovo diagramma](../modeling/media/uml-adddiagram.png "UML_AddDiagram")

3. Digitare un nome per il nuovo diagramma.

4. Nella casella **Aggiungi a progetto di modello** :

   - Selezionare un progetto di modello già esistente nella soluzione, quindi fare clic su **OK**.

     \- oppure -

   1. Selezionare **Crea un nuovo progetto di modello**e quindi fare clic su **OK**.

   2. Nella finestra di dialogo **Crea nuovo progetto di modello** , digitare un nome e un percorso per il nuovo progetto, quindi fare clic su **OK**.

        ![Finestra di dialogo Crea nuovo progetto di modello](../modeling/media/uml-createmodel.png "UML_CreateModel")

        Se la soluzione è aperta, il nuovo progetto verrà aggiunto alla soluzione. Se non sono presenti soluzioni aperte, sarà possibile digitare un nome per una nuova soluzione.

   Se è già disponibile un progetto di modello, sarà possibile usare anche la procedura seguente.

#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Per aggiungere un diagramma a un progetto di modello esistente

1. In **Esplora soluzioni**fare clic sul nodo del progetto di modellazione.

    > [!NOTE]
    > Il progetto di modellazione contiene una cartella di definizione del modello denominata **ModelDefinition**.

2. Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento-** *nome \<project >* , in **modelli**, fare clic sul tipo di diagramma di modellazione, ad esempio **diagramma dei componenti UML**.

4. Digitare un nome per il diagramma, quindi fare clic su **Aggiungi**.

     Il diagramma modello verrà aperto e verrà visualizzato nel progetto di modello.

    > [!CAUTION]
    > Non aggiungere, copiare o trascinare file di diagramma esistenti in altri progetti di modello o in altre posizioni nella soluzione. Ciò provocherebbe la scomparsa di elementi dai diagrammi copiati oppure errori all'apertura dei diagrammi. È necessario aprire il file di diagramma dal progetto di modello in cui è stato creato. Un diagramma UML è infatti una visualizzazione del modello di proprietà del rispettivo progetto di modello. Per copiare un file di diagramma, creare un nuovo diagramma e quindi copiare gli elementi dal diagramma di origine al nuovo diagramma. Per ulteriori informazioni, vedere [risoluzione dei problemi relativi a progetti e diagrammi di modellazione](#TroubleshootingModelingProjects).

#### <a name="to-create-a-blank-modeling-project"></a>Per creare un progetto di modello vuoto

1. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

2. Nella finestra di dialogo **nuovo progetto** , in **modelli installati**, fare clic su **progetti di modellazione**.

3. Nella finestra centrale fare clic su **progetto di modello**.

4. Assegnare un nome al progetto e specificare un percorso nelle caselle **nome** e **percorso** .

5. Nella casella **soluzione** selezionare **Aggiungi a soluzione** per aggiungere il nuovo progetto a una soluzione già aperta. in alternativa, **creare una nuova soluzione** per chiudere qualsiasi soluzione aperta e aggiungere il progetto a una nuova soluzione.

## <a name="RemovingModelingDiagrams"></a>Rimozione di diagrammi di modellazione da un progetto
 È possibile eliminare un diagramma in modo definitivo oppure escludere temporaneamente un diagramma da un progetto e quindi ripristinarlo.

#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Per eliminare un diagramma da un progetto in modo definitivo

- In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul file principale che rappresenta il diagramma, quindi fare clic su **Elimina**.

     Il diagramma verrà rimosso dal progetto e dal file system. Gli elementi visualizzati nel diagramma non vengono rimossi da **Esplora modelli UML**.

    > [!NOTE]
    > Ogni diagramma ha due file, uno affiliato all'altro. Ad esempio, se è presente un diagramma componente con nome `CD1`, sarà necessario eliminare il file con nome `CD1.componentdiagram`. Il file secondario con nome `CD1.componentdiagram.layout` verrà eliminato automaticamente.

#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Per escludere temporaneamente un diagramma da un progetto

- In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul file di diagramma, quindi scegliere **Escludi dal progetto**.

     Il diagramma verrà rimosso dal progetto, ma non dal file system.

    > [!NOTE]
    > Gli elementi visualizzati nel diagramma non vengono rimossi da **Esplora modelli UML**.

#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Per ripristinare un diagramma escluso temporaneamente in un progetto

1. In **Esplora soluzioni**fare clic sul nodo del progetto di modellazione.

    > [!NOTE]
    > Il progetto di modellazione contiene una cartella di definizione del modello denominata **ModelDefinition**.

2. Scegliere **Aggiungi elemento esistente**dal menu **progetto** .

3. Nella finestra di dialogo **Aggiungi elemento esistente** individuare il file di diagramma, selezionare il file e quindi fare clic su **Aggiungi**.

     Il diagramma modello verrà aperto e verrà visualizzato nel progetto di modello.

    > [!NOTE]
    > Ogni diagramma ha una coppia di file nel file system. Non selezionare un file con estensione `.layout`. Visual Studio non supporta inoltre l'aggiunta di diagrammi UML esistenti a più progetti di modellazione. Ogni file di diagramma deve essere aperto nel progetto di modello in cui è stato creato. Un diagramma UML mostra infatti una visualizzazione del modello di proprietà del rispettivo progetto di modello.

## <a name="NonModelDiagrams"></a>Diagrammi che non richiedono progetti di modellazione
 I tipi di diagramma seguenti non fanno parte di un modello di progetto:

- Diagramma classi creati come visualizzazioni del codice sorgente. Non sono correlati ai diagrammi classi UML. Per ulteriori informazioni, vedere [progettazione e visualizzazione di classi e tipi](../ide/designing-and-viewing-classes-and-types.md).

- Mappe codice Vedere [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

- Diagrammi che non sono diagrammi UML o diagrammi livello, ad esempio linguaggi specifici di dominio.

## <a name="TroubleshootingModelingProjects"></a>Risoluzione dei problemi relativi a progetti e diagrammi di modellazione
 La tabella seguente illustra i problemi che si possono verificare con i progetti di modello o i diagrammi e come risolverli:

|**Problema**|**Cause**|**Risoluzione**|
|---------------|----------------|--------------------|
|Non è possibile aprire o caricare il progetto di modello nella soluzione.<br /><br /> Viene visualizzato il seguente messaggio:<br /><br /> "Uno o più progetti della soluzione non sono stati caricati correttamente. Per dettagli, vedere la finestra di output".<br /><br /> Nella finestra di output viene visualizzato il messaggio seguente:<br /><br /> "*ModelingProjectFilenameAndPath*. modelproj: errore: formato GUID non riconosciuto".|Un progetto di modello include riferimenti a progetti con lo stesso nome e nella stessa soluzione.<br /><br /> Ad esempio, un livello è collegato a progetti con lo stesso nome che si trovano nella stessa soluzione.|Usare un editor di testo per aprire il file del progetto di modello, rimuovere i riferimenti e quindi provare ad aprire di nuovo il progetto di modello.<br /><br /> Per evitare questo problema, non aggiungere riferimenti a progetti con lo stesso nome. Assicurarsi che i nomi dei progetti siano univoci.|
|Elementi mancanti da diagrammi aggiunti, copiati o trascinati in altri progetti di modello o altre posizioni nella soluzione.<br /><br /> -oppure-<br /><br /> I messaggi seguenti vengono visualizzati quando si tenta di aprire un diagramma:<br /><br /> -"Alcune forme o connettori nel diagramma risultano mancanti perché le relative definizioni non esistono nel progetto. Le definizioni sono state eliminate dal modello durante la chiusura del diagramma oppure il diagramma è stato copiato in un progetto che non contiene tali definizioni".<br /><br /> -oppure-<br /><br /> -"Questo documento è aperto da un altro progetto".|Il file di diagramma è stato aggiunto, trascinato o copiato da un progetto di modello a un altro progetto di modello o in un'altra posizione nella soluzione.|Per copiare un file di diagramma, creare un nuovo diagramma e quindi copiare gli elementi dal diagramma di origine al nuovo diagramma.|

## <a name="see-also"></a>Vedere anche
 [Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md) [strutturare la soluzione di modellazione](../modeling/structure-your-modeling-solution.md)
