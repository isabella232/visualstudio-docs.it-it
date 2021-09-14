---
title: 'Procedura dettagliata: Aggiornare un grafico in un documento usando i pulsanti di opzione'
description: Informazioni su come usare i pulsanti di opzione in una personalizzazione a livello di documento Microsoft Word per consentire agli utenti di selezionare gli stili del grafico nel documento.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d95ab38581945c61000b3cfcca26ed1ba3fd2c5d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710037"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>Procedura dettagliata: Aggiornare un grafico in un documento usando i pulsanti di opzione
  Questa procedura dettagliata illustra come usare i pulsanti di opzione in una personalizzazione a livello di documento per Microsoft Office Word, per consentire agli utenti di selezionare stili del grafico nel documento.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Aggiunta di un grafico al documento di un progetto a livello di documento in fase di progettazione.

- Raggruppamento dei pulsanti di opzione aggiungendoli a un controllo utente.

- Modifica dello stile del grafico quando si seleziona un'opzione.

  Per visualizzare il risultato come esempio completato, vedere l'esempio di controlli Word Office esempi di [sviluppo e procedure dettagliate](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nel creare un progetto Documento di Word.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto Documento di Word con il nome **My Chart Options**. Nella procedura guidata selezionare **Crea un nuovo documento**. Per altre informazioni, vedere [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **progetto My Chart Options** a **Esplora soluzioni**.

## <a name="add-a-chart-to-the-document"></a>Aggiungere un grafico al documento

### <a name="to-add-a-chart"></a>Per aggiungere un grafico

1. Nel documento di Word ospitato nella finestra di progettazione Visual Studio, fare clic sulla scheda Inserisci sulla barra **multifunzione.**

2. Nel gruppo **Testo** fare clic sul **pulsante a** discesa Inserisci oggetto e quindi su **Oggetto**.

     Verrà **visualizzata la finestra** di dialogo Oggetto .

3. **Nell'elenco Tipo di** oggetto della scheda **Crea** nuovo selezionare Microsoft **Graph Chart** e quindi fare clic su **OK.**

     Un grafico viene aggiunto al documento nel punto di inserimento e la **finestra Foglio** dati viene visualizzata con alcuni dati predefiniti.

4. Chiudere la **finestra Foglio dati** per accettare i valori predefiniti nel grafico e fare clic all'interno del documento per spostare lo stato attivo dal grafico.

5. Fare clic con il pulsante destro del mouse sul grafico e **quindi scegliere Formato oggetto**.

6. Nella scheda **Layout** della finestra di **dialogo Formato oggetto** selezionare **Quadrato** e fare clic su **OK.**

## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto
 I pulsanti di opzione in un documento non si escludono a vicenda per impostazione predefinita. È possibile farli funzionare correttamente aggiungendoli a un controllo utente e quindi scrivendo il codice per controllare la selezione.

### <a name="to-add-a-user-control"></a>Per aggiungere un controllo utente

1. Selezionare il **progetto My Chart Options** in **Esplora soluzioni**.

2. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra **di dialogo Aggiungi nuovo elemento** fare clic su Controllo **utente**, assegnare al controllo il nome **ChartOptions e** fare clic su **Aggiungi**.

### <a name="to-add-windows-form-controls-to-the-user-control"></a>Per aggiungere controlli Windows Form al controllo utente

1. Se il controllo utente non è visibile nella finestra di progettazione, fare doppio clic **su ChartOptions** in **Esplora soluzioni**.

2. Dalla scheda **Controlli comuni** della Casella **degli** strumenti trascinare il primo controllo **Pulsante** di opzione nel controllo utente e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**columnChart**|
    |**Text**|**Istogramma**|

3. Aggiungere un secondo **pulsante di opzione** al controllo utente e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**barChart**|
    |**Text**|**Grafico a barre**|

4. Aggiungere un terzo **pulsante di opzione** al controllo utente e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**lineChart**|
    |**Text**|**Grafico a linee**|

5. Aggiungere un quarto **pulsante di opzione** al controllo utente e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**areaBlockChart**|
    |**Text**|**Grafico ad area**|

