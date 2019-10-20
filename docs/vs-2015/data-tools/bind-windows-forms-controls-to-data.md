---
title: Associare controlli Windows Forms ai dati | Microsoft Docs
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
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf93d96594b65b06670567e8c23cd83ccb7f1ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672968"
---
# <a name="bind-windows-forms-controls-to-data"></a>Associare controlli Windows Form ai dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile associare origini dati ai controlli trascinando oggetti dalla finestra **origini dati** in un Windows Form o in un controllo esistente in un form. Prima di trascinare gli elementi, è possibile impostare il tipo di controllo a cui si desidera eseguire l'associazione. Vengono visualizzati valori diversi a seconda che si scelga la tabella o una singola colonna.  È anche possibile impostare valori personalizzati. Per una tabella, "Details" indica che ogni colonna è associata a un controllo separato.

 ![Associa origine dati a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata associare un'origine dati a DataGridView")

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="bind-to--data-in-a-datagridview-control"></a>Eseguire l'associazione ai dati in un controllo DataGridView
 Per DataGridView, l'intera tabella è associata a quel singolo controllo. Quando si trascina un oggetto DataGridView nel form, viene visualizzata anche una striscia di strumenti per spostarsi tra i record (<xref:System.Windows.Forms.BindingNavigator>). Un [set di dati](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti. Nell'illustrazione seguente viene aggiunto anche un TableAdapterManager perché la tabella Customers ha una relazione con la tabella Orders. Queste variabili sono tutte dichiarate nel codice generato automaticamente come membri privati nella classe del modulo. Il codice generato automaticamente per il riempimento di DataGridView si trova nel gestore eventi Form_Load. Il codice per il salvataggio dei dati per aggiornare il database si trova nel gestore eventi Save per BindingNavigator. È possibile spostare o modificare il codice in base alle esigenze.

 ![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView con BindingNavigator")

 È possibile personalizzare il comportamento di DataGridView e BindingNavigator facendo clic sullo smart tag nell'angolo superiore destro di ogni:

 ![Smart tag per DataGridView e strumento di navigazione binding](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView e smart tag del navigatore di binding")

 Se i controlli necessari per l'applicazione non sono disponibili nella finestra **origini dati** , è possibile aggiungere controlli. Per altre informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

 È anche possibile trascinare elementi dalla finestra **origini dati** nei controlli già presenti in un form per associare il controllo ai dati. Un controllo già associato ai dati ha le associazioni dati reimpostate sull'elemento trascinato più di recente. Per essere destinazioni di rilascio valide, i controlli devono essere in grado di visualizzare il tipo di dati sottostante dell'elemento trascinato nella finestra **origini dati** . Non è ad esempio possibile trascinare un elemento con un tipo di dati <xref:System.DateTime> in un <xref:System.Windows.Forms.CheckBox>, perché il <xref:System.Windows.Forms.CheckBox> non è in grado di visualizzare una data.

## <a name="bind-to--data-in-individual-controls"></a>Eseguire l'associazione ai dati nei singoli controlli
 Quando si associa un'origine dati a "Details", ogni colonna del set di dati viene associata a un controllo separato.

 ![Associa origine dati ai dettagli](../data-tools/media/raddata-bind-data-source-to-details.png "raddata associare l'origine dati ai dettagli")

> [!IMPORTANT]
> Si noti che nell'illustrazione precedente si trascina dalla proprietà Orders della tabella Customers, non dalla tabella Orders. Associando la proprietà Customer. Orders, i comandi di spostamento eseguiti in DataGridView vengono riflessi immediatamente nei controlli dettagli. Se è stato trascinato dalla tabella Orders, i controlli verrebbero comunque associati al set di dati, ma non verrebbero sincronizzati con DataGridView.

 Nella figura seguente vengono mostrati i controlli con associazione a dati predefiniti che vengono aggiunti al form dopo che la proprietà Orders della tabella Customers è associata a "Details" nella finestra **origini dati** .

 ![Tabella Orders associata ai dettagli](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata Ordina la tabella associata ai dettagli")

 Si noti anche che ogni controllo dispone di uno smart tag. Questo tag Abilita le personalizzazioni che si applicano solo a tale controllo.

## <a name="see-also"></a>Vedere anche
 [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
