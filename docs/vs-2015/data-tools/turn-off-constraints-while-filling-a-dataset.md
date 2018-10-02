---
title: Disattivare i vincoli durante il riempimento di un set di dati | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4b14830b7ed4922b4e383ef245c0366c184b606e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526276"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Disattivare i vincoli durante il riempimento di un set di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [disattivare i vincoli durante il riempimento di un set di dati](https://docs.microsoft.com/visualstudio/data-tools/turn-off-constraints-while-filling-a-dataset).  
  
  
Se un set di dati contiene i vincoli (ad esempio i vincoli di chiave esterna), theycan genera errori relativi all'ordine delle operazioni che vengono eseguite a fronte del set di dati. Ad esempio, il caricamento di record figlio prima dei record padre loadingrelated, può violano un vincolo e causare un errore. Non appena si carica un record figlio, il vincolo controlla il relativo record figlio e genera un errore.  
  
 Se non vi sono alcun meccanismo per consentire la sospensione di vincolo temporaneo, verrebbe generato un errore ogni volta che si è tentato di caricare un record nella tabella figlio. Un altro modo per sospendere tutti i vincoli in un set di dati è con il <xref:System.Data.DataRow.BeginEdit%2A>, e <xref:System.Data.DataRow.EndEdit%2A> proprietà.  
  
> [!NOTE]
>  Gli eventi di convalida (ad esempio, <xref:System.Data.DataTable.ColumnChanging> e<xref:System.Data.DataTable.RowChanging>) non verrà generato quando i vincoli sono disabilitati.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>Per sospendere l'aggiornamento dei vincoli a livello di codice  
  
-   Nell'esempio seguente viene illustrato come disattivare temporaneamente la verifica dei vincoli in un set di dati:  
  
     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Per sospendere l'aggiornamento dei vincoli tramite la finestra di progettazione set di dati  
  
1.  Aprire il set di dati nel [creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md). Per altre informazioni, vedere [procedura: aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Nel **le proprietà** impostare nella finestra di <xref:System.Data.DataSet.EnforceConstraints%2A> proprietà `false`.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Relazioni nei set di dati](../data-tools/relationships-in-datasets.md)

