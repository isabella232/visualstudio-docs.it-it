---
title: 'Procedura: ottenere versioni specifiche di un DataRow | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- row states
- updating datasets, row states
- DataRow object
ms.assetid: d7cde25e-cef5-4559-b994-be00e258ac1f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: ed409bdafaa15052a7190480a7cbc46ac766de84
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519106"
---
# <a name="how-to-get-specific-versions-of-a-datarow"></a>Procedura: ottenere versioni specifiche di un DataRow
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando vengono apportate modifiche alle righe di dati, il set di dati consente di mantenere entrambi originale (<xref:System.Data.DataRowVersion>) e dell'operatore new (<xref:System.Data.DataRowVersion>) le versioni di riga. Ad esempio, prima di chiamare il `AcceptChanges` metodo, l'applicazione possa accedere a diverse versioni di un record (come definito nel <xref:System.Data.DataRowVersion> enumerazione) ed elaborarli di conseguenza le modifiche.  
  
> [!NOTE]
>  Versioni diverse di una riga esistano solo dopo che è stata modificata e prima perché ha avuto la `AcceptChanges` metodo chiamato. Dopo il `AcceptChanges` chiamata al metodo, le versioni correnti e originali sono uguali.  
  
 Passando il <xref:System.Data.DataRowVersion> valore con l'indice di colonna (o nome della colonna sotto forma di stringa) restituisce il valore di particolare versione di riga tale colonna. La colonna modificata è identificata durante la <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> eventi, in modo che è opportuno esaminare le diverse versioni ai fini della convalida di riga. Tuttavia, se è stata sospesa temporaneamente i vincoli, tali eventi non verranno generati e sarà necessario identificare a livello di programmazione quali colonne sono state modificate. È possibile farlo eseguendo l'iterazione tramite il <xref:System.Data.DataTable.Columns%2A> raccolta e confrontare i diversi <xref:System.Data.DataRowVersion> valori.  
  
## <a name="accessing-the-original-version-of-a-datarow"></a>Accesso alla versione originale di un DataRow  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Per ottenere la versione originale di un record  
  
-   Accedere al valore di una colonna passando il <xref:System.Data.DataRowVersion> della riga di cui si desidera restituire.  
  
     L'esempio seguente illustra come usare un <xref:System.Data.DataRowVersion> valore da ottenere il valore originale di una `CompanyName` campo un <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="accessing-the-current-version-of-a-datarow"></a>Accesso alla versione corrente di un DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Per ottenere la versione corrente di un record  
  
-   Accedere al valore di una colonna e aggiungere un parametro per l'indice che indica quale versione di una riga a cui si desidera restituire.  
  
     L'esempio seguente illustra come usare un <xref:System.Data.DataRowVersion> valore da ottenere il valore corrente di un `CompanyName` campo un <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Salvataggio dei dati](../data-tools/saving-data.md)   
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Panoramica delle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)