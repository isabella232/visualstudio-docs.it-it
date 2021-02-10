---
title: "Procedura dettagliata: creare un'attività del flusso di lavoro del sito personalizzato | Microsoft Docs"
description: In questa procedura dettagliata, vedere come creare un'attività personalizzata per un flusso di lavoro di SharePoint a livello di sito con Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f2b722ccef084286287b9825c43fa9069f64dcc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937719"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Procedura dettagliata: creare un'attività personalizzata del flusso di lavoro del sito
  In questa procedura dettagliata viene illustrato come creare un'attività personalizzata per un flusso di lavoro a livello di sito tramite [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . I flussi di lavoro a livello di sito si applicano all'intero sito, non solo a un elenco sul sito. L'attività personalizzata crea un elenco di annunci di backup e quindi copia il contenuto dell'elenco degli annunci al suo interno.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un flusso di lavoro a livello di sito.

- Creazione di un'attività personalizzata del flusso di lavoro.

- Creazione ed eliminazione di un elenco SharePoint.

- Copia di elementi da un elenco a un altro.

- Visualizzazione di un elenco sulla barra QuickLaunch.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

## <a name="create-a-site-workflow-custom-activity-project"></a>Creare un progetto di attività personalizzata del flusso di lavoro del sito
 Per prima cosa, creare un progetto per mantenere e testare l'attività personalizzata del flusso di lavoro.

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Per creare un progetto di attività personalizzata del flusso di lavoro del sito

1. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto** per visualizzare la finestra di dialogo **nuovo progetto** .

2. Espandere il nodo **SharePoint** sotto **Visual C#** o **Visual Basic**, quindi scegliere il nodo **2010** .

3. Nel riquadro **modelli** scegliere il modello di **progetto SharePoint 2010** .

4. Nella casella **nome** immettere **AnnouncementBackup**, quindi scegliere il pulsante **OK** .

     Viene visualizzata la **personalizzazione guidata SharePoint** .

5. Nella pagina **specificare il sito e il livello di sicurezza per il debug** scegliere il pulsante di opzione **Distribuisci come soluzione farm** , quindi scegliere il pulsante **fine** per accettare il livello di attendibilità e il sito predefinito.

     Questo passaggio consente di impostare il livello di attendibilità della soluzione come soluzione farm, l'unica opzione disponibile per i progetti di flusso di lavoro.

6. In **Esplora soluzioni** scegliere il nodo del progetto, quindi nella barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

7. In **Visual C#** o **Visual Basic** espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

8. Nel riquadro **modelli** scegliere il modello **flusso di lavoro sequenziale (solo soluzione farm)** , quindi scegliere il pulsante **Aggiungi** .

     Viene visualizzata la **personalizzazione guidata SharePoint** .

9. Nella pagina **specificare il nome del flusso di lavoro per il debug** accettare il nome predefinito (AnnouncementBackup-Workflow1). Modificare il tipo di modello di flusso di lavoro nel **flusso di lavoro del sito**, quindi scegliere il pulsante **Avanti** .

10. Scegliere il pulsante **fine** per accettare le impostazioni predefinite rimanenti.

## <a name="add-a-custom-workflow-activity-class"></a>Aggiungere una classe di attività del flusso di lavoro personalizzata
 Aggiungere quindi una classe al progetto in modo che contenga il codice per l'attività personalizzata del flusso di lavoro.

#### <a name="to-add-a-custom-workflow-activity-class"></a>Per aggiungere una classe di attività del flusso di lavoro personalizzata

1. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento** per visualizzare la finestra di dialogo **Aggiungi nuovo elemento** .

2. Nella visualizzazione albero **modelli installati** scegliere il nodo **codice** , quindi scegliere il modello **classe** nell'elenco dei modelli di elemento di progetto. Usare il nome predefinito Class1. Fare clic sul pulsante **Aggiungi**.

3. Sostituire tutto il codice in Class1 con quanto segue:

     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]

4. Salvare il progetto, quindi nella barra dei menu scegliere **Compila**  >  **Compila soluzione**.

     Class1 viene visualizzato come azione personalizzata nella **casella degli strumenti** nella scheda **componenti di AnnouncementBackup** .

## <a name="add-the-custom-activity-to-the-site-workflow"></a>Aggiungere l'attività personalizzata al flusso di lavoro del sito
 Aggiungere quindi un'attività al flusso di lavoro per contenere il codice personalizzato.

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Per aggiungere un'attività personalizzata al flusso di lavoro del sito

1. Aprire Workflow1 in Progettazione flussi di lavoro in visualizzazione progettazione.

2. Trascinare Class1 dalla **casella degli strumenti** in modo che venga visualizzato sotto l' `onWorkflowActivated1` attività oppure aprire il menu di scelta rapida per Class1, scegliere **copia**, aprire il menu di scelta rapida per la riga sotto l' `onWorkflowActivated1` attività, quindi scegliere **Incolla**.

3. Salvare il progetto.

## <a name="test-the-site-workflow-custom-activity"></a>Testare l'attività personalizzata del flusso di lavoro del sito
 Eseguire quindi il progetto e avviare il flusso di lavoro del sito. L'attività personalizzata consente di creare un elenco di annunci di backup e di copiarvi il contenuto dall'elenco degli annunci corrente. Il codice controlla anche se un elenco di backup esiste già prima di crearne uno. Se un elenco di backup esiste già, viene eliminato. Il codice aggiunge anche un collegamento al nuovo elenco nella barra QuickLaunch del sito di SharePoint.

#### <a name="to-test-the-site-workflow-custom-activity"></a>Per testare l'attività personalizzata del flusso di lavoro del sito

1. Premere il tasto **F5** per eseguire il progetto e distribuirlo in SharePoint.

2. Sulla barra QuickLaunch scegliere il collegamento **elenchi** per visualizzare tutti gli elenchi disponibili nel sito di SharePoint. Si noti che è presente un solo elenco per gli **annunci denominati**.

3. Nella parte superiore della pagina Web di SharePoint scegliere il collegamento **flussi di lavoro del sito** .

4. Nella sezione avviare un nuovo flusso di lavoro scegliere il collegamento **AnnouncementBackup-Workflow1** . Viene avviato il flusso di lavoro del sito ed eseguito il codice nell'azione personalizzata.

5. Sulla barra QuickLaunch scegliere il collegamento **backup annunci** . Si noti che tutti gli annunci contenuti nell'elenco degli **annunci** sono stati copiati in questo nuovo elenco.

## <a name="see-also"></a>Vedi anche
- [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
