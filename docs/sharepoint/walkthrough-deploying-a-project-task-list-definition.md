---
title: 'Procedura dettagliata: Distribuzione di una Project Elenco attività di | Microsoft Docs'
description: In questa procedura dettagliata usare Visual Studio creare, personalizzare, eseguire il debug e distribuire un SharePoint per tenere traccia delle attività del progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 88b4be482cc0ad99829a065b8bc423258b69de49
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135871"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Procedura dettagliata: Distribuire una definizione dell'elenco attività di progetto

In questa procedura guidata viene illustrato come utilizzare [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] per creare, personalizzare, eseguire il debug e distribuire un elenco di SharePoint per tenere traccia delle attività del progetto.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti

- Edizioni supportate di Microsoft Windows e SharePoint.

- Visual Studio 2017 o Azure DevOps Services.

## <a name="create-a-sharepoint-list"></a>Crea un elenco di SharePoint

Creare un progetto di elenco di SharePoint e associare la definizione dell'elenco alle attività.

1. Aprire la **finestra di dialogo** Project, espandere il nodo SharePoint e quindi scegliere il nodo **2010.** 

2. Nel riquadro **Modelli** scegliere il modello SharePoint **2010 Project,** assegnare al progetto il nome **ProjectTaskList** e quindi scegliere **OK.**

     Verrà **visualizzata SharePoint personalizzazione** guidata.

3. Specificare il sito SharePoint locale da usare per il debug, scegliere il pulsante di opzione Distribuisci come soluzione **farm** e quindi scegliere **il pulsante** Fine.

4. Aprire il menu di scelta rapida per il progetto e quindi scegliere **Aggiungi**  >  **nuovo elemento**.

5. Nel riquadro **Modelli** scegliere il **modello Elenco** e quindi scegliere il **pulsante** Aggiungi.

     Verrà **visualizzata SharePoint personalizzazione** guidata.

6. Nella casella **Quale nome si vuole visualizzare per l'elenco?** immettere **Project Elenco attività**.

7. Scegliere il **pulsante di** opzione Crea un elenco non personalizzabile in base a un tipo di elenco esistente, quindi nel relativo elenco scegliere Attività e quindi fare clic sul **pulsante** Fine. 

     L'elenco, la funzionalità e il pacchetto vengono visualizzati in **Esplora soluzioni**.

## <a name="add-an-event-receiver"></a>Aggiungere un ricevitore di eventi

Nell'elenco attività è possibile aggiungere un ricevitore di eventi tramite cui vengono impostate automaticamente la scadenza e la descrizione dell'attività. La procedura seguente aggiunge un semplice gestore eventi all'istanza di elenco come ricevitore di eventi.

1. Aprire il menu di scelta rapida per il nodo del progetto, **scegliere Aggiungi** e quindi **Nuovo elemento.**

2. Nell'elenco dei SharePoint modelli scegliere il modello **Ricevitore** di eventi e quindi denomarlo **ProjectTaskListEventReceiver.**

     Verrà **visualizzata SharePoint personalizzazione** guidata.

3. Nella pagina **Scegli ricevitore Impostazioni**  eventi scegliere Elenca eventi elemento come tipo di ricevitore di eventi nell'elenco Tipo di ricevitore **di** eventi desiderato.

4. **Nell'elenco Quale elemento deve essere l'origine evento** scegliere **Attività**.

5. Nell'elenco degli eventi da gestire selezionare la casella di controllo accanto a **È stato** aggiunto un elemento e quindi scegliere il **pulsante** Fine.

     Al progetto viene aggiunto un nuovo nodo ricevitore di eventi con un file di codice denominato **ProjectTaskListEventReceiver.**

6. Aggiungere codice al `ItemAdded` metodo nel file di codice **ProjectTaskListEventReceiver.** Ogni volta che viene aggiunta una nuova attività, all'attività vengono aggiunte una data di scadenza predefinita e una descrizione. La data di scadenza predefinita è il 1° luglio 2009.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs" id="Snippet1":::

## <a name="customize-the-project-task-list-feature"></a>Personalizzare la funzionalità dell'elenco attività del progetto

Quando si crea una soluzione SharePoint, Visual Studio automaticamente le funzionalità per gli elementi di progetto predefiniti. È possibile personalizzare le impostazioni dell'elenco attività SharePoint progetto usando Progettazione funzionalità.

1. In **Esplora soluzioni** espandere **Funzionalità**.

2. Aprire il menu di scelta rapida **per Feature1** e quindi scegliere **Progettazione visualizzazioni**.

3. Nella casella **Titolo** immettere Project Elenco attività **funzionalità**.

4. **Nell'elenco Ambito** scegliere **Web**.

5. Nella finestra **Proprietà** immettere **1.0.0.0** come valore per la **proprietà** Version.

