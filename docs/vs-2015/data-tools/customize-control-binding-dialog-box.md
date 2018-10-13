---
title: Personalizza associazione nella finestra di dialogo controllo | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.datauicustomization
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Customize Control Binding dialog box
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8cc2e591c144afeb0720cdbf05280a499d10c70c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247013"
---
# <a name="customize-control-binding-dialog-box"></a>Finestra di dialogo Personalizza associazione controllo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usare la **Personalizza associazione controlli** per specificare quali controlli saranno disponibili per gli elementi nella finestra di dialogo il [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 Ogni elemento di **Zdroje dat** finestra è associato un elenco di controlli che possono essere associate all'elemento. I controlli disponibili per ogni elemento sono determinati dal tipo di dati dell'elemento. Ogni tipo di dati include un elenco di controlli associati validi definito in questa finestra di dialogo, incluso un controllo predefinito.  
  
 Prima che si trascina un elemento in un'area di progettazione per creare un controllo con associazione a dati, è possibile selezionare il controllo da creare. Se si trascina un elemento dal **Zdroje dat** finestra in un'area di progettazione senza selezionare un controllo, il controllo predefinito per il tipo di dati dell'elemento selezionato viene aggiunto all'area di progettazione.  
  
 Per altre informazioni su come usare questa finestra di dialogo per personalizzare l'elenco di controlli per gli elementi di **Zdroje dat** finestra, vedere [aggiungere controlli personalizzati alla finestra Origini dei dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Tipo di dati**  
 Visualizza un elenco di tipi che viene associato a controlli:  
  
-   Le tabelle, entità e gli oggetti sono rappresentati come **[elenco]** tipi.  
  
-   Le colonne o proprietà pubbliche dell'entità e degli oggetti sono rappresentate come tipo di dati effettivo della colonna o proprietà nell'archivio dati sottostante.  
  
-   Gli oggetti con le forme definite dall'utente vengono rappresentati come **[altro]**. Ad esempio, se l'applicazione include un controllo personalizzato che consente di visualizzare i dati da più di una proprietà di un oggetto, selezionare la **[altro]** tipo di dati per il controllo.  
  
 **Controlli associati**  
 Visualizza un elenco di controlli che è possibile associare a un particolare tipo di dati. Se si desidera associare il tipo di dati selezionato in un particolare controllo la **tipo di dati** elencare, selezionare la casella di controllo corrispondente. Deselezionare la casella di controllo per rimuovere un'associazione. Controlli selezionati vengono visualizzati nel menu di scelta rapida presentato dal **Zdroje dat** finestra per un elemento del tipo di dati associato.  
  
 È possibile aggiungere controlli all'elenco mediante l'aggiunta di controlli che dispongono di uno dei diversi attributi di data binding per il **casella degli strumenti**. Per altre informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dei dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 **Impostare il valore predefinito**  
 Assegna il tipo di controllo selezionato per impostazione predefinita per gli elementi del tipo di dati selezionato. Il controllo predefinito viene visualizzato come la selezione nel menu di scelta rapida presentato dal primo il **Zdroje dat** finestra per un elemento. Tipo di controllo solo uno può essere assegnato come l'impostazione predefinita per un tipo di dati.  
  
 **Cancellare l'impostazione predefinita**  
 Rimuove la designazione di un controllo come predefinito per il tipo di dati selezionato. Se non vi è alcun valore predefinito per il tipo di dati selezionato **[Nessuno]** viene visualizzato come la selezione nel menu di scelta rapida presentato dal primo il **Zdroje dat** finestra per un elemento del tipo associato.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Aggiungere controlli personalizzati alla finestra Origini dei dati](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)