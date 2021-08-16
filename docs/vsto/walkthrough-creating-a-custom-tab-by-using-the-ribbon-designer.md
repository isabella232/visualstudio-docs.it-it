---
title: 'Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione'
description: Informazioni su come creare una scheda personalizzata e quindi aggiungere e posizionare i controlli su di essa usando la finestra di progettazione della barra multifunzione.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b4099365a1c5709c6b4c74af3eb6eec0a5eb72b2d367527ce9168ce9cc1f51bd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121267364"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione
  Usando la finestra di progettazione della barra multifunzione è possibile creare una scheda personalizzata per aggiungervi e posizionarvi controlli.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- [Creare riquadri azioni](#BKMK_CreateActionsPanes).

- [Creare una scheda personalizzata](#BKMK_CreateCustomTab).

- [Nascondere e visualizzare i riquadri azioni usando i pulsanti nella scheda personalizzata](#BKMK_HideShowActionsPane).

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-an-excel-workbook-project"></a>Creare un progetto Excel cartella di lavoro
 I passaggi per l'utilizzo della finestra di progettazione della barra multifunzione sono quasi identici per tutte le applicazioni Office. In questo esempio viene usata una cartella di lavoro di Excel.

### <a name="to-create-an-excel-workbook-project"></a>Per creare un progetto cartella di lavoro di Excel

- Creare un progetto Excel cartella di lavoro con il nome **MyExcelRibbon**. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre la nuova cartella di lavoro nella finestra di progettazione e aggiunge il **progetto MyExcelRibbon** **a Esplora soluzioni**.

## <a name="create-actions-panes"></a><a name="BKMK_CreateActionsPanes"></a> Creare riquadri azioni
 Aggiungere due riquadri azioni personalizzati al progetto. Successivamente si aggiungeranno alcuni pulsanti che mostrano e nascondono questi riquadri azioni alla scheda personalizzata.

### <a name="to-create-actions-panes"></a>Per creare i riquadri azioni

1. Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

2. Nella finestra **di dialogo Aggiungi** nuovo elemento selezionare **ActionsPaneControl** e quindi scegliere **Aggiungi.**

     Il file **ActionsPaneControl1.cs** **o ActionsPaneControl1.vb** viene aperto nella finestra di progettazione.

3. Dalla scheda **Controlli comuni della** casella degli **strumenti** aggiungere un'etichetta all'area di progettazione.

4. Nella finestra **Proprietà** impostare la **proprietà Text** di label1 su Actions **Pane 1.**

5. Ripetere i passaggi da 1 a 5 per creare un secondo riquadro azioni e una seconda etichetta. Impostare la **proprietà Text** della seconda etichetta su Actions **Pane 2**.

## <a name="create-a-custom-tab"></a><a name="BKMK_CreateCustomTab"></a> Creare una scheda personalizzata
 Per la progettazione di applicazioni di Office, è necessario che gli utenti abbiano sempre il controllo dell'interfaccia utente dell'applicazione di Office. Per aggiungere questa funzionalità relativa ai riquadri azioni, è possibile aggiungere pulsanti che mostrano e nascondono ciascun riquadro azioni da una scheda personalizzata della barra multifunzione. Per creare una scheda personalizzata, aggiungere un **elemento Barra multifunzione (finestra di** progettazione visiva) al progetto. La finestra di progettazione consente di aggiungere e posizionare controlli, impostarne le proprietà e gestirne gli eventi.

### <a name="to-create-a-custom-tab"></a>Per creare una scheda personalizzata

1. Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione (finestra di progettazione visiva)**.

3. Modificare il nome della nuova barra multifunzione **in MyRibbon** e scegliere **Aggiungi.**

     Nella finestra di progettazione della barra multifunzione viene aperto un file **MyRibbon.cs** o **MyRibbon.vb** , che visualizza una scheda e un gruppo predefiniti.

4. Nella finestra di progettazione della barra multifunzione scegliere la scheda predefinita.

5. Nella finestra **Proprietà** espandere la **proprietà ControlId** e quindi impostare la **proprietà ControlIdType** su **Custom.**

6. Impostare la **proprietà Etichetta** su **Scheda personalizzata.**

7. Nella finestra di progettazione della barra multifunzione scegliere **group1.**

8. Nella finestra **Proprietà** impostare **Etichetta** su Gestione **riquadri azioni.**

9. Dalla scheda **Office della barra multifunzione** della casella degli **strumenti** trascinare un pulsante in **group1.**

10. Selezionare **button1**.

11. Nella finestra **Proprietà** impostare **Etichetta su** Mostra riquadro **azioni 1.**

12. Aggiungere un secondo pulsante **a group1** e impostare la **proprietà Label** su Show Actions **Pane 2**.

13. Dalla scheda **Office della casella** degli strumenti trascinare un controllo **ToggleButton** in **group1.**

14. Impostare la **proprietà Etichetta** su Nascondi **riquadro azioni.**

## <a name="hide-and-show-actions-panes-by-using-buttons-on-the-custom-tab"></a><a name="BKMK_HideShowActionsPane"></a> Nascondere e visualizzare i riquadri azioni usando i pulsanti nella scheda personalizzata
 L'ultimo passaggio consiste nell'aggiungere codice che risponde all'utente. Aggiungere gestori eventi per gli eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> dei due pulsanti e per l'evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> dell'interruttore. Aggiungere codice a questi gestori eventi per abilitare e disabilitare la visualizzazione dei riquadri azioni.

### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Per nascondere e mostrare i riquadri azioni mediante i pulsanti della scheda personalizzata

1. In **Esplora soluzioni** aprire il menu di scelta rapida per *MyRibbon.cs* o *MyRibbon.vb* e quindi scegliere **Visualizza codice.**

2. Aggiungere il codice riportato di seguito all'inizio della classe `MyRibbon`. Mediante questo codice vengono creati due oggetti riquadro azioni.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb" id="Snippet1":::

3. Sostituire il metodo `MyRibbon_Load` con il codice seguente. Mediante questo codice vengono aggiunti alla raccolta <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> oggetti riquadro azioni, che vengono nascosti. Il codice Visual C# associa inoltre delegati a vari eventi del controllo della barra multifunzione.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb" id="Snippet2":::

4. Aggiungere i tre metodi per la gestione eventi riportati di seguito alla classe `MyRibbon`. Questi metodi gestiscono gli eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> dei due pulsanti e l'evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> dell'interruttore. I gestori eventi per button1 e button2 mostrano riquadri azioni alternativi. Il gestore eventi per toggleButton1 mostra e nasconde il riquadro azioni attivo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb" id="Snippet3":::

## <a name="test-the-custom-tab"></a>Testare la scheda personalizzata
 Quando si esegue il progetto, Excel viene avviata la scheda **My Custom Tab (Scheda personalizzata)** sulla barra multifunzione. Scegliere i pulsanti nella **scheda Personalizzata per** visualizzare e nascondere i riquadri azioni.

### <a name="to-test-the-custom-tab"></a>Per verificare la scheda personalizzata

1. Premere **F5** per eseguire il progetto.

2. Scegliere la **scheda My Custom Tab (Scheda** personalizzata).

3. Nel gruppo **Gestione riquadri azioni** personalizzati scegliere **Mostra riquadro azioni 1.**

     Verrà visualizzato il riquadro azioni con **l'etichetta Actions Pane 1**.

4. Scegliere **Mostra riquadro azioni 2.**

     Verrà visualizzato il riquadro azioni con **l'etichetta Actions Pane 2**.

5. Scegliere **Nascondi riquadro azioni.**

     I riquadri azioni non sono più visibili.

## <a name="next-steps"></a>Passaggi successivi
 È possibile trovare ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Office nei seguenti argomenti:

- Aggiunta di un'interfaccia utente basata sul contesto a una personalizzazione a livello di documento. Per altre informazioni, vedere Panoramica [del riquadro Azioni.](../vsto/actions-pane-overview.md)

- Estensione di un modulo standard o personalizzato di Microsoft Office Outlook. Per altre informazioni, vedere [Procedura dettagliata: Progettare un'area Outlook modulo.](../vsto/walkthrough-designing-an-outlook-form-region.md)

## <a name="see-also"></a>Vedi anche
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Procedura: Iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Procedura: Modificare la posizione di una scheda sulla barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)
- [Procedura: Aggiungere controlli alla visualizzazione backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)
