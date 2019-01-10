---
title: Associare controlli Windows Form ai dati
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: c9acd074eb1d4ac73ca0f905376f22f6e2e11b08
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53897724"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Associare controlli Windows Form ai dati in Visual Studio

È possibile visualizzare i dati agli utenti dell'applicazione mediante l'associazione dati a un Windows Form. Per creare questi controlli con associazione a dati, trascinare elementi dal **Zdroje dat** finestra in Progettazione Windows Form in Visual Studio.

![Operazione di trascinamento sull'origine dati](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Se il **Zdroje dat** finestra non è visibile, è possibile aprirla scegliendo **View** > **Other Windows** > **Zdroje dat** , o premendo **MAIUSC**+**Alt**+**1!d**. Deve essere un progetto aperto in Visual Studio per vedere le **Zdroje dat** finestra.

Prima si trascinano elementi, è possibile impostare il tipo di controllo che si desidera associare. Vengono visualizzati valori diversi a seconda che si scelga la tabella stessa, o una singola colonna.  È anche possibile impostare valori personalizzati. Per una tabella, **dettagli** significa che ogni colonna è associata a un controllo separato.

![Associare l'origine dati a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Controlli di BindingSource e BindingNavigator

Il componente <xref:System.Windows.Forms.BindingSource> ha due scopi. In primo luogo, fornisce un livello di astrazione quando si associa i controlli ai dati. I controlli nel form sono associati ai <xref:System.Windows.Forms.BindingSource> componente anziché direttamente a un'origine dati. In secondo luogo, è possibile gestire una raccolta di oggetti. Aggiunta di un tipo per il <xref:System.Windows.Forms.BindingSource> crea un elenco di quel tipo.

Per altre informazioni sul <xref:System.Windows.Forms.BindingSource> componente, vedere:

- [Componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component)

- [Cenni preliminari sul componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [Architettura del componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

Il [controllo BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) fornisce un'interfaccia utente per l'esplorazione dei dati visualizzati in un'applicazione Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Associazione ai dati in un controllo DataGridView

Per un [controllo DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), l'intera tabella è associato a tale controllo singolo. Quando si trascina un **DataGridView** al form, uno strumento di rimozione per l'esplorazione dei record (<xref:System.Windows.Forms.BindingNavigator>) viene inoltre visualizzato. Oggetto [set di dati](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti. Nella figura seguente, un [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) viene aggiunto anche perché la tabella Customers è una relazione con la tabella Orders. Queste variabili sono tutti dichiarate nel codice generato automaticamente come membri privati nella classe del modulo. Il codice generato automaticamente per il riempimento il **DataGridView** si trova nel `Form_Load` gestore dell'evento. Il codice per il salvataggio dei dati per aggiornare il database si trova nel `Save` gestore dell'evento per il **BindingNavigator**. È possibile spostare o modificare il codice in base alle esigenze.

![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

È possibile personalizzare il comportamento dei **DataGridView** e il **BindingNavigator** facendo clic sullo smart tag nell'angolo superiore destro della ognuno:

![DataGridView e associazione Navigator smart tag](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Se i controlli dell'applicazione deve non è disponibile dall'interno di **Zdroje dat** finestra, è possibile aggiungere controlli. Per altre informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dei dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

È anche possibile trascinare elementi dal **Zdroje dat** finestra nei controlli già presenti in un form per associare il controllo ai dati. Un controllo che è già associato a dati con il data binding reimpostati sull'elemento trascinato più di recente. Per essere obiettivi di rilascio validi, i controlli devono essere in grado di visualizzare il tipo di dati sottostante di elementi trascinati su di esso dal **Zdroje dat** finestra. Ad esempio, non valido a trascinare un elemento che ha un tipo di dati <xref:System.DateTime> in un <xref:System.Windows.Forms.CheckBox>, in quanto il <xref:System.Windows.Forms.CheckBox> non è in grado di visualizzare una data.

## <a name="bind-to-data-in-individual-controls"></a>Associazione ai dati in controlli singoli

Quando si associa un'origine dati al **dettagli**, ogni colonna nel set di dati è associata a un controllo separato.

![Associare l'origine dati per i dettagli](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Si noti che nella figura precedente, si trascina dalla proprietà Orders della tabella Customers, non dalla tabella Orders. Dall'associazione per il `Customer.Orders` proprietà, i comandi di navigazione apportate nel **DataGridView** si riflette immediatamente i controlli dei dettagli. Se è stato trascinato dalla tabella Orders, i controlli sarebbero ancora essere associati al set di dati, ma non si potrebbe non essere sincronizzati con il **DataGridView**.

La figura seguente mostra l'impostazione predefinita i controlli con associazione a dati che vengono aggiunti al modulo dopo che la proprietà di ordini nella tabella Customers è associata a **informazioni dettagliate** nel **Zdroje dat** finestra.

![Tabella degli ordini associata ai dettagli](../data-tools/media/raddata-orders-table-bound-to-details.png)

Si noti anche che ogni controllo ha uno smart tag. Questo tag consente le personalizzazioni che si applicano a solo tale controllo.

## <a name="see-also"></a>Vedere anche

- [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Data binding in Windows Form (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)