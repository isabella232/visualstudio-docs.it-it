---
title: Aggiungere controlli al foglio di lavoro in fase di esecuzione nel VSTO del componente aggiuntivo
description: Informazioni su come usare la barra multifunzione per consentire agli utenti di aggiungere un controllo Button, un controllo NamedRange e un oggetto ListObject a un foglio di lavoro.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d8706772526682c8856cedf5881ee0cd3f75dc76
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032147"
---
# <a name="walkthrough-add-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>Procedura dettagliata: Aggiungere controlli a un foglio di lavoro in fase di VSTO progetto di componente aggiuntivo
  È possibile aggiungere controlli a qualsiasi foglio di lavoro aperto mediante un componente aggiuntivo VSTO per Excel. Questa procedura dettagliata illustra come usare la barra multifunzione per consentire agli utenti l'aggiunta di oggetti <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> e <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro. Per informazioni, vedere [Aggiungere controlli Office documenti in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)

 **Si applica a:** Le informazioni contenute in questo argomento si applicano VSTO di componenti aggiuntivi per Excel. Per altre informazioni, vedere [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).

 Vengono illustrate le attività seguenti:

- Creazione di un'interfaccia utente per l'aggiunta di controlli al foglio di lavoro.

- Aggiunta di controlli al foglio di lavoro.

- Rimozione di controlli dal foglio di lavoro.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Excel

## <a name="create-a-new-excel-vsto-add-in-project"></a>Creare un nuovo Excel VSTO di componente aggiuntivo
 Creare innanzitutto un progetto di componente aggiuntivo VSTO per Excel.

### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Per creare un nuovo progetto di componente aggiuntivo VSTO per Excel

1. In creare un progetto Excel VSTO componente aggiuntivo con [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] il nome **ExcelDynamicControls**. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Aggiungere un riferimento **all'Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** assembly. Tale riferimento è necessario per aggiungere a livello di codice un controllo Windows Form al foglio di lavoro più avanti in questa procedura dettagliata.

## <a name="provide-a-ui-to-add-controls-to-a-worksheet"></a>Fornire un'interfaccia utente per aggiungere controlli a un foglio di lavoro
 Aggiungere una scheda personalizzata alla barra multifunzione di Excel. Gli utenti possono selezionare caselle di controllo nella scheda per aggiungere i controlli a un foglio di lavoro.

#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Per creare un'interfaccia utente per l'aggiunta di controlli a un foglio di lavoro

1. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Nella finestra **di dialogo Aggiungi nuovo elemento** selezionare Barra multifunzione **(finestra di progettazione visiva)** e quindi fare clic su **Aggiungi**.

     Un file denominato **Ribbon1.cs o** **Ribbon1.vb** viene aperto nella finestra di progettazione della barra multifunzione e visualizza una scheda e un gruppo predefiniti.

3. Dalla scheda **Controlli barra multifunzione di Office** della **Casella degli strumenti** trascinare un controllo ToggleButton in **group1**.

4. Fare clic su **CheckBox1** per selezionarlo.

5. Nella finestra **Proprietà** modificare le seguenti proprietà:

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**Button**|
    |**Etichetta**|**Button**|

6. Aggiungere una seconda casella di controllo a **group1** e quindi modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**NamedRange**|
    |**Etichetta**|**NamedRange**|

7. Aggiungere una terza casella di controllo **a group1** e quindi modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**ListObject**|
    |**Etichetta**|**ListObject**|

## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di lavoro
 I controlli gestiti possono essere aggiunti solo a elementi host che fungono da contenitori. Poiché i progetti di componenti aggiuntivi VSTO vengono usati con qualsiasi cartella di lavoro aperta, il componente aggiuntivo VSTO converte il foglio di lavoro in un elemento host oppure ottiene un elemento host esistente, prima di aggiungere il controllo. Aggiungere codice ai gestori di eventi Click di ciascun controllo per generare un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> basato su un foglio di lavoro aperto. Aggiungere quindi un oggetto <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> e <xref:Microsoft.Office.Tools.Excel.ListObject> alla selezione corrente nel foglio di lavoro.

### <a name="to-add-controls-to-a-worksheet"></a>Per aggiungere controlli a un foglio di lavoro

1. Nella finestra di progettazione della barra multifunzione fare doppio clic su **Pulsante**.

     Il <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> gestore eventi della casella di controllo **Pulsante** viene aperto nell'editor di codice.

2. Sostituire il gestore eventi `Button_Click` con il codice seguente.

     Questo codice usa il metodo `GetVstoObject` per ottenere un elemento host che rappresenta il primo foglio di lavoro nella cartella di lavoro e quindi viene aggiunto un controllo <xref:Microsoft.Office.Tools.Excel.Controls.Button> per la cella attualmente selezionata.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet2":::

