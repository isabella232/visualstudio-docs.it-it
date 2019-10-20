---
title: Disabilitare i vincoli durante il riempimento di un set di dati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6646f669bf2c465d8e0f705f8fba956b979952ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667172"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Disattivare i vincoli durante il riempimento di un set di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se un set di dati contiene vincoli, ad esempio vincoli di chiave esterna, possono far scattare genera errori correlati all'ordine delle operazioni eseguite sul set di dati. Ad esempio, il caricamento dei record figlio prima che i record padre loadingrelated possano violare un vincolo e causare un errore. Non appena si carica un record figlio, il vincolo controlla il record padre correlato e genera un errore.

 Se non è disponibile alcun meccanismo per consentire la sospensione temporanea dei vincoli, viene generato un errore ogni volta che si tenta di caricare un record nella tabella figlio. Un altro modo per sospendere tutti i vincoli in un set di dati consiste nell'<xref:System.Data.DataRow.BeginEdit%2A> e <xref:System.Data.DataRow.EndEdit%2A> proprietà.

> [!NOTE]
> Gli eventi di convalida, ad esempio <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging>, non verranno generati quando i vincoli sono spenti.

### <a name="to-suspend-update-constraints-programmatically"></a>Per sospendere i vincoli di aggiornamento a livello di codice

- Nell'esempio seguente viene illustrato come disattivare temporaneamente il controllo dei vincoli in un set di dati:

     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]

### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Per sospendere i vincoli di aggiornamento usando il Progettazione DataSet

1. Aprire il set di dati nel Progettazione DataSet. Per altre informazioni, vedere [procedura: aprire un set di dati nel Progettazione DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Nella finestra **Proprietà** impostare la proprietà <xref:System.Data.DataSet.EnforceConstraints%2A> su `false`.

## <a name="see-also"></a>Vedere anche
 [Compilare set di impostazioni usando relazioni TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) [nei DataSet](../data-tools/relationships-in-datasets.md)
