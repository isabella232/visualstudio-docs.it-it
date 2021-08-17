---
title: Finestra di progettazione della barra multifunzione
description: Informazioni su come usare la finestra di progettazione della barra multifunzione per aggiungere schede, gruppi e controlli personalizzati alla barra multifunzione di un'Microsoft Office personalizzata.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5bef09e7b808b4473f15b2d103bac7a55ce1eef8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025771"
---
# <a name="ribbon-designer"></a>Finestra di progettazione della barra multifunzione
  La finestra di progettazione della barra multifunzione è un'area di disegno di progettazione visiva. Usare la finestra di progettazione della barra multifunzione per aggiungere schede, gruppi e controlli personalizzati alla barra multifunzione di un Microsoft Office app Microsoft Office personalizzata.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Per aprire la finestra di progettazione della barra multifunzione, aggiungere **un elemento Barra multifunzione (finestra di** progettazione visiva) al progetto. È quindi possibile usare gli strumenti di progettazione per le attività seguenti:

- [Progettare il layout della barra multifunzione](#DesigningRibbonLayout)

- [Gestire gli eventi e impostare le proprietà del controllo](#HandleEventsSetProperties)

- [Aggiungere controlli alla visualizzazione Backstage](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
> Esistono alcune attività che non è possibile eseguire usando la finestra di progettazione della barra multifunzione. Per altre informazioni su queste attività e su come è possibile eseguire queste attività, vedere Panoramica [della barra multifunzione.](../vsto/ribbon-overview.md)

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Aggiungere un elemento barra multifunzione (finestra di progettazione visiva) a un progetto
 Per usare la finestra di progettazione della barra multifunzione, aggiungere **un nuovo elemento Barra multifunzione (finestra di** progettazione visiva) al progetto. Per altre informazioni, vedere [Procedura: Introduzione alla personalizzazione della barra multifunzione.](../vsto/how-to-get-started-customizing-the-ribbon.md)

 Quando si aggiunge un nuovo **elemento Barra multifunzione (finestra di** progettazione visiva), Visual Studio automaticamente i file seguenti al progetto:

- Un file di codice della barra multifunzione. Questo file ha il nome specificato per l'elemento **Barra multifunzione (finestra di** progettazione visiva) nella finestra **di** dialogo Aggiungi nuovo elemento. Aggiungere codice per gestire gli eventi della barra multifunzione in questo file.

- Un file di codice della finestra di progettazione della barra multifunzione. Questo file contiene il codice generato dalla finestra di progettazione della barra multifunzione e non deve essere modificato direttamente.

- Un file di risorse. Questo file contiene i valori delle proprietà di ogni controllo sulla barra multifunzione.

  Se si dispone già di un elemento della barra **multifunzione (finestra** di progettazione visiva) da un altro progetto, è possibile riutilizzarlo nel progetto corrente usando la finestra di dialogo **Aggiungi** elemento esistente.

## <a name="design-a-ribbon"></a><a name="DesigningRibbonLayout"></a> Progettare una barra multifunzione
 È possibile aprire la finestra di progettazione della barra multifunzione in tre modi:

- In **Esplora soluzioni** fare doppio clic sul file di codice della barra multifunzione.

- In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file di codice della barra multifunzione e **quindi scegliere Progettazione visualizzazioni**.

- In **Esplora soluzioni** selezionare il file di codice della barra multifunzione e quindi scegliere **Progettazione** **dal** menu Visualizza.

  La finestra di progettazione della barra multifunzione contiene una scheda e un gruppo predefiniti. È possibile rimuovere la scheda e il gruppo predefiniti dalla finestra di progettazione della barra multifunzione. Per rimuovere il gruppo predefinito, fare clic con il pulsante destro **del mouse su Group1** e quindi scegliere **Elimina.** Per rimuovere la scheda predefinita, fare clic con il pulsante destro del mouse su un'area vuota dell'area di progettazione e quindi scegliere **Rimuovi scheda della barra multifunzione.**

  È anche possibile aggiungere schede, gruppi e controlli personalizzati alla finestra di progettazione della barra multifunzione. È possibile trovare questi controlli nella casella degli **strumenti**, nel gruppo Office **della barra** multifunzione. Esistono tre modi per aggiungere controlli dal gruppo Office **barra** multifunzione alla finestra di progettazione della barra multifunzione:

- Trascinare un controllo in un'area appropriata nella finestra di progettazione della barra multifunzione.

- Fare clic su un controllo e quindi su un'area appropriata nella finestra di progettazione della barra multifunzione.

- Selezionare un'area appropriata nella finestra di progettazione, quindi fare doppio clic su un controllo nella Casella degli **strumenti**.

### <a name="ribbon-design-workflow"></a>Flusso di lavoro di progettazione della barra multifunzione
 Per progettare il layout della barra multifunzione, seguire questa procedura di base:

1. [Aggiungere una scheda personalizzata alla barra multifunzione.](#AddTabToRibbon)

2. [Aggiungere gruppi alla scheda](#AddGroupsToTab).

3. [Aggiungere controlli ai gruppi](#AddControlsToGroups).

   I controlli possono essere rilasciati solo nei gruppi. Non è possibile trascinare un controllo direttamente in una scheda o nella barra multifunzione. I gruppi possono essere eliminati solo nelle schede. Non è possibile trascinare un gruppo direttamente su una barra multifunzione.

   Disporre i controlli trascinandoli nelle posizioni corrette. È possibile impostare le proprietà di un controllo usando la **finestra** Proprietà.

   Non è possibile trascinare i controlli da una scheda a un'altra sulla barra multifunzione. Se si vuole spostare un controllo in un'altra scheda, è necessario usare il comando Taglia per rimuovere il controllo da una scheda e quindi incollarlo in un'altra scheda.  Se si taglia il controllo e lo si incolla, il gestore eventi smette di funzionare. È possibile riconnettere il gestore eventi nella **finestra** Proprietà. Per altre informazioni, vedere [Finestra Proprietà](../ide/reference/properties-window.md).

### <a name="add-custom-tabs-to-the-ribbon"></a><a name="AddTabToRibbon"></a> Aggiungere schede personalizzate alla barra multifunzione
 È possibile aggiungere una scheda personalizzata alla barra multifunzione in tre modi:

- Aggiungere una scheda dalla Casella **degli strumenti**.

- Fare clic con il pulsante destro del mouse sulla finestra di progettazione della barra multifunzione e **quindi scegliere Aggiungi scheda della barra multifunzione.**

- Aprire **l'Editor raccolta schede** e quindi fare clic su **Aggiungi.**

   Per aprire l'Editor **raccolta** schede , nella finestra Proprietà selezionare la proprietà **Schede** e quindi fare clic sul pulsante con i puntini di sospensione ASP.NET ![Mobile Designer](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer"). 

  Dopo aver aggiunto una scheda, è possibile aggiungere gruppi per contenere i controlli.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Rimuovere schede personalizzate dalla barra multifunzione
 Esistono tre modi per rimuovere una scheda personalizzata dalla barra multifunzione:

- Fare clic con il pulsante destro del mouse sulla finestra di progettazione e **quindi scegliere Rimuovi scheda della barra multifunzione.**

- Nel riquadro **Comandi** della **finestra** Proprietà fare clic su Rimuovi scheda della barra **multifunzione.**

- Aprire **l'Editor raccolta schede**, selezionare la scheda e quindi fare clic su **Rimuovi**.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Modificare la posizione di una scheda sulla barra multifunzione
 È possibile modificare l'ordine delle schede personalizzate in una barra multifunzione. È anche possibile posizionare le schede personalizzate prima o dopo una scheda incorporata sulla barra multifunzione. Per altre informazioni, vedere [Procedura: Modificare la posizione di una scheda nella barra multifunzione.](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Personalizzare le schede predefinite sulla barra multifunzione
 Una scheda incorporata è una scheda già presente sulla barra multifunzione di un Microsoft Office app Microsoft Office personalizzata. Ad esempio, **la scheda** Dati è una scheda predefinita in Excel.

 È possibile aggiungere gruppi e controlli a una scheda incorporata. Per impostazione predefinita, un gruppo personalizzato viene visualizzato come ultimo gruppo in una scheda predefinita, anche se è possibile spostarlo prima o dopo qualsiasi gruppo predefinito nella scheda.

 Non è possibile rimuovere gruppi predefiniti.

 Per informazioni dettagliate su come personalizzare una scheda predefinita, vedere [Procedura: Personalizzare una scheda predefinita.](../vsto/how-to-customize-a-built-in-tab.md)

### <a name="add-groups-to-a-tab"></a><a name="AddGroupsToTab"></a> Aggiungere gruppi a una scheda
 I gruppi organizzano logicamente i controlli sulla barra multifunzione. Aggiungere gruppi alle schede. Aggiungere tutti gli altri controlli al gruppo.

### <a name="add-controls-to-groups"></a><a name="AddControlsToGroups"></a> Aggiungere controlli ai gruppi
 Aggiungere uno o più controlli a un gruppo. Nella tabella seguente vengono descritti i singoli controlli.

|Controllo|Descrizione|
|-------------|-----------------|
|**Box**|Contenitore che organizza i controlli in un gruppo. È possibile aggiungere qualsiasi controllo a una casella, ad eccezione di un separatore, un gruppo o una scheda. Una casella può essere orizzontale o verticale.|
|**Button**|Pulsante che avvia un'azione. È possibile aggiungere un pulsante a un gruppo, un gruppo di pulsanti, un elenco a discesa, una raccolta, un menu o un pulsante di menu.|
|**ButtonGroup**|Gruppo che contiene uno o più pulsanti, interruttori, menu, pulsanti divisi e raccolte. È possibile aggiungere un gruppo di pulsanti a un gruppo o a un menu.|
|**CheckBox**|Casella selezionata o deselezionata per attivare o disattivare un'opzione.|
|**ComboBox**|Casella di modifica a cui è associata una casella di riepilogo. Gli utenti possono digitare o selezionare la propria scelta. Nella casella viene visualizzata la selezione corrente. Usare la proprietà per aggiungere e rimuovere elementi in fase di esecuzione prima o dopo il caricamento della barra multifunzione <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> nell'Office applicazione.|
|**Dropdown**|Elenco di elementi selezionabili dall'utente. L'utente non può digitare un nuovo elemento in un elenco a discesa.<br /><br /> Usare la <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> proprietà per aggiungere elementi all'elenco. È possibile aggiungere e rimuovere elementi in fase di esecuzione.<br /><br /> Usare la <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> proprietà per aggiungere pulsanti all'elenco. Tuttavia, non è possibile aggiungere e rimuovere pulsanti in fase di esecuzione dopo il caricamento della barra multifunzione nell Office app.|
|**Editbox**|Casella in cui l'utente può digitare testo.|
|**Raccolta**|Menu che presenta una matrice o una griglia di scelte visive tra cui gli utenti possono selezionare. È possibile controllare il layout delle selezioni nel menu. Usare le proprietà e per specificare il numero di righe e colonne che visualizzano gli <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> elementi e i pulsanti della <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> raccolta.|
|**Etichetta**|Testo che è possibile usare per identificare i controlli sulla barra multifunzione.|
|**Menu**|Elenco a discesa che può contenere uno dei controlli seguenti:<br /><br /> - Pulsante<br />- Casella di controllo<br />- Raccolta<br />- Menu<br />- Pulsante Dividi<br />- Pulsante Di attivazione/disattivazione<br />- Separatore<br /><br /> Per aggiungere un controllo a un menu nella finestra di progettazione della barra multifunzione, fare clic sulla freccia giù nel menu per esporre l'area di progettazione del menu. È quindi possibile trascinare i controlli barra multifunzione dalla **Casella** degli strumenti nel menu. Per disporre i controlli, trascinarli nelle posizioni desiderate.<br /><br /> Per aggiungere controlli a dopo il caricamento della barra multifunzione nell'applicazione Office, è necessario impostare la proprietà su true prima che la barra <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> multifunzione venga caricata.  Per informazioni su come eseguire questa operazione, vedere Panoramica del modello [a oggetti della barra multifunzione.](../vsto/ribbon-object-model-overview.md)|
|**Separatore**|Barra sottile usata per separare gli elementi in un elenco. Quando viene aggiunta a un gruppo, la barra è verticale. Quando viene aggiunta a un menu, la barra è orizzontale.|
|**SplitButton**|Pulsante con un menu associato. Un pulsante di divisione può contenere uno dei controlli seguenti:<br /><br /> - Pulsante<br />- Casella di controllo<br />- Raccolta<br />- Menu<br />- Pulsante Dividi<br />- Pulsante Di attivazione/disattivazione<br />- Separatore<br /><br /> Analogamente al menu, il pulsante di divisione ha una propria area di progettazione. Tuttavia, a differenza di un menu, è possibile aggiornare solo gli elementi in un pulsante di divisione prima che la barra multifunzione venga caricata nell'Office app. Per informazioni su come aggiornare gli elementi in un pulsante di divisione, vedere Panoramica del modello a [oggetti della barra multifunzione.](../vsto/ribbon-object-model-overview.md)|
|**ToggleButton**|Pulsante che viene visualizzato premuto o non premuto.|

## <a name="handle-events-and-setting-properties"></a><a name="HandleEventsSetProperties"></a> Gestire gli eventi e impostare le proprietà
 La finestra di progettazione della barra multifunzione consente di impostare le proprietà del controllo in fase di progettazione tramite la **finestra** Proprietà. Inoltre, la barra multifunzione espone un modello a oggetti fortemente tipizzato che è possibile usare per ottenere e impostare le proprietà dei controlli barra multifunzione in fase di esecuzione.

 È possibile fare doppio clic su qualsiasi controllo nella finestra di progettazione per aprire un gestore eventi per l'evento predefinito del controllo. È possibile creare gestori eventi per tutti gli altri eventi del controllo usando la **finestra** Proprietà.

 Gli eventi e le proprietà della barra multifunzione si trovano nello spazio <xref:Microsoft.Office.Tools.Ribbon> dei nomi . L'elemento Barra multifunzione (finestra di progettazione **visiva)** aggiunge automaticamente un riferimento a questo assembly nel progetto e inserisce l'istruzione **using** o **Imports** appropriata nella parte superiore del file di codice della barra multifunzione.

 Per informazioni sulla gestione degli eventi della barra multifunzione e sull'impostazione delle proprietà dei controlli barra multifunzione in fase di esecuzione, vedere Panoramica del modello [a oggetti della barra multifunzione.](../vsto/ribbon-object-model-overview.md)

## <a name="customize-backstage-view"></a><a name="CustomizingMicrosoftOfficeButton"></a> Personalizzare la visualizzazione Backstage
 È possibile usare la finestra di progettazione della barra multifunzione per aggiungere controlli al menu visualizzato quando si fa clic sulla **scheda File.** Questo menu è denominato visualizzazione Backstage.

 Non è possibile posizionare i controlli prima o dopo i controlli predefiniti usando la finestra di progettazione della barra multifunzione. Un controllo incorporato è un controllo già visualizzato nella visualizzazione Backstage. Se si desidera posizionare i controlli prima o dopo i controlli predefiniti, è necessario usare il codice XML della barra multifunzione. Per altre informazioni sulla barra **multifunzione (XML),** vedere XML [della barra multifunzione.](../vsto/ribbon-xml.md) Per altre informazioni sulla personalizzazione della visualizzazione Backstage, vedere Introduzione alla visualizzazione [Backstage di Office 2010](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) per gli sviluppatori e Personalizzare la visualizzazione [Backstage di Office 2010](/previous-versions/office/developer/office-2010/ee815851(v=office.14))per gli sviluppatori .

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Per informazioni su come aggiungere controlli alla visualizzazione Backstage, vedere [Procedura: Aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

## <a name="accessibility-in-the-ribbon-designer"></a><a name="Accessibility"></a> Accessibilità nella finestra di progettazione della barra multifunzione
 È possibile usare i tasti di scelta rapida per spostare i controlli nella finestra di progettazione della barra multifunzione. Alcuni tasti di scelta rapida si applicano a tutti i controlli e altri solo ai controlli che dispongono di menu.

 I tasti di scelta rapida applicabili a tutti i controlli sono illustrati nella tabella seguente.

|Azione|Tasto di scelta rapida|
|------------|-----------------------|
|Spostare un controllo prima del controllo precedente nell'elenco.|**CTRL+FRECCIA DESTRA** + **Su**<br /><br /> **CTRL+FRECCIA DESTRA** + **A sinistra**|
|Spostare un controllo dopo il controllo successivo nell'elenco.|**CTRL+FRECCIA DESTRA** + **In basso**<br /><br /> **CTRL+FRECCIA DESTRA** + **A destra**|
|Spostare la selezione da un controllo a un altro nello stesso gruppo. Per un pannello a discesa, spostarsi tra il controllo padre e i controlli nel pannello a discesa.|**Attivo**<br /><br /> **Giù**|
|Scorrere in avanti tutti i controlli.|**TAB**|
|Scorrere al contrario tutti i controlli.|**MAIUSC** + **Scheda**|
|Eliminare il controllo o il set di controlli selezionato.|**Elimina**|
|Copiare i controlli selezionati.|**CTRL+FRECCIA DESTRA** + **C**|
|Tagliare i controlli selezionati.|**CTRL+FRECCIA DESTRA** + **X**|
|Incollare i controlli dagli Appunti.|**CTRL+FRECCIA DESTRA** + **V**|
|Selezionare la casella **degli strumenti**.|**CTRL+FRECCIA DESTRA** + **ALT** + **X**|
|Selezionare il componente padre.|**ESC**|

 I tasti di scelta rapida che si applicano solo Microsoft Office menu, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> e sono illustrati nella tabella <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> seguente.

|Azione|Tasto di scelta rapida|
|------------|-----------------------|
|Selezionare il controllo padre se il pannello a discesa è aperto ed è presente un controllo selezionato nel pannello a discesa.|**Sinistra**|
|Chiudere il pannello a discesa se il pannello a discesa è aperto e il controllo padre è selezionato.|**Sinistra**|
|Aprire il pannello a discesa.|**va bene**|
|Selezionare il primo controllo nel pannello a discesa se il pannello a discesa è aperto.|**va bene**|
|Chiudere un pannello a discesa.|**ESC**|

## <a name="see-also"></a>Vedi anche

- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione al codice XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Procedura: Iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
