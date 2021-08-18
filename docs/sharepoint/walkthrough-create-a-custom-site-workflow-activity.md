---
title: "Procedura dettagliata: Creare un'attività del flusso di lavoro del sito | Microsoft Docs"
description: In questa procedura dettagliata viene illustrato come creare un'attività personalizzata per un flusso di lavoro SharePoint sito usando Visual Studio.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 8a7beaea3b9a7becc2b162304287b4e1b340fceb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135858"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Procedura dettagliata: Creare un'attività del flusso di lavoro del sito personalizzata
  Questa procedura dettagliata illustra come creare un'attività personalizzata per un flusso di lavoro a livello di sito usando [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . I flussi di lavoro a livello di sito si applicano all'intero sito, non solo a un elenco nel sito. L'attività personalizzata crea un elenco di annunci di backup e quindi ne copia il contenuto.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un flusso di lavoro a livello di sito.

- Creazione di un'attività del flusso di lavoro personalizzata.

- Creazione ed eliminazione di un SharePoint di lavoro.

- Copia di elementi da un elenco a un altro.

- Visualizzazione di un elenco sulla barra Avvio rapido.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

## <a name="create-a-site-workflow-custom-activity-project"></a>Creare un progetto di attività personalizzata del flusso di lavoro del sito
 Creare prima di tutto un progetto per contenere e testare l'attività del flusso di lavoro personalizzata.

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Per creare un progetto di attività personalizzata del flusso di lavoro del sito

1. Nella barra dei menu scegliere **File** nuovo Project  >    >   per visualizzare la **finestra di dialogo Project** nuova cartella.

2. Espandere il **SharePoint** in **Visual C#** o **Visual Basic** e quindi scegliere il **nodo 2010.**

3. Nel riquadro **Modelli** scegliere il modello SharePoint **2010 Project** 2010.

4. Nella casella **Nome** immettere **AnnouncementBackup** e quindi fare clic sul **pulsante OK.**

     Verrà **visualizzata SharePoint personalizzazione** guidata.

5. Nella pagina **Specificare il sito e** il livello di sicurezza per il debug  scegliere il pulsante di opzione Distribuisci come soluzione **farm** e quindi scegliere il pulsante Fine per accettare il livello di attendibilità e il sito predefinito.

     Questo passaggio imposta il livello di attendibilità per la soluzione come soluzione farm, l'unica opzione disponibile per i progetti del flusso di lavoro.

6. In **Esplora soluzioni** scegliere il nodo del progetto e quindi nella barra dei menu scegliere Project  >  **Aggiungi nuovo elemento**.

7. In **Visual C#** o **Visual Basic** espandere  il nodo SharePoint e quindi scegliere il **nodo 2010.**

8. Nel riquadro **Modelli** scegliere il modello Flusso di **lavoro sequenziale (solo** soluzione farm) e quindi scegliere **il pulsante** Aggiungi.

     Verrà **visualizzata SharePoint personalizzazione** guidata.

9. Nella pagina **Specificare il nome del flusso di lavoro per il debug** accettare il nome predefinito (AnnouncementBackup - Workflow1). Modificare il tipo di modello di flusso di lavoro **in Flusso di** lavoro sito e quindi scegliere il **pulsante** Avanti.

10. Scegliere il **pulsante** Fine per accettare le impostazioni predefinite rimanenti.

## <a name="add-a-custom-workflow-activity-class"></a>Aggiungere una classe di attività del flusso di lavoro personalizzata
 Aggiungere quindi una classe al progetto per contenere il codice per l'attività del flusso di lavoro personalizzata.

#### <a name="to-add-a-custom-workflow-activity-class"></a>Per aggiungere una classe di attività del flusso di lavoro personalizzata

1. Nella barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento** per visualizzare la finestra di **dialogo** Aggiungi nuovo elemento.

2. Nella visualizzazione **albero Modelli installati** scegliere il nodo **Codice** e quindi scegliere **il** modello Classe nell'elenco di modelli di elemento di progetto. Usare il nome predefinito Class1. Fare clic sul pulsante **Aggiungi**.

3. Sostituire tutto il codice in Class1 con il codice seguente:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb" id="Snippet1":::

4. Salvare il progetto e quindi scegliere Compila soluzione nella barra dei  >  menu.

     Class1 viene visualizzato come azione personalizzata nella casella **degli strumenti** nella scheda **Componenti announcementBackup.**

## <a name="add-the-custom-activity-to-the-site-workflow"></a>Aggiungere l'attività personalizzata al flusso di lavoro del sito
 Aggiungere quindi un'attività al flusso di lavoro per contenere il codice personalizzato.

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Per aggiungere un'attività personalizzata al flusso di lavoro del sito

1. Aprire Workflow1 nella finestra di progettazione del flusso di lavoro nella visualizzazione Progettazione.

2. Trascinare Class1  dalla Casella degli strumenti in modo che venga visualizzata sotto l'attività oppure aprire il menu di scelta rapida per Class1, scegliere Copia , aprire il menu di scelta rapida per la riga sotto l'attività e quindi scegliere `onWorkflowActivated1`  `onWorkflowActivated1` **Incolla**.

3. Salvare il progetto.

## <a name="test-the-site-workflow-custom-activity"></a>Testare l'attività personalizzata del flusso di lavoro del sito
 Eseguire quindi il progetto e avviare il flusso di lavoro del sito. L'attività personalizzata crea un elenco di annunci di backup e ne copia il contenuto dall'elenco annunci corrente. Il codice controlla anche se esiste già un elenco di backup prima di crearne uno. Se esiste già un elenco di backup, viene eliminato. Il codice aggiunge anche un collegamento al nuovo elenco nella barra SharePoint quicklaunch del sito.

#### <a name="to-test-the-site-workflow-custom-activity"></a>Per testare l'attività personalizzata del flusso di lavoro del sito

1. Premere **F5 per** eseguire il progetto e distribuirlo SharePoint.

2. Nella barra Avvio rapido scegliere  il collegamento Elenchi per visualizzare tutti gli elenchi disponibili nel SharePoint sito. Si noti che è presente un solo elenco per gli annunci denominati **Annunci**.

3. Nella parte superiore della pagina Web SharePoint scegliere il **collegamento Flussi di lavoro del** sito.

4. Nella sezione Avvia un nuovo flusso di lavoro scegliere il **collegamento AnnouncementBackup - Workflow1.** Verrà avviato il flusso di lavoro del sito ed eseguito il codice nell'azione personalizzata.

5. Sulla barra Avvio rapido scegliere il collegamento **Backup** annunci. Si noti che tutti gli annunci contenuti **nell'elenco** Annunci sono stati copiati in questo nuovo elenco.

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
