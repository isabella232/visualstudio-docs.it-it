---
title: 'Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3a56f8bdfed38d77a939ab8e8b159510da7fcb15
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438602"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione
  Usando la finestra di progettazione della barra multifunzione è possibile creare una scheda personalizzata per aggiungervi e posizionarvi controlli.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Questa procedura dettagliata illustra le attività seguenti:

- [Creare riquadri azioni](#BKMK_CreateActionsPanes).

- [Creare una scheda personalizzata](#BKMK_CreateCustomTab).

- [Nascondere e mostrare i riquadri azioni mediante i pulsanti della scheda personalizzata](#BKMK_HideShowActionsPane).

> [!NOTE]
> I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-an-excel-workbook-project"></a>Creare un progetto cartella di lavoro di Excel
 I passaggi per l'utilizzo della finestra di progettazione della barra multifunzione sono quasi identici per tutte le applicazioni Office. In questo esempio viene usata una cartella di lavoro di Excel.

### <a name="to-create-an-excel-workbook-project"></a>Per creare un progetto cartella di lavoro di Excel

- Creare un progetto cartella di lavoro di Excel con il nome **MyExcelRibbon**. Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio verrà visualizzata la nuova cartella di lavoro nella finestra di progettazione e aggiunge il **MyExcelRibbon** progetto al **Esplora soluzioni**.

## <a name="BKMK_CreateActionsPanes"></a> Creare riquadri azioni
 Aggiungere due riquadri azioni personalizzati al progetto. Successivamente si aggiungeranno alcuni pulsanti che mostrano e nascondono questi riquadri azioni alla scheda personalizzata.

### <a name="to-create-actions-panes"></a>Per creare i riquadri azioni

1. Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

2. Nel **Aggiungi nuovo elemento** finestra di dialogo **ActionsPaneControl**, quindi scegliere **Add**.

     Il **ActionsPaneControl1.cs** oppure **ActionsPaneControl1.vb** file viene aperto nella finestra di progettazione.

3. Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, aggiungere un'etichetta all'area di progettazione.

4. Nel **delle proprietà** impostare nella finestra di **testo** proprietà di label1 su **Actions Pane 1**.

5. Ripetere i passaggi da 1 a 5 per creare un secondo riquadro azioni e una seconda etichetta. Impostare il **testo** proprietà dell'etichetta secondo **Actions Pane 2**.

## <a name="BKMK_CreateCustomTab"></a> Creare una scheda personalizzata
 Per la progettazione di applicazioni di Office, è necessario che gli utenti abbiano sempre il controllo dell'interfaccia utente dell'applicazione di Office. Per aggiungere questa funzionalità relativa ai riquadri azioni, è possibile aggiungere pulsanti che mostrano e nascondono ciascun riquadro azioni da una scheda personalizzata della barra multifunzione. Per creare una scheda personalizzata, aggiungere un **sulla barra multifunzione (finestra di progettazione visiva)** elemento al progetto. La finestra di progettazione consente di aggiungere e posizionare controlli, impostarne le proprietà e gestirne gli eventi.

### <a name="to-create-a-custom-tab"></a>Per creare una scheda personalizzata

1. Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione (finestra di progettazione visiva)**.

3. Modificare il nome della nuova barra multifunzione **MyRibbon**, quindi scegliere **Add**.

     Nella finestra di progettazione della barra multifunzione viene aperto un file **MyRibbon.cs** o **MyRibbon.vb** , che visualizza una scheda e un gruppo predefiniti.

4. Nella finestra di progettazione della barra multifunzione scegliere la scheda predefinita.

5. Nel **proprietà** finestra, espandere il **ControlId** proprietà e quindi impostare il **ControlIdType** proprietà **Custom**.

6. Impostare il **Label** proprietà **My Custom Tab**.

7. Nella finestra di progettazione della barra multifunzione, scegliere **group1**.

8. Nel **delle proprietà** impostare nella finestra **etichetta** al **Actions Pane Manager**.

9. Dal **controlli della barra multifunzione di Office** scheda della finestra di **della casella degli strumenti**, trascinare un pulsante in **group1**.

10. Selezionare **button1**.

11. Nel **delle proprietà** impostare nella finestra **etichetta** al **Show Actions Pane 1**.

12. Aggiungere un secondo pulsante su **group1**e impostare le **Label** proprietà **Show Actions Pane 2**.

13. Dal **controlli della barra multifunzione di Office** scheda della finestra di **della casella degli strumenti**, trascinare un **ToggleButton** sul controllo **group1**.

14. Impostare il **Label** proprietà **Hide Actions Pane**.

## <a name="BKMK_HideShowActionsPane"></a> Nascondere e mostrare i riquadri azioni mediante i pulsanti della scheda personalizzata
 L'ultimo passaggio consiste nell'aggiungere codice che risponde all'utente. Aggiungere gestori eventi per gli eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> dei due pulsanti e per l'evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> dell'interruttore. Aggiungere codice a questi gestori eventi per abilitare e disabilitare la visualizzazione dei riquadri azioni.

### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Per nascondere e mostrare i riquadri azioni mediante i pulsanti della scheda personalizzata

1. In **Esplora soluzioni**, aprire il menu di scelta rapida *MyRibbon.cs* oppure *MyRibbon. vb*, quindi scegliere **Visualizza codice**.

2. Aggiungere il codice riportato di seguito all'inizio della classe `MyRibbon`. Mediante questo codice vengono creati due oggetti riquadro azioni.

     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]

3. Sostituire il metodo `MyRibbon_Load` con il codice seguente. Mediante questo codice vengono aggiunti alla raccolta <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> oggetti riquadro azioni, che vengono nascosti. Il codice Visual C# associa inoltre delegati a vari eventi del controllo della barra multifunzione.

     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]

4. Aggiungere i tre metodi per la gestione eventi riportati di seguito alla classe `MyRibbon`. Questi metodi gestiscono gli eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> dei due pulsanti e l'evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> dell'interruttore. I gestori eventi per button1 e button2 mostrano riquadri azioni alternativi. Il gestore eventi per toggleButton1 mostra e nasconde il riquadro azioni attivo.

     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]

