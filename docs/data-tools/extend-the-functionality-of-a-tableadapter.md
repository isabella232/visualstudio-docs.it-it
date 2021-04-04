---
title: Estendere la funzionalità di un TableAdapter
description: Informazioni su come estendere la funzionalità di un TableAdapter aggiungendo codice al file di classe parziale del TableAdapter.
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
ms.workload:
- data-storage
ms.openlocfilehash: f8cea8ec761bf50ddc0f928112975c366f62418b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215838"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Estendere la funzionalità di un TableAdapter

È possibile estendere la funzionalità di un TableAdapter aggiungendo codice al file di classe parziale del TableAdapter.

Il codice che definisce un TableAdapter viene rigenerato quando vengono apportate modifiche a TableAdapter nell' **Progettazione DataSet** o quando una procedura guidata modifica la configurazione di un TableAdapter. Per impedire l'eliminazione del codice durante la rigenerazione di un TableAdapter, aggiungere il codice al file di classe parziale del TableAdapter.

Le classi parziali consentono di dividere il codice per una classe specifica tra più file fisici. Per ulteriori informazioni, vedere [partial](/dotnet/visual-basic/language-reference/modifiers/partial) o [partial (Type)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Individuare gli oggetti TableAdapter nel codice

Sebbene i TableAdapter siano progettati con la **Progettazione DataSet**, le classi TableAdapter generate non sono classi annidate di <xref:System.Data.DataSet> . Gli oggetti TableAdapter si trovano in uno spazio dei nomi in base al nome del set di dati associato del TableAdapter. Se, ad esempio, l'applicazione contiene un set di dati denominato `HRDataSet` , gli oggetti TableAdapter si troveranno `HRDataSetTableAdapters` nello spazio dei nomi. La convenzione di denominazione segue questo modello: *DataSetName*  +  `TableAdapters` .

Nell'esempio seguente si presuppone che un oggetto TableAdapter denominato `CustomersTableAdapter` si trovi in un progetto con `NorthwindDataSet` .

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Per creare una classe parziale per un TableAdapter

1. Aggiungere una nuova classe al progetto passando al menu **progetto** e selezionando **Aggiungi classe**.

2. Denominare la classe `CustomersTableAdapterExtended`.

3. Selezionare **Aggiungi**.

4. Sostituire il codice con lo spazio dei nomi corretto e il nome della classe parziale per il progetto come indicato di seguito:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb" id="Snippet2":::

## <a name="see-also"></a>Vedi anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
