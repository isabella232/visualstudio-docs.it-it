---
title: Visualizzare riquadri attività personalizzati con messaggi di posta elettronica in Outlook
description: Informazioni su come visualizzare un'istanza univoca di un riquadro attività personalizzato con ogni messaggio di posta elettronica in Microsoft Outlook creato o aperto.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], displaying with e-mail messages
- displaying custom task panes in e-mail
- e-mail [Office development in Visual Studio], custom task panes displayed in
- custom task panes [Office development in Visual Studio], displaying with e-mail messages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9fb3d933bd661a4a00a3998d9199b3cd469f7dbc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075593"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>Procedura dettagliata: Visualizzare riquadri attività personalizzati con messaggi di posta elettronica in Outlook
  Questa procedura dettagliata illustra come visualizzare un'istanza univoca di un riquadro attività personalizzato con ogni messaggio di posta elettronica creato o aperto. Gli utenti possono visualizzare o nascondere il riquadro attività personalizzato usando un pulsante nella barra multifunzione di ogni messaggio di posta elettronica.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Per visualizzare un riquadro attività personalizzato con più finestre di esplorazione o di controllo, è necessario creare un'istanza del riquadro attività personalizzato per ogni finestra aperta. Per altre informazioni sul comportamento dei riquadri attività personalizzati in Outlook, vedere [Riquadri attività personalizzati.](../vsto/custom-task-panes.md)

> [!NOTE]
> Questa procedura dettagliata presenta il codice del componente aggiuntivo VSTO in sezioni di piccole dimensioni per semplificare la descrizione della logica su cui si basa il codice.

 Vengono illustrate le attività seguenti:

- Progettazione dell'interfaccia utente del riquadro attività personalizzato.

- Creazione di un'interfaccia utente della barra multifunzione personalizzata.

- Visualizzazione dell'interfaccia utente personalizzata della barra multifunzione con messaggi di posta elettronica.

- Creazione di una classe per la gestione delle finestre di controllo e dei riquadri attività personalizzati.

- Inizializzazione e pulizia delle risorse usate dal componente aggiuntivo VSTO.

- Sincronizzazione dell'interruttore della barra multifunzione con il riquadro attività personalizzato.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] o Microsoft Outlook 2010.

## <a name="create-the-project"></a>Creare il progetto
 I riquadri attività personalizzati vengono implementati VSTO componenti aggiuntivi. Per iniziare, creare VSTO progetto di componente aggiuntivo per Outlook.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di **componente aggiuntivo di Outlook** denominato **OutlookMailItemTaskPane**. Usare il modello di progetto per il **componente aggiuntivo di Outlook** . Per altre informazioni, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il file di codice *ThisAddIn.cs* o *ThisAddIn.vb* e aggiunge il progetto **OutlookMailItemTaskPane** a **Esplora soluzioni**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Progettare l'interfaccia utente del riquadro attività personalizzato
 Non sono presenti finestre di visualizzazione visiva per i riquadri attività personalizzati, ma è possibile progettare un controllo utente con l'interfaccia utente desiderata. Il riquadro attività personalizzato in questo componente aggiuntivo VSTO ha un'interfaccia utente semplice che contiene un controllo <xref:System.Windows.Forms.TextBox> . Più avanti in questa procedura dettagliata il controllo utente verrà aggiunto al riquadro attività personalizzato.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Per progettare l'interfaccia utente del riquadro attività personalizzato

1. In **Esplora soluzioni** fare clic sul progetto **OutlookMailItemTaskPane** .

2. Nel menu **Progetto** fare clic su **Aggiungi controllo utente**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento** modificare il nome del controllo utente in **TaskPaneControl**, quindi fare clic su **Aggiungi**.

     Il controllo utente viene visualizzato nella finestra di progettazione.

4. Nella scheda **Controlli comuni** della **casella degli strumenti** trascinare un controllo **TextBox** nel controllo utente.

## <a name="design-the-user-interface-of-the-ribbon"></a>Progettare l'interfaccia utente della barra multifunzione
 Uno degli obiettivi di questo VSTO aggiuntivo è offrire agli utenti un modo per nascondere o visualizzare il riquadro attività personalizzato dalla barra multifunzione di ogni messaggio di posta elettronica. Per fornire l'interfaccia utente, creare un'interfaccia utente della barra multifunzione personalizzata che visualizza un interruttore che gli utenti possono selezionare per visualizzare o nascondere il riquadro attività personalizzato.

### <a name="to-create-a-custom-ribbon-ui"></a>Per creare un'interfaccia utente della barra multifunzione personalizzata

1. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione (finestra di progettazione visiva)**.

