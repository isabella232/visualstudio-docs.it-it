---
title: Associare controlli WPF ai dati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 16a3868f564f39d4908adf74a6b1a44ae83ebc9d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437052"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Associare controlli WPF ai dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile visualizzare i dati per gli utenti dell'applicazione mediante l'associazione dei dati ai controlli [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)]. Per creare questi controlli con associazione a dati, è possibile trascinare elementi dal **Zdroje dat** finestra nelle [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. In questo argomento vengono descritte alcune delle più comuni attività, strumenti e classi che è possibile utilizzare per creare applicazioni [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] associate a dati.

 Per informazioni generali su come creare controlli associati a dati in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Per altre informazioni sul data binding di [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)], vedere [Panoramica sul data binding](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Attività coinvolte nell'associazione di controlli WPF a dati
 Nella tabella seguente vengono elencate le attività che possono essere eseguite trascinando gli elementi dalla finestra **Origini dati** a [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)].

|Attività|Altre informazioni|
|----------|----------------------|
|Creare nuovi controlli associati a dati.<br /><br /> Associare controlli esistenti a dati.|[Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [WPF di associare controlli a un set di dati](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Creare controlli che visualizzano i dati correlati in una relazione padre-figlio: quando l'utente seleziona un record di dati padre in un controllo, un altro controllo visualizza i dati figlio correlati per il record selezionato.|[Visualizzare dati correlati in applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Creare una *tabella di ricerca* che consente di visualizzare le informazioni contenute in una tabella in base al valore di un campo della chiave esterna in un'altra tabella.|[Creare tabelle di ricerca in applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Associare un controllo a un'immagine di un database.|[Associare controlli alle immagini di un database](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Obiettivi di rilascio validi
 È possibile trascinare gli elementi della finestra **Origini dati** solo in obiettivi di rilascio validi in [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)]. Esistono due tipi principali di destinazioni di rilascio valide: contenitori e controlli. Un contenitore è un elemento dell'interfaccia utente che in genere contiene i controlli. Una griglia e una finestra, ad esempio, sono contenitori.

## <a name="generated-xaml-and-code"></a>Codice e XAML generati
 Quando si trascina un elemento dal **Zdroje dat** finestra per il [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)], [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] che definisce un nuovo controllo associato a dati (o associa un controllo esistente all'origine dati). Per alcune origini dati, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera anche il codice nel file code-behind che inserisce i dati nell'origine dati.

 La tabella seguente elenca i [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] e il codice [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera per ogni tipo di origine dati nel **Zdroje dat** finestra.

|Origine dati|Generazione di XAML per l'associazione di un controllo all'origine dati|Generazione di codice per l'inserimento dei dati nell'origine dati|
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|
|Set di dati|Yes|Yes|
|[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]|Yes|Yes|
|Service|Yes|No|
|Object|Yes|No|

### <a name="datasets"></a>Dataset
 Quando si trascina una tabella o una colonna dal **Zdroje dat** finestra di progettazione, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] che esegue le operazioni seguenti:

- Aggiunge il dataset e un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nel dataset.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, XAML associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, il XAML crea il controllo che è stato selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] apporta inoltre le modifiche seguenti al file code-behind:

- Crea un gestore dell'evento <xref:System.Windows.FrameworkElement.Loaded> per l'elemento [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] contenente il controllo. Il gestore dell'evento inserisce i dati nella tabella, recupera l'oggetto <xref:System.Windows.Data.CollectionViewSource> dalle risorse del contenitore, quindi imposta come elemento corrente il primo elemento di dati. Se un <xref:System.Windows.FrameworkElement.Loaded> gestore dell'evento esiste già, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aggiunge questo codice al gestore dell'evento esistente.

### <a name="entity-data-models"></a>Entity Data Model
 Quando si trascina un'entità o una proprietà dell'entità dal **Zdroje dat** finestra di progettazione, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] che esegue le operazioni seguenti:

- Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'entità.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, il [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] crea il controllo che è stato selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

  Visual Studio apporta inoltre le modifiche seguenti al file code-behind:

- Aggiunge un nuovo metodo che restituisce una query per l'entità trascinata nella finestra di progettazione (o per l'entità contenente la proprietà trascinata nella finestra di progettazione). Il nuovo metodo è Get*EntityName*Query, dove *EntityName* è il nome dell'entità.

- Crea un gestore dell'evento <xref:System.Windows.FrameworkElement.Loaded> per l'elemento [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] contenente il controllo. Il gestore eventi chiama Get*EntityName*metodo per inserire i dati, recupera le entità di Query di <xref:System.Windows.Data.CollectionViewSource> da risorse del contenitore, quindi rende i primo elemento di dati dell'elemento corrente. Se un <xref:System.Windows.FrameworkElement.Loaded> gestore dell'evento esiste già, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aggiunge questo codice al gestore dell'evento esistente.

### <a name="services"></a>Servizi
 Quando si trascina un oggetto servizio o a una proprietà di **Zdroje dat** finestra di progettazione, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] che crea un controllo con associazione a dati (o associa un controllo esistente all'oggetto o una proprietà). [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], tuttavia, non genera il codice che inserisce i dati nell'oggetto servizio del proxy. È necessario scrivere questo codice manualmente. Per un esempio che illustra come eseguire questa operazione, vedere [WPF di associare controlli a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

 Visual Studio genera XAML che esegue le operazioni seguenti:

- Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'oggetto restituito dal servizio.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, il [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] crea il controllo che è stato selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Oggetti
 Quando si trascina un oggetto o a una proprietà di **Zdroje dat** finestra di progettazione, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] che crea un controllo con associazione a dati (o associa un controllo esistente all'oggetto o una proprietà). [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], tuttavia, non genera il codice per inserire i dati nell'oggetto. È necessario scrivere questo codice manualmente.

> [!NOTE]
> Devono essere pubblico e delle classi personalizzate, per impostazione predefinita, dispone di un costruttore senza parametri. Non possono essere classi annidate che hanno un "punto" nella relativa sintassi. Per altre informazioni, vedere [XAML e classi personalizzate per WPF](http://msdn.microsoft.com/library/e7313137-581e-4a64-8453-d44e15a6164a).

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Genera l'errore [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] che esegue le operazioni seguenti:

- Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'oggetto.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, XAML associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, il XAML crea il controllo che è stato selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Vedere anche
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
