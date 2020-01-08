---
title: Disattivare i vincoli durante il riempimento di un set di dati
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 13cde04c3a10833c25fdc351d730b866f876e8da
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586133"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Disattivare i vincoli durante il riempimento di un set di dati

Se un set di dati contiene vincoli, ad esempio vincoli di chiave esterna, può generare errori correlati all'ordine delle operazioni eseguite sul set di dati. Ad esempio, il caricamento di record figlio prima del caricamento dei record padre correlati può violare un vincolo e causare un errore. Non appena si carica un record figlio, il vincolo controlla il record padre correlato e genera un errore.

Se non è disponibile alcun meccanismo per consentire la sospensione temporanea dei vincoli, viene generato un errore ogni volta che si tenta di caricare un record nella tabella figlio. Un altro modo per sospendere tutti i vincoli in un set di dati consiste nell'<xref:System.Data.DataRow.BeginEdit%2A>e <xref:System.Data.DataRow.EndEdit%2A> proprietà.

> [!NOTE]
> Gli eventi di convalida, ad esempio <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging>, non verranno generati quando i vincoli sono spenti.

## <a name="to-suspend-update-constraints-programmatically"></a>Per sospendere i vincoli di aggiornamento a livello di codice

- Nell'esempio seguente viene illustrato come disattivare temporaneamente il controllo dei vincoli in un set di dati:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Per sospendere i vincoli di aggiornamento usando il Progettazione DataSet

1. Aprire il set di dati in **Progettazione DataSet**. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un set di dati nel Progettazione DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Nella finestra **Proprietà** impostare la proprietà <xref:System.Data.DataSet.EnforceConstraints%2A> su `false`.

## <a name="see-also"></a>Vedere anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Relazioni nei set di dati](../data-tools/relationships-in-datasets.md)
