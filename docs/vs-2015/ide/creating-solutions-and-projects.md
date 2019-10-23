---
title: Creazione di soluzioni e progetti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
ms.assetid: 836f8ca0-3fc9-4f4b-9090-45f2e4d2e9c8
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 47083fe3f496cb855a7fb7101a886290e53cfbce
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619124"
---
# <a name="creating-solutions-and-projects"></a>Creating Solutions and Projects
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I progetti sono i contenitori logici di tutti gli elementi necessari per compilare l'applicazione. Quando si crea un progetto scegliendo **File &#124; Nuovo &#124; Progetto** dal menu principale, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crea una soluzione in cui inserirlo. È quindi possibile aggiungere altri progetti nuovi o esistenti alla soluzione, se necessario. È possibile creare progetti dai file di codice esistenti ed è possibile creare progetti temporanei (solo .NET) che verranno eliminati al termine del loro uso.

> [!NOTE]
> Le descrizioni in questo argomento sono basate sull'edizione Visual Studio Community. Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti in questa sezione, in quanto dipendono dalle impostazioni o dall'edizione di Visual Studio. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-project-from-an-installed-project-template"></a>Creare un progetto da un modello di progetto installato
 Scegliere **File &#124; Nuovo &#124; Progetto** dal menu principale per visualizzare la finestra di dialogo Nuovo progetto. Nel riquadro sinistro sotto **Installati &#124; Modelli** selezionare il linguaggio di programmazione e la piattaforma o la tecnologia, quindi scegliere un modello tra quelli disponibili nel riquadro centrale.

 Nella finestra di dialogo **Nuovo progetto** l'elenco a discesa **Soluzione** offre l'opzione per creare il nuovo progetto in una soluzione nuova o esistente o in una nuova istanza di Visual Studio.

## <a name="create-a-project-from-existing-code-files"></a>Creare un progetto da file di codice esistenti
 Se si ha una raccolta di file di origine separati, è possibile creare facilmente un progetto che li contenga. Scegliere **File &#124; Nuovo &#124; Progetto da codice esistente** per avviare la **Creazione guidata nuovo progetto da file di codice esistenti** e seguire le istruzioni.

> [!TIP]
> Questa opzione risulta più adatta per raccolte di file relativamente semplici.

## <a name="create-a-temporary-project-c-and-visual-basic"></a>Creare un progetto temporaneo (C# e Visual Basic)
 Quando si lavora con i progetti temporanei, è possibile creare ed effettuare prove con un progetto .NET senza specificare un percorso sul disco. Quando si crea un progetto, è sufficiente selezionare un tipo di progetto e un modello e specificare un nome nella finestra di dialogo **Nuovo progetto** . In qualsiasi momento mentre si lavora con il progetto temporaneo è possibile salvarlo o rimuoverlo.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Creare un progetto .NET che usa una specifica versione di .NET Framework
 È possibile creare un progetto destinato a versioni precedenti di .NET Framework mediante il menu a discesa della versione prescelta di **.NET Framework** nella parte superiore della finestra di dialogo **Nuovo progetto** . Impostare questo valore prima di selezionare un modello di progetto, poiché nell'elenco verranno visualizzati solo i modelli compatibili con tale versione di .NET Framework.

 È necessario disporre di .NET Framework 3.5 installato nel sistema peri accedere alle versioni di framework precedenti alla 4.0.

## <a name="downloading-sample-solutions"></a>Download di soluzioni di esempio
 È possibile usare Visual Studio per scaricare e installare esempi di soluzioni dalla [raccolta di codici MSDN](http://go.microsoft.com/fwlink/?LinkId=254185).

 È possibile scaricare esempi individualmente oppure scaricare un Pacchetto di esempi contenente gli esempi correlati che condividono una tecnologia o un argomento. Si riceverà una notifica al momento della pubblicazione delle modifiche apportate al codice sorgente per ogni esempio scaricato.

 Per altre informazioni vedere [Visual Studio Samples](../ide/visual-studio-samples.md) (Esempi di Visual Studio).

## <a name="adding-single-files-at-the-solution-level"></a>Aggiunta di file singoli a livello di soluzione
 In alcuni casi più progetti possono fare riferimento a un solo file oppure un file potrebbe contenere testo o dati vari che appartengono logicamente al livello della soluzione anziché a un progetto specifico.  Per aggiungere un elemento singolo a una soluzione:

1. Fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Aggiungi &#124; Nuovo elemento** o **Aggiungi &#124; Elemento esistente**.

## <a name="creating-empty-solutions"></a>Creazione di soluzioni vuote
 Anche se un progetto deve risiedere in una soluzione, è possibile creare una soluzione senza progetti.

#### <a name="to-create-an-empty-solution"></a>Per creare una soluzione vuota

1. Scegliere **Nuovo** dal menu **File** , quindi **Nuovo progetto**.

2. Nel riquadro sinistro selezionare **Installato**, **Altri tipi di progetto**, quindi **Soluzioni di Visual Studio** dall'elenco espanso.

3. Nel riquadro centrale selezionare **Soluzione vuota**.

4. Impostare i valori **Nome** e **Percorso** per la soluzione, quindi fare clic su **OK**.

   Dopo aver creato una soluzione vuota, è possibile aggiungervi progetti o elementi nuovi o esistenti facendo clic su **Aggiungi nuovo elemento** o **Aggiungi elemento esistente** nel menu **Progetto** .

### <a name="deleting-solutions"></a>Eliminazione di soluzioni
 È possibile eliminare definitivamente una soluzione, ma non usando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Prima di eliminare una soluzione, spostare eventuali progetti da riutilizzare in un'altra soluzione. Usare quindi Esplora file per eliminare la directory contenente i due file di soluzione con estensione sln e suo.

> [!NOTE]
> Il file con estensione suo è un file nascosto che non viene visualizzato nelle impostazioni predefinite di Esplora file.

##### <a name="to-delete-a-solution"></a>Per eliminare una soluzione

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione da eliminare e selezionare **Apri cartella in Esplora file**.

2. In Esplora file spostarsi in alto di un livello.

3. Selezionare la directory contenente la soluzione e premere CANC.

## <a name="see-also"></a>Vedere anche
 [Soluzioni e progetti ](../ide/solutions-and-projects-in-visual-studio.md) [NIB procedura: creare soluzioni multiprogetto](https://msdn.microsoft.com/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)
