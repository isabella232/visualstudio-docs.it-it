---
title: Associare controlli Windows Form ai dati | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d2aefe68761d31f87d84c9215a6187c28e7b471b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668990"
---
# <a name="bind-windows-forms-controls-to-data"></a>Associare controlli Windows Form ai dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile associare origini dati a controlli mediante il trascinamento di oggetti dal **Zdroje dat** finestra in un Windows Form o in un controllo esistente in un form. Prima si trascinano elementi, è possibile impostare il tipo di controllo che si desidera associare. Vengono visualizzati valori diversi a seconda che si scelga la tabella stessa, o una singola colonna.  È anche possibile impostare valori personalizzati. Per una tabella "Dettagli" significa che ogni colonna è associata a un controllo separato.  
  
 ![Associare l'origine dati a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata origine di dati di associazione di DataGridView")  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Associazione ai dati in un controllo DataGridView  
 Per DataGridView, l'intera tabella è associato a tale controllo singolo. Quando si trascina un controllo DataGridView al form, uno strumento di rimozione per l'esplorazione dei record (<xref:System.Windows.Forms.BindingNavigator>) viene inoltre visualizzato. Oggetto [set di dati](../data-tools/dataset-tools-in-visual-studio.md), oggetto TableAdapter <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti. Nella figura seguente, viene inoltre aggiunto un componente TableAdapterManager perché la tabella Customers è una relazione con la tabella Orders. Queste variabili sono tutti dichiarate nel codice generato automaticamente come membri privati nella classe del modulo. Il codice generato automaticamente per il riempimento DataGridView è disponibile nel gestore eventi form_load. Il codice per il salvataggio dei dati per aggiornare il database si trova nel gestore dell'evento Save di BindingNavigator. È possibile spostare o modificare il codice in base alle esigenze.  
  
 ![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView con BindingNavigator")  
  
 È possibile personalizzare il comportamento di DataGridView e di BindingNavigator facendo clic sullo smart tag nell'angolo superiore destro della ognuno:  
  
 ![DataGridView e associazione Navigator smart tag](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView e associazione Navigator smart tag")  
  
 Se i controlli dell'applicazione deve non è disponibile dall'interno di **Zdroje dat** finestra, è possibile aggiungere controlli. Per altre informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dei dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 È anche possibile trascinare elementi dal **Zdroje dat** finestra nei controlli già presenti in un form per associare il controllo ai dati. Un controllo che è già associato a dati con il data binding reimpostati sull'elemento trascinato più di recente. Per essere obiettivi di rilascio validi, i controlli devono essere in grado di visualizzare il tipo di dati sottostante di elementi trascinati su di esso dal **Zdroje dat** finestra. Ad esempio, non valido a trascinare un elemento che ha un tipo di dati <xref:System.DateTime> in un <xref:System.Windows.Forms.CheckBox>, in quanto il <xref:System.Windows.Forms.CheckBox> non è in grado di visualizzare una data.  
  
## <a name="bind-to--data-in-individual-controls"></a>Associazione ai dati in controlli singoli  
 Quando si associa un'origine dati per "Dettagli", ogni colonna nel set di dati è associata a un controllo separato.  
  
 ![Associare l'origine dati per informazioni dettagliate](../data-tools/media/raddata-bind-data-source-to-details.png "raddata origine di dati di associazione per i dettagli")  
  
> [!IMPORTANT]
>  Si noti che nella figura precedente, si trascina dalla proprietà Orders della tabella Customers, non dalla tabella Orders. Tramite l'associazione alla proprietà Orders, i comandi di navigazione apportati nel DataGridView si rifletteranno immediatamente i controlli dei dettagli. Se è stato trascinato dalla tabella Orders, i controlli sarebbero ancora associati al set di dati, ma non potrebbe non essere sincronizzati con il controllo DataGridView.  
  
 La figura seguente mostra l'impostazione predefinita i controlli con associazione a dati che vengono aggiunti al form una volta associata la proprietà di ordini nella tabella Customers "Dettagli" nel **Zdroje dat** finestra.  
  
 ![Tabella degli ordini associati a informazioni dettagliate](../data-tools/media/raddata-orders-table-bound-to-details.png "tabella Orders raddata associato ai dettagli")  
  
 Si noti anche che ogni controllo ha uno smart tag. Questo tag consente le personalizzazioni che si applicano a solo tale controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
