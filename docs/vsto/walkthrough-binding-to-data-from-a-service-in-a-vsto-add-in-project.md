---
title: "Procedura dettagliata: Eseguire l'associazione ai dati da un servizio in un progetto di componente aggiuntivo VSTO"
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6ba36b62aa9f4330cc88eaa198d0488d7e43b341
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982083"
---
# <a name="walkthrough-bind-to-data-from-a-service-in-a-vsto-add-in-project"></a>Procedura dettagliata: Eseguire l'associazione ai dati da un servizio in un progetto di componente aggiuntivo VSTO
  È possibile associare dati ai controlli host nei progetti di componente aggiuntivo VSTO. Questa procedura dettagliata illustra come aggiungere controlli a un documento di Microsoft Office Word, associare i controlli ai dati recuperati dal servizio per la gestione del contenuto MSDN e rispondere agli eventi in fase di esecuzione.

 **Si applica a:** Le informazioni contenute in questo argomento si applicano ai progetti a livello di applicazione per Word 2010. Per altre informazioni, vedere [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).

 Questa procedura dettagliata illustra le attività seguenti:

- Aggiunta di un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> controllo a un documento in fase di esecuzione.

- Associazione di <xref:Microsoft.Office.Tools.Word.RichTextContentControl> controllo ai dati da un servizio web.

- Risposta all'evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> di un controllo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> .

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-project"></a>Creare un nuovo progetto
 Il primo passaggio consiste nel creare un progetto di componente aggiuntivo VSTO per Word.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di componente aggiuntivo VSTO di Word denominato **MTPS Content Service**usando Visual Basic o C#.

     Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il file `ThisAddIn.vb` o `ThisAddIn.cs` e aggiunge il progetto a **Esplora soluzioni**.

## <a name="add-a-web-service"></a>Aggiungere un servizio web
 In questa procedura dettagliata utilizzare un servizio web denominato MTPS Content Service. Questo servizio web restituisce le informazioni da un determinato articolo MSDN sotto forma di stringa XML o testo normale. In un passaggio successivo viene illustrato come visualizzare le informazioni restituite in un controllo contenuto.

### <a name="to-add-the-mtps-content-service-to-the-project"></a>Per aggiungere MTPS content service al progetto

1. Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.

2. Nella **Configurazione guidata origine dati**fare clic su **Servizio**e quindi fare clic su **Avanti**.

3. Nel campo **Indirizzo** digitare l'URL seguente:

     **http://services.msdn.microsoft.com/ContentServices/ContentService.asmx**

4. Fare clic su **Vai**.

5. Nel campo **Spazio dei nomi** digitare **ContentService**e fare clic su **OK**.

6. Nella finestra di dialogo della procedura guidata **Aggiungi riferimento** fare clic su **Fine**.

## <a name="add-a-content-control-and-bind-to-data-at-runtime"></a>Aggiungere un controllo contenuto ed eseguire l'associazione ai dati in fase di esecuzione
 Nei progetti di componente aggiuntivo VSTO, aggiungere e associare i controlli in fase di esecuzione. Per questa procedura dettagliata, configurare il controllo content per recuperare i dati dal servizio web quando un utente fa clic all'interno del controllo.

### <a name="to-add-a-content-control-and-bind-to-data"></a>Per aggiungere un controllo contenuto ed eseguire l'associazione a dati

1. Nella classe `ThisAddIn` dichiarare le variabili per il servizio MTPS Content Service, il controllo contenuto e il data binding.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#2)]

2. Aggiungere il metodo seguente alla classe `ThisAddIn` . Questo metodo crea un controllo contenuto all'inizio del documento attivo.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#4)]

3. Aggiungere il metodo seguente alla classe `ThisAddIn` . Questo metodo inizializza gli oggetti necessari per creare e inviare una richiesta al servizio web.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#6)]

4. Creare un gestore eventi per recuperare il documento di MSDN Library relativo ai controlli contenuto quando un utente fa clic all'interno del controllo contenuto e associa i dati al controllo contenuto.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#5)]

5. Chiamare i metodi `AddRichTextControlAtRange` e `InitializeServiceObjects` dal metodo `ThisAddIn_Startup` . Per i programmatori C#, aggiungere un gestore eventi.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#3)]

## <a name="test-the-add-in"></a>Testare il componente aggiuntivo
 Quando si apre Word, viene visualizzato il controllo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> . Il testo del controllo cambia quando si fa clic al suo interno.

### <a name="to-test-the-vsto-add-in"></a>Per testare il componente aggiuntivo VSTO

1. Premere **F5**.

2. Fare clic all'interno del controllo contenuto.

     Le informazioni vengono scaricate da MTPS Content Service e visualizzate nel controllo contenuto.

## <a name="see-also"></a>Vedere anche
- [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
