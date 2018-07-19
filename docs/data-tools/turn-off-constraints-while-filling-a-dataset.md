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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d128216f84228c9cd4946f9a38c6c1b7845f92f1
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117238"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Disattivare i vincoli durante il riempimento di un set di dati

Se un set di dati contiene i vincoli (ad esempio i vincoli di chiave esterna), possono generare errori correlati all'ordine delle operazioni che vengono eseguite a fronte del set di dati. Ad esempio, il caricamento dei record figlio prima del caricamento correlate record padre possono violino i vincoli e causare un errore. Non appena si carica un record figlio, il vincolo controlla il relativo record figlio e genera un errore.

Se non vi sono alcun meccanismo per consentire la sospensione di vincolo temporaneo, verrebbe generato un errore ogni volta che si è tentato di caricare un record nella tabella figlio. Un altro modo per sospendere tutti i vincoli in un set di dati è con il <xref:System.Data.DataRow.BeginEdit%2A>, e <xref:System.Data.DataRow.EndEdit%2A> proprietà.

> [!NOTE]
> Gli eventi di convalida (ad esempio, <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging>) non verrà generato quando i vincoli sono disabilitati.

## <a name="to-suspend-update-constraints-programmatically"></a>Per sospendere l'aggiornamento dei vincoli a livello di codice

-   Nell'esempio seguente viene illustrato come disattivare temporaneamente la verifica dei vincoli in un set di dati:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Per sospendere l'aggiornamento dei vincoli tramite la finestra di progettazione set di dati

1.  Aprire il set di dati nel **Progettazione Dataset**. Per altre informazioni, vedere [procedura dettagliata: creazione di un set di dati in Progettazione Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Nel **le proprietà** impostare nella finestra di <xref:System.Data.DataSet.EnforceConstraints%2A> proprietà `false`.

## <a name="see-also"></a>Vedere anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Relazioni nei set di dati](../data-tools/relationships-in-datasets.md)