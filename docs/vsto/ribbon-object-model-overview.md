---
title: Panoramica del modello a oggetti della barra multifunzione
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e8c0e18146361cfbe89433d79962afcb89de3061
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961309"
---
# <a name="ribbon-object-model-overview"></a>Panoramica del modello a oggetti della barra multifunzione
  Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] espone un modello a oggetti fortemente tipizzati che è possibile usare per ottenere e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione. Ad esempio, è possibile in modo dinamico popola i controlli menu, o mostrare e nascondere controlli in base al contesto. È anche possibile aggiungere schede, gruppi e controlli a una barra multifunzione, ma solo prima della barra multifunzione viene caricata dall'applicazione di Office. Per informazioni, vedere [impostare le proprietà che diventano di sola lettura](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Questo modello a oggetti della barra multifunzione è costituito principalmente il [classe Ribbon](#RibbonClass), [sulla barra multifunzione eventi](#RibbonEvents), e [classi dei controlli della barra multifunzione](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a> Classe Ribbon  
 Quando si aggiunge un nuovo **sulla barra multifunzione (finestra di progettazione visiva)** voce a un progetto, Visual Studio aggiunge un **della barra multifunzione** classe al progetto. Il **sulla barra multifunzione** classe eredita dal <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> classe.  
  
 Questa classe viene visualizzata come una classe parziale che viene suddivisa tra file di codice della barra multifunzione e il file di codice di progettazione della barra multifunzione.  
  
##  <a name="RibbonEvents"></a> Eventi della barra multifunzione  
 Il **sulla barra multifunzione** classe contiene i seguenti tre eventi:  
  
|event|Descrizione|  
|-----------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Generato quando l'applicazione di Office viene caricata la personalizzazione della barra multifunzione. Il <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> gestore eventi viene aggiunto automaticamente al file di codice della barra multifunzione. Utilizzare questo gestore eventi per eseguire il codice personalizzato al caricamento della barra multifunzione.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Consente di memorizzare nella cache immagini la personalizzazione della barra multifunzione al caricamento della barra multifunzione. Se si scrive codice per memorizzare nella cache le immagini della barra multifunzione in questo gestore eventi, è possibile ottenere un lieve aumento delle prestazioni. Per altre informazioni, vedere <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Generato quando si chiude l'istanza della barra multifunzione.|  
  
##  <a name="RibbonControlClasses"></a> Controlli della barra multifunzione  
 Il <xref:Microsoft.Office.Tools.Ribbon> dello spazio dei nomi contiene un tipo per ogni controllo contenuto nel **controlli della barra multifunzione di Office** gruppo o il **casella degli strumenti**.  
  
 Nella tabella seguente mostra il tipo per ogni `Ribbon` controllo. Per una descrizione di ogni controllo, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).  
  
|Nome controllo|Nome di classe|  
|------------------|----------------|  
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Pulsante**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**Gruppo di pulsanti.**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**Elenco a discesa**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**Casella di modifica**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Gallery**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Gruppo**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Etichetta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separatore**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**TAB**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 Il <xref:Microsoft.Office.Tools.Ribbon> dello spazio dei nomi Usa il prefisso "Ribbon" per questi tipi per evitare un conflitto di nomi con i nomi delle classi di controlli nel <xref:System.Windows.Forms> dello spazio dei nomi.  
  
 Quando si aggiunge un controllo alla finestra di progettazione della barra multifunzione, la finestra di progettazione della barra multifunzione dichiara la classe per il controllo come un campo nel file di codice di progettazione della barra multifunzione.  
  
### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Attività comuni usando le proprietà dei controlli della barra multifunzione  
 Ogni `Ribbon` controllo contiene proprietà che è possibile usare per eseguire diverse attività, ad esempio l'assegnazione di un'etichetta a un controllo, o nascondere e visualizzare i controlli.  
  
 In alcuni casi, le proprietà diventano di sola lettura dopo il caricamento della barra multifunzione o dopo l'aggiunta di un controllo a un menu dinamico. Per altre informazioni, vedere [impostare le proprietà che diventano di sola lettura](#SettingReadOnlyProperties).  
  
 La tabella seguente descrive alcune delle attività che è possibile eseguire usando `Ribbon` proprietà del controllo.  
  
