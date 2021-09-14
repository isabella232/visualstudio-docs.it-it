---
title: Estendere la funzionalità di un TableAdapter
description: Informazioni su come estendere la funzionalità di un oggetto TableAdapter aggiungendo codice al file di classe parziale del TableAdapter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 29c7d9924d822cabdb28c9d3048e457cd7b88d64
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631398"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Estendere la funzionalità di un TableAdapter

È possibile estendere la funzionalità di un oggetto TableAdapter aggiungendo codice al file di classe parziale del TableAdapter.

Il codice che definisce un TableAdapter viene rigenerato quando vengono apportate modifiche al TableAdapter nel **Progettazione DataSet** o quando una procedura guidata modifica la configurazione di un oggetto TableAdapter. Per impedire l'eliminazione del codice durante la rigenerazione di un TableAdapter, aggiungere codice al file di classe parziale del TableAdapter.

Le classi parziali consentono di dividere il codice per una classe specifica tra più file fisici. Per altre informazioni, vedere [Parziale](/dotnet/visual-basic/language-reference/modifiers/partial) o [parziale (tipo).](/dotnet/csharp/language-reference/keywords/partial-type)

## <a name="locate-tableadapters-in-code"></a>Individuare gli oggetti TableAdapter nel codice

Mentre gli oggetti TableAdapter sono progettati con Progettazione DataSet **,** le classi TableAdapter generate non sono classi annidate di <xref:System.Data.DataSet> . Gli oggetti TableAdapter si trovano in uno spazio dei nomi in base al nome del set di dati associato del TableAdapter. Ad esempio, se l'applicazione contiene un set di dati denominato , gli oggetti TableAdapter si trovano `HRDataSet` nello spazio dei nomi `HRDataSetTableAdapters` . La convenzione di denominazione segue questo modello: *DatasetName*  +  `TableAdapters` .

Nell'esempio seguente si presuppone che un oggetto TableAdapter denominato `CustomersTableAdapter` sia in un progetto con `NorthwindDataSet` .

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Per creare una classe parziale per un oggetto TableAdapter

1. Aggiungere una nuova classe al progetto dal **menu** Project e selezionando **Aggiungi classe**.

2. Denominare la classe `CustomersTableAdapterExtended`.

3. Selezionare **Aggiungi**.

4. Sostituire il codice con lo spazio dei nomi e il nome di classe parziale corretti per il progetto, come indicato di seguito:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb" id="Snippet2":::

## <a name="see-also"></a>Vedi anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
