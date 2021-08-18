---
title: Panoramica del modello a oggetti della barra multifunzione
description: Informazioni su come Visual Studio Tools per Office runtime espone un modello a oggetti fortemente tipizzato che è possibile usare per ottenere e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f7d840db368f61c0e85b5b21d7ff1c0a32b4a472
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032212"
---
# <a name="ribbon-object-model-overview"></a>Panoramica del modello a oggetti della barra multifunzione
  espone un modello a oggetti fortemente tipizzato che è possibile usare per ottenere e impostare le proprietà dei controlli della barra [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] multifunzione in fase di esecuzione. Ad esempio, è possibile popolare dinamicamente i controlli menu o mostrare e nascondere i controlli contestualmente. È anche possibile aggiungere schede, gruppi e controlli a una barra multifunzione, ma solo prima che la barra multifunzione venga caricata dall Office app Office barra multifunzione. Per informazioni, vedere [Impostare le proprietà che diventano di sola lettura.](#SettingReadOnlyProperties)

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Questo modello a oggetti della barra multifunzione è costituito principalmente dalla [classe Ribbon](#RibbonClass), da [eventi della](#RibbonEvents)barra multifunzione e dalle classi di controlli della barra [multifunzione](#RibbonControlClasses).

## <a name="ribbon-class"></a><a name="RibbonClass"></a> Classe Ribbon
 Quando si aggiunge un nuovo **elemento Barra multifunzione (finestra di** progettazione visiva) a un progetto, Visual Studio aggiunge una classe **Ribbon** al progetto. La **classe Ribbon** eredita dalla classe <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> .

 Questa classe viene visualizzata come classe parziale suddivisa tra il file di codice della barra multifunzione e il file di codice della finestra di progettazione della barra multifunzione.

## <a name="ribbon-events"></a><a name="RibbonEvents"></a> Eventi della barra multifunzione
 La **classe Ribbon** contiene i tre eventi seguenti:

|Event|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Generato quando l'applicazione Office carica la personalizzazione della barra multifunzione. Il <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> gestore eventi viene aggiunto automaticamente al file di codice della barra multifunzione. Usare questo gestore eventi per eseguire codice personalizzato quando viene caricata la barra multifunzione.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Consente di memorizzare nella cache le immagini nella personalizzazione della barra multifunzione quando la barra multifunzione viene caricata. È possibile ottenere un leggero miglioramento delle prestazioni se si scrive codice per memorizzare nella cache le immagini della barra multifunzione in questo gestore eventi. Per altre informazioni, vedere <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Generato alla chiusura dell'istanza della barra multifunzione.|

## <a name="ribbon-controls"></a><a name="RibbonControlClasses"></a> Controlli della barra multifunzione
 Lo spazio dei nomi contiene un tipo per ogni controllo visualizzato nel gruppo Office della barra <xref:Microsoft.Office.Tools.Ribbon> multifunzione della casella degli **strumenti**. 

 Nella tabella seguente viene illustrato il tipo per ogni `Ribbon` controllo. Per una descrizione di ogni controllo, vedere Panoramica [della barra multifunzione.](../vsto/ribbon-overview.md)

|Nome del controllo|Nome di classe|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**Dropdown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**Editbox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Raccolta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Gruppo**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Etichetta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Separatore**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**TAB**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 Lo <xref:Microsoft.Office.Tools.Ribbon> spazio dei nomi usa il prefisso "Ribbon" per questi tipi per evitare conflitti di nome con i nomi delle classi di controllo nello spazio dei <xref:System.Windows.Forms> nomi .

 Quando si aggiunge un controllo alla finestra di progettazione della barra multifunzione, la finestra di progettazione della barra multifunzione dichiara la classe per tale controllo come campo nel file di codice della finestra di progettazione della barra multifunzione.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Attività comuni che usano le proprietà dei controlli della barra multifunzione
 Ogni controllo contiene proprietà che è possibile usare per eseguire varie attività, ad esempio l'assegnazione di un'etichetta a un controllo o la visualizzazione e la visualizzazione `Ribbon` di controlli.

 In alcuni casi, le proprietà diventano di sola lettura dopo il caricamento della barra multifunzione o dopo l'aggiunta di un controllo a un menu dinamico. Per altre informazioni, vedere [Impostare le proprietà che diventano di sola lettura.](#SettingReadOnlyProperties)

 Nella tabella seguente vengono descritte alcune delle attività che è possibile eseguire utilizzando le proprietà `Ribbon` del controllo .

|Per questa attività:|Eseguire questa operazione:|
|--------------------|--------------|
|Nascondere o visualizzare un controllo.|Usare la proprietà Visible.|
|Abilitare o disabilitare un controllo.|Usare la proprietà Enabled.|
|Impostare le dimensioni di un controllo .|Usare la proprietà ControlSize.|
|Ottiene l'immagine visualizzata in un controllo .|Usare la proprietà Image.|
|Modificare l'etichetta di un controllo.|Usare la proprietà Label.|
|Aggiungere dati definiti dall'utente a un controllo .|Usare la proprietà Tag.|
|Ottenere gli elementi in <xref:Microsoft.Office.Tools.Ribbon.RibbonBox> un oggetto , , <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> o<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> Controllo.|Usare la proprietà Items.|
|Aggiungere elementi a <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> un controllo , o <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Usare la proprietà Items.|
|Aggiungere controlli a un oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> .|Usare la proprietà Items.<br /><br /> Per aggiungere controlli a dopo il caricamento della barra multifunzione nell'applicazione Office, è necessario impostare la proprietà su true prima che la barra multifunzione venga caricata <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> nell'applicazione Office.  Per informazioni, vedere [Impostare le proprietà che diventano di sola lettura.](#SettingReadOnlyProperties)|
|Ottiene l'elemento selezionato di un oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> ,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Usare la proprietà SelectedItem. Per un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> oggetto , usare la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> .|
|Ottenere i gruppi in un oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonTab> .|Usare la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|
|Consente di specificare il numero di righe e colonne visualizzate in un oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Usare le <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> e .|

## <a name="set-properties-that-become-read-only"></a><a name="SettingReadOnlyProperties"></a> Impostare proprietà che diventano di sola lettura
 Alcune proprietà possono essere impostate solo prima del caricamento della barra multifunzione. È possibile impostare queste proprietà in tre posizioni:

- Nella finestra Visual Studio **proprietà.**

- Nel costruttore della **classe Ribbon.**

- Nel `CreateRibbonExtensibilityObject` metodo della `ThisAddin` classe , o `ThisWorkbook` del `ThisDocument` progetto.

  I menu dinamici forniscono alcune eccezioni. È possibile creare nuovi controlli, impostarne le proprietà e quindi aggiungerli a un menu dinamico in fase di esecuzione, anche dopo il caricamento della barra multifunzione che contiene il menu.

  Le proprietà dei controlli aggiunti a un menu dinamico possono essere impostate in qualsiasi momento.

  Per altre informazioni, vedere [Proprietà che diventano di sola lettura.](#ReadOnlyProperties)

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Impostare le proprietà nel costruttore della barra multifunzione
 È possibile impostare le proprietà di `Ribbon` un controllo nel costruttore della classe **Ribbon.** Questo codice deve essere visualizzato dopo la chiamata al `InitializeComponent` metodo . Nell'esempio seguente viene aggiunto un nuovo pulsante a un gruppo se l'ora corrente è 17:00 Pacific Time (UTC-8) o successiva.

 Aggiungere il codice seguente.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb" id="Snippet1":::

 Nei progetti Visual C# aggiornati da Visual Studio 2008, il costruttore viene visualizzato nel file di codice della barra multifunzione.

 Nei Visual Basic o nei progetti Visual C# creati in , il costruttore viene visualizzato nel file di codice della finestra di [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] progettazione della barra multifunzione. Questo file è denominato *YourRibbonItem.* Designer.cs o *YourRibbonItem.* Designer.vb. Per visualizzare questo file nei Visual Basic, è necessario fare clic sul pulsante **Mostra** tutti i file in Esplora soluzioni.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Impostare le proprietà nel metodo CreateRibbonExtensibilityObject
 È possibile impostare le proprietà di un `Ribbon` controllo quando si esegue l'override del metodo nella classe , o del `CreateRibbonExtensibilityObject` `ThisAddin` `ThisWorkbook` `ThisDocument` progetto. Per altre informazioni sul metodo `CreateRibbonExtensibilityObject` , vedere Cenni [preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).

 Nell'esempio seguente vengono impostate le proprietà della barra multifunzione nel metodo della classe di `CreateRibbonExtensibilityObject` un progetto Excel cartella di `ThisWorkbook` lavoro.

 Aggiungere il codice seguente.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs" id="Snippet2":::

### <a name="properties-that-become-read-only"></a><a name="ReadOnlyProperties"></a> Proprietà che diventano di sola lettura
 La tabella seguente illustra le proprietà che possono essere impostate solo prima del caricamento della barra multifunzione.

> [!NOTE]
> È possibile impostare le proprietà dei controlli nei menu dinamici in qualsiasi momento. Questa tabella non è applicabile in questo caso.

|Proprietà|Classe di controllo Della barra multifunzione|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Buttontype**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Columncount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Controlid**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Dinamico**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Gruppi**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Nome**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**Position**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Rowcount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Startfromscratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Schede**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Title**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Impostare le proprietà per le barre multifunzione visualizzate Outlook controlli
 Viene creata una nuova istanza della barra multifunzione ogni volta che un utente apre un controllo in cui viene visualizzata la barra multifunzione. Tuttavia, è possibile impostare le proprietà elencate nella tabella precedente solo prima della creazione della prima istanza della barra multifunzione. Dopo la creazione della prima istanza, queste proprietà diventano di sola lettura perché la prima istanza definisce il file XML Outlook per caricare la barra multifunzione.

 Se si dispone di logica condizionale che imposta una di queste proprietà su un valore diverso quando vengono create altre istanze della barra multifunzione, questo codice non avrà alcun effetto.

> [!NOTE]
> Assicurarsi che la **proprietà Name** sia impostata per ogni controllo aggiunto a un Outlook barra multifunzione. Se si aggiunge un controllo a una barra multifunzione Outlook in fase di esecuzione, è necessario impostare questa proprietà nel codice. Se si aggiunge un controllo a una barra Outlook in fase di progettazione, la proprietà Name viene impostata automaticamente.

## <a name="ribbon-control-events"></a>Eventi del controllo barra multifunzione
 Ogni classe di controllo contiene uno o più eventi. Nella tabella seguente vengono descritti questi eventi.

|Event|Descrizione|
|-----------|-----------------|
|Fare clic su|Si verifica quando si fa clic su un controllo .|
|Textchanged|Si verifica quando viene modificato il testo di una casella di modifica o di una casella combinata.|
|Caricamento di elementi|Si verifica quando la raccolta Items del controllo viene richiesta da Office. Office memorizza nella cache la raccolta Items fino a quando il codice non modifica le proprietà del controllo o non si chiama il <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> metodo .|
|Buttonclick|Si verifica quando si fa clic su un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> pulsante in o <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> .|
|SelectionChanged|Si verifica quando la selezione in un <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> oggetto o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> viene modificata.|
|DialogLauncherClick|Si verifica quando si fa clic sull'icona di avvio della finestra di dialogo nell'angolo inferiore destro di un gruppo.|

 I gestori eventi per questi eventi hanno i due parametri seguenti.

|Parametro|Descrizione|
|---------------|-----------------|
|*Mittente*|Un oggetto <xref:System.Object> che rappresenta il controllo che ha generato l'evento.|
|*e*|Oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> che contiene <xref:Microsoft.Office.Core.IRibbonControl>. Usare questo controllo per accedere a qualsiasi proprietà non disponibile nel modello a oggetti della barra multifunzione fornito da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|

## <a name="see-also"></a>Vedi anche
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Procedura: Iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: Aggiornare i controlli in una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)
- [Procedura: Aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione al codice XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)
