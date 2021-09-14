---
title: Aggiungere controlli da documentare in fase di VSTO componente aggiuntivo
description: Informazioni su come usare la barra multifunzione per consentire agli utenti di aggiungere una classe Button o un'interfaccia RichTextContentControl a un documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ddc4f42be5c1b9a6fb439cdb097480b8d7a60e76
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710042"
---
# <a name="walkthrough-add-controls-to-a-document-at-run-time-in-a-vsto-add-in"></a>Procedura dettagliata: Aggiungere controlli a un documento in fase di esecuzione in VSTO componente aggiuntivo
  È possibile aggiungere controlli a qualsiasi Microsoft Office documento di Word aperto usando VSTO componente aggiuntivo. Questa procedura dettagliata illustra come usare la barra multifunzione per consentire agli utenti di aggiungere un <xref:Microsoft.Office.Tools.Word.Controls.Button> oggetto o a un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> documento.

 **Si applica a:** le informazioni contenute in questo argomento si applicano ai progetti di componente aggiuntivo VSTO per Word 2010. Per altre informazioni, vedere [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).

 Vengono illustrate le attività seguenti:

- Creazione di un nuovo progetto di componente aggiuntivo VSTO per Word.

- Creazione di un'interfaccia utente per l'aggiunta di controlli al documento.

- Aggiunta di controlli ai documenti in fase di esecuzione.

- Rimozione di controlli dal documento.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-word-add-in-project"></a>Creare un nuovo progetto di componente aggiuntivo di Word
 Creare innanzitutto un progetto di componente aggiuntivo VSTO per Word.

### <a name="to-create-a-new-word-vsto-add-in-project"></a>Per creare un nuovo progetto di componente aggiuntivo VSTO per Word.

1. Creare un VSTO di componente aggiuntivo per Word con il nome **WordDynamicControls.** Per altre informazioni, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Aggiungere un riferimento all'assembly **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** . Tale riferimento è necessario per aggiungere un controllo Windows Form a livello di codice al documento più avanti in questa procedura dettagliata.

## <a name="provide-a-ui-to-add-controls-to-a-document"></a>Fornire un'interfaccia utente per aggiungere controlli a un documento
 Aggiungere una scheda personalizzata alla barra multifunzione di Word. Gli utenti possono selezionare caselle di controllo nella scheda per aggiungere i controlli a un documento.

### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>Per creare un'interfaccia utente per l'aggiunta di controlli a un documento

1. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione (finestra di progettazione visiva)**.

3. Modificare il nome della nuova barra multifunzione in **MyRibbon** e quindi scegliere **Aggiungi**.

    Nella finestra di progettazione della barra multifunzione viene aperto un file **MyRibbon.cs** o **MyRibbon.vb** , che visualizza una scheda e un gruppo predefiniti.

4. Nella finestra di progettazione della barra multifunzione fare clic sul gruppo **group1** .

5. Nella finestra **Proprietà** impostare la proprietà **Etichetta** per **group1** su **Add Controls**.

6. Dalla scheda **Controlli barra multifunzione di Office** della **Casella degli strumenti** trascinare un controllo **ToggleButton** in **group1**.

7. Fare clic su **CheckBox1** per selezionarlo.

8. Nella finestra **Proprietà** modificare le seguenti proprietà:

   | Proprietà | Valore |
   |-----------|-----------------------|
   | **Nome** | **addButtonCheckBox** |
   | **Label** | **Pulsante Aggiungi** |

9. Aggiungere una seconda casella di controllo a **group1** e quindi modificare le proprietà seguenti.

   | Proprietà | Valore |
   |-----------|---------------------------|
   | **Nome** | **addRichTextCheckBox** |
   | **Label** | **Add Rich Text Control** |

10. Nella finestra di progettazione della barra multifunzione fare doppio clic su **Aggiungi pulsante**.

     Il gestore eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> della casella di controllo **Aggiungi pulsante** viene aperto nell'editor di codice.

11. Tornare alla finestra di progettazione della barra multifunzione e fare doppio clic su **Add Rich Text Control**.

     Il gestore eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> della casella di controllo **Add Rich Text Control** viene aperto nell'editor di codice.

    Più avanti in questa procedura dettagliata si aggiungerà codice a questi gestori eventi per aggiungere e rimuovere i controlli nel documento attivo.

## <a name="add-and-remove-controls-on-the-active-document"></a>Aggiungere e rimuovere controlli nel documento attivo
 Nel codice del componente aggiuntivo VSTO è necessario convertire il documento attivo in un <xref:Microsoft.Office.Tools.Word.Document>*elemento host* prima di poter aggiungere un controllo. Nelle soluzioni Office si possono aggiungere controlli gestiti solo agli elementi host, che agiscono da contenitori per i controlli. In VSTO progetti di componente aggiuntivo, gli elementi host possono essere creati in fase di esecuzione usando il `GetVstoObject` metodo .

 Aggiungere metodi alla classe `ThisAddIn` che possono essere chiamati per aggiungere o rimuovere un oggetto <xref:Microsoft.Office.Tools.Word.Controls.Button> o <xref:Microsoft.Office.Tools.Word.RichTextContentControl> nel documento attivo. Più avanti in questa procedura dettagliata si chiameranno tali metodi dai gestori eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> delle caselle di controllo sulla barra multifunzione.

### <a name="to-add-and-remove-controls-on-the-active-document"></a>Per aggiungere e rimuovere controlli nel documento attivo

1. In **Esplora soluzioni** fare doppio clic su *ThisAddIn.cs* o *ThisAddIn.vb* per aprire il file nell'editor di codice.

