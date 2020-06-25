---
title: Associare controlli Windows Form ai dati
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b6a1d240c865ecc6abddd399c94122a757ee0983
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283008"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Associare controlli Windows Form ai dati in Visual Studio

È possibile visualizzare i dati per gli utenti dell'applicazione associando i dati a Windows Forms. Per creare questi controlli associati a dati, trascinare gli elementi dalla finestra **origini dati** nel Progettazione Windows Form in Visual Studio.

![Operazione di trascinamento dell'origine dati](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Se la finestra **origini dati** non è visibile, è possibile aprirla scegliendo **Visualizza**  >  **altre**  >  **origini dati**di Windows o premendo **MAIUSC** + **ALT** + **D**. Per visualizzare la finestra **origini dati** , è necessario aprire un progetto in Visual Studio.

Prima di trascinare gli elementi, è possibile impostare il tipo di controllo a cui si desidera eseguire l'associazione. Vengono visualizzati valori diversi a seconda che si scelga la tabella o una singola colonna.  È anche possibile impostare valori personalizzati. Per una tabella, **Dettagli** indica che ogni colonna è associata a un controllo separato.

![Associa origine dati a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Controlli BindingSource e BindingNavigator

Il componente <xref:System.Windows.Forms.BindingSource> ha due scopi. In primo luogo, fornisce un livello di astrazione durante l'associazione dei controlli ai dati. I controlli nel form sono associati al <xref:System.Windows.Forms.BindingSource> componente anziché direttamente a un'origine dati. In secondo luogo, è in grado di gestire una raccolta di oggetti. Se si aggiunge un tipo a <xref:System.Windows.Forms.BindingSource> , viene creato un elenco di tale tipo.

Per ulteriori informazioni sul <xref:System.Windows.Forms.BindingSource> componente, vedere:

- [Componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component)

- [Cenni preliminari sul componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [Architettura del componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

Il [controllo BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) fornisce un'interfaccia utente per spostarsi tra i dati visualizzati da un'applicazione Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Eseguire l'associazione ai dati in un controllo DataGridView

Per un [controllo DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), l'intera tabella viene associata a tale controllo. Quando si trascina un **oggetto DataGridView** nel form, viene visualizzata anche una barra degli strumenti per spostarsi tra i record ( <xref:System.Windows.Forms.BindingNavigator> ). Un [set di dati](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> e viene <xref:System.Windows.Forms.BindingNavigator> visualizzato nella barra dei componenti. Nell'illustrazione seguente viene aggiunto anche un [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) perché la tabella Customers ha una relazione con la tabella Orders. Queste variabili sono tutte dichiarate nel codice generato automaticamente come membri privati nella classe del modulo. Il codice generato automaticamente per il riempimento di **DataGridView** si trova nel `Form_Load` gestore eventi. Il codice per il salvataggio dei dati per aggiornare il database si trova nel `Save` gestore eventi per **BindingNavigator**. È possibile spostare o modificare il codice in base alle esigenze.

![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

È possibile personalizzare il comportamento di **DataGridView** e **BindingNavigator** facendo clic sullo smart tag nell'angolo in alto a destra di ogni:

![Smart tag per DataGridView e strumento di navigazione binding](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Se i controlli necessari per l'applicazione non sono disponibili nella finestra **origini dati** , è possibile aggiungere controlli. Per altre informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

È anche possibile trascinare elementi dalla finestra **origini dati** nei controlli già presenti in un form per associare il controllo ai dati. Un controllo già associato ai dati ha le associazioni dati reimpostate sull'elemento trascinato più di recente. Per essere destinazioni di rilascio valide, i controlli devono essere in grado di visualizzare il tipo di dati sottostante dell'elemento trascinato nella finestra **origini dati** . Ad esempio, non è possibile trascinare un elemento con tipo di dati in <xref:System.DateTime> <xref:System.Windows.Forms.CheckBox> , perché <xref:System.Windows.Forms.CheckBox> non è in grado di visualizzare una data.

## <a name="bind-to-data-in-individual-controls"></a>Eseguire l'associazione ai dati nei singoli controlli

Quando si associa un'origine dati ai **Dettagli**, ogni colonna del set di dati viene associata a un controllo separato.

![Associa origine dati ai dettagli](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Si noti che nell'illustrazione precedente si trascina dalla proprietà Orders della tabella Customers, non dalla tabella Orders. Con l'associazione alla `Customer.Orders` proprietà, i comandi di spostamento eseguiti in **DataGridView** vengono riflessi immediatamente nei controlli dettagli. Se è stato trascinato dalla tabella Orders, i controlli verrebbero comunque associati al set di dati, ma non verrebbero sincronizzati con **DataGridView**.

Nella figura seguente vengono mostrati i controlli associati a dati predefiniti che vengono aggiunti al form dopo che la proprietà Orders della tabella Customers è associata ai **Dettagli** nella finestra **origini dati** .

![Tabella Orders associata ai dettagli](../data-tools/media/raddata-orders-table-bound-to-details.png)

Si noti anche che ogni controllo dispone di uno smart tag. Questo tag Abilita le personalizzazioni che si applicano solo a tale controllo.

## <a name="see-also"></a>Vedi anche

- [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Data Binding in Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)
