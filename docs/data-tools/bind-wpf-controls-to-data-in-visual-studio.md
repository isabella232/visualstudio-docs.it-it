---
title: Associare controlli WPF ai dati - Parte 1
description: Associare i controlli WPF ai dati. Per creare questi controlli associati a dati, trascinare elementi dalla finestra Origini dati in WPF Designer in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e491fcb8e7dad813eeb5594f6e8cbb9d64ade6ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075263"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Associare controlli WPF ai dati in Visual Studio

È possibile visualizzare i dati per gli utenti dell'applicazione mediante l'associazione dei dati ai controlli [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]. Per creare questi controlli associati a dati, è possibile trascinare elementi dalla **finestra Origini** dati in [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] in Visual Studio. In questo argomento vengono descritte alcune delle più comuni attività, strumenti e classi che è possibile utilizzare per creare applicazioni [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] associate a dati.

Per informazioni generali su come creare controlli associati a dati in Visual Studio, vedere Associare controlli ai dati [in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Per altre informazioni sul data binding di [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)], vedere [Panoramica sul data binding](/dotnet/desktop-wpf/data/data-binding-overview).

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

Quando si trascina un  elemento dalla finestra Origini dati a , Visual Studio genera che definisce un nuovo controllo associato a dati (o associa un controllo [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] esistente [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] all'origine dati). Per alcune origini dati, Visual Studio genera anche codice nel file code-behind che inserisce dati nell'origine dati.

Nella tabella seguente sono [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] elencati il codice e Visual Studio generati per ogni tipo di origine dati nella **finestra Origini** dati .

| Origine dati | Generazione di XAML per l'associazione di un controllo all'origine dati | Generazione di codice per l'inserimento dei dati nell'origine dati |
| - | - | - |
| Set di dati | Sì | Sì |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | Sì | Sì |
| Servizio | Sì | No |
| Oggetto | Sì | No |

### <a name="datasets"></a>Set di dati

Quando si trascina una tabella o una colonna dalla **finestra** Origini dati alla finestra di progettazione, Visual Studio [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] genera un'operazione che esegue le operazioni seguenti:

- Aggiunge il dataset e un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nel dataset.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, XAML associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, xaml crea il controllo selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

Visual Studio apporta inoltre le modifiche seguenti al file code-behind:

- Crea un gestore dell'evento <xref:System.Windows.FrameworkElement.Loaded> per l'elemento [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] contenente il controllo. Il gestore dell'evento inserisce i dati nella tabella, recupera l'oggetto <xref:System.Windows.Data.CollectionViewSource> dalle risorse del contenitore, quindi imposta come elemento corrente il primo elemento di dati. Se esiste <xref:System.Windows.FrameworkElement.Loaded> già un gestore eventi, Visual Studio aggiunge questo codice al gestore eventi esistente.

### <a name="entity-data-models"></a>Entity Data Model

Quando si trascina un'entità o  una proprietà dell'entità dalla finestra Origini dati alla finestra di progettazione, Visual Studio [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] genera un'operazione che esegue le operazioni seguenti:

- Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'entità.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, crea il controllo selezionato per l'elemento trascinato e associa il [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

Visual Studio apporta inoltre le modifiche seguenti al file code-behind:

- Aggiunge un nuovo metodo che restituisce una query per l'entità trascinata nella finestra di progettazione (o per l'entità contenente la proprietà trascinata nella finestra di progettazione). Il nuovo metodo ha il nome `Get<EntityName>Query` , dove è il nome `\<EntityName>` dell'entità.

- Crea un gestore dell'evento <xref:System.Windows.FrameworkElement.Loaded> per l'elemento [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] contenente il controllo. Il gestore eventi chiama il metodo per riempire l'entità con dati, recupera l'oggetto dalle risorse del contenitore e quindi imposta il primo elemento di dati come `Get<EntityName>Query` <xref:System.Windows.Data.CollectionViewSource> elemento corrente. Se esiste <xref:System.Windows.FrameworkElement.Loaded> già un gestore eventi, Visual Studio aggiunge questo codice al gestore eventi esistente.

### <a name="services"></a>Servizi

Quando si trascina un oggetto  servizio o una proprietà dalla finestra Origini dati alla finestra di progettazione, Visual Studio genera che crea un controllo associato a dati (o associa un controllo esistente all'oggetto o alla [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] proprietà ). Tuttavia, Visual Studio non genera codice che riempie l'oggetto servizio proxy con dati. È necessario scrivere questo codice manualmente. Per un esempio che illustra come eseguire questa operazione, vedere [Associare controlli WPF a un servizio dati WCF.](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)

Visual Studio genera XAML che esegue le operazioni seguenti:

- Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'oggetto restituito dal servizio.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, crea il controllo selezionato per l'elemento trascinato e associa il [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Oggetti

Quando si trascina un oggetto  o una proprietà dalla finestra Origini dati alla finestra di progettazione, Visual Studio genera che crea un controllo associato a dati (o associa un controllo esistente all'oggetto o alla [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] proprietà ). Tuttavia, Visual Studio non genera codice per riempire l'oggetto con dati. È necessario scrivere questo codice manualmente.

> [!NOTE]
> Le classi personalizzate devono essere pubbliche e, per impostazione predefinita, avere un costruttore senza parametri. Non possono essere classi annidate con un "punto" nella sintassi. Per altre informazioni, vedere [XAML e classi personalizzate per WPF.](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf)

Visual Studio genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] che esegue le operazioni seguenti:

- Aggiunge un nuovo oggetto <xref:System.Windows.Data.CollectionViewSource> alle risorse del contenitore in cui è stato trascinato l'elemento. <xref:System.Windows.Data.CollectionViewSource> è un oggetto che può essere utilizzato per esplorare e visualizzare i dati nell'oggetto.

- Crea un data binding per un controllo. Se si trascina l'elemento in un controllo esistente della finestra di progettazione, XAML associa il controllo all'elemento. Se si trascina l'elemento in un contenitore, xaml crea il controllo selezionato per l'elemento trascinato e associa il controllo all'elemento. Il controllo viene creato all'interno di un nuovo oggetto <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Vedi anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
