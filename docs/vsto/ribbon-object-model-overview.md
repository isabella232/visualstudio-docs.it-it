---
title: Panoramica del modello a oggetti della barra multifunzione
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6ca22704345fefb4944bda7dd9f71942fe8dfb50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "71256021"
---
# <a name="ribbon-object-model-overview"></a>Panoramica del modello a oggetti della barra multifunzione
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Espone un modello a oggetti fortemente tipizzato che è possibile utilizzare per ottenere e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione. Ad esempio, è possibile popolare in modo dinamico i controlli menu o mostrare e nascondere i controlli in modo contestuale. È anche possibile aggiungere schede, gruppi e controlli a una barra multifunzione, ma solo prima che la barra multifunzione venga caricata dall'applicazione di Office. Per informazioni, vedere [impostare le proprietà che diventano](#SettingReadOnlyProperties)di sola lettura.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Questo modello a oggetti della barra multifunzione è costituito principalmente dalla [classe Ribbon](#RibbonClass), dagli [Eventi Ribbon](#RibbonEvents)e dalle [classi del controllo Ribbon](#RibbonControlClasses).

## <a name="ribbon-class"></a><a name="RibbonClass"></a> Ribbon (classe)
 Quando si aggiunge un nuovo elemento della **barra multifunzione (finestra di progettazione visiva)** a un progetto, Visual Studio aggiunge una classe **Ribbon** al progetto. La classe **Ribbon** eredita dalla <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> classe.

 Questa classe viene visualizzata come classe parziale divisa tra il file di codice della barra multifunzione e il file di codice della finestra di progettazione della barra multifunzione.

## <a name="ribbon-events"></a><a name="RibbonEvents"></a> Eventi della barra multifunzione
 La classe **Ribbon** contiene i tre eventi seguenti:

|Event|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Generato quando l'applicazione di Office carica la personalizzazione della barra multifunzione. Il <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> gestore eventi viene aggiunto automaticamente al file di codice della barra multifunzione. Utilizzare questo gestore eventi per eseguire codice personalizzato quando la barra multifunzione viene caricata.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Consente di memorizzare nella cache le immagini nella personalizzazione della barra multifunzione quando la barra multifunzione viene caricata. È possibile ottenere un lieve miglioramento delle prestazioni se si scrive codice per memorizzare nella cache le immagini della barra multifunzione in questo gestore eventi. Per altre informazioni, vedere <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Generato quando l'istanza della barra multifunzione viene chiusa.|

## <a name="ribbon-controls"></a><a name="RibbonControlClasses"></a> Controlli della barra multifunzione
 Lo <xref:Microsoft.Office.Tools.Ribbon> spazio dei nomi contiene un tipo per ogni controllo visualizzato nel gruppo **controlli della barra multifunzione di Office** della **casella degli strumenti**.

 La tabella seguente illustra il tipo per ogni `Ribbon` controllo. Per una descrizione di ogni controllo, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).

|Nome del controllo|Nome di classe|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**Casella**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Raccolta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Gruppo**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Etichetta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Separatore**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Scheda**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 Lo <xref:Microsoft.Office.Tools.Ribbon> spazio dei nomi utilizza il prefisso "Ribbon" per questi tipi per evitare un conflitto di nome con i nomi delle classi del controllo nello <xref:System.Windows.Forms> spazio dei nomi.

 Quando si aggiunge un controllo alla finestra di progettazione della barra multifunzione, la finestra di progettazione della barra multifunzione dichiara la classe per il controllo come campo nel file di codice della finestra di progettazione della barra multifunzione.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Attività comuni mediante le proprietà dei controlli della barra multifunzione
 Ogni `Ribbon` controllo contiene proprietà che è possibile usare per eseguire varie attività, ad esempio l'assegnazione di un'etichetta a un controllo o l'occultamento e la visualizzazione di controlli.

 In alcuni casi, le proprietà diventano di sola lettura dopo il caricamento della barra multifunzione o dopo l'aggiunta di un controllo a un menu dinamico. Per altre informazioni, vedere [impostare le proprietà che diventano di sola lettura](#SettingReadOnlyProperties).

 Nella tabella seguente vengono descritte alcune attività che è possibile eseguire tramite le `Ribbon` proprietà del controllo.

