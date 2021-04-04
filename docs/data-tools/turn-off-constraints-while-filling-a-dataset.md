---
title: Disattivare i vincoli durante il riempimento di un set di dati
description: Informazioni su come disattivare i vincoli durante il riempimento di un set di dati. Sospendere i vincoli di aggiornamento a livello di codice o usando il Progettazione DataSet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 3280894ba1634f9775def74a88dcb413c94ba77a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215708"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Disattivare i vincoli durante il riempimento di un set di dati

Se un set di dati contiene vincoli, ad esempio vincoli di chiave esterna, può generare errori correlati all'ordine delle operazioni eseguite sul set di dati. Ad esempio, il caricamento di record figlio prima del caricamento dei record padre correlati può violare un vincolo e causare un errore. Non appena si carica un record figlio, il vincolo controlla il record padre correlato e genera un errore.

Se non è disponibile alcun meccanismo per consentire la sospensione temporanea dei vincoli, viene generato un errore ogni volta che si tenta di caricare un record nella tabella figlio. Un altro modo per sospendere tutti i vincoli in un set di dati è con le <xref:System.Data.DataRow.BeginEdit%2A> proprietà, e <xref:System.Data.DataRow.EndEdit%2A> .

> [!NOTE]
> Gli eventi di convalida, ad esempio <xref:System.Data.DataTable.ColumnChanging> e, <xref:System.Data.DataTable.RowChanging> non verranno generati quando i vincoli sono spenti.

## <a name="to-suspend-update-constraints-programmatically"></a>Per sospendere i vincoli di aggiornamento a livello di codice

- Nell'esempio seguente viene illustrato come disattivare temporaneamente il controllo dei vincoli in un set di dati:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet10":::

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Per sospendere i vincoli di aggiornamento usando il Progettazione DataSet

1. Aprire il set di dati in **Progettazione DataSet**. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un set di dati nel Progettazione DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Nella finestra **Proprietà** impostare la proprietà <xref:System.Data.DataSet.EnforceConstraints%2A> su `false`.

## <a name="see-also"></a>Vedi anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Relazioni nei set di dati](../data-tools/relationships-in-datasets.md)
