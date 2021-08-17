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
ms.openlocfilehash: 311bdc7d0bf236f29d09804257aaaa8ce991f32f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075346"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Associare controlli Windows Form ai dati in Visual Studio

È possibile visualizzare i dati agli utenti dell'applicazione associando i dati Windows Form. Per creare questi controlli associati a dati, trascinare gli **elementi** dalla finestra Origini dati Windows Progettazione Form in Visual Studio.

![Operazione di trascinamento dell'origine dati](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Se la **finestra Origini** dati non è visibile, è possibile aprirla scegliendo Visualizza altre Windows dati oppure premendo  >    >   **MAIUSC** + **ALT** + **D.** Per visualizzare la finestra Origini dati, è Visual Studio un **progetto** aperto.

Prima di trascinare gli elementi, è possibile impostare il tipo di controllo a cui si vuole eseguire l'associazione. Vengono visualizzati valori diversi a seconda che si sceeni la tabella stessa o una singola colonna.  È anche possibile impostare valori personalizzati. Per una tabella, **Details** indica che ogni colonna è associata a un controllo separato.

![Associare un'origine dati a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Controlli BindingSource e BindingNavigator

Il componente <xref:System.Windows.Forms.BindingSource> ha due scopi. In primo luogo, fornisce un livello di astrazione quando si associano i controlli ai dati. I controlli nel form sono associati al <xref:System.Windows.Forms.BindingSource> componente anziché direttamente a un'origine dati. In secondo momento, può gestire una raccolta di oggetti . L'aggiunta di un <xref:System.Windows.Forms.BindingSource> tipo a crea un elenco di tale tipo.

Per altre informazioni sul <xref:System.Windows.Forms.BindingSource> componente, vedere:

- [Componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component)

- [Panoramica del componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [Architettura del componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

Il [controllo BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) fornisce un'interfaccia utente per spostarsi tra i dati visualizzati da un'Windows applicazione.

## <a name="bind-to-data-in-a-datagridview-control"></a>Eseguire il binding ai dati in un controllo DataGridView

Per un [controllo DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), l'intera tabella è associata a tale singolo controllo. Quando si trascina un **controllo DataGridView** nel form, viene visualizzata anche una barra degli strumenti per lo spostamento tra record ( <xref:System.Windows.Forms.BindingNavigator> ). Nella barra dei componenti vengono visualizzati un [oggetto DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md) <xref:System.Windows.Forms.BindingSource> , e <xref:System.Windows.Forms.BindingNavigator> . Nella figura seguente viene aggiunto [anche un TableAdapterManager](/previous-versions/bb384426(v=vs.140)) perché la tabella Customers ha una relazione con la tabella Orders. Queste variabili vengono tutte dichiarate nel codice generato automaticamente come membri privati nella classe del modulo. Il codice generato automaticamente per il riempimento di **DataGridView** si trova nel `Form_Load` gestore eventi . Il codice per salvare i dati per aggiornare il database si trova nel gestore `Save` eventi per **BindingNavigator.** È possibile spostare o modificare questo codice in base alle esigenze.

![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

È possibile personalizzare il comportamento di **DataGridView** e **BindingNavigator** facendo clic sullo smart tag nell'angolo superiore destro di ognuno:

![Smart tag DataGridView e Strumento di navigazione dell'associazione](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Se i controlli per l'applicazione non sono disponibili all'interno della **finestra Origini** dati, è possibile aggiungere controlli. Per altre informazioni, vedere [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

È anche possibile trascinare elementi dalla **finestra Origini** dati nei controlli già presenti in un form per associare il controllo ai dati. I data binding di un controllo già associato ai dati vengono reimpostati sull'elemento trascinato più di recente. Per essere destinazioni di rilascio valide, i controlli devono essere in grado di visualizzare il tipo di dati sottostante dell'elemento trascinato su di esso dalla **finestra Origini** dati. Ad esempio, non è valido trascinare un elemento con tipo di dati in , perché non è in grado di <xref:System.DateTime> <xref:System.Windows.Forms.CheckBox> visualizzare una <xref:System.Windows.Forms.CheckBox> data.

## <a name="bind-to-data-in-individual-controls"></a>Eseguire il binding ai dati nei singoli controlli

Quando si associa un'origine dati **a Details**, ogni colonna del set di dati viene associata a un controllo separato.

![Associare l'origine dati ai dettagli](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Si noti che nell'illustrazione precedente si trascina dalla proprietà Orders della tabella Customers, non dalla tabella Orders. Tramite l'associazione alla proprietà , i comandi di navigazione `Customer.Orders` evasi in **DataGridView** si riflettono immediatamente nei controlli dei dettagli. Se si trascina dalla tabella Orders, i controlli vengono comunque associati al set di dati, ma non vengono sincronizzati con **DataGridView.**

Nella figura seguente vengono illustrati i controlli associati a dati predefiniti aggiunti al form dopo che la proprietà Orders della tabella Customers è stata associata a **Details** nella **finestra Origini** dati.

![Tabella Orders associata ai dettagli](../data-tools/media/raddata-orders-table-bound-to-details.png)

Si noti anche che ogni controllo ha uno smart tag. Questo tag abilita le personalizzazioni che si applicano solo a tale controllo.

## <a name="see-also"></a>Vedi anche

- [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Data binding in Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)