## <a name="add-references"></a>Aggiungere riferimenti
 Per accedere al grafico dal controllo utente in un documento, è necessario avere un riferimento `Microsoft.Office.Interop.Graph` all'assembly nel progetto.

### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Per aggiungere un riferimento all'assembly Microsoft.Office.Interop.Graph

1. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

     Verrà visualizzata la finestra di dialogo **Aggiungi riferimento**.

2. Nella scheda **.NET** selezionare **Microsoft.Office. Interoperabilità. Graph** e fare clic **su OK.** Selezionare la versione 14.0.0.0 dell'assembly.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Modificare lo stile del grafico quando viene selezionato un pulsante di opzione
 Per far funzionare i pulsanti correttamente, creare un evento pubblico nel controllo utente, aggiungere una proprietà per impostare il tipo di selezione e creare una routine per l'evento `CheckedChanged` di ogni pulsante di opzione.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Per creare un evento e una proprietà in un controllo utente

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul controllo utente e quindi scegliere **Visualizza codice**.

2. Aggiungere il codice per creare un evento `SelectionChanged` e la proprietà `Selection` nella classe `ChartOptions`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet9":::

### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Per gestire l'evento CheckedChange dei pulsanti di opzione

1. Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `areaBlockChart` e quindi generare l'evento.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet10":::

2. Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `barChart`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet11":::

3. Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `columnChart`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet12":::

4. Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `lineChart`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet13":::

5. In C# è necessario aggiungere gestori eventi per i pulsanti di opzione. È possibile aggiungere questo codice al costruttore `ChartOptions` dopo la chiamata a `InitializeComponent`. Per informazioni sulla creazione di gestori eventi, vedere [Procedura: Creare gestori eventi in Office Projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet14":::

## <a name="add-the-user-control-to-the-document"></a>Aggiungere il controllo Utente al documento
 Quando si compila la soluzione, il nuovo controllo utente viene aggiunto automaticamente alla casella **degli strumenti**. È quindi possibile trascinare il controllo dalla **Casella degli** strumenti al documento.

### <a name="to-add-the-user-control-your-document"></a>Per aggiungere il controllo utente al documento

1. Nel menu **Compila** scegliere **Compila soluzione**.

     Il **controllo utente ChartOptions** viene aggiunto alla casella **degli strumenti**.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **ThisDocument.vb** o **ThisDocument.cs** e **quindi scegliere Progettazione visualizzazioni**.

3. Trascinare `ChartOptions` il controllo dalla Casella degli **strumenti** al documento.

     Nella finestra **Proprietà** assegnare al controllo il nome appena aggiunto al  `ChartOptions1` documento.

## <a name="change-the-chart-type"></a>Modificare il tipo di grafico
 Creare un gestore eventi per modificare il tipo di grafico in base all'opzione selezionata nel controllo utente.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Per modificare il tipo di grafico visualizzato nel documento

1. Aggiungi alla classe `ThisDocument` il gestore eventi indicato di seguito.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet15":::

2. In C# è necessario aggiungere un gestore eventi per il controllo utente all'evento <xref:Microsoft.Office.Tools.Word.Document.Startup>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet16":::

## <a name="test-the-application"></a>Testare l'applicazione
 A questo punto è possibile testare il documento per accertarsi che lo stile del grafico sia aggiornato correttamente quando si seleziona un pulsante di opzione.

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Selezionare vari pulsanti di opzione.

3. Verificare che lo stile del grafico sia modificato in base alla selezione.

## <a name="next-steps"></a>Passaggi successivi
 Ecco alcune possibili attività successive:

- Usare un pulsante per popolare una casella di testo. Per altre informazioni, vedere [Procedura dettagliata: Visualizzare il testo in una casella di testo in un documento usando un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Modificare la formattazione selezionando uno stile da una casella combinata. Per altre informazioni, vedere [Procedura dettagliata: Modificare la formattazione dei documenti usando i controlli CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Vedi anche
- [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)
- [Office di sviluppo e procedure dettagliate](../vsto/office-development-samples-and-walkthroughs.md)
- [Limitazioni dei controlli Windows Form nei Office documenti](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
