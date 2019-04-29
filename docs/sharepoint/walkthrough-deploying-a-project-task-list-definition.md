---
title: 'Procedura dettagliata: Distribuzione di una definizione di elenco attività di progetto | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7ea7063ce432841e812312b7c7c36721a7d2d099
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62784231"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Procedura dettagliata: Distribuire una definizione di elenco attività di progetto

In questa procedura guidata viene illustrato come utilizzare [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] per creare, personalizzare, eseguire il debug e distribuire un elenco di SharePoint per tenere traccia delle attività del progetto.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti

- Edizioni supportate di Microsoft Windows e SharePoint.

- Visual Studio 2017 o servizi di Azure DevOps.

## <a name="create-a-sharepoint-list"></a>Creare un elenco di SharePoint

Creare un progetto di elenco di SharePoint e associare la definizione dell'elenco alle attività.

1. Aprire il **nuovo progetto** finestra di dialogo espandere il **SharePoint** nodo e quindi scegliere il **2010** nodo.

2. Nel **modelli** riquadro, scegliere il **progetto SharePoint 2010** modello, nome del progetto **ProjectTaskList**e quindi scegliere il **OK**pulsante.

     Il **Personalizzazione guidata SharePoint** viene visualizzata.

3. Specificare il sito di SharePoint locale utilizzato per il debug, scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **fine** pulsante.

4. Aprire il menu di scelta rapida per il progetto e quindi scegliere **Add** > **nuovo elemento**.

5. Nel **modelli** riquadro, scegliere il **elenco** modello e quindi scegliere il **Add** pulsante.

     Il **Personalizzazione guidata SharePoint** viene visualizzata.

6. Nel **quale nome si desidera visualizzare per l'elenco?** casella, immettere **elenco attività progetti**.

7. Scegliere il **creare un elenco non personalizzabile basato su un tipo di elenco esistente di** pulsante di opzione e nel relativo elenco, scegliere **attività**e quindi scegliere il **fine** pulsante.

     Vengono visualizzati l'elenco, funzionalità e pacchetto **Esplora soluzioni**.

## <a name="add-an-event-receiver"></a>Aggiungere un ricevitore di eventi

Nell'elenco attività è possibile aggiungere un ricevitore di eventi tramite cui vengono impostate automaticamente la scadenza e la descrizione dell'attività. La procedura seguente aggiunge un gestore di evento semplice per l'istanza di elenco come un ricevitore di eventi.

1. Aprire il menu di scelta rapida per il nodo del progetto, scegliere **Add**, quindi scegliere **nuovo elemento**.

2. Nell'elenco dei modelli di SharePoint, scegliere il **ricevitore di eventi** modello, quindi denominarlo **ProjectTaskListEventReceiver**.

     Il **Personalizzazione guidata SharePoint** viene visualizzata.

3. Nel **scegliere le impostazioni del ricevitore di eventi** pagina, scegliere **eventi elementi elenco** come tipo di ricevitore di eventi nel **quale tipo di ricevitore di eventi da** elenco.

4. Nel **selezionare l'elemento deve essere l'origine evento** casella di riepilogo **attività**.

5. Nell'elenco di eventi da gestire, selezionare la casella di controllo accanto a **è stato aggiunto un elemento**, quindi scegliere il **fine** pulsante.

     Un nuovo nodo di ricevitore di eventi viene aggiunto al progetto con un file di codice denominato **ProjectTaskListEventReceiver**.

6. Aggiungere il codice per il `ItemAdded` metodo nella **ProjectTaskListEventReceiver** file di codice. Ogni volta che viene aggiunta una nuova attività, un valore predefinito di scadenza e una descrizione viene aggiunto all'attività. Il valore predefinito di scadenza Data è 1 ° luglio 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>Personalizzare la funzionalità elenco attività di progetto

Quando si crea una soluzione di SharePoint, Visual Studio crea automaticamente le funzionalità per l'impostazione predefinita gli elementi del progetto. È possibile personalizzare le impostazioni di elenco attività di progetto per il sito di SharePoint utilizzando la finestra di progettazione di funzionalità.

1. Nelle **Esplora soluzioni**, espandere **funzionalità**.

2. Aprire il menu di scelta rapida **Feature1**, quindi scegliere **Progettazione viste**.

3. Nel **Title** casella, immettere **Project Task List Feature**.

4. Nel **ambito** casella di riepilogo **Web**.

5. Nel **delle proprietà** finestra, immettere **1.0.0.0** come valore per il **versione** proprietà.

## <a name="customize-the-project-task-list-package"></a>Personalizzare il pacchetto di elenco attività di progetto

Quando si crea un progetto SharePoint, Visual Studio aggiunge automaticamente le funzionalità che contengono gli elementi di progetto predefiniti per il pacchetto. È possibile personalizzare le impostazioni di elenco attività di progetto per il sito di SharePoint utilizzando la finestra di progettazione del pacchetto.

1. In **SolutionExplorer**, aprire il menu di scelta rapida **pacchetto**, quindi scegliere **Progettazione viste**.

2. Nel **Name** casella, immettere **ProjectTaskListPackage**.

3. Selezionare il **Reimposta Server Web** casella di controllo.

## <a name="build-and-test-the-project-task-list"></a>Compilare e testare l'elenco di attività di progetto

Quando si esegue il progetto, viene aperto il sito di SharePoint. Tuttavia, è necessario passare manualmente al percorso dell'elenco attività.

1. Scegliere il **F5** chiave per compilare e distribuire l'elenco delle attività del progetto.

     Viene aperto il sito di SharePoint.

2. Scegliere il **Home** scheda.

3. Nella barra laterale a sinistra, scegliere il **elenco attività progetti** collegamento.

     Viene visualizzata la pagina di elenco attività del progetto.

4. Nel **strumenti elenco** scheda, scegliere il **elementi** scheda.

5. Nel **elementi** gruppo, scegliere il **nuovo elemento** pulsante.

6. Nel **Title** testo casella, immettere **Attività1**.

7. Scegliere il **salvare** pulsante.

     Dopo aver aggiornato il sito, il **Attività1** attività sarà visualizzata con una data di scadenza di 7/1/2009.

8. Scegli **Attività1**.

     La visualizzazione dettagliata dell'attività vengono visualizzati, e la descrizione "This is a un'attività critica".

## <a name="deploy-the-project-task-list"></a>Distribuire l'elenco di attività di progetto

Dopo aver compilato e testare l'elenco di attività di progetto, è possibile distribuirlo per il *LocalSystem* o una *sistema remoto*. Il sistema locale è lo stesso computer in cui è stato sviluppato la soluzione, mentre un sistema remoto è un computer diverso.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Per distribuire l'elenco di attività di progetto al sistema locale

Nella barra dei menu di Visual Studio, scegliere **compilare** > **Distribuisci soluzione**.

Visual Studio viene riciclato il pool di applicazioni IIS, viene ritratta qualsiasi versione della soluzione esistente, copia il pacchetto della soluzione (*wsp*) file in SharePoint e quindi attiva le relative funzionalità. È ora possibile usare la soluzione in SharePoint. Per altre informazioni sui passaggi di configurazione di distribuzione, vedere [come: Modificare una configurazione di distribuzione di SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Per distribuire l'elenco di attività di progetto in un sistema remoto

1. Nella barra dei menu di Visual Studio, scegliere **compilare** > **pubblica**.

2. Nel **Publish** finestra di dialogo scegliere la **pubblicare nel File System** pulsante di opzione.

     È possibile modificare il percorso di destinazione nel **Publish** finestra di dialogo facendo clic sui puntini di sospensione ![icona con puntini di sospensione](../sharepoint/media/ellipsisicon.gif "puntini di sospensione") e quindi passando a un'altra posizione.

3. Scegliere il **pubblica** pulsante.

     Oggetto *wsp* file viene creato per la soluzione.

4. Copia il *wsp* file nel sistema remoto di SharePoint.

5. Usare PowerShell `Add-SPUserSolution` comando per installare il pacchetto nell'installazione di SharePoint remota. (Per le soluzioni farm, utilizzare il `Add-SPSolution` comando.)

     Ad esempio `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Usare PowerShell `Install-SPUserSolution` comando per distribuire la soluzione. (Per le soluzioni farm, utilizzare il `Install-SPSolution` comando.)

     Ad esempio `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Per altre informazioni sulla distribuzione remota, vedere [utilizzo di soluzioni](http://go.microsoft.com/fwlink/?LinkId=217680) e [aggiunta e distribuzione di soluzioni con PowerShell in SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni su come personalizzare e distribuire soluzioni di SharePoint dagli argomenti seguenti:

- [Procedura dettagliata: Creare una colonna del sito, tipo di contenuto ed elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)

- [Windows PowerShell per SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>Vedere anche
[Il pacchetto e distribuire soluzioni di SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