3. In **Esplora soluzioni** selezionare *Ribbon1.cs* o *Ribbon1.vb*.

4. Scegliere **Progettazione** dal menu **Visualizza**.

5. Nella finestra di progettazione della barra multifunzione fare doppio clic **su NamedRange**.

6. Sostituire il gestore eventi `NamedRange_Click` con il codice seguente.

     Questo codice usa il metodo `GetVstoObject` per ottenere un elemento host che rappresenta il primo foglio di lavoro nella cartella di lavoro e quindi definisce un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> per la cella o le celle attualmente selezionate.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet3":::

7. Nella finestra di progettazione della barra multifunzione fare doppio clic **su ListObject**.

8. Sostituire il gestore eventi `ListObject_Click` con il codice seguente.

     Questo codice usa il metodo `GetVstoObject` per ottenere un elemento host che rappresenta il primo foglio di lavoro nella cartella di lavoro e quindi definisce un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> per la cella o le celle attualmente selezionate.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet4":::

9. Aggiungere le seguenti istruzioni alla parte iniziale del file di codice della barra multifunzione.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet1":::

## <a name="remove-controls-from-the-worksheet"></a>Rimuovere i controlli dal foglio di lavoro
 I controlli non sono resi permanenti quando il foglio di lavoro viene salvato e chiuso. È necessario rimuovere a livello di codice tutti i controlli Windows Form generati prima che il foglio di lavoro venga salvato, altrimenti quando la cartella di lavoro viene nuovamente aperta, verrà visualizzata solo una struttura del controllo. Aggiungere all'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> il codice per rimuovere i controlli Windows Form dalla raccolta di controlli dell'elemento host generato. Per altre informazioni, vedere Rendere persistenti i controlli [dinamici nei Office documenti.](../vsto/persisting-dynamic-controls-in-office-documents.md)

### <a name="to-remove-controls-from-the-worksheet"></a>Per rimuovere i controlli dal foglio di lavoro

1. In **Esplora soluzioni** selezionare *ThisAddIn.cs* o *ThisAddIn.vb*.

2. Scegliere **Codice** dal menu **Visualizza**.

3. Aggiungi alla classe `ThisAddIn` il metodo seguente. In questo codice si ottiene il primo foglio di lavoro della cartella di lavoro e viene usato il metodo `HasVstoObject` per controllare se il foglio di lavoro dispone di un oggetto foglio di lavoro generato. Se l'oggetto foglio di lavoro generato dispone di controlli, il codice ottiene tale oggetto ed esegue l'iterazione della raccolta di controlli rimuovendo questi ultimi.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet6":::

4. In C# è necessario creare un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>. Questo codice può essere inserito nel metodo `ThisAddIn_Startup`. Per altre informazioni sulla creazione di gestori eventi, vedere [Procedura: Creare gestori](../vsto/how-to-create-event-handlers-in-office-projects.md)eventi in Office progetti . Sostituire il metodo `ThisAddIn_Startup` con il codice seguente.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet5":::

## <a name="test-the-solution"></a>Testare la soluzione
 Aggiungere controlli a un foglio di lavoro selezionandoli da una scheda personalizzata sulla barra multifunzione. Quando si salva il foglio di lavoro, questi controlli vengono rimossi.

### <a name="to-test-the-solution"></a>Per testare la soluzione.

1. Premere **F5** per eseguire il progetto.

2. Selezionare una qualsiasi cella di Sheet1.

3. Fare clic sulla scheda **Componenti aggiuntivi** .

4. Nel gruppo **group1** fare clic su **Pulsante**.

     Nella cella selezionata viene visualizzato un pulsante.

5. Selezionare una cella diversa di Sheet1.

6. Nel gruppo **group1** fare clic su **NamedRange**.

     Per la cella selezionata viene definito un intervallo denominato.

7. Selezionare una serie di celle di Sheet1.

8. Nel gruppo **group1** fare clic su **ListObject**.

     Per le celle selezionate viene aggiunto un oggetto elenco.

9. Salvare il foglio di lavoro.

     I controlli aggiunti a Sheet1 non vengono più visualizzati.

## <a name="next-steps"></a>Passaggi successivi
 In questo argomento vengono fornite altre informazioni sui controlli nei progetti di componenti aggiuntivi VSTO per Excel:

- Per informazioni su come salvare i controlli in un foglio di lavoro, vedere l'esempio di controlli dinamici del componente aggiuntivo Excel VSTO in esempi e procedure dettagliate Office [sviluppo.](../vsto/office-development-samples-and-walkthroughs.md)

## <a name="see-also"></a>Vedi anche
- [Excel soluzioni](../vsto/excel-solutions.md)
- [Windows di controlli form in Office documenti](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Controlli su Office documenti](../vsto/controls-on-office-documents.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Controllo ListObject](../vsto/listobject-control.md)