2. Aggiungere il codice seguente alla classe `ThisAddIn` . Questo codice dichiara gli oggetti <xref:Microsoft.Office.Tools.Word.Controls.Button> e <xref:Microsoft.Office.Tools.Word.RichTextContentControl> che rappresentano i controlli che verranno aggiunti al documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet1":::

3. Aggiungi alla classe `ThisAddIn` il metodo seguente. Quando l'utente fa clic sulla casella di controllo **Aggiungi pulsante** sulla barra multifunzione, questo metodo aggiunge un oggetto <xref:Microsoft.Office.Tools.Word.Controls.Button> alla selezione corrente nel documento se la casella di controllo è selezionata oppure rimuove l'oggetto <xref:Microsoft.Office.Tools.Word.Controls.Button> se la casella di controllo è deselezionata.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet2":::

4. Aggiungi alla classe `ThisAddIn` il metodo seguente. Quando l'utente fa clic sulla casella di controllo **Add Rich Text Control** sulla barra multifunzione, questo metodo aggiunge un oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> alla selezione corrente nel documento se la casella di controllo è selezionata oppure rimuove l'oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> se la casella di controllo è deselezionata.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet3":::

## <a name="remove-the-button-control-when-the-document-is-saved"></a>Rimuovere il controllo Button quando il documento viene salvato
 I controlli Windows Form non vengono mantenuti quando il documento viene salvato e quindi chiuso. Nel documento, però, rimane un wrapper ActiveX per ogni controllo e il bordo di questo wrapper è visibile agli utenti finali quando il documento viene riaperto. Esistono diversi modi per pulire i controlli form creati Windows in modo dinamico VSTO componenti aggiuntivi. In questa procedura dettagliata il controllo viene rimosso a livello <xref:Microsoft.Office.Tools.Word.Controls.Button> di codice quando il documento viene salvato.

### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Per rimuovere il controllo Button quando il documento viene salvato

1. Nel file *di codice ThisAddIn.cs* *o ThisAddIn.vb* aggiungere il metodo seguente alla `ThisAddIn` classe . Questo metodo è un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> . Se al documento salvato è associato un elemento host <xref:Microsoft.Office.Tools.Word.Document> , il gestore eventi ottiene l'elemento host e rimuove il controllo <xref:Microsoft.Office.Tools.Word.Controls.Button> , se esistente.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet4":::

2. In C# aggiungere il codice seguente al gestore eventi `ThisAddIn_Startup` . Questo codice è necessario in C# per connettere il gestore eventi `Application_DocumentBeforeSave` all'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet5":::

## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Aggiungere e rimuovere controlli quando l'utente fa clic sulle caselle di controllo sulla barra multifunzione
 Infine, modificare i gestori eventi delle caselle di controllo aggiunte alla barra multifunzione per aggiungere o rimuovere <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> controlli nel documento.

### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Per aggiungere o rimuovere controlli quando l'utente fa clic sulle caselle di controllo sulla barra multifunzione

1. Nel file *di codice MyRibbon.cs* o *MyRibbon.vb* sostituire i gestori eventi e generati `addButtonCheckBox_Click` con il codice `addRichTextCheckBox_Click` seguente. Questo codice ridefinisce i gestori eventi per chiamare i metodi `ToggleButtonOnDocument` e `ToggleRichTextControlOnDocument` che sono stati aggiunti alla classe `ThisAddIn` più indietro in questa procedura dettagliata.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs" id="Snippet6":::

## <a name="test-the-solution"></a>Testare la soluzione
 Aggiungere controlli a un documento selezionandoli dalla scheda personalizzata sulla barra multifunzione. Quando si salva il documento, il controllo <xref:Microsoft.Office.Tools.Word.Controls.Button> viene rimosso.

### <a name="to-test-the-solution"></a>Per testare la soluzione.

1. Premere **F5** per eseguire il progetto.

2. Nel documento attivo premere **INVIO** più volte per aggiungere nuovi paragrafi vuoti al documento.

3. Selezionare il primo paragrafo.

4. Fare clic sulla scheda **Componenti aggiuntivi** .

5. Nel gruppo **Add Controls** fare clic su **Aggiungi pulsante**.

     Nel primo paragrafo viene visualizzato un pulsante.

6. Selezionare l'ultimo paragrafo.

7. Nel gruppo **Add Controls** fare clic su **Add Rich Text Control**.

     All'ultimo paragrafo viene aggiunto un controllo contenuto RTF.

8. Salvare il documento.

     Il pulsante viene rimosso dal documento.

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni sui controlli nei componenti aggiuntivi VSTO, vedere questi argomenti:

- Per un esempio che illustra come aggiungere molti altri tipi di controlli a un documento in fase di esecuzione e ricreare i controlli quando il documento viene riaperto, vedere l'esempio di controlli dinamici di Word Add-In in procedure dettagliate e esempi di sviluppo di [Office](../vsto/office-development-samples-and-walkthroughs.md).

- Per una procedura dettagliata che illustra come aggiungere controlli a un foglio di lavoro usando un componente aggiuntivo VSTO per Excel, vedere [Procedura dettagliata:](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)Aggiungere controlli a un foglio di lavoro in fase di esecuzione nel progetto di componente aggiuntivo VSTO .

## <a name="see-also"></a>Vedi anche
- [Soluzioni Word](../vsto/word-solutions.md)
- [Aggiungere controlli ai Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Rendere persistenti i controlli dinamici Office documenti](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Procedura: Aggiungere controlli form Windows a Office documenti](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Procedura: Aggiungere controlli contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Estendere documenti di Word Excel cartelle di lavoro VSTO componenti aggiuntivi in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
