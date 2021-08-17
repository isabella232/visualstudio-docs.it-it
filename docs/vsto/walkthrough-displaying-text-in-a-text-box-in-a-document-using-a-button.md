---
title: Visualizzare il testo nella casella di testo nel documento usando il pulsante
description: Informazioni su come usare pulsanti e caselle di testo in una personalizzazione a livello di documento per Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e86ff0baf55be711759cdae47304e2013483e40f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075580"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Procedura dettagliata: Visualizzare il testo in una casella di testo in un documento usando un pulsante
  Questa procedura dettagliata illustra come usare i pulsanti e le caselle di testo in una personalizzazione a livello di documento per Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Aggiunta di controlli al documento di Word in un progetto a livello di documento in fase di progettazione.

- Popolamento di una casella di testo quando si fa clic su un pulsante.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nel creare un progetto Documento di Word.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto Documento di Word con il **nome My Word Button**. Nella procedura guidata selezionare **Crea un nuovo documento.**

     Per altre informazioni, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **progetto My Word Button** a **Esplora soluzioni**.

## <a name="add-controls-to-the-word-document"></a>Aggiungere controlli al documento di Word
 I controlli dell'interfaccia utente sono costituiti da un pulsante e da una casella di testo nel documento di Word.

### <a name="to-add-a-button-and-a-text-box"></a>Per aggiungere un pulsante e una casella di testo

1. Verificare che il documento sia aperto nella finestra di progettazione di Visual Studio.

2. Dalla scheda **Controlli comuni** della casella **degli strumenti** trascinare un controllo <xref:Microsoft.Office.Tools.Word.Controls.TextBox> nel documento.

   > [!NOTE]
   > In Word i controlli vengono rilasciati in linea con il testo per impostazione predefinita. È possibile modificare la modalità di inserimento di controlli e oggetti forma modificando l'impostazione predefinita nella **scheda** Modifica della **finestra di** dialogo Opzioni in Word.

3. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

4. Trovare **TextBox1** nella casella **di riepilogo** a discesa della finestra Proprietà e modificare la proprietà **Name** della casella di testo in **displayText**.

5. Trascinare **un controllo** Pulsante nel documento e modificare le proprietà seguenti.

   |Proprietà|Valore|
   |--------------|-----------|
   |**Nome**|**insertText**|
   |**Text**|**Inserisci testo**|

   È ora possibile scrivere il codice che verrà eseguito quando si fa clic sul pulsante.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Popolare la casella di testo quando si fa clic sul pulsante
 Ogni volta che l'utente fa clic sul **pulsante, Hello World!** viene aggiunto alla casella di testo.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Per scrivere nella casella di testo quando si fa clic sul pulsante

1. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse su ThisDocument**, quindi scegliere **Visualizza** codice dal menu di scelta rapida.

2. Aggiungere il codice seguente al gestore eventi <xref:System.Windows.Forms.Control.Click> del pulsante.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet7":::

3. In C# è necessario aggiungere un gestore eventi per il pulsante all'evento <xref:Microsoft.Office.Tools.Word.Document.Startup>. Per informazioni sulla creazione di gestori eventi, vedere [Procedura: Creare gestori eventi in Office progetti](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet8":::

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare il documento per assicurarsi che il messaggio **Hello World.** viene visualizzato nella casella di testo quando si fa clic sul pulsante.

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Fare clic sul pulsante.

3. Verificare che **sia Hello World!** viene visualizzato nella casella di testo.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra i concetti di base relativi all'uso di pulsanti e caselle di testo nei documenti di Word. Ecco alcune possibili attività successive:

- Uso di una casella combinata per modificare la formattazione. Per altre informazioni, vedere Procedura [dettagliata: Modificare la formattazione dei documenti usando i controlli CheckBox.](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)

- Uso di pulsanti di opzione per selezionare gli stili del grafico. Per altre informazioni, vedere [Procedura dettagliata: Aggiornare un grafico in un documento usando i pulsanti di opzione.](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)

## <a name="see-also"></a>Vedi anche
- [Windows Panoramica dei controlli form Office documenti](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)
- [Office e procedure dettagliate per lo sviluppo di applicazioni](../vsto/office-development-samples-and-walkthroughs.md)
- [Procedura: Aggiungere controlli form Windows a Office documenti](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
