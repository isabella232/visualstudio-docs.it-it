---
title: Associare controlli Windows Form ai dati
description: Associare Windows form ai dati in Visual Studio in modo che sia possibile visualizzare i dati agli utenti dell'applicazione.
ms.custom: SEO-VS-2020
ms.date: 11/03/2017
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d891cc83008c844ddc694b958be6314c9f2de63a7c8383a541fc3ccd265d00bc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240640"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Associare controlli Windows Form ai dati in Visual Studio

È possibile visualizzare i dati agli utenti dell'applicazione associando i dati Windows Form. Per creare questi controlli associati a  dati, trascinare gli elementi dalla finestra Origini dati Windows Progettazione form in Visual Studio.

![Operazione di trascinamento dell'origine dati](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Se la **finestra Origini** dati non è visibile, è possibile aprirla scegliendo Visualizza Windows origini dati oppure premendo   >    >    + **MAIUSC ALT** + **D.** È necessario avere un progetto aperto in Visual Studio per visualizzare la **finestra Origini** dati.

Prima di trascinare gli elementi, è possibile impostare il tipo di controllo a cui si vuole eseguire l'associazione. Vengono visualizzati valori diversi a seconda che si scegli la tabella stessa o una singola colonna.  È anche possibile impostare valori personalizzati. Per una tabella, **Details** indica che ogni colonna è associata a un controllo separato.

![Associare l'origine dati a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Controlli BindingSource e BindingNavigator

Il componente <xref:System.Windows.Forms.BindingSource> ha due scopi. In primo luogo, fornisce un livello di astrazione quando si associano i controlli ai dati. I controlli nel form sono associati al <xref:System.Windows.Forms.BindingSource> componente anziché direttamente a un'origine dati. In secondo momento, può gestire una raccolta di oggetti . L'aggiunta di un <xref:System.Windows.Forms.BindingSource> tipo a crea un elenco di tale tipo.

Per altre informazioni sul <xref:System.Windows.Forms.BindingSource> componente, vedere:

- [Componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component)

- [Panoramica del componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [Architettura del componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

Il [controllo BindingNavigator fornisce](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) un'interfaccia utente per lo spostamento tra i dati visualizzati da un Windows app.

## <a name="bind-to-data-in-a-datagridview-control"></a>Eseguire l'associazione ai dati in un controllo DataGridView

Per un [controllo DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), l'intera tabella è associata a tale singolo controllo. Quando si trascina un **controllo DataGridView** nel form, viene visualizzata anche una barra degli strumenti per lo spostamento tra record ( <xref:System.Windows.Forms.BindingNavigator> ). Un [Oggetto DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md) <xref:System.Windows.Forms.BindingSource> , e vengono visualizzati nella barra dei <xref:System.Windows.Forms.BindingNavigator> componenti. Nella figura seguente viene aggiunto anche [un oggetto TableAdapterManager](/previous-versions/bb384426(v=vs.140)) perché la tabella Customers ha una relazione con la tabella Orders. Queste variabili vengono tutte dichiarate nel codice generato automaticamente come membri privati nella classe del modulo. Il codice generato automaticamente per il riempimento di **DataGridView** si trova nel `Form_Load` gestore eventi. Il codice per salvare i dati per aggiornare il database si trova nel gestore `Save` eventi per **BindingNavigator**. È possibile spostare o modificare questo codice in base alle esigenze.

![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

È possibile personalizzare il comportamento di **DataGridView** e **BindingNavigator** facendo clic sullo smart tag nell'angolo superiore destro di ognuno:

![Smart tag DataGridView e Binding Navigator](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Se i controlli dell'applicazione non sono disponibili all'interno della **finestra Origini** dati, è possibile aggiungere controlli. Per altre informazioni, vedere [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

È anche possibile trascinare elementi dalla finestra **Origini** dati nei controlli già presenti in un form per associare il controllo ai dati. Per un controllo già associato ai dati, le associazioni dati vengono reimpostate sull'elemento trascinato più di recente. Per essere destinazioni di rilascio valide, i controlli devono essere in grado di visualizzare il tipo di dati sottostante dell'elemento trascinato nella finestra **Origini** dati. Ad esempio, non è valido trascinare un elemento con un tipo di dati di in , perché non è in grado di <xref:System.DateTime> <xref:System.Windows.Forms.CheckBox> visualizzare una <xref:System.Windows.Forms.CheckBox> data.

## <a name="bind-to-data-in-individual-controls"></a>Eseguire l'associazione ai dati nei singoli controlli

Quando si associa un'origine dati **a Details**, ogni colonna del set di dati viene associata a un controllo separato.

![Associare l'origine dati ai dettagli](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Si noti che nella figura precedente si trascina dalla proprietà Orders della tabella Customers, non dalla tabella Orders. Tramite l'associazione alla proprietà , i comandi di navigazione `Customer.Orders` esettuati in **DataGridView** si riflettono immediatamente nei controlli dei dettagli. Se si trascina dalla tabella Orders, i controlli verrebbero comunque associati al set di dati, ma non verrebbero sincronizzati con **DataGridView**.

La figura seguente mostra i controlli con associazione a dati predefiniti aggiunti al form dopo che la proprietà Orders nella tabella Customers è associata a **Details** nella **finestra Origini** dati.

![Tabella Orders associata ai dettagli](../data-tools/media/raddata-orders-table-bound-to-details.png)

Si noti anche che ogni controllo ha uno smart tag. Questo tag abilita le personalizzazioni che si applicano solo a tale controllo.

## <a name="see-also"></a>Vedi anche

- [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Data binding in Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)