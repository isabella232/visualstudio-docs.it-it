---
title: Associare controlli WPF ai dati - parte 1
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0d1769440ea72ff477ac78230f2c7c1bb71b5ace
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816277"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Associare controlli WPF ai dati in Visual Studio

È possibile visualizzare i dati per gli utenti dell'applicazione mediante l'associazione dei dati ai controlli [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]. Per creare questi controlli con associazione a dati, è possibile trascinare elementi dal **Zdroje dat** finestra nel [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] in Visual Studio. In questo argomento vengono descritte alcune delle più comuni attività, strumenti e classi che è possibile utilizzare per creare applicazioni [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] associate a dati.

Per informazioni generali su come creare controlli associati a dati in Visual Studio, vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Per altre informazioni sul data binding di [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)], vedere [Panoramica sul data binding](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Attività coinvolte nell'associazione di controlli WPF a dati

Nella tabella seguente vengono elencate le attività che possono essere eseguite trascinando gli elementi dalla finestra **Origini dati** a [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].

|Attività|Altre informazioni|
|----------| - |
|Creare nuovi controlli associati a dati.<br /><br /> Associare controlli esistenti a dati.|[Associare controlli WPF a un set di dati](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Creare controlli che visualizzano i dati correlati in una relazione padre-figlio: quando l'utente seleziona un record di dati padre in un controllo, un altro controllo visualizza i dati figlio correlati per il record selezionato.|[Visualizzare dati correlati in applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Creare una *tabella di ricerca* che consente di visualizzare le informazioni contenute in una tabella in base al valore di un campo della chiave esterna in un'altra tabella.|[Creare tabelle di ricerca in applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Associare un controllo a un'immagine di un database.|[Associare controlli alle immagini di un database](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Obiettivi di rilascio validi

È possibile trascinare gli elementi della finestra **Origini dati** solo in obiettivi di rilascio validi in [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. Esistono due tipi principali di destinazioni di rilascio valide: contenitori e controlli. Un contenitore è un elemento dell'interfaccia utente che in genere contiene i controlli. Una griglia e una finestra, ad esempio, sono contenitori.

## <a name="generated-xaml-and-code"></a>Codice e XAML generati

Quando si trascina un elemento dal **Zdroje dat** finestra per il [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], Visual Studio genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] che definisce un nuovo controllo associato a dati (o associa un controllo esistente all'origine dati). Per alcune origini dati, Visual Studio genera il codice nel file code-behind che inserisce i dati nell'origine dati.

La tabella seguente elenca i [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] e il codice generato da Visual Studio per ogni tipo di origine dati nel **Zdroje dat** finestra.

| Origine dati | Generazione di XAML per l'associazione di un controllo all'origine dati | Generazione di codice per l'inserimento dei dati nell'origine dati |
| - | - | - |
| Set di dati | Yes | Yes |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | Yes | Yes |
| Service | Yes | No |
| Object | Yes | No |

### <a name="datasets"></a>Dataset

Quando si trascina una tabella o una colonna dal **Zdroje dat** finestra di progettazione, Visual Studio genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] che esegue le operazioni seguenti:

- Aggiunge il dataset e un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nel dataset.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, XAML associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, il XAML crea il controllo che è stato selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

Visual Studio apporta inoltre le modifiche seguenti al file code-behind:

- Crea un gestore dell'evento <xref:System.Windows.FrameworkElement.Loaded> per l'elemento [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] contenente il controllo. Il gestore dell'evento inserisce i dati nella tabella, recupera l'oggetto <xref:System.Windows.Data.CollectionViewSource> dalle risorse del contenitore, quindi imposta come elemento corrente il primo elemento di dati. Se un <xref:System.Windows.FrameworkElement.Loaded> gestore eventi esiste già, Visual Studio aggiunge questo codice al gestore dell'evento esistente.

### <a name="entity-data-models"></a>Entity Data Model

Quando si trascina un'entità o una proprietà dell'entità dal **Zdroje dat** finestra di progettazione, Visual Studio genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] che esegue le operazioni seguenti:

- Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'entità.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, il [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crea il controllo che è stato selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

Visual Studio apporta inoltre le modifiche seguenti al file code-behind:

- Aggiunge un nuovo metodo che restituisce una query per l'entità trascinata nella finestra di progettazione (o per l'entità contenente la proprietà trascinata nella finestra di progettazione). Il nuovo metodo con il nome `Get<EntityName>Query`, dove `\<EntityName>` è il nome dell'entità.

- Crea un gestore dell'evento <xref:System.Windows.FrameworkElement.Loaded> per l'elemento [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] contenente il controllo. Chiamate del gestore eventi di `Get<EntityName>Query` per inserire l'entità di dati, che consente di recuperare il <xref:System.Windows.Data.CollectionViewSource> da risorse del contenitore, quindi rende i primo elemento di dati dell'elemento corrente. Se un <xref:System.Windows.FrameworkElement.Loaded> gestore eventi esiste già, Visual Studio aggiunge questo codice al gestore dell'evento esistente.

### <a name="services"></a>Servizi

Quando si trascina un oggetto servizio o a una proprietà di **Zdroje dat** finestra di progettazione, Visual Studio genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] che crea un controllo con associazione a dati (o associa un controllo esistente all'oggetto o una proprietà). Tuttavia, Visual Studio genera il codice che compila l'oggetto servizio del proxy con i dati. È necessario scrivere questo codice manualmente. Per un esempio che illustra come eseguire questa operazione, vedere [WPF di associare controlli a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

Visual Studio genera XAML che esegue le operazioni seguenti:

- Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'oggetto restituito dal servizio.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, il [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crea il controllo che è stato selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Oggetti

Quando si trascina un oggetto o a una proprietà di **Zdroje dat** finestra di progettazione, Visual Studio genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] che crea un controllo con associazione a dati (o associa un controllo esistente all'oggetto o una proprietà). Tuttavia, Visual Studio non genera codice per inserire l'oggetto dati. È necessario scrivere questo codice manualmente.

> [!NOTE]
> Devono essere pubblico e delle classi personalizzate, per impostazione predefinita, dispone di un costruttore senza parametri. Non possono essere classi annidate che hanno un "punto" nella relativa sintassi. Per altre informazioni, vedere [XAML e classi personalizzate per WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

Visual Studio genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] che esegue le operazioni seguenti:

- Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'oggetto.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, XAML associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, il XAML crea il controllo che è stato selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Vedere anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)