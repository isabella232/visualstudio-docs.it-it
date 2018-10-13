---
title: 'Procedura: eseguire il Commit delle modifiche in un set di dati | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataSet.AcceptChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], committing changes
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 41d27c248763f42db6543db0a9b4e56e4c4eac82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276432"
---
# <a name="how-to-commit-changes-in-a-dataset"></a>Procedura: eseguire il commit delle modifiche in un dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si apportano modifiche ai record in un set di dati per l'aggiornamento, inserimento ed eliminazione di record, il set di dati mantiene le versioni originali e correnti dei record. Inoltre, ogni riga del <xref:System.Data.DataRow.RowState%2A> tiene traccia della proprietà se i record si trovano nello stato originale o sono stati aggiornati, inseriti o eliminati. Queste informazioni sono utili quando è necessario trovare una particolare versione di una riga. In genere, si otterrebbe un sottoinsieme di tutti i record modificati per l'invio a un altro processo. Per altre informazioni, vedere [procedura: recuperare le righe modificate](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9). Dopo aver elaborato tutte le righe modificate, è possibile applicare le modifiche chiamando il `AcceptChanges` metodo per il <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, o <xref:System.Data.DataRow>. Il `AcceptChanges` metodo viene chiamato automaticamente quando si chiamano i metodi di aggiornamento di un [TableAdapter](../data-tools/tableadapter-overview.md) o adattatore di dati. Chiamare `AcceptChanges` dopo l'invio di modifiche a un database.  
  
 Quando si chiama <xref:System.Data.DataSet.AcceptChanges%2A> nella <xref:System.Data.DataSet>, qualsiasi <xref:System.Data.DataRow> oggetti ancora in modalità di modifica completate correttamente le modifiche apportate. Il <xref:System.Data.DataRow.RowState%2A> proprietà della ognuno <xref:System.Data.DataRow> anche viene modificato. <xref:System.Data.DataRowState> e <xref:System.Data.DataRowState> righe diventare <xref:System.Data.DataRowState>, e <xref:System.Data.DataRowState> vengono rimosse le righe.  
  
 Se il <xref:System.Data.DataSet> contiene <xref:System.Data.ForeignKeyConstraint> oggetti, richiamando il <xref:System.Data.DataSet.AcceptChanges%2A> metodo determina inoltre il <xref:System.Data.AcceptRejectRule> possano essere applicate.  
  
### <a name="to-commit-changes-in-a-dataset"></a>Per eseguire il commit delle modifiche in un set di dati  
  
-   Chiamare il `AcceptChanges` metodo in uno una <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, o <xref:System.Data.DataRow> per salvare le modifiche in tali oggetti.  
  
     Nell'esempio seguente viene illustrato come chiamare le `AcceptChanges` metodo per eseguire il commit delle modifiche nel `Customers` tabella dopo l'aggiornamento di un'origine dati:  
  
     [!code-csharp[VbRaddataEditing#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#11)]
     [!code-vb[VbRaddataEditing#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#11)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [Salvataggio dei dati](../data-tools/saving-data.md)   
 [Procedura: recuperare le righe modificate](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)