---
title: 'Procedura dettagliata: distribuzione di un progetto Elenco attività definizione | Microsoft Docs'
description: In questa procedura dettagliata, usare Visual Studio per creare, personalizzare, eseguire il debug e distribuire un elenco SharePoint per tenere traccia delle attività del progetto.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0be8eed2dc41ad433c0e0514dfd34e3c6e3d7193
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970419"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Procedura dettagliata: distribuire una definizione di elenco attività progetto

In questa procedura guidata viene illustrato come utilizzare [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] per creare, personalizzare, eseguire il debug e distribuire un elenco di SharePoint per tenere traccia delle attività del progetto.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti

- Edizioni supportate di Microsoft Windows e SharePoint.

- Visual Studio 2017 o Azure DevOps Services.

## <a name="create-a-sharepoint-list"></a>Crea un elenco di SharePoint

Creare un progetto di elenco di SharePoint e associare la definizione dell'elenco alle attività.

1. Aprire la finestra di dialogo **nuovo progetto** , espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

2. Nel riquadro **modelli** scegliere il modello di **progetto SharePoint 2010** , denominare il progetto **ProjectTaskList**, quindi scegliere il pulsante **OK** .

     Viene visualizzata la **personalizzazione guidata SharePoint** .

3. Specificare il sito di SharePoint locale usato per il debug, scegliere il pulsante di opzione **Distribuisci come soluzione farm** , quindi scegliere il pulsante **fine** .

4. Aprire il menu di scelta rapida per il progetto, quindi scegliere **Aggiungi**  >  **nuovo elemento**.

5. Nel riquadro **modelli** scegliere il modello **elenco** , quindi scegliere il pulsante **Aggiungi** .

     Viene visualizzata la **personalizzazione guidata SharePoint** .

6. Nella casella specificare il **nome da visualizzare per l'elenco** immettere **Project elenco attività**.

7. Scegliere il pulsante **di opzione crea un elenco non personalizzabile in base a un tipo di elenco esistente** , quindi scegliere **attività** dal relativo elenco, quindi scegliere il pulsante **fine** .

     L'elenco, la funzionalità e il pacchetto vengono visualizzati in **Esplora soluzioni**.

## <a name="add-an-event-receiver"></a>Aggiungere un ricevitore di eventi

Nell'elenco attività è possibile aggiungere un ricevitore di eventi tramite cui vengono impostate automaticamente la scadenza e la descrizione dell'attività. Nella procedura seguente viene aggiunto un gestore eventi semplice all'istanza di elenco come ricevitore di eventi.

1. Aprire il menu di scelta rapida per il nodo del progetto, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.

2. Nell'elenco dei modelli di SharePoint scegliere il modello **ricevitore di eventi** e denominarlo **ProjectTaskListEventReceiver**.

     Viene visualizzata la **personalizzazione guidata SharePoint** .

3. Nella pagina **selezione Impostazioni ricevitore evento** scegliere **eventi elemento elenco** come tipo di ricevitore di eventi nell'elenco **tipo di ricevitore di eventi desiderato** .

4. Nell'elenco **elemento che deve essere l'origine evento** scegliere **attività**.

5. Nell'elenco di eventi da gestire, selezionare la casella di controllo accanto a **un elemento aggiunto**, quindi scegliere il pulsante **fine** .

     Al progetto viene aggiunto un nuovo nodo ricevitore di eventi con un file di codice denominato **ProjectTaskListEventReceiver**.

6. Aggiungere il codice al `ItemAdded` metodo nel file di codice **ProjectTaskListEventReceiver** . Ogni volta che viene aggiunta una nuova attività, all'attività viene aggiunta una data di scadenza predefinita e una descrizione. La data di scadenza predefinita è il 1 luglio 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>Personalizzare la funzionalità elenco attività progetto

Quando si crea una soluzione di SharePoint, Visual Studio crea automaticamente funzionalità per gli elementi del progetto predefiniti. È possibile personalizzare le impostazioni dell'elenco attività del progetto per il sito di SharePoint utilizzando la finestra di progettazione della funzionalità.

1. In **Esplora soluzioni** espandere **funzionalità**.

2. Aprire il menu di scelta rapida per **Feature1**, quindi scegliere **Progettazione visualizzazioni**.

3. Nella casella **titolo** immettere **progetto elenco attività funzionalità**.

4. Nell'elenco **ambito** scegliere **Web**.

5. Nella finestra **Proprietà** immettere **1.0.0.0** come valore per la proprietà **Version** .

## <a name="customize-the-project-task-list-package"></a>Personalizzare il pacchetto elenco attività del progetto

Quando si crea un progetto SharePoint, Visual Studio aggiunge automaticamente al pacchetto le funzionalità che contengono gli elementi del progetto predefiniti. È possibile personalizzare le impostazioni dell'elenco attività del progetto per il sito di SharePoint utilizzando Progettazione pacchetti.

1. In **SolutionExplorer** aprire il menu di scelta rapida per **Package**, quindi scegliere **Visualizza finestra di progettazione**.

2. Nella casella **nome** immettere **ProjectTaskListPackage**.

3. Selezionare la casella di controllo **Reimposta server Web** .

## <a name="build-and-test-the-project-task-list"></a>Compilare e testare l'elenco attività del progetto

Quando si esegue il progetto, viene aperto il sito di SharePoint. Tuttavia, è necessario passare manualmente al percorso dell'elenco attività.

1. Premere il tasto **F5** per compilare e distribuire l'elenco di attività del progetto.

     Verrà aperto il sito di SharePoint.

2. Scegliere la scheda **Home** .

3. Nella barra laterale sinistra scegliere il collegamento **Project elenco attività** .

     Verrà visualizzata la pagina Project Elenco attività.

4. Nella scheda **Strumenti elenco** scegliere la scheda **elementi** .

5. Nel gruppo **elementi** scegliere il pulsante **nuovo elemento** .

6. Nella casella di testo **titolo** immettere **Task1**.

7. Scegliere il pulsante **Salva** .

     Dopo l'aggiornamento del sito, l'attività **Task1** viene visualizzata con una data di scadenza pari a 7/1/2009.

8. Scegliere **Task1**.

     Viene visualizzata la visualizzazione dettagliata dell'attività e la descrizione mostra "si tratta di un'attività critica".

## <a name="deploy-the-project-task-list"></a>Distribuire l'elenco di attività del progetto

Dopo aver compilato e testato l'elenco attività progetto, è possibile distribuirlo al *sistema locale* o a un *sistema remoto*. Il sistema locale è lo stesso computer in cui è stata sviluppata la soluzione, mentre un sistema remoto è un computer diverso.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Per distribuire l'elenco di attività del progetto nel sistema locale

Sulla barra dei menu di Visual Studio scegliere **Compila**  >  **distribuzione soluzione**.

Visual Studio ricicla il pool di applicazioni IIS, ritira le versioni esistenti della soluzione, copia il file del pacchetto di soluzione (con *estensione wsp*) in SharePoint e quindi ne attiva le funzionalità. È ora possibile usare la soluzione in SharePoint. Per ulteriori informazioni sui passaggi di configurazione della distribuzione, vedere [procedura: modificare una configurazione di distribuzione di SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Per distribuire l'elenco di attività del progetto in un sistema remoto

1. Sulla barra dei menu di Visual Studio scegliere **Compila**  >  **pubblicazione**.

2. Nella finestra di dialogo **pubblica** scegliere il pulsante **di opzione pubblica sul file System** .

     È possibile modificare il percorso di destinazione nella finestra di dialogo **pubblica** scegliendo il pulsante con i puntini di sospensione ![icona dei puntini](../sharepoint/media/ellipsisicon.gif "Icona con i puntini di sospensione") di sospensione e quindi passando a un'altra posizione.

3. Fare clic sul pulsante **Pubblica**.

     Viene creato un file con *estensione wsp* per la soluzione.

4. Copiare il file con *estensione wsp* nel sistema SharePoint remoto.

5. Usare il `Add-SPUserSolution` comando di PowerShell per installare il pacchetto nell'installazione remota di SharePoint. Per le soluzioni farm, utilizzare il `Add-SPSolution` comando.

     Ad esempio: `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Usare il `Install-SPUserSolution` comando di PowerShell per distribuire la soluzione. Per le soluzioni farm, utilizzare il `Install-SPSolution` comando.

     Ad esempio: `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Per altre informazioni sulla distribuzione remota, vedere [uso delle soluzioni](/previous-versions/office/developer/sharepoint-2010/ee534972(v=office.14)) e [aggiunta e distribuzione di soluzioni con PowerShell in SharePoint 2010](http://www.dotnetmafia.com/blogs/dotnettipoftheday/archive/2009/12/02/adding-and-deploying-solutions-with-powershell-in-sharepoint-2010.aspx).

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni su come personalizzare e distribuire le soluzioni SharePoint, vedere gli argomenti seguenti:

- [Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)

- [Windows PowerShell per SharePoint Server 2010](/powershell/module/sharepoint-server)

## <a name="see-also"></a>Vedi anche
[Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
