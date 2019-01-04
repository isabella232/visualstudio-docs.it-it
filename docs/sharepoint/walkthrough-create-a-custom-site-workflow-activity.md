---
title: "Procedura dettagliata: Creare un'attività flusso di lavoro del sito personalizzato | Microsoft Docs"
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e828926b5ddfc70f64f729849aaec99dbdade103
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951813"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Procedura dettagliata: Creare un'attività flusso di lavoro del sito personalizzata
  Questa procedura dettagliata viene illustrato come creare un'attività personalizzata per un flusso di lavoro a livello di sito utilizzando [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. (I flussi di lavoro a livello di sito si applicano all'intero sito, non solo un elenco nel sito). L'attività personalizzata consente di creare un elenco di annunci di backup e quindi copia il contenuto dell'elenco di annunci al suo interno.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
- Creazione di un flusso di lavoro a livello di sito.  
  
- Creazione di un'attività flusso di lavoro personalizzato.  
  
- Creazione ed eliminazione di un elenco di SharePoint.  
  
- Copia gli elementi da un unico elenco a altro.  
  
- Visualizzazione di un elenco nella barra Avvio veloce.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.
  
-   Visual Studio.  
  
## <a name="create-a-site-workflow-custom-activity-project"></a>Creare un progetto di attività personalizzata flusso di lavoro sito
 In primo luogo, creare un progetto per gestire e testare l'attività flusso di lavoro personalizzato.  
  
#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Per creare un progetto di attività personalizzata flusso di lavoro sito  
  
1.  Nella barra dei menu, scegliere **File** > **New** > **progetto** per visualizzare il **nuovo progetto** nella finestra di dialogo.  
  
2.  Espandere la **SharePoint** nodo sotto **Visual c#** o **Visual Basic**, quindi scegliere il **2010** nodo.  
  
3.  Nel **modelli** riquadro, scegliere il **progetto SharePoint 2010** modello.  
  
4.  Nel **Name** casella, immettere **AnnouncementBackup**e quindi scegliere il **OK** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** viene visualizzata.  
  
5.  Nel **specificare il livello di sito e la sicurezza per il debug** pagina, scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **fine** pulsante per accettare il sito di livello e predefinito trust.  
  
     Questo passaggio consente di impostare il livello di attendibilità per la soluzione come soluzione farm, l'unica opzione disponibile per i progetti di flusso di lavoro.  
  
6.  Nelle **Esplora soluzioni**, scegliere il nodo del progetto e quindi nella barra dei menu, scegliere **Project** > **Aggiungi nuovo elemento**.  
  
7.  In presenza di una **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
8.  Nel **modelli** riquadro, scegliere il **flusso di lavoro sequenziale (solo soluzione Farm)** modello e quindi scegliere il **Add** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** viene visualizzata.  
  
9. Nel **specificare il nome del flusso di lavoro per il debug** pagina, accettare il nome predefinito (AnnouncementBackup - Workflow1). Modificare il tipo di modello del flusso di lavoro in **sito flusso di lavoro**, quindi scegliere il **successivo** pulsante.  
  
10. Scegliere il **fine** pulsante per accettare le impostazioni predefinite rimanenti.  
  
## <a name="add-a-custom-workflow-activity-class"></a>Aggiungere una classe di attività flusso di lavoro personalizzato
 Successivamente, aggiungere una classe al progetto per contenere il codice per l'attività flusso di lavoro personalizzato.  
  
#### <a name="to-add-a-custom-workflow-activity-class"></a>Per aggiungere una classe di attività flusso di lavoro personalizzato  
  
1.  Nella barra dei menu, scegliere **Project** > **Aggiungi nuovo elemento** per visualizzare la **Aggiungi nuovo elemento** nella finestra di dialogo.  
  
2.  Nel **modelli installati** visualizzazione ad albero, scegliere il **codice** nodo e quindi scegliere il **classe** modello nell'elenco dei modelli di elemento di progetto. Usare il nome predefinito Class1. Scegliere il pulsante **Aggiungi**.  
  
3.  Sostituire tutto il codice in Class1 con gli elementi seguenti:  
  
     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]  
  
4.  Salvare il progetto e quindi nella barra dei menu scegliere **compilare** > **Compila soluzione**.  
  
     Class1 viene visualizzato come un'azione personalizzata nel **casella degli strumenti** nel **AnnouncementBackup componenti** scheda.  
  
## <a name="add-the-custom-activity-to-the-site-workflow"></a>Aggiungere l'attività personalizzata al flusso di lavoro sito
 Successivamente, aggiungere un'attività al flusso di lavoro per contenere il codice personalizzato.  
  
#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Per aggiungere un'attività personalizzata al flusso di lavoro sito
  
1.  Aprire Workflow1 in Progettazione flussi di lavoro nella visualizzazione progettazione.  
  
2.  Trascinare Class1 dal **casella degli strumenti** in modo che venga visualizzata sotto il `onWorkflowActivated1` attività o aprire il menu di scelta rapida per Class1, scegliere **copia**, aprire il menu di scelta rapida per la riga sotto il `onWorkflowActivated1` attività, quindi scegliere **Incolla**.  
  
3.  Salvare il progetto.  
  
## <a name="test-the-site-workflow-custom-activity"></a>Testare l'attività personalizzata flusso di lavoro sito
 Successivamente, eseguire il progetto e avviare il flusso di lavoro del sito. L'attività personalizzata consente di creare un elenco di annunci di backup e copia il contenuto dall'elenco di annunci corrente al suo interno. Il codice di verifica anche se un elenco di backup esiste già prima di crearne una. Se esiste già un elenco di backup, viene eliminato. Il codice aggiunge anche un collegamento per il nuovo elenco sulla barra Avvio veloce del sito di SharePoint.  
  
#### <a name="to-test-the-site-workflow-custom-activity"></a>Per testare l'attività personalizzata flusso di lavoro sito  
  
1.  Scegliere il **F5** tasto per eseguire il progetto e distribuirlo in SharePoint.  
  
2.  Nella barra Avvio veloce scegliere il **Elenca** link per visualizzare tutti gli elenchi che sono disponibili nel sito di SharePoint. Si noti che è disponibile solo un elenco degli annunci denominata **annunci**.  
  
3.  Nella parte superiore della pagina Web di SharePoint, scegliere il **flussi di lavoro sito** collegamento.  
  
4.  Sotto l'inizio di una sezione del flusso di lavoro nuove, scegliere il **AnnouncementBackup - Workflow1** collegamento. Verrà avviato il flusso di lavoro del sito e viene eseguito il codice dell'azione personalizzata.  
  
5.  Nella barra Avvio veloce scegliere il **annunci Backup** collegamento. Si noti che tutti gli annunci che sono contenuti nel **annunci** elenco sono stati copiati in questo nuovo elenco.  
  
## <a name="see-also"></a>Vedere anche
 [Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)   
 [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
