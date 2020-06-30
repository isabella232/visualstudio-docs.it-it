---
title: Associare controlli WPF ai dati (parte 1) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 25b144409ae58f006602706a5b5cb498c0535ea2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540166"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Associare controlli WPF ai dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile visualizzare i dati per gli utenti dell'applicazione mediante l'associazione dei dati ai controlli [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)]. Per creare questi controlli associati a dati, è possibile trascinare gli elementi dalla finestra **origini dati** [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . In questo argomento vengono descritte alcune delle più comuni attività, strumenti e classi che è possibile utilizzare per creare applicazioni [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] associate a dati.

 Per informazioni generali su come creare controlli associati a dati in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Per altre informazioni sul data binding di [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)], vedere [Panoramica sul data binding](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Attività coinvolte nell'associazione di controlli WPF a dati
 Nella tabella seguente vengono elencate le attività che possono essere eseguite trascinando gli elementi dalla finestra **Origini dati** a [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)].

|Attività|Ulteriori informazioni|
|----------|----------------------|
|Creare nuovi controlli associati a dati.<br /><br /> Associare controlli esistenti a dati.|[Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [associare controlli WPF a un DataSet](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Creare controlli che visualizzano i dati correlati in una relazione padre-figlio: quando l'utente seleziona un record di dati padre in un controllo, un altro controllo visualizza i dati figlio correlati per il record selezionato.|[Visualizzare dati correlati in applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Creare una *tabella di ricerca* che consente di visualizzare le informazioni contenute in una tabella in base al valore di un campo della chiave esterna in un'altra tabella.|[Creare tabelle di ricerca in applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Associare un controllo a un'immagine di un database.|[Associare controlli alle immagini di un database](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Obiettivi di rilascio validi
 È possibile trascinare gli elementi della finestra **Origini dati** solo in obiettivi di rilascio validi in [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)]. Esistono due tipi principali di destinazioni di rilascio valide: contenitori e controlli. Un contenitore è un elemento dell'interfaccia utente che in genere contiene i controlli. Una griglia e una finestra, ad esempio, sono contenitori.

## <a name="generated-xaml-and-code"></a>Codice e XAML generati
 Quando si trascina un elemento dalla finestra **origini dati** a [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] , [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] che definisce un nuovo controllo associato a dati (o associa un controllo esistente all'origine dati). Per alcune origini dati, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera anche il codice nel file code-behind che inserisce i dati nell'origine dati.

 Nella tabella seguente sono elencati i [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] codici e [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generati da per ogni tipo di origine dati nella finestra **origini dati** .

|Origine dati|Generazione di XAML per l'associazione di un controllo all'origine dati|Generazione di codice per l'inserimento dei dati nell'origine dati|
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|
|Set di dati|Sì|Sì|
|[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]|Sì|Sì|
|Servizio|Sì|No|
|Oggetto|Sì|No|

### <a name="datasets"></a>Set di dati
 Quando si trascina una tabella o una colonna dalla finestra **origini dati** alla finestra di progettazione, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] che esegue le operazioni seguenti:

- Aggiunge il dataset e un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nel dataset.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, XAML associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, il codice XAML crea il controllo selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]apporta inoltre le modifiche seguenti al file code-behind:

- Crea un gestore dell'evento <xref:System.Windows.FrameworkElement.Loaded> per l'elemento [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] contenente il controllo. Il gestore dell'evento inserisce i dati nella tabella, recupera l'oggetto <xref:System.Windows.Data.CollectionViewSource> dalle risorse del contenitore, quindi imposta come elemento corrente il primo elemento di dati. Se un <xref:System.Windows.FrameworkElement.Loaded> gestore eventi esiste già, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aggiunge questo codice al gestore eventi esistente.

### <a name="entity-data-models"></a>Entity Data Model
 Quando si trascina un'entità o una proprietà dell'entità dalla finestra **origini dati** alla finestra di progettazione, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] che esegue le operazioni seguenti:

- Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'entità.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, il [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] Crea il controllo selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

  Visual Studio apporta inoltre le modifiche seguenti al file code-behind:

- Aggiunge un nuovo metodo che restituisce una query per l'entità trascinata nella finestra di progettazione (o per l'entità contenente la proprietà trascinata nella finestra di progettazione). Il nome del nuovo metodo è Get*EntityName*query, dove *EntityName* è il nome dell'entità.

- Crea un gestore dell'evento <xref:System.Windows.FrameworkElement.Loaded> per l'elemento [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] contenente il controllo. Il gestore eventi chiama il metodo di query Get*EntityName*per inserire i dati nell'entità, recupera l'oggetto <xref:System.Windows.Data.CollectionViewSource> dalle risorse del contenitore, quindi rende il primo elemento di dati l'elemento corrente. Se un <xref:System.Windows.FrameworkElement.Loaded> gestore eventi esiste già, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aggiunge questo codice al gestore eventi esistente.

### <a name="services"></a>Servizi
 Quando si trascina un oggetto servizio o una proprietà dalla finestra **origini dati** alla finestra di progettazione, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] che crea un controllo con associazione a dati (o associa un controllo esistente all'oggetto o alla proprietà). [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], tuttavia, non genera il codice che inserisce i dati nell'oggetto servizio del proxy. È necessario scrivere questo codice manualmente. Per un esempio in cui viene illustrato come eseguire questa operazione, vedere [associare controlli WPF a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

 Visual Studio genera XAML che esegue le operazioni seguenti:

- Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'oggetto restituito dal servizio.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, il [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] Crea il controllo selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Oggetti
 Quando si trascina un oggetto o una proprietà dalla finestra **origini dati** alla finestra di progettazione, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] che crea un controllo con associazione a dati (o associa un controllo esistente all'oggetto o alla proprietà). [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], tuttavia, non genera il codice per inserire i dati nell'oggetto. È necessario scrivere questo codice manualmente.

> [!NOTE]
> Le classi personalizzate devono essere pubbliche e, per impostazione predefinita, hanno un costruttore senza parametri. Non possono essere classi annidate con "punto" nella sintassi. Per ulteriori informazioni, vedere [XAML e classi personalizzate per WPF](https://msdn.microsoft.com/library/e7313137-581e-4a64-8453-d44e15a6164a).

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]genera [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] che esegue le operazioni seguenti:

- Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'oggetto.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, XAML associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, il codice XAML crea il controllo selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Vedere anche
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