|Per questa attività:|Eseguire questa operazione:|
|--------------------|--------------|
|Nascondere o visualizzare un controllo.|Utilizzare la proprietà Visible.|
|Abilitare o disabilitare un controllo.|Utilizzare la proprietà Enabled.|
|Impostare la dimensione di un controllo.|Usare la proprietà ControlSize.|
|Ottiene l'immagine visualizzata in un controllo.|Usare la proprietà Image.|
|Modificare l'etichetta di un controllo.|Utilizzare la proprietà Label.|
|Aggiungere i dati definiti dall'utente a un controllo.|Usare la proprietà Tag.|
|Ottenere gli elementi in un oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonBox> ,, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> o<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> controllo.|Utilizzare la proprietà Items.|
|Aggiungere elementi a un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> controllo, o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Utilizzare la proprietà Items.|
|Aggiungere i controlli a un <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> .|Utilizzare la proprietà Items.<br /><br /> Per aggiungere controlli al <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> dopo che la barra multifunzione è stata caricata nell'applicazione di Office, è necessario impostare la <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> proprietà su **true** prima che la barra multifunzione venga caricata nell'applicazione di Office. Per informazioni, vedere [impostare le proprietà che diventano](#SettingReadOnlyProperties)di sola lettura.|
|Ottiene l'elemento selezionato di un oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> ,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Utilizzare la proprietà SelectedItem. Per un oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> , usare la <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> Proprietà.|
|Ottenere i gruppi in un oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonTab> .|Usare la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|
|Consente di specificare il numero di righe e colonne visualizzate in un oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Usare le <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> proprietà e.|

## <a name="set-properties-that-become-read-only"></a><a name="SettingReadOnlyProperties"></a> Impostare le proprietà che diventano di sola lettura
 Alcune proprietà possono essere impostate solo prima del caricamento della barra multifunzione. Sono disponibili tre posizioni per impostare queste proprietà:

- Nella finestra **Proprietà** di Visual Studio.

- Nel costruttore della classe **Ribbon** .

- Nel `CreateRibbonExtensibilityObject` metodo della `ThisAddin` `ThisWorkbook` classe, o `ThisDocument` del progetto.

  I menu dinamici forniscono alcune eccezioni. È possibile creare nuovi controlli, impostarne le proprietà e quindi aggiungerli a un menu dinamico in fase di esecuzione, anche dopo che la barra multifunzione che contiene il menu è stata caricata.

  Le proprietà dei controlli aggiunti a un menu dinamico possono essere impostate in qualsiasi momento.

  Per ulteriori informazioni, vedere [proprietà che diventano](#ReadOnlyProperties)di sola lettura.

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Impostare le proprietà nel costruttore della barra multifunzione
 È possibile impostare le proprietà di un `Ribbon` controllo nel costruttore della classe **Ribbon** . Questo codice deve essere visualizzato dopo la chiamata al `InitializeComponent` metodo. Nell'esempio seguente viene aggiunto un nuovo pulsante a un gruppo se l'ora corrente è 17:00 Pacific Time (UTC-8) o versione successiva.

 Aggiungere il codice seguente.

 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]

 Nei progetti Visual C# aggiornati da Visual Studio 2008, il costruttore viene visualizzato nel file di codice della barra multifunzione.

 Nei progetti Visual Basic o nei progetti Visual C# creati in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , il costruttore viene visualizzato nel file di codice della finestra di progettazione della barra multifunzione. Questo file è denominato *ElementoBarraMultifunzione*. Designer.cs o *ElementoBarraMultifunzione*. Designer. vb. Per visualizzare questo file in Visual Basic progetti, è necessario prima fare clic sul pulsante **Mostra tutti i file** in Esplora soluzioni.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Impostare le proprietà nel metodo CreateRibbonExtensibilityObject
 È possibile impostare le proprietà di un `Ribbon` controllo quando si esegue l'override del `CreateRibbonExtensibilityObject` metodo `ThisAddin` nella `ThisWorkbook` classe, o `ThisDocument` del progetto. Per ulteriori informazioni sul `CreateRibbonExtensibilityObject` metodo, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).

 Nell'esempio seguente vengono impostate le proprietà della barra multifunzione nel `CreateRibbonExtensibilityObject` metodo della `ThisWorkbook` classe di un progetto di cartella di lavoro di Excel.

 Aggiungere il codice seguente.

 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]