## <a name="customize-the-project-task-list-package"></a>Personalizzare il pacchetto dell'elenco attività del progetto

Quando si crea un SharePoint, Visual Studio automaticamente le funzionalità che contengono gli elementi di progetto predefiniti al pacchetto. È possibile personalizzare le impostazioni dell'elenco attività SharePoint progetto usando Progettazione pacchetti.

1. In **SolutionExplorer** aprire il menu di scelta rapida **per Pacchetto** e quindi scegliere **Progettazione visualizzazioni**.

2. Nella casella **Nome** immettere **ProjectTaskListPackage**.

3. Selezionare la **casella di controllo Reimposta server** Web .

## <a name="build-and-test-the-project-task-list"></a>Compilare e testare l'elenco di attività del progetto

Quando si esegue il progetto, viene aperto SharePoint sito web. Tuttavia, è necessario passare manualmente al percorso dell'elenco attività.

1. Scegliere il **tasto F5** per compilare e distribuire l'elenco di attività del progetto.

     Verrà SharePoint sito di lavoro.

2. Scegliere la **scheda Home.**

3. Nella barra laterale sinistra scegliere il **Project Elenco attività** collegamento.

     Viene Project Elenco attività pagina dei dati.

4. Nella scheda **Strumenti elenco** scegliere la **scheda** Elementi.

5. Nel gruppo **Elementi** scegliere il **pulsante Nuovo** elemento.

6. Nella casella **di** testo Titolo immettere **Task1**.

7. Scegliere il **pulsante** Salva.

     Dopo l'aggiornamento del sito, l'attività **Task1** viene visualizzata con una data di scadenza di 1/7/2009.

8. Scegliere **Task1**.

     Viene visualizzata la visualizzazione dettagliata dell'attività e la descrizione indica "Si tratta di un'attività critica".

## <a name="deploy-the-project-task-list"></a>Distribuire l'elenco di attività del progetto

Dopo aver compilato e testato l'elenco attività del progetto, è possibile distribuirlo nel *sistema locale* o in un *sistema remoto.* Il sistema locale è lo stesso computer in cui è stata sviluppata la soluzione, mentre un sistema remoto è un computer diverso.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Per distribuire l'elenco attività del progetto nel sistema locale

Nella barra Visual Studio menu scegliere **Compila**  >  **distribuisci soluzione**.

Visual Studio ricicla il pool di applicazioni IIS, ritira tutte le versioni esistenti della soluzione, copia il file del pacchetto della soluzione (con estensione *wsp)* in SharePoint e quindi ne attiva le funzionalità. È ora possibile usare la soluzione in SharePoint. Per altre informazioni sui passaggi di configurazione della distribuzione, vedere [Procedura: Modificare una configurazione SharePoint distribuzione .](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Per distribuire l'elenco attività del progetto in un sistema remoto

1. Nella barra Visual Studio menu scegliere **Compila**  >  **pubblica**.

2. Nella finestra **di** dialogo Pubblica scegliere il **pulsante di opzione** Pubblica nel file system .

     È possibile modificare il  percorso di destinazione nella finestra di ![](../sharepoint/media/ellipsisicon.gif "Icona con i puntini di sospensione") dialogo Pubblica scegliendo il pulsante con i puntini di sospensione Icona puntini di sospensione e quindi passando a un'altra posizione.

3. Fare clic sul pulsante **Pubblica**.

     Per la soluzione viene creato un file con estensione *wsp.*

4. Copiare il file *con estensione wsp* nel sistema SharePoint remoto.

5. Usare il comando PowerShell `Add-SPUserSolution` per installare il pacchetto nell'installazione SharePoint remota. Per le soluzioni farm, usare il `Add-SPSolution` comando .

     Ad esempio, `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Usare il comando PowerShell `Install-SPUserSolution` per distribuire la soluzione. Per le soluzioni farm, usare il `Install-SPSolution` comando .

     Ad esempio, `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Per altre informazioni sulla distribuzione remota, vedere [Uso](/previous-versions/office/developer/sharepoint-2010/ee534972(v=office.14)) di soluzioni e Aggiunta e distribuzione di soluzioni [con PowerShell in SharePoint 2010.](http://www.dotnetmafia.com/blogs/dotnettipoftheday/archive/2009/12/02/adding-and-deploying-solutions-with-powershell-in-sharepoint-2010.aspx)

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su come personalizzare e distribuire soluzioni SharePoint, vedere gli argomenti seguenti:

- [Procedura dettagliata: Creare una colonna del sito, un tipo di contenuto ed un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)

- [Windows PowerShell per SharePoint Server 2010](/powershell/module/sharepoint-server)

## <a name="see-also"></a>Vedi anche
[Creare un pacchetto e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
