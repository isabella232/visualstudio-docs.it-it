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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ab5ff2fe9702d56ddc2c4b767ac40f3d63ddbe15
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631115"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Disattivare i vincoli durante il riempimento di un set di dati

Se un set di dati contiene vincoli, ad esempio vincoli di chiave esterna, possono generare errori correlati all'ordine delle operazioni eseguite sul set di dati. Ad esempio, il caricamento dei record figlio prima del caricamento dei record padre correlati può violare un vincolo e causare un errore. Non appena si carica un record figlio, il vincolo verifica la presenza del record padre correlato e genera un errore.

Se non esistesse alcun meccanismo per consentire la sospensione temporanea dei vincoli, viene generato un errore ogni volta che si tenta di caricare un record nella tabella figlio. Un altro modo per sospendere tutti i vincoli in un set di dati è con <xref:System.Data.DataRow.BeginEdit%2A> le proprietà , e <xref:System.Data.DataRow.EndEdit%2A> .

> [!NOTE]
> Gli eventi di convalida , ad esempio e , non verranno <xref:System.Data.DataTable.ColumnChanging> generati quando i vincoli sono <xref:System.Data.DataTable.RowChanging> disattivati.

## <a name="to-suspend-update-constraints-programmatically"></a>Per sospendere l'aggiornamento dei vincoli a livello di codice

- Nell'esempio seguente viene illustrato come disattivare temporaneamente il controllo dei vincoli in un set di dati:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet10":::

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Per sospendere i vincoli di aggiornamento utilizzando il Progettazione DataSet

1. Aprire il set di dati in **Progettazione DataSet**. Per altre informazioni, vedere [Procedura dettagliata: Creazione di un set di dati nel Progettazione DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Nella finestra **Proprietà** impostare la proprietà <xref:System.Data.DataSet.EnforceConstraints%2A> su `false`.

## <a name="see-also"></a>Vedi anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Relazioni nei set di dati](../data-tools/relationships-in-datasets.md)
