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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bc537e76e87e519019cfbb1c3f612eb0a4bd6181
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433368"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Creare diagrammi e progetti di modellazione UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I modelli UML semplificano la comprensione, l'esame e la progettazione di sistemi software. Visual Studio fornisce i modelli per cinque dei diagrammi UML usati più frequentemente: attività, classi, componenti, sequenza e caso di utilizzo. È anche possibile creare diagrammi livello, che semplificano la definizione della struttura del sistema.  
  
 I diagrammi di modellazione UML e i diagrammi livello possono essere usati solo all'interno di un progetto di modello. Ogni progetto di modello include un modello UML condiviso e alcuni diagrammi UML. Ogni diagramma è una visualizzazione parziale del modello. Il modello UML include tutti gli elementi dei diagrammi UML e può essere visualizzato tramite Esplora modelli UML. Per informazioni sui modelli e la loro relazione con i diagrammi, vedere [modelli e diagrammi UML modifica](../modeling/edit-uml-models-and-diagrams.md). Per informazioni sui modelli di progetto nel controllo della versione, vedere [gestire modelli e diagrammi nel controllo della versione](../modeling/manage-models-and-diagrams-under-version-control.md) e [strutturare la soluzione di modellazione](../modeling/structure-your-modeling-solution.md)  
  
