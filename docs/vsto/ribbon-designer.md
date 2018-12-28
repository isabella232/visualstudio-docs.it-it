---
title: Finestra di progettazione della barra multifunzione
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 160cde8b4a2e6034cb9c5ced7c6a13d57c1b546c
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804799"
---
# <a name="ribbon-designer"></a>Finestra di progettazione della barra multifunzione
  La finestra di progettazione della barra multifunzione è un'area di progettazione visiva. Utilizzare la finestra di progettazione della barra multifunzione per aggiungere schede personalizzate, gruppi e controlli alla barra multifunzione di un'applicazione Microsoft Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Per aprire la finestra di progettazione della barra multifunzione, aggiungere un **sulla barra multifunzione (finestra di progettazione visiva)** elemento al progetto. È quindi possibile usare gli strumenti di progettazione per le attività seguenti:

-   [Progettare il layout della barra multifunzione](#DesigningRibbonLayout)

-   [Gestire gli eventi e impostare le proprietà del controllo](#HandleEventsSetProperties)

-   [Aggiungere controlli alla visualizzazione Backstage](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
>  Esistono alcune attività che è possibile eseguire utilizzando la finestra di progettazione della barra multifunzione. Per altre informazioni su queste attività e come è possibile eseguire queste attività, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).

 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [ricerca per categorie Usare la finestra di progettazione della barra multifunzione per personalizzare la barra multifunzione in Outlook? ](http://go.microsoft.com/fwlink/?LinkID=130312).

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Aggiungere un elemento barra multifunzione (finestra di progettazione visiva) a un progetto
 Per usare la finestra di progettazione della barra multifunzione, aggiungere una nuova **sulla barra multifunzione (finestra di progettazione visiva)** elemento al progetto. Per altre informazioni, vedere [Procedura: Introduzione alla personalizzazione della barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).

 Quando si aggiunge un nuovo **sulla barra multifunzione (finestra di progettazione visiva)** item, Visual Studio aggiunge automaticamente i file seguenti al progetto:

- Un file di codice della barra multifunzione. Questo file contiene il nome specificato per il **sulla barra multifunzione (finestra di progettazione visiva)** degli elementi nella **Aggiungi nuovo elemento** nella finestra di dialogo. Aggiungere il codice per gestire gli eventi della barra multifunzione a questo file.

- Un file di codice di progettazione della barra multifunzione. Questo file contiene il codice generato dalla finestra di progettazione della barra multifunzione e non deve essere modificato direttamente.

- Un file di risorse. Questo file contiene i valori delle proprietà di ogni controllo sulla barra multifunzione.

  Se si dispone già di un **sulla barra multifunzione (finestra di progettazione visiva)** elemento da un altro progetto, è possibile riutilizzarlo nel progetto corrente usando la **Aggiungi elemento esistente** nella finestra di dialogo.

##  <a name="DesigningRibbonLayout"></a> Progettare una barra multifunzione
 Esistono tre modi per aprire la finestra di progettazione della barra multifunzione:

- Nelle **Esplora soluzioni**, fare doppio clic sul file di codice della barra multifunzione.

- Nelle **Esplora soluzioni**, fare clic sul file di codice della barra multifunzione e quindi fare clic su **Progettazione viste**.

- Nella **Esplora soluzioni**, selezionare il file di codice della barra multifunzione e quindi fare clic su **progettazione** sul **visualizzazione** menu.

  La finestra di progettazione della barra multifunzione contiene una scheda predefinita e un gruppo. È possibile rimuovere la scheda predefinita e il gruppo dalla finestra di progettazione della barra multifunzione. Per rimuovere il gruppo predefinito, fare doppio clic su **Group1**, quindi fare clic su **eliminare**. Per rimuovere la scheda predefinita, fare doppio clic su un'area vuota dell'area di progettazione e quindi fare clic su **Rimuovi scheda della barra multifunzione**.

  È anche possibile aggiungere schede personalizzate, gruppi e controlli alla finestra di progettazione della barra multifunzione. È possibile trovare questi controlli nel **casella degli strumenti**, nella **controlli della barra multifunzione di Office** gruppo. Esistono tre modi per aggiungere i controlli di **controlli della barra multifunzione di Office** gruppo alla finestra di progettazione della barra multifunzione:

- Trascinare un controllo in un'area appropriata della finestra di progettazione della barra multifunzione.

- Fare clic su un controllo e quindi fare clic su un'area appropriata nella finestra di progettazione della barra multifunzione.

- Selezionare un'area appropriata nella finestra di progettazione e quindi fare doppio clic su un controllo nel **casella degli strumenti**.

### <a name="ribbon-design-workflow"></a>Flusso di lavoro di progettazione della barra multifunzione
 Seguire questi passaggi di base per progettare il layout della barra multifunzione:

1. [Aggiungere una scheda personalizzata alla barra multifunzione](#AddTabToRibbon).

2. [Aggiungere gruppi alla scheda](#AddGroupsToTab).

3. [Aggiungere controlli ai gruppi](#AddControlsToGroups).

   I controlli possono essere eliminati solo nei gruppi. è possibile trascinare un controllo direttamente a una scheda o alla barra multifunzione. I gruppi possono essere rilasciati solo nelle schede; è possibile trascinare un gruppo direttamente a una barra multifunzione.

   Disporre i controlli trascinandoli nelle posizioni corrette. È possibile impostare le proprietà di un controllo usando il **proprietà** finestra.

   È possibile trascinare i controlli da una scheda a altra nella barra multifunzione. Se si desidera spostare un controllo a un'altra scheda, è necessario usare il **Taglia** comando per rimuovere il controllo da una scheda e quindi incollare il controllo in un'altra scheda. Se si taglia il controllo e incollare il codice, il gestore eventi smette di funzionare. È possibile riconnettersi al gestore eventi di **proprietà** finestra. Per altre informazioni, vedere [finestra proprietà](../ide/reference/properties-window.md).

###  <a name="AddTabToRibbon"></a> Aggiungere schede personalizzate alla barra multifunzione
 Esistono tre modi per aggiungere una scheda personalizzata alla barra multifunzione:

- Aggiungere una scheda dal **casella degli strumenti**.

- Fare doppio clic su finestra di progettazione della barra multifunzione e quindi fare clic su **Aggiungi scheda della barra multifunzione**.

- Aprire il **Editor della raccolta Tab**, quindi fare clic su **Add**.

   Per aprire la **Editor della raccolta Tab**, nel **delle proprietà** finestra, seleziona il **schede** proprietà e quindi fare clic sul pulsante con puntini di sospensione ![ASP.NET per dispositivi mobili Finestra di progettazione ellisse](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer").

  Dopo aver aggiunto una scheda, è possibile aggiungere gruppi che contengano i controlli.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Rimuovere le schede personalizzate dalla barra multifunzione
 Esistono tre modi per rimuovere una scheda personalizzata dalla barra multifunzione:

-   Pulsante destro del mouse nella finestra di progettazione e quindi fare clic su **Rimuovi scheda della barra multifunzione**.

-   Nel **comandi** riquadro della **delle proprietà** finestra, fare clic su **Rimuovi scheda della barra multifunzione**.

-   Aprire il **Editor della raccolta Tab**, selezionare la scheda e quindi fare clic su **rimuovere**.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Modificare la posizione di una scheda della barra multifunzione
 È possibile modificare l'ordine delle schede personalizzate in una barra multifunzione. È anche possibile posizionare le schede personalizzate prima o dopo una scheda incorporata nella barra multifunzione. Per altre informazioni, vedere [Procedura: Modificare la posizione di una scheda della barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Personalizzare le schede incorporate nella barra multifunzione
 Una scheda incorporata rappresenta una scheda già presente sulla barra multifunzione di un'applicazione Microsoft Office. Ad esempio, il **dati** scheda è una scheda incorporata in Excel.

 È possibile aggiungere gruppi e controlli in una scheda incorporata, Per impostazione predefinita, un gruppo personalizzato viene visualizzato come ultimo gruppo in una scheda incorporata, anche se è possibile spostarlo prima o dopo un gruppo incorporato nella scheda.

 Non è possibile rimuovere gruppi incorporati.

 Per informazioni dettagliate su come personalizzare una scheda incorporata, vedere [come: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md).

###  <a name="AddGroupsToTab"></a> Aggiungere gruppi in una scheda
 I gruppi organizzano in modo logico i controlli della barra multifunzione. Aggiungere gruppi a schede. Aggiungere tutti gli altri controlli al gruppo.

###  <a name="AddControlsToGroups"></a> Aggiungere controlli ai gruppi
 Aggiungere uno o più controlli a un gruppo. La tabella seguente descrive ogni controllo.

|Control|Descrizione|
|-------------|-----------------|
|**Box**|Un contenitore che organizza i controlli in un gruppo. È possibile aggiungere qualsiasi controllo a una casella, ad eccezione di un separatore, un gruppo o una scheda. Una casella può essere orizzontale o verticale.|
|**Pulsante**|Un pulsante che avvia un'azione. È possibile aggiungere un pulsante a un gruppo, un gruppo di pulsanti, un elenco di riepilogo a discesa, una raccolta, un menu o un pulsante di menu combinato.|
|**Gruppo di pulsanti.**|Un gruppo che contiene uno o più pulsanti, interruttori, menu, pulsanti di menu combinato e raccolte. È possibile aggiungere un gruppo di pulsanti a un gruppo o un menu.|
|**CheckBox**|Una casella selezionata o deselezionata per attivare o disattivare un'opzione.|
|**ComboBox**|Una casella di modifica è associata una casella di elenco. Gli utenti possono digitare o selezionare le proprie preferenze. Viene visualizzata la selezione corrente. Usare il <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> proprietà da aggiungere e rimuovere elementi in fase di esecuzione prima o dopo la barra multifunzione viene caricata nell'applicazione Office.|
|**Elenco a discesa**|Un elenco di elementi che l'utente può selezionare. L'utente non è possibile digitare un nuovo elemento in un elenco a discesa.<br /><br /> Usare il <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> proprietà per aggiungere elementi all'elenco. È possibile aggiungere e rimuovere elementi in fase di esecuzione.<br /><br /> Usare il <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> proprietà da aggiungere pulsanti all'elenco. Tuttavia, non è possibile aggiungere e rimuovere pulsanti in fase di esecuzione dopo che è stata caricata nell'applicazione Office.|
|**Casella di modifica**|Una casella in cui l'utente può digitare testo.|
|**Gallery**|Un menu di scelta che presenta una matrice o griglia di scelte visive selezionabili dagli utenti. È possibile controllare il layout delle selezioni nel menu di scelta. Usare la <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> e il <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> le proprietà per specificare il numero di righe e colonne che verranno visualizzati gli elementi e i pulsanti della raccolta.|
|**Etichetta**|Testo che è possibile usare per identificare i controlli della barra multifunzione.|
|**Menu**|Un elenco di riepilogo a discesa che può contenere uno dei seguenti controlli:<br /><br /> -Pulsante<br />: Casella di controllo<br />-Raccolta<br />-Menu<br />-Pulsante di menu combinato<br />-Pulsante Mostra/Nascondi<br />-Separatore<br /><br /> Per aggiungere un controllo a un menu nella finestra di progettazione della barra multifunzione, fare clic sulla freccia in giù nel menu di scelta per esporre l'area di progettazione menu. È quindi possibile trascinare i controlli della barra multifunzione dal **casella degli strumenti** nel menu. Per disporre i controlli, trascinarli nelle posizioni desiderate.<br /><br /> Per aggiungere controlli per la <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> dopo che è stata caricata nell'applicazione Office, è necessario impostare il <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> proprietà **true** prima del caricamento della barra multifunzione. Per informazioni su come eseguire questa operazione, vedere [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md).|
|**Separatore**|Barra sottile utilizzata per separare gli elementi in un elenco. Quando aggiunta a un gruppo, la barra è verticale. Quando aggiunta a un menu di scelta, la barra è orizzontale.|
|**SplitButton**|Pulsante associato un menu. Un pulsante di menu combinato può contenere i controlli seguenti:<br /><br /> -Pulsante<br />: Casella di controllo<br />-Raccolta<br />-Menu<br />-Pulsante di menu combinato<br />-Pulsante Mostra/Nascondi<br />-Separatore<br /><br /> Analogamente al menu, pulsante di menu combinato ha la propria area di progettazione. Tuttavia, a differenza di un menu, è possibile aggiornare solo gli elementi in un pulsante di menu combinato prima del caricamento della barra multifunzione nell'applicazione Office. Per informazioni su come aggiornare gli elementi in un pulsante di menu combinato, vedere [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md).|
|**ToggleButton**|Un pulsante che appare premuto o meno.|

##  <a name="HandleEventsSetProperties"></a> Gestire gli eventi e impostazione delle proprietà
 La finestra di progettazione della barra multifunzione consente di impostare le proprietà del controllo in fase di progettazione utilizzando il **proprietà** finestra. Inoltre, la barra multifunzione espone un modello a oggetti fortemente tipizzati che è possibile usare per ottenere e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione.

 È possibile fare doppio clic su qualsiasi controllo nella finestra di progettazione per aprire un gestore eventi per l'evento del controllo predefinito. È possibile creare gestori eventi per tutti gli altri eventi di controllo usando il **proprietà** finestra.

 Proprietà ed eventi della barra multifunzione si trovano nel <xref:Microsoft.Office.Tools.Ribbon> dello spazio dei nomi. Il **della barra multifunzione (finestra di progettazione visiva)** elemento aggiunge automaticamente un riferimento a questo assembly nel progetto e inserisce appropriato **usando** oppure **importazioni** all'inizio l'istruzione del file di codice della barra multifunzione.

 Per informazioni sulla gestione degli eventi della barra multifunzione e impostare le proprietà dei controlli barra multifunzione in fase di esecuzione, vedere [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md).

##  <a name="CustomizingMicrosoftOfficeButton"></a> Personalizzare la visualizzazione Backstage
 È possibile usare la finestra di progettazione della barra multifunzione per aggiungere controlli al menu visualizzato quando si sceglie la **File** scheda. Questo menu è detto visualizzazione Backstage.

 È possibile posizionare i controlli prima o dopo i controlli incorporati tramite la finestra di progettazione della barra multifunzione. Un controllo incorporato è un controllo già disponibile nella visualizzazione Backstage. Se si desidera posizionare controlli prima o dopo i controlli incorporati, è necessario usare XML della barra multifunzione. Per altre informazioni sulle **sulla barra multifunzione (XML)**, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md). Per altre informazioni sulla personalizzazione della visualizzazione Backstage, vedere [Introduzione alla visualizzazione Backstage di Office 2010 per sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182189) e [personalizzare la visualizzazione Backstage di Office 2010 per gli sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182188).

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Per informazioni su come aggiungere controlli alla visualizzazione Backstage, vedere [come: Aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

##  <a name="Accessibility"></a> Accessibilità nella finestra di progettazione della barra multifunzione
 È possibile utilizzare i tasti di scelta rapida per spostare i controlli nella finestra di progettazione della barra multifunzione. Alcuni tasti di scelta rapida si applicano a tutti i controlli e alcuni si applicano solo ai controlli che dispongono di menu.

 I tasti di scelta rapida che si applicano a tutti i controlli vengono visualizzati nella tabella seguente.

|Operazione|Tasto di scelta rapida|
|------------|-----------------------|
|Spostare un controllo prima che il controllo precedente nell'elenco.|**CTRL**+**backup**<br /><br /> **CTRL**+**sinistra**|
|Spostare un controllo dopo il controllo successivo nell'elenco.|**CTRL**+**verso il basso**<br /><br /> **CTRL**+**destra**|
|Spostare la selezione da un controllo a un'altra nello stesso gruppo. Per un pannello a discesa, spostare tra il controllo padre e i controlli nel Pannello di riepilogo a discesa.|**Su**<br /><br /> **Giù**|
|Eseguire l'iterazione in avanti con tutti i controlli.|**TAB**|
|Eseguire l'iterazione di tutti i controlli in ordine ascendente.|**MAIUSC**+**TAB**|
|Eliminare il controllo selezionato o un set di controlli.|**Eliminazione**|
|Copiare i controlli selezionati.|**Ctrl**+**C**|
|Taglio dei controlli selezionati.|**Ctrl**+**X**|
|Incollare i controlli dagli Appunti.|**Ctrl**+**V**|
|Selezionare il **casella degli strumenti**.|**CTRL**+**Alt**+**X**|
|Selezionare il componente padre.|**ESC**|

 I tasti di scelta rapida che si applicano solo al Menu Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>, e <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> vengono visualizzati nella tabella seguente.

|Operazione|Tasto di scelta rapida|
|------------|-----------------------|
|Selezionare il controllo padre se il pannello di riepilogo a discesa è aperto ed è presente un controllo selezionato nel Pannello di riepilogo a discesa.|**A sinistra**|
|Chiudere il pannello di riepilogo a discesa se il pannello di riepilogo a discesa è aperto e viene selezionato il controllo padre.|**A sinistra**|
|Aprire il pannello di riepilogo a discesa.|**A destra**|
|Se il pannello di riepilogo a discesa è aperto, selezionare il primo controllo nel Pannello di riepilogo a discesa.|**A destra**|
|Chiude un pannello di riepilogo a discesa.|**ESC**|

## <a name="see-also"></a>Vedere anche

- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Procedura: Introduzione alla personalizzazione della barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