3. Modificare il nome della nuova barra multifunzione in **ManageTaskPaneRibbon** e fare clic su **Aggiungi**.

     Il file *ManageTaskPaneRibbon.cs* o *ManageTaskPaneRibbon.vb* si apre nella finestra di progettazione della barra multifunzione e visualizza una scheda e un gruppo predefiniti.

4. Nella finestra di progettazione della barra multifunzione fare clic su **group1**.

5. Nella finestra **Proprietà** impostare la proprietà **Label** su **Task Pane Manager**.

6. Nella scheda **Controlli barra multifunzione di Office** della **casella degli strumenti** trascinare un controllo ToggleButton nel gruppo **Task Pane Manager** .

7. Fare clic su **toggleButton1**.

8. Nella finestra **Proprietà** impostare la proprietà **Label** su **Mostra riquadro attività**.

## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>Visualizzare l'interfaccia utente personalizzata della barra multifunzione con messaggi di posta elettronica
 Il riquadro attività personalizzato creato in questa procedura dettagliata è progettato per essere visualizzato solo nelle finestre di controllo che contengono i messaggi di posta elettronica. Quindi, impostare le proprietà per visualizzare l'interfaccia utente della barra multifunzione personalizzata solo con queste finestre.

### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>Per visualizzare l'interfaccia utente personalizzata della barra multifunzione con messaggi di posta elettronica

1. Nella finestra di progettazione della barra multifunzione fare clic sulla barra multifunzione **ManageTaskPaneRibbon** .

2. Nella finestra **Proprietà** fare clic su sull'elenco a discesa accanto a **RibbonType**, quindi selezionare **Microsoft.Outlook.Mail.Compose** e **Microsoft.Outlook.Mail.Read**.

## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Creare una classe per gestire le finestre di controllo e i riquadri attività personalizzati
 Esistono diversi casi in cui il VSTO deve identificare il riquadro attività personalizzato associato a un messaggio di posta elettronica specifico. ad esempio:

- Quando l'utente chiude un messaggio di posta elettronica. In questo caso, il componente aggiuntivo VSTO deve rimuovere il riquadro attività personalizzato corrispondente per assicurare che le risorse usate dal componente aggiuntivo VSTO vengano pulite correttamente.

- Quando l'utente chiude il riquadro attività personalizzato. In questo caso, il VSTO componente aggiuntivo deve aggiornare lo stato dell'interruttore sulla barra multifunzione del messaggio di posta elettronica.

- Quando l'utente fa clic sull'interruttore sulla barra multifunzione. In questo caso, il componente aggiuntivo VSTO deve nascondere o visualizzare il riquadro attività corrispondente.

  Per consentire al VSTO di tenere traccia del riquadro attività personalizzato associato a ogni messaggio di posta elettronica aperto, creare una classe personalizzata che esegue il wrapping di coppie <xref:Microsoft.Office.Interop.Outlook.Inspector> di <xref:Microsoft.Office.Tools.CustomTaskPane> oggetti e . Questa classe crea un nuovo oggetto riquadro attività personalizzato per ogni messaggio di posta elettronica ed elimina il riquadro attività personalizzato quando il messaggio di posta elettronica corrispondente viene chiuso.

### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Per creare una classe per gestire le finestre di controllo e i riquadri attività personalizzati

1. In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul file *ThisAddIn.cs* o *ThisAddIn.vb* , quindi fare clic su **Visualizza codice**.

2. Aggiungere le seguenti istruzioni nella parte iniziale del file.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet2":::