|Per questa attività:|Eseguire questa operazione:|  
|--------------------|--------------|  
|Nascondere o mostrare un controllo.|Usare la proprietà Visible.|  
|Abilitare o disabilitare un controllo.|Usare la proprietà Enabled.|  
|Impostare le dimensioni di un controllo.|Usare la proprietà ControlSize.|  
|Ottenere l'immagine visualizzata su un controllo.|Usare la proprietà dell'immagine.|  
|Modificare l'etichetta di un controllo.|Usare la proprietà dell'etichetta.|  
|Aggiungere dati definiti dall'utente a un controllo.|Usare i Tag (proprietà).|  
|Ottenere gli elementi in un <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>, o<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> controllo.|Usare la proprietà di elementi.|  
|Aggiungere elementi a un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> controllo.|Usare la proprietà di elementi.|  
|Aggiungere controlli a un <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Usare la proprietà di elementi.<br /><br /> Per aggiungere controlli per il <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> dopo che è stata caricata nell'applicazione Office, è necessario impostare il <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> proprietà **true** prima del caricamento della barra multifunzione nell'applicazione Office. Per informazioni, vedere [impostare le proprietà che diventano di sola lettura](#SettingReadOnlyProperties).|  
|Ottenere l'elemento selezionato di un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Usare la proprietà SelectedItem. Per un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, usare il <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> proprietà.|  
|Ottenere i gruppi in un <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Usare la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|  
|Specificare il numero di righe e colonne che vengono visualizzati in un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Usare la <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> e <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> proprietà.|  
  
##  <a name="SettingReadOnlyProperties"></a> Impostare le proprietà che diventano di sola lettura  
 Alcune proprietà possono essere impostate solo prima del caricamento della barra multifunzione. Ci sono tre posizioni per impostare queste proprietà:  
  
- In Visual Studio **proprietà** finestra.  
  
- Nel costruttore della **sulla barra multifunzione** classe.  
  
- Nel `CreateRibbonExtensibilityObject` metodo per il `ThisAddin`, `ThisWorkbook`, o `ThisDocument` classe del progetto.  
  
  Menu dinamici offrono alcune eccezioni. È possibile creare nuovi controlli, impostarne le proprietà e quindi aggiungerli a un menu dinamico in fase di esecuzione, anche dopo il caricamento della barra multifunzione che contiene il menu di scelta.  
  
  In qualsiasi momento, è possono impostare le proprietà dei controlli aggiunti a un menu dinamico.  
  
  Per altre informazioni, vedere [proprietà che diventano di sola lettura](#ReadOnlyProperties).  
  
### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Impostare le proprietà nel costruttore della barra multifunzione  
 È possibile impostare le proprietà di un `Ribbon` nel costruttore del controllo il **della barra multifunzione** classe. Questo codice deve essere visualizzato dopo la chiamata al `InitializeComponent` (metodo). L'esempio seguente aggiunge un nuovo pulsante a un gruppo se l'ora corrente è 17.00 fuso orario Pacifico (UTC-8) o versione successiva.  
  
 Aggiungere il codice seguente.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]  
  
 Nell'oggetto visivo C# progetti che è stato aggiornato da Visual Studio 2008, il costruttore viene visualizzato nel file di codice della barra multifunzione.  
  
 Nei progetti Visual Basic o nell'oggetto visivo C# progetti creati in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], il costruttore viene visualizzato nel file di codice di progettazione della barra multifunzione. Questo file è denominato *YourRibbonItem*. Designer.cs o *YourRibbonItem*. VB. Per visualizzare questo file nei progetti Visual Basic, è innanzitutto necessario scegliere il **Mostra tutti i file** pulsante in Esplora soluzioni.  
  
### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Impostare le proprietà nel metodo CreateRibbonExtensibilityObject  
 È possibile impostare le proprietà di un `Ribbon` controllare quando esegue l'override di `CreateRibbonExtensibilityObject` metodo nella `ThisAddin`, `ThisWorkbook`, o `ThisDocument` classe del progetto. Per altre informazioni sul `CreateRibbonExtensibilityObject` metodo, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).  
  
 Nell'esempio seguente imposta le proprietà della barra multifunzione nel `CreateRibbonExtensibilityObject` metodo di `ThisWorkbook` classe di un progetto cartella di lavoro di Excel.  
  
 Aggiungere il codice seguente.  
  
 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]  
  