### <a name="properties-that-become-read-only"></a><a name="ReadOnlyProperties"></a> Proprietà che diventano di sola lettura
 Nella tabella seguente vengono illustrate le proprietà che è possibile impostare solo prima del caricamento della barra multifunzione.

> [!NOTE]
> È possibile impostare le proprietà dei controlli nei menu dinamici in qualsiasi momento. Questa tabella non è applicabile in questo caso.

|Proprietà|Classe del controllo Ribbon|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Dinamico**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Gruppi**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Name**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**Posizione**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**RowCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Schede**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Title**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Impostare le proprietà per le barre multifunzione visualizzate nei controlli di Outlook
 Una nuova istanza della barra multifunzione viene creata ogni volta che un utente apre un controllo in cui viene visualizzata la barra multifunzione. Tuttavia, è possibile impostare le proprietà elencate nella tabella precedente solo prima che venga creata la prima istanza della barra multifunzione. Una volta creata la prima istanza, queste proprietà diventano di sola lettura perché la prima istanza definisce il file XML utilizzato da Outlook per caricare la barra multifunzione.

 Se si dispone di una logica condizionale che imposta una di queste proprietà su un valore diverso quando vengono create altre istanze della barra multifunzione, questo codice non avrà alcun effetto.

> [!NOTE]
> Verificare che la proprietà **Name** sia impostata per ogni controllo aggiunto a una barra multifunzione di Outlook. Se si aggiunge un controllo a una barra multifunzione di Outlook in fase di esecuzione, è necessario impostare questa proprietà nel codice. Se si aggiunge un controllo a una barra multifunzione di Outlook in fase di progettazione, la proprietà Name viene impostata automaticamente.

## <a name="ribbon-control-events"></a>Eventi del controllo Ribbon
 Ogni classe del controllo contiene uno o più eventi. Nella tabella seguente vengono descritti questi eventi.

|Event|Descrizione|
|-----------|-----------------|
|Fare clic su|Si verifica quando si fa clic su un controllo.|
|TextChanged|Si verifica quando viene modificato il testo di una casella di modifica o di una casella combinata.|
|ItemsLoading|Si verifica quando la raccolta di elementi del controllo viene richiesta da Office. Office memorizza nella cache la raccolta Items fino a quando il codice non modifica le proprietà del controllo o si chiama il <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> metodo.|
|ButtonClick|Si verifica quando <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> si fa clic su un pulsante in un oggetto o.|
|SelectionChanged|Si verifica in seguito alla modifica della selezione in un oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|
|DialogLauncherClick|Si verifica quando si fa clic sull'icona dell'utilità di avvio della finestra di dialogo nell'angolo inferiore destro di un gruppo.|

 I gestori eventi per questi eventi presentano i due parametri seguenti.

|Parametro|Descrizione|
|---------------|-----------------|
|*mittente*|Un oggetto <xref:System.Object> che rappresenta il controllo che ha generato l'evento.|
|*e*|Oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> che contiene <xref:Microsoft.Office.Core.IRibbonControl>. Utilizzare questo controllo per accedere a qualsiasi proprietà non disponibile nel modello a oggetti della barra multifunzione fornito da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|

## <a name="see-also"></a>Vedere anche
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Procedura dettagliata: creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: aggiornare i controlli in una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)
- [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Procedura: esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione a XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Procedura: visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)