3. Aggiungere il codice seguente al file *ThisAddIn.cs* o *ThisAddIn.vb* , al di fuori della classe `ThisAddIn` (per Visual C#, aggiungere questo codice all'interno dello spazio dei nomi `OutlookMailItemTaskPane` ). La classe `InspectorWrapper` gestisce una coppia di oggetti <xref:Microsoft.Office.Interop.Outlook.Inspector> e <xref:Microsoft.Office.Tools.CustomTaskPane> . La definizione della classe verrà completata nei passaggi successivi.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet3":::

4. Aggiungere il costruttore seguente dopo il codice aggiunto nel passaggio precedente. Il costruttore crea e inizializza un nuovo riquadro attività personalizzato associato all'oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> passato. In C# il costruttore collega anche i gestori eventi all'evento <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> e all'evento <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> dell'oggetto <xref:Microsoft.Office.Tools.CustomTaskPane> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet4":::

5. Aggiungere il metodo seguente dopo il codice aggiunto nel passaggio precedente. Questo metodo è un gestore eventi per l'evento <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> dell'oggetto <xref:Microsoft.Office.Tools.CustomTaskPane> contenuto nella classe `InspectorWrapper` . Questo codice aggiorna lo stato dell'interruttore quando l'utente apre o chiude il riquadro attività personalizzato.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet5":::

6. Aggiungere il metodo seguente dopo il codice aggiunto nel passaggio precedente. Questo metodo è un gestore eventi per <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> l'evento <xref:Microsoft.Office.Interop.Outlook.Inspector> dell'oggetto che contiene il messaggio di posta elettronica corrente. Il gestore eventi libera le risorse quando il messaggio di posta elettronica viene chiuso. Il gestore eventi rimuove anche il riquadro attività personalizzato corrente dalla raccolta `CustomTaskPanes` . In questo modo è possibile evitare più istanze del riquadro attività personalizzato quando viene aperto il messaggio di posta elettronica successivo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet6":::

7. Aggiungere il codice seguente dopo il codice aggiunto nel passaggio precedente. Più avanti in questa procedura dettagliata, questa proprietà verrà chiamata da un metodo nell'interfaccia utente della barra multifunzione personalizzata per visualizzare o nascondere il riquadro attività personalizzato.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet7":::

## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Inizializzare e pulire le risorse usate dal componente aggiuntivo
 Aggiungere il codice alla classe `ThisAddIn` per inizializzare il componente aggiuntivo VSTO quando viene caricato e per pulire le risorse usate dal componente aggiuntivo VSTO quando viene scaricato. È possibile inizializzare VSTO componente aggiuntivo impostando un gestore eventi per l'evento e passando tutti i messaggi di posta <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> elettronica esistenti a questo gestore eventi. Quando il componente aggiuntivo VSTO viene scaricato, rimuovere il gestore eventi e pulire gli oggetti usati dal componente aggiuntivo VSTO.

### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>Per inizializzare e pulire le risorse usate dal componente aggiuntivo VSTO

1. Nel file *ThisAddIn.cs* o *ThisAddIn.vb* individuare la definizione della classe `ThisAddIn` .

2. Aggiungere le seguenti dichiarazioni alla classe `ThisAddIn` :

   - Il campo `inspectorWrappersValue` contiene tutti gli oggetti <xref:Microsoft.Office.Interop.Outlook.Inspector> e `InspectorWrapper` gestiti dal componente aggiuntivo VSTO.

   - Il campo `inspectors` gestisce un riferimento alla raccolta di finestre di controllo nell'istanza Outlook corrente. Questo riferimento impedisce al Garbage Collector di liberare la memoria che contiene il gestore eventi per l'evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> , che verrà dichiarato nel passaggio successivo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet8":::

3. Sostituire il metodo `ThisAddIn_Startup` con il codice seguente. Questo codice collega un gestore eventi all'evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> e passa tutti gli oggetti <xref:Microsoft.Office.Interop.Outlook.Inspector> esistenti al gestore eventi. Se l'utente carica il componente aggiuntivo VSTO dopo che Outlook è già in esecuzione, il componente aggiuntivo VSTO usa queste informazioni per creare riquadri attività personalizzati per tutti i messaggi di posta elettronica già aperti.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet9":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet9":::

4. Sostituire il metodo `ThisAddIn_ShutDown` con il codice seguente. Questo codice rimuove il gestore eventi <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> e pulisce gli oggetti usati dal componente aggiuntivo VSTO.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet10":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet10":::

5. Aggiungere il gestore eventi <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> seguente alla classe `ThisAddIn` . Se un nuovo contiene un messaggio di posta elettronica, il metodo crea un'istanza di un nuovo oggetto per gestire la relazione tra il messaggio di posta elettronica e <xref:Microsoft.Office.Interop.Outlook.Inspector> `InspectorWrapper` il riquadro attività corrispondente.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet11":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet11":::

6. Aggiungere la proprietà seguente alla classe `ThisAddIn` . Questa proprietà espone il campo `inspectorWrappersValue` privato al codice esterno alla classe `ThisAddIn` .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet12":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet12":::

## <a name="checkpoint"></a>Checkpoint
 Compilare il progetto per verificare l'assenza di errori.

### <a name="to-build-your-project"></a>Per compilare il progetto

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **OutlookMailItemTaskPane** , quindi fare clic su **Compila**. Verificare che il progetto venga compilato senza errori.

## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Sincronizzare l'interruttore della barra multifunzione con il riquadro attività personalizzato
 L'interruttore risulterà premuto quando il riquadro attività è visibile e non premuto quando il riquadro attività è nascosto. Per sincronizzare lo stato dell'interruttore con il riquadro attività personalizzato, modificare il gestore eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> dell'interruttore.

### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Per sincronizzare il riquadro attività personalizzato con l'interruttore

1. Nella finestra di progettazione della barra multifunzione fare doppio clic sull'interruttore **Mostra riquadro attività** .

     Visual Studio genera automaticamente un gestore eventi denominato `toggleButton1_Click`, che gestisce l'evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> dell'interruttore. Visual Studio apre anche il file *ManageTaskPaneRibbon.cs* o *ManageTaskPaneRibbon.vb* nell'editor di codice.

2. Aggiungere le istruzioni seguenti nella parte superiore del file *ManageTaskPaneRibbon.cs* o *ManageTaskPaneRibbon.vb* .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb" id="Snippet14":::

3. Sostituire il gestore eventi `toggleButton1_Click` con il codice seguente. Quando un utente fa clic sull'interruttore, questo metodo nasconde o visualizza il riquadro attività personalizzato associato alla finestra di controllo corrente.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb" id="Snippet15":::

## <a name="test-the-project"></a>Testare il progetto
 Quando si avvia il debug del progetto, viene aperto Outlook e viene caricato il componente aggiuntivo VSTO. Il VSTO componente aggiuntivo visualizza un'istanza univoca del riquadro attività personalizzato con ogni messaggio di posta elettronica aperto. Creare diversi nuovi messaggi di posta elettronica per testare il codice.

### <a name="to-test-the-vsto-add-in"></a>Per testare il componente aggiuntivo VSTO

1. Premere **F5**.

2. In Outlook fare clic su **Nuovo** per creare un nuovo messaggio di posta elettronica.

3. Sulla barra multifunzione del messaggio di posta elettronica fare **clic** sulla scheda Componenti aggiuntivi e quindi sul pulsante Mostra **riquadro** attività.

    Verificare che sia visualizzato un riquadro attività con il titolo **Riquadro attività** My con il messaggio di posta elettronica.

4. Nella casella di testo del riquadro attività digitare **First task pane** .

5. Chiudere il riquadro attività.

    Verificare che lo stato del pulsante **Mostra riquadro attività** sia cambiato in modo che non venga più premuto.

6. Fare di nuovo clic sul pulsante **Mostra riquadro attività** .

    Verificare che il riquadro attività si apra e che la casella di testo contenga ancora la stringa **First task pane**.

7. In Outlook fare clic su **Nuovo per** creare un secondo messaggio di posta elettronica.

8. Sulla barra multifunzione del messaggio di posta elettronica fare **clic** sulla scheda Componenti aggiuntivi e quindi sul pulsante Mostra **riquadro** attività.

    Verificare che un riquadro attività con il titolo **Riquadro** attività My sia visualizzato con il messaggio di posta elettronica e che la casella di testo in questo riquadro attività sia vuota.

9. Nella casella di testo del riquadro attività digitare **Second task pane** .

10. Passare lo stato attivo al primo messaggio di posta elettronica.

     Verificare che il riquadro attività associato a questo messaggio di posta elettronica visualizzi ancora Primo riquadro **attività** nella casella di testo.

    Il componente aggiuntivo VSTO gestisce anche scenari più avanzati che è possibile provare. Ad esempio, è possibile testare il comportamento quando si visualizzano messaggi di posta elettronica usando i **pulsanti Elemento successivo** e **Elemento** precedente. È anche possibile testare il comportamento quando si scarica il componente aggiuntivo VSTO, si aprono diversi messaggi di posta elettronica e quindi si ricarica il VSTO componente aggiuntivo.

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni su come creare i riquadri attività personalizzati, vedere gli argomenti seguenti:

- Creare un riquadro attività personalizzato in un VSTO componente aggiuntivo per un'applicazione diversa. Per altre informazioni sulle applicazioni che supportano i riquadri attività personalizzati, vedere [Riquadri attività personalizzati](../vsto/custom-task-panes.md).

- Automatizzare un'applicazione di Microsoft Office usando un riquadro attività personalizzato. Per altre informazioni, vedere [Procedura dettagliata: Automatizzare un'applicazione da un riquadro attività personalizzato.](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)

- Creare un pulsante della barra multifunzione in Excel da usare per visualizzare o nascondere un riquadro attività personalizzato. Per altre informazioni, vedere [Procedura dettagliata: Sincronizzare un riquadro attività personalizzato con un pulsante della barra multifunzione.](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)

## <a name="see-also"></a>Vedi anche
- [Riquadri attività personalizzati](../vsto/custom-task-panes.md)
- [Procedura: Aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Procedura dettagliata: Automatizzare un'applicazione da un riquadro attività personalizzato](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Procedura dettagliata: Sincronizzare un riquadro attività personalizzato con un pulsante della barra multifunzione](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Outlook panoramica del modello a oggetti](../vsto/outlook-object-model-overview.md)
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