###  <a name="ReadOnlyProperties"></a> Proprietà che diventano di sola lettura  
 La tabella seguente illustra le proprietà che possono essere impostate solo prima del caricamento della barra multifunzione.  
  
> [!NOTE]  
>  È possibile impostare le proprietà dei controlli nel menu dinamici in qualsiasi momento. Questa tabella non è applicabile in questo caso.  
  
|Proprietà|Classe del controllo della barra multifunzione|  
|--------------|--------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Numero colonne**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dinamica**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Gruppi**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Name**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**posizione**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Conteggio delle righe**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Schede**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Titolo**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Impostare le proprietà di barre multifunzione visualizzate nei controlli di Outlook  
 Ogni volta che un utente apre un controllo in cui viene visualizzata la barra multifunzione viene creata una nuova istanza della barra multifunzione. Tuttavia, è possibile impostare le proprietà elencate nella tabella precedente solo prima che venga creata la prima istanza della barra multifunzione. Dopo la prima istanza viene creata, queste proprietà diventano di sola lettura perché la prima istanza definisce il file XML usato da Outlook per caricare la barra multifunzione.  
  
 Se si dispone di logica condizionale che imposta una di queste proprietà su un valore diverso quando vengono create altre istanze della barra multifunzione, questo codice non avrà effetto.  
  
> [!NOTE]  
>  Verificare che il **nome** viene impostata per ogni controllo che aggiunge a una barra multifunzione di Outlook. Se si aggiunge un controllo a una barra multifunzione di Outlook in fase di esecuzione, è necessario impostare questa proprietà nel codice. Se si aggiunge un controllo a una barra multifunzione di Outlook in fase di progettazione, il nome viene impostata automaticamente.  
  
## <a name="ribbon-control-events"></a>Eventi di controllo della barra multifunzione  
 Ogni classe del controllo contiene uno o più eventi. Nella tabella seguente vengono descritti questi eventi.  
  
|event|Descrizione|  
|-----------|-----------------|  
|Clic|Si verifica quando viene selezionato un controllo.|  
|TextChanged|Si verifica quando viene modificato il testo di una casella di modifica o la casella combinata.|  
|ItemsLoading|Si verifica quando la raccolta di elementi del controllo viene richiesto da Office. Office vengono memorizzati nella cache la raccolta di elementi fino a quando il codice modifica le proprietà del controllo o si chiama il <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> (metodo).|  
|ButtonClick|Si verifica quando un pulsante in un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> o <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> si fa clic.|  
|Evento SelectionChanged|Si verifica quando la selezione in un <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> le modifiche.|  
|DialogLauncherClick|Si verifica quando viene selezionato l'icona di avvio delle finestra di dialogo nell'angolo inferiore destro di un gruppo.|  
  
 I gestori eventi per questi eventi sono i due parametri seguenti.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*Mittente*|Un <xref:System.Object> che rappresenta il controllo che ha generato l'evento.|  
|*e*|Oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> che contiene <xref:Microsoft.Office.Core.IRibbonControl>. Usare questo controllo per accedere a qualsiasi proprietà che non è disponibile nel modello a oggetti della barra multifunzione fornito dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|  
  
## <a name="see-also"></a>Vedere anche  
 [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Procedura: Introduzione alla personalizzazione della barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: Aggiornare i controlli in una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)   
 [Procedura: Aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Procedura: Mostra errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)  