## <a name="test-the-custom-tab"></a>Verificare la scheda personalizzata
 Quando si esegue il progetto, viene avviato Excel e il **My Custom Tab** verrà visualizzata la scheda della barra multifunzione. Scegliere i pulsanti sulla **My Custom Tab** per mostrare e nascondere i riquadri azioni.

### <a name="to-test-the-custom-tab"></a>Per verificare la scheda personalizzata

1. Premere **F5** per eseguire il progetto.

2. Scegliere il **My Custom Tab** scheda.

3. Nel **Custom Actions Pane Manager** gruppo, scegliere **Show Actions Pane 1**.

     Il riquadro azioni viene visualizzata e viene visualizzata l'etichetta **Actions Pane 1**.

4. Scegli **Show Actions Pane 2**.

     Il riquadro azioni viene visualizzata e viene visualizzata l'etichetta **Actions Pane 2**.

5. Scegli **Hide Actions Pane**.

     I riquadri azioni non sono più visibili.

## <a name="next-steps"></a>Passaggi successivi
 È possibile trovare ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Office nei seguenti argomenti:

- Aggiunta di un'interfaccia utente basata sul contesto a una personalizzazione a livello di documento. Per altre informazioni, vedere [Cenni preliminari sul riquadro azioni](../vsto/actions-pane-overview.md).

- Estensione di un modulo standard o personalizzato di Microsoft Office Outlook. Per altre informazioni, vedere [Procedura dettagliata: Progettare un'area del modulo Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Vedere anche
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Procedura: Introduzione alla personalizzazione della barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Procedura: Modificare la posizione di una scheda della barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)
- [Procedura: Aggiungere controlli alla visualizzazione backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)
