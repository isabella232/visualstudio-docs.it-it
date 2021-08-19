---
title: 'Procedura dettagliata: Creare menu di scelta rapida per i segnalibri'
description: Informazioni su come creare menu di scelta rapida per i controlli Segnalibro in una personalizzazione a livello di documento per Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b852dce9799ebe7aee87bbecbe2beee7a6cd4616
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115018"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>Procedura dettagliata: Creare menu di scelta rapida per i segnalibri
  Questa procedura dettagliata illustra come creare menu di scelta rapida per i controlli in una personalizzazione a livello di <xref:Microsoft.Office.Tools.Word.Bookmark> documento per Word. Quando un utente fa clic con il pulsante destro del mouse sul testo in un segnalibro, viene visualizzato un menu di scelta rapida che offre all'utente le opzioni per la formattazione del testo.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- [Creare il progetto](#BKMK_CreateProject).

- [Aggiungere testo e segnalibri al documento](#BKMK_addtextandbookmarks).

- [Aggiungere comandi a un menu di scelta rapida.](#BKMK_AddCmndsShortMenu)

- [Formattare il testo nel segnalibro](#BKMK_formattextbkmk).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-the-project"></a><a name="BKMK_CreateProject"></a> Creare il progetto
 Il primo passaggio consiste nel creare un progetto documento di Word in Visual Studio.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

- Creare un progetto di documento di Word con il nome **My Bookmark Shortcut Menu**. Nella procedura guidata selezionare **Crea un nuovo documento**. Per altre informazioni, vedere [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **progetto My Bookmark Shortcut Menu** a **Esplora soluzioni**.

## <a name="add-text-and-bookmarks-to-the-document"></a><a name="BKMK_addtextandbookmarks"></a> Aggiungere testo e segnalibri al documento
 Aggiungere del testo al documento e quindi aggiungere due segnalibri sovrapposti.

### <a name="to-add-text-to-your-document"></a>Per aggiungere testo al documento

- Nel documento visualizzato nella finestra di progettazione del progetto digitare il testo seguente.

     **Questo è un esempio di creazione di un menu di scelta rapida quando si fa clic con il pulsante destro del mouse sul testo in un segnalibro.**

### <a name="to-add-a-bookmark-control-to-your-document"></a>Per aggiungere un controllo Bookmark al documento

1. Nella casella **degli** strumenti trascinare un controllo nel documento dalla scheda **Controlli** <xref:Microsoft.Office.Tools.Word.Bookmark> di Word.

    Verrà **visualizzata la finestra di** dialogo Aggiungi controllo segnalibro .

2. Selezionare le parole "creazione di un menu di scelta rapida quando si fa clic con il pulsante destro del mouse sul testo" e quindi fare clic su **OK.**

    `bookmark1` viene aggiunto al documento.

3. Aggiungere un altro controllo alle parole "fare clic con il pulsante <xref:Microsoft.Office.Tools.Word.Bookmark> destro del mouse sul testo in un segnalibro".

    `bookmark2` viene aggiunto al documento.

   > [!NOTE]
   > Le parole "fare clic con il pulsante destro del mouse sul testo" sono sia in `bookmark1` che `bookmark2` in .

   Quando si aggiunge un segnalibro a un documento in fase di progettazione, viene <xref:Microsoft.Office.Tools.Word.Bookmark> creato un controllo . È possibile programmare in base a diversi eventi del segnalibro. È possibile scrivere codice nel caso del segnalibro in modo che quando l'utente fa clic con il pulsante destro del mouse sul testo nel <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> segnalibro, viene visualizzato un menu di scelta rapida.

## <a name="add-commands-to-a-shortcut-menu"></a><a name="BKMK_AddCmndsShortMenu"></a> Aggiungere comandi a un menu di scelta rapida
 Aggiungere pulsanti al menu di scelta rapida visualizzato quando si fa clic con il pulsante destro del mouse sul documento.

### <a name="to-add-commands-to-a-shortcut-menu"></a>Per aggiungere comandi a un menu di scelta rapida

1. Aggiungere un **elemento XML della** barra multifunzione al progetto. Per altre informazioni, vedere [Procedura: Introduzione alla personalizzazione della barra multifunzione.](../vsto/how-to-get-started-customizing-the-ribbon.md)

2. In **Esplora soluzioni** selezionare **ThisDocument.cs** o **ThisDocument.vb**.

3. Sulla barra dei menu scegliere **Visualizza**  >  **codice**.

     Il file **di classe ThisDocument** verrà aperto nell'editor di codice.

4. Aggiungere il codice seguente alla **classe ThisDocument.** Questo codice esegue l'override del metodo CreateRibbonExtensibilityObject e restituisce la classe XML della barra multifunzione all Office appliazione.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet1":::

5. In **Esplora soluzioni** selezionare il file XML della barra multifunzione. Per impostazione predefinita, il file XML della barra multifunzione è denominato Ribbon1.xml.

6. Sulla barra dei menu scegliere **Visualizza**  >  **codice**.

     Il file XML della barra multifunzione viene aperto nell'editor di codice.

7. Nell'editor di codice sostituire il contenuto del file XML della barra multifunzione con il codice seguente.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="BoldButton" label="Bold" onAction="ButtonClick"
               getVisible="GetVisible" />
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"
              getVisible="GetVisible"/>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

     Questo codice aggiunge due pulsanti al menu di scelta rapida visualizzato quando si fa clic con il pulsante destro del mouse sul documento.

8. In **Esplora soluzioni** fare clic con il pulsante destro `ThisDocument` del mouse su e quindi scegliere Visualizza **codice**.

9. Dichiarare le variabili seguenti e una variabile segnalibro a livello di classe.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet2":::

10. In **Esplora soluzioni** selezionare il file di codice della barra multifunzione. Per impostazione predefinita, il file di codice della barra multifunzione è **denominato Ribbon1.cs** o **Ribbon1.vb.**

11. Sulla barra dei menu scegliere **Visualizza**  >  **codice**.

     Il file di codice della barra multifunzione viene aperto nell'editor di codice.

12. Nel file di codice della barra multifunzione aggiungere il metodo seguente. Si tratta di un metodo di callback per i due pulsanti aggiunti al menu di scelta rapida del documento. Questo metodo determina se questi pulsanti vengono visualizzati nel menu di scelta rapida. I pulsanti grassetto e corsivo vengono visualizzati solo se si fa clic con il pulsante destro del mouse sul testo all'interno del segnalibro.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb" id="Snippet5":::

## <a name="format-the-text-in-the-bookmark"></a><a name="BKMK_formattextbkmk"></a> Formattare il testo nel segnalibro

### <a name="to-format-the-text-in-the-bookmark"></a>Per formattare il testo nel segnalibro

1. Nel file di codice della barra multifunzione aggiungere un `ButtonClick` gestore eventi per applicare la formattazione al segnalibro.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb" id="Snippet6":::

2. **Esplora soluzioni** selezionare **ThisDocument.cs** o **ThisDocument.vb**.

3. Sulla barra dei menu scegliere **Visualizza**  >  **codice**.

     Il file **di classe ThisDocument** verrà aperto nell'editor di codice.

4. Aggiungere il codice seguente alla **classe ThisDocument.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet3":::

    > [!NOTE]
    > È necessario scrivere codice per gestire il caso in cui i segnalibri si sovrappongono. In caso contrario, per impostazione predefinita, il codice verrà chiamato per tutti i segnalibri nella selezione.

5. In C# è necessario aggiungere gestori eventi per i controlli segnalibro <xref:Microsoft.Office.Tools.Word.Document.Startup> all'evento . Per informazioni sulla creazione di gestori eventi, vedere [Procedura: Creare gestori](../vsto/how-to-create-event-handlers-in-office-projects.md)eventi in Office progetti .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet4":::

## <a name="test-the-application"></a>Testare l'applicazione
 Testare il documento per verificare che le voci di menu in grassetto e corsivo vengano visualizzate nel menu di scelta rapida quando si fa clic con il pulsante destro del mouse sul testo in un segnalibro e che il testo sia formattato correttamente.

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Fare clic con il pulsante destro del mouse nel primo segnalibro e quindi scegliere **Grassetto**.

3. Verificare che tutto il testo in `bookmark1` sia formattato in grassetto.

4. Fare clic con il pulsante destro del mouse sul testo in cui si sovrappongono i segnalibri e quindi scegliere **Corsivo.**

5. Verificare che tutto il testo in sia in corsivo e che solo la parte del testo che si sovrapponga sia `bookmark2` `bookmark1` in `bookmark2` corsivo.

## <a name="next-steps"></a>Passaggi successivi
 Ecco alcune possibili attività successive:

- Scrivere codice per rispondere agli eventi dei controlli host in Excel. Per altre informazioni, vedere [Procedura dettagliata: Programmare sugli eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

- Usare una casella di controllo per modificare la formattazione in un segnalibro. Per altre informazioni, vedere [Procedura dettagliata: Modificare la formattazione dei documenti usando i controlli CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Vedi anche
- [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Controllo Segnalibro](../vsto/bookmark-control.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