> [!NOTE]
> Esiste un altro tipo di diagramma, il diagramma classi .NET, usato per visualizzare il codice programma. Per altre informazioni, vedere [progettazione e visualizzazione di classi e tipi](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
## <a name="CreatingModelingDiagrams"></a> Creare un diagramma in un progetto di modellazione  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Per creare un diagramma e aggiungerlo a un progetto  
  
1. Nel **Architecture** menu, scegliere **nuovo diagramma livello o UML**.  
  
2. Nel **Aggiungi nuovo diagramma** finestra di dialogo, scegliere il tipo di diagramma di modellazione che si desidera.  
  
    ![Aggiungi nuovo diagramma finestra di dialogo](../modeling/media/uml-adddiagram.png "UML_AddDiagram")  
  
3. Digitare un nome per il nuovo diagramma.  
  
4. Nel **aggiunta al progetto di modellazione** casella:  
  
   - Selezionare un progetto di modellazione esistente nella soluzione e quindi fare clic su **OK**.  
  
     \- oppure -  
  
   1. Selezionare **creare un nuovo progetto di modellazione**, quindi fare clic su **OK**.  
  
   2. Nel **Crea nuovo progetto di modellazione** della finestra di dialogo digitare un nome e un percorso per il nuovo progetto e quindi fare clic su **OK**.  
  
        ![Creare una finestra di dialogo Nuovo progetto di modellazione](../modeling/media/uml-createmodel.png "UML_CreateModel")  
  
        Se la soluzione è aperta, il nuovo progetto verrà aggiunto alla soluzione. Se non sono presenti soluzioni aperte, sarà possibile digitare un nome per una nuova soluzione.  
  
   Se è già disponibile un progetto di modello, sarà possibile usare anche la procedura seguente.  
  
#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Per aggiungere un diagramma a un progetto di modello esistente  
  
1. Nelle **Esplora soluzioni**, la modellazione di fare clic sul nodo del progetto.  
  
    > [!NOTE]
    > Il progetto di modellazione contiene una cartella di definizione di modello denominata **ModelDefinition**.  
  
2. Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3. Nel **Aggiungi nuovo elemento -**  *\<nome progetto >* nella finestra di dialogo **modelli**, fare clic su di modellazione diagramma tipo, ad esempio, **UML Diagramma dei componenti**.  
  
4. Digitare un nome per il diagramma e quindi fare clic su **Add**.  
  
     Il diagramma modello verrà aperto e verrà visualizzato nel progetto di modello.  
  
    > [!CAUTION]
    > Non aggiungere, copiare o trascinare file di diagramma esistenti in altri progetti di modello o in altre posizioni nella soluzione. Ciò provocherebbe la scomparsa di elementi dai diagrammi copiati oppure errori all'apertura dei diagrammi. È necessario aprire il file di diagramma dal progetto di modello in cui è stato creato. Un diagramma UML è infatti una visualizzazione del modello di proprietà del rispettivo progetto di modello. Per copiare un file di diagramma, creare un nuovo diagramma e quindi copiare gli elementi dal diagramma di origine al nuovo diagramma. Per altre informazioni, vedere [diagrammi e progetti di modellazione di risoluzione dei problemi](#TroubleshootingModelingProjects).  
  
#### <a name="to-create-a-blank-modeling-project"></a>Per creare un progetto di modello vuoto  
  
1. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
2. Nel **nuovo progetto** nella finestra di dialogo **modelli installati**, fare clic su **progetti di modellazione**.  
  
3. Nella finestra centrale fare clic su **progetto di modellazione**.  
  
4. Denominare il progetto e specificare il percorso nel **Name** e **posizione** caselle.  
  
5. Nel **soluzione** , quindi selezionare **aggiungere alla soluzione** per aggiungere il nuovo progetto a una soluzione già aperta oppure **Crea nuova soluzione** per chiudere eventuali soluzioni aperte e aggiungere il progetto per una nuova soluzione.  
  
## <a name="RemovingModelingDiagrams"></a> Rimozione di diagrammi da un progetto di modellazione  
 È possibile eliminare un diagramma in modo definitivo oppure escludere temporaneamente un diagramma da un progetto e quindi ripristinarlo.  
  
#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Per eliminare un diagramma da un progetto in modo definitivo  
  
- Nelle **Esplora soluzioni**, fare doppio clic su file principale che rappresenta il diagramma e quindi fare clic su **eliminare**.  
  
     Il diagramma verrà rimosso dal progetto e dal file system. Gli elementi mostrati nel diagramma non vengono rimossi dalle **Esplora modelli UML**.  
  
    > [!NOTE]
    > Ogni diagramma ha due file, uno affiliato all'altro. Ad esempio, se è presente un diagramma componente con nome `CD1`, sarà necessario eliminare il file con nome `CD1.componentdiagram`. Il file secondario con nome `CD1.componentdiagram.layout` verrà eliminato automaticamente.  
  
#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Per escludere temporaneamente un diagramma da un progetto  
  
- Nelle **Esplora soluzioni**, fare clic sul file del diagramma e quindi fare clic su **Escludi dal progetto**.  
  
     Il diagramma verrà rimosso dal progetto, ma non dal file system.  
  
    > [!NOTE]
    > Gli elementi mostrati nel diagramma non vengono rimossi dalle **Esplora modelli UML**.  
  
#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Per ripristinare un diagramma escluso temporaneamente in un progetto  
  
1. Nelle **Esplora soluzioni**, la modellazione di fare clic sul nodo del progetto.  
  
    > [!NOTE]
    > Il progetto di modellazione contiene una cartella di definizione di modello denominata **ModelDefinition**.  
  
2. Nel **Project** menu, fare clic su **Aggiungi elemento esistente**.  
  
3. Nel **Aggiungi elemento esistente** finestra di dialogo, individuare il file di diagramma, selezionare il file e quindi fare clic su **Add**.  
  
     Il diagramma modello verrà aperto e verrà visualizzato nel progetto di modello.  
  
    > [!NOTE]
    > Ogni diagramma ha una coppia di file nel file system. Non selezionare un file con estensione `.layout`. Visual Studio non supporta inoltre l'aggiunta di diagrammi UML esistenti a più progetti di modellazione. Ogni file di diagramma deve essere aperto nel progetto di modello in cui è stato creato. Un diagramma UML mostra infatti una visualizzazione del modello di proprietà del rispettivo progetto di modello.  
  
## <a name="NonModelDiagrams"></a> Diagrammi che non necessitano di progetti di modellazione  
 I tipi di diagramma seguenti non fanno parte di un modello di progetto:  
  
- Diagramma classi creati come visualizzazioni del codice sorgente. Non sono correlati ai diagrammi classi UML. Per altre informazioni, vedere [progettazione e visualizzazione di classi e tipi](../ide/designing-and-viewing-classes-and-types.md).  
  
- Mappe codice Vedere [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).  
  
- Diagrammi che non sono diagrammi UML o diagrammi livello, ad esempio linguaggi specifici di dominio.  
  
## <a name="TroubleshootingModelingProjects"></a> Risoluzione dei problemi relativi a diagrammi e progetti di modellazione  
 La tabella seguente illustra i problemi che si possono verificare con i progetti di modello o i diagrammi e come risolverli:  
  
|**Problema**|**Cause**|**Risoluzione**|  
|---------------|----------------|--------------------|  
|Non è possibile aprire o caricare il progetto di modello nella soluzione.<br /><br /> Viene visualizzato il seguente messaggio:<br /><br /> "Uno o più progetti della soluzione non sono stati caricati correttamente. Per dettagli, vedere la finestra di output".<br /><br /> Nella finestra di output viene visualizzato il messaggio seguente:<br /><br /> "*ModelingProjectFilenameAndPath*. modelproj: errore: Formato Guid non riconosciuto".|Un progetto di modello include riferimenti a progetti con lo stesso nome e nella stessa soluzione.<br /><br /> Ad esempio, un livello è collegato a progetti con lo stesso nome che si trovano nella stessa soluzione.|Usare un editor di testo per aprire il file del progetto di modello, rimuovere i riferimenti e quindi provare ad aprire di nuovo il progetto di modello.<br /><br /> Per evitare questo problema, non aggiungere riferimenti a progetti con lo stesso nome. Assicurarsi che i nomi dei progetti siano univoci.|  
|Elementi mancanti da diagrammi aggiunti, copiati o trascinati in altri progetti di modello o altre posizioni nella soluzione.<br /><br /> -oppure-<br /><br /> I messaggi seguenti vengono visualizzati quando si tenta di aprire un diagramma:<br /><br /> -"Alcune forme o connettori nel diagramma non sono presenti perché le relative definizioni non esistono nel progetto. Le definizioni sono state eliminate dal modello durante la chiusura del diagramma oppure il diagramma è stato copiato in un progetto che non contiene tali definizioni".<br /><br /> -oppure-<br /><br /> -"Questo documento viene aperto da un altro progetto".|Il file di diagramma è stato aggiunto, trascinato o copiato da un progetto di modello a un altro progetto di modello o in un'altra posizione nella soluzione.|Per copiare un file di diagramma, creare un nuovo diagramma e quindi copiare gli elementi dal diagramma di origine al nuovo diagramma.|  
  
## <a name="see-also"></a>Vedere anche  
 [Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Strutturare la soluzione di modellazione](../modeling/structure-your-modeling-solution.md)
