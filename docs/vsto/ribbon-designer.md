---
title: Finestra di progettazione della barra multifunzione
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e1c2941b0c088a832540fd3380c993fe2c380b44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985619"
---
# <a name="ribbon-designer"></a>Finestra di progettazione della barra multifunzione
  La finestra di progettazione della barra multifunzione è un'area di progettazione visiva. Utilizzare la finestra di progettazione della barra multifunzione per aggiungere schede, gruppi e controlli personalizzati alla barra multifunzione di un'applicazione Microsoft Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Per aprire la finestra di progettazione della barra multifunzione, aggiungere un elemento **barra multifunzione (finestra di progettazione visiva)** al progetto. È quindi possibile utilizzare gli strumenti di progettazione per le seguenti attività:

- [Progettare il layout della barra multifunzione](#DesigningRibbonLayout)

- [Gestire gli eventi e impostare le proprietà del controllo](#HandleEventsSetProperties)

- [Aggiungere controlli alla visualizzazione Backstage](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
> È possibile eseguire alcune attività usando la finestra di progettazione della barra multifunzione. Per altre informazioni su queste attività e su come è possibile realizzarle, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Aggiungere un elemento barra multifunzione (finestra di progettazione visiva) a un progetto
 Per usare la finestra di progettazione della barra multifunzione, aggiungere un nuovo elemento della **barra multifunzione (finestra di progettazione visiva)** al progetto. Per altre informazioni, vedere [procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).

 Quando si aggiunge un nuovo elemento della **barra multifunzione (finestra di progettazione visiva)** , Visual Studio aggiunge automaticamente i file seguenti al progetto:

- Un file di codice della barra multifunzione. Il nome di questo file è specificato per l'elemento **barra multifunzione (finestra di progettazione visiva)** nella finestra di dialogo **Aggiungi nuovo elemento** . Aggiungere il codice per gestire gli eventi della barra multifunzione in questo file.

- File di codice della finestra di progettazione della barra multifunzione. Questo file contiene il codice generato dalla finestra di progettazione della barra multifunzione e non deve essere modificato direttamente.

- Un file di risorse. Questo file contiene i valori delle proprietà di ogni controllo sulla barra multifunzione.

  Se si dispone già di un elemento **barra multifunzione (finestra di progettazione visiva)** da un altro progetto, è possibile riutilizzarlo nel progetto corrente utilizzando la finestra di dialogo **Aggiungi elemento esistente** .

## <a name="design-a-ribbon"></a><a name="DesigningRibbonLayout"></a> Progettare una barra multifunzione
 Sono disponibili tre modi per aprire la finestra di progettazione della barra multifunzione:

- In **Esplora soluzioni**fare doppio clic sul file di codice della barra multifunzione.

- In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul file di codice della barra multifunzione, quindi scegliere **Visualizza finestra di progettazione**.

- In **Esplora soluzioni**selezionare il file di codice della barra multifunzione, quindi scegliere **finestra di progettazione** dal menu **Visualizza** .

  La finestra di progettazione della barra multifunzione contiene una scheda e un gruppo predefiniti. È possibile rimuovere la scheda e il gruppo predefiniti dalla finestra di progettazione della barra multifunzione. Per rimuovere il gruppo predefinito, fare clic con il pulsante destro del mouse su **Group1**e quindi scegliere **Elimina**. Per rimuovere la scheda predefinita, fare clic con il pulsante destro del mouse su un'area vuota dell'area di progettazione, quindi scegliere **Rimuovi scheda della barra multifunzione**.

  È anche possibile aggiungere schede, gruppi e controlli personalizzati alla finestra di progettazione della barra multifunzione. È possibile trovare questi controlli nella **casella degli strumenti**, nel gruppo **controlli della barra multifunzione di Office** . Sono disponibili tre modi per aggiungere controlli dal gruppo di **controlli della barra multifunzione di Office** alla finestra di progettazione della barra multifunzione:

- Trascinare un controllo in un'area appropriata della finestra di progettazione della barra multifunzione.

- Fare clic su un controllo, quindi fare clic su un'area appropriata nella finestra di progettazione della barra multifunzione.

- Selezionare un'area appropriata nella finestra di progettazione, quindi fare doppio clic su un controllo nella **casella degli strumenti**.

### <a name="ribbon-design-workflow"></a>Flusso di lavoro progettazione della barra multifunzione
 Per progettare il layout della barra multifunzione, seguire questa procedura di base:

1. [Aggiungere una scheda personalizzata alla barra multifunzione](#AddTabToRibbon).

2. [Aggiungere gruppi alla scheda](#AddGroupsToTab).

3. [Aggiungere controlli ai gruppi](#AddControlsToGroups).

   I controlli possono essere eliminati solo nei gruppi; non è possibile trascinare un controllo direttamente in una scheda o nella barra multifunzione. I gruppi possono essere eliminati solo nelle schede; non è possibile trascinare un gruppo direttamente in una barra multifunzione.

   Disporre i controlli trascinandoli nelle posizioni corrette. È possibile impostare le proprietà di un controllo utilizzando la finestra **Proprietà** .

   Non è possibile trascinare i controlli da una scheda a un'altra sulla barra multifunzione. Se si desidera spostare un controllo in un'altra scheda, è necessario utilizzare il comando **taglia** per rimuovere il controllo da una scheda, quindi incollare il controllo in un'altra scheda. Se il controllo viene tagliato e incollato, il gestore dell'evento smette di funzionare. È possibile riconnettere il gestore eventi nella finestra **Proprietà** . Per ulteriori informazioni, vedere [finestra Proprietà](../ide/reference/properties-window.md).

### <a name="add-custom-tabs-to-the-ribbon"></a><a name="AddTabToRibbon"></a> Aggiungere schede personalizzate alla barra multifunzione
 Sono disponibili tre modi per aggiungere una scheda personalizzata alla barra multifunzione:

- Aggiungere una scheda dalla **casella degli strumenti**.

- Fare clic con il pulsante destro del mouse sulla finestra di progettazione Ribbon, quindi scegliere **Aggiungi scheda della barra multifunzione**

- Aprire l' **Editor della raccolta di schede**e quindi fare clic su **Aggiungi**.

   Per aprire l' **Editor della raccolta di schede**, nella finestra **Proprietà** selezionare la proprietà **tabulazioni** , quindi fare clic sul pulsante con i puntini di sospensione ![ASP.NET Mobile Designer ellisse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer").

  Dopo aver aggiunto una scheda, è possibile aggiungere gruppi che contengano i controlli.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Rimuovi schede personalizzate dalla barra multifunzione
 Sono disponibili tre modi per rimuovere una scheda personalizzata dalla barra multifunzione:

- Fare clic con il pulsante destro del mouse sulla finestra di progettazione, quindi scegliere **Rimuovi scheda barra multifunzione**.

- Nel riquadro **comandi** della finestra **Proprietà** fare clic su **Rimuovi scheda della barra multifunzione**.

- Aprire l' **Editor della raccolta di schede**, selezionare la scheda e quindi fare clic su **Rimuovi**.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Modificare la posizione di una scheda sulla barra multifunzione
 È possibile modificare l'ordine delle schede personalizzate su una barra multifunzione. È anche possibile posizionare le schede personalizzate prima o dopo una scheda incorporata nella barra multifunzione. Per ulteriori informazioni, vedere [procedura: modificare la posizione di una scheda nella barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Personalizzare le schede predefinite sulla barra multifunzione
 Una scheda incorporata è una scheda già presente sulla barra multifunzione di un'applicazione Microsoft Office. Ad esempio, la scheda **dati** è una scheda incorporata in Excel.

 È possibile aggiungere gruppi e controlli a una scheda incorporata. Per impostazione predefinita, un gruppo personalizzato viene visualizzato come ultimo gruppo in una scheda incorporata, ma è possibile spostarlo prima o dopo qualsiasi gruppo incorporato nella scheda.

 Non è possibile rimuovere i gruppi incorporati.

 Per informazioni dettagliate su come personalizzare una scheda incorporata, vedere [procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md).

### <a name="add-groups-to-a-tab"></a><a name="AddGroupsToTab"></a> Aggiungere gruppi a una scheda
 I gruppi organizzano in modo logico i controlli sulla barra multifunzione. Aggiungere gruppi alle tabulazioni. Aggiungere tutti gli altri controlli al gruppo.

### <a name="add-controls-to-groups"></a><a name="AddControlsToGroups"></a> Aggiungere controlli ai gruppi
 Aggiungere uno o più controlli a un gruppo. Nella tabella seguente viene descritto ogni controllo.

|Controllo|Descrizione|
|-------------|-----------------|
|**Box**|Contenitore che organizza i controlli in un gruppo. È possibile aggiungere qualsiasi controllo a una casella, eccetto un separatore, un gruppo o una scheda. Una casella può essere orizzontale o verticale.|
|**Button**|Pulsante che avvia un'azione. È possibile aggiungere un pulsante a un gruppo, un gruppo di pulsanti, un elenco a discesa, una raccolta, un menu o un pulsante di menu combinato.|
|**ButtonGroup**|Gruppo che contiene uno o più pulsanti, pulsanti di menu, pulsanti di menu combinato e raccolte. È possibile aggiungere un gruppo di pulsanti a un gruppo o a un menu.|
|**CheckBox**|Casella selezionata o deselezionata per attivare o disattivare un'opzione.|
|**ComboBox**|Casella di modifica con una casella di riepilogo collegata. Gli utenti possono digitare o selezionare la scelta. Nella casella viene visualizzata la selezione corrente. Utilizzare la <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> proprietà per aggiungere e rimuovere elementi in fase di esecuzione prima o dopo il caricamento della barra multifunzione nell'applicazione di Office.|
|**DropDown**|Elenco di elementi che l'utente può selezionare. L'utente non può digitare un nuovo elemento in un elenco a discesa.<br /><br /> Utilizzare la <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> proprietà per aggiungere elementi all'elenco. È possibile aggiungere e rimuovere elementi in fase di esecuzione.<br /><br /> Utilizzare la <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> proprietà per aggiungere pulsanti all'elenco. Tuttavia, non è possibile aggiungere e rimuovere pulsanti in fase di esecuzione dopo che la barra multifunzione è stata caricata nell'applicazione di Office.|
|**Casella**|Casella in cui l'utente può digitare il testo.|
|**Raccolta**|Menu che presenta una matrice o una griglia di scelte visive da cui gli utenti possono selezionare. È possibile controllare il layout delle selezioni nel menu. Utilizzare le <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> proprietà e <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> per specificare il numero di righe e colonne in cui vengono visualizzati gli elementi e i pulsanti della raccolta.|
|**Etichetta**|Testo che è possibile utilizzare per identificare i controlli sulla barra multifunzione.|
|**Menu**|Elenco a discesa che può contenere uno dei seguenti controlli:<br /><br /> -Pulsante<br />-Casella di controllo<br />-Raccolta<br />-Menu<br />-Pulsante Split<br />-Interruttore<br />-Separatore<br /><br /> Per aggiungere un controllo a un menu nella finestra di progettazione della barra multifunzione, fare clic sulla freccia rivolta verso il basso nel menu per esporre l'area di progettazione dei menu. È quindi possibile trascinare i controlli della barra multifunzione dalla **casella degli strumenti** nel menu. Per disporre i controlli, trascinarli nelle posizioni desiderate.<br /><br /> Per aggiungere controlli al <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> dopo che la barra multifunzione è stata caricata nell'applicazione di Office, è necessario impostare la <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> proprietà su **true** prima di caricare la barra multifunzione. Per informazioni su come eseguire questa operazione, vedere [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md).|
|**Separatore**|Barra sottile utilizzata per separare gli elementi in un elenco. Quando viene aggiunto a un gruppo, la barra è verticale. Quando viene aggiunto a un menu, la barra è orizzontale.|
|**SplitButton**|Un pulsante con un menu collegato. Un pulsante di suddivisione può contenere uno dei seguenti controlli:<br /><br /> -Pulsante<br />-Casella di controllo<br />-Raccolta<br />-Menu<br />-Pulsante Split<br />-Interruttore<br />-Separatore<br /><br /> Come il menu, il pulsante di menu combinato ha una propria area di progettazione. Tuttavia, a differenza di un menu, è possibile aggiornare gli elementi solo in un pulsante di menu combinato prima che la barra multifunzione venga caricata nell'applicazione di Office. Per informazioni su come aggiornare gli elementi in un pulsante di suddivisione, vedere [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md).|
|**ToggleButton**|Pulsante visualizzato premuto o non premuto.|

## <a name="handle-events-and-setting-properties"></a><a name="HandleEventsSetProperties"></a> Gestire gli eventi e impostare le proprietà
 La finestra di progettazione della barra multifunzione consente di impostare le proprietà del controllo in fase di progettazione utilizzando la finestra **Proprietà** . Inoltre, la barra multifunzione espone un modello a oggetti fortemente tipizzato che è possibile utilizzare per ottenere e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione.

 È possibile fare doppio clic su un controllo nella finestra di progettazione per aprire un gestore eventi per l'evento predefinito del controllo. È possibile creare gestori di eventi per tutti gli altri eventi del controllo utilizzando la finestra **Proprietà** .

 Gli eventi e le proprietà della barra multifunzione si trovano nello <xref:Microsoft.Office.Tools.Ribbon> spazio dei nomi. L'elemento **barra multifunzione (finestra di progettazione visiva)** aggiunge automaticamente un riferimento a questo assembly nel progetto e inserisce l'istruzione **using** o **Imports** appropriata all'inizio del file di codice della barra multifunzione.

 Per informazioni sulla gestione degli eventi della barra multifunzione e sull'impostazione delle proprietà dei controlli della barra multifunzione in fase di esecuzione, vedere la [Panoramica del modello a oggetti](../vsto/ribbon-object-model-overview.md)

## <a name="customize-backstage-view"></a><a name="CustomizingMicrosoftOfficeButton"></a> Personalizzare la visualizzazione Backstage
 È possibile utilizzare la finestra di progettazione della barra multifunzione per aggiungere controlli al menu visualizzato quando si fa clic sulla scheda **file** . Questo menu è denominato visualizzazione Backstage.

 Non è possibile posizionare i controlli prima o dopo i controlli incorporati tramite la finestra di progettazione della barra multifunzione. Un controllo incorporato è un controllo già visualizzato nella visualizzazione Backstage. Se si desidera posizionare i controlli prima o dopo i controlli incorporati, è necessario utilizzare la barra multifunzione XML. Per ulteriori informazioni sulla **barra multifunzione (XML)**, vedere [Ribbon XML](../vsto/ribbon-xml.md). Per ulteriori informazioni sulla personalizzazione della visualizzazione Backstage, vedere [Introduzione alla visualizzazione Backstage di office 2010 per gli sviluppatori](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) e [personalizzare la visualizzazione Backstage di Office 2010 per gli sviluppatori](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Per informazioni su come aggiungere controlli alla visualizzazione Backstage, vedere [procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

## <a name="accessibility-in-the-ribbon-designer"></a><a name="Accessibility"></a> Accessibilità nella finestra di progettazione della barra multifunzione
 È possibile utilizzare i tasti di scelta rapida per spostare i controlli nella finestra di progettazione della barra multifunzione. Alcuni tasti di scelta rapida si applicano a tutti i controlli e alcuni si applicano solo ai controlli che dispongono di menu.

 Nella tabella seguente sono illustrati i tasti di scelta rapida che si applicano a tutti i controlli.

|Action|Tasti di scelta rapida|
|------------|-----------------------|
|Spostare un controllo prima del controllo precedente nell'elenco.|**CTRL** + **In alto**<br /><br /> **CTRL** + A **sinistra**|
|Spostare un controllo dopo il controllo successivo nell'elenco.|**CTRL** + In **basso**<br /><br /> **CTRL** + A **destra**|
|Spostare la selezione da un controllo a un altro nello stesso gruppo. Per un pannello a discesa, spostarsi tra il controllo padre e i controlli nel pannello a discesa.|**Attivo**<br /><br /> **Giù**|
|Eseguire l'iterazione in tutti i controlli.|**Scheda**|
|Eseguire l'iterazione fino al contrario di tutti i controlli.|**Sposta** + **Scheda**|
|Elimina il controllo o il set di controlli selezionato.|**Elimina**|
|Copiare i controlli selezionati.|**CTRL** + **C**|
|Taglia i controlli selezionati.|**CTRL** + **X**|
|Incollare i controlli dagli Appunti.|**CTRL** + **V**|
|Selezionare la **casella degli strumenti**.|**CTRL** + **ALT** + **X**|
|Selezionare il componente padre.|**ESC**|

 I tasti di scelta rapida che si applicano solo al menu Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> e <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> sono illustrati nella tabella seguente.

|Action|Tasti di scelta rapida|
|------------|-----------------------|
|Selezionare il controllo padre se il pannello a discesa è aperto ed è selezionato un controllo nel pannello a discesa.|**Sinistra**|
|Chiudere il pannello a discesa se il pannello a discesa è aperto e il controllo padre è selezionato.|**Sinistra**|
|Aprire il pannello a discesa.|**Ok**|
|Selezionare il primo controllo nel pannello a discesa se il pannello a discesa è aperto.|**Ok**|
|Chiudere un pannello a discesa.|**ESC**|

## <a name="see-also"></a>Vedere anche

- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura: esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione a XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
