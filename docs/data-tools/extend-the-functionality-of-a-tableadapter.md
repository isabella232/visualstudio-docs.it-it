---
title: Estendere la funzionalità di un TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 989eb815a6e55b5ecaed0b960963eb036b73065a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970539"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Estendere la funzionalità di un TableAdapter

È possibile estendere la funzionalità di un oggetto TableAdapter aggiungendo codice al file di classe parziale dell'oggetto TableAdapter.

Il codice che definisce un oggetto TableAdapter viene rigenerato quando vengono apportate modifiche all'oggetto TableAdapter nel **Progettazione Dataset**, o quando una procedura guidata modifica la configurazione di un oggetto TableAdapter. Per evitare che il codice in corso l'eliminazione durante la rigenerazione di un oggetto TableAdapter, aggiungere codice al file di classe parziale dell'oggetto TableAdapter.

Le classi parziali consentono di codice per una classe specifica da dividere tra più file fisici. Per altre informazioni, vedere [parziali](/dotnet/visual-basic/language-reference/modifiers/partial) oppure [parziale (tipo)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Individuare gli oggetti TableAdapter nel codice

Anche se gli oggetti TableAdapter sono progettati con la **Progettazione Dataset**, le classi TableAdapter generate non sono classi annidate di <xref:System.Data.DataSet>. Gli oggetti TableAdapter si trovano in uno spazio dei nomi basato sul nome del set di dati dell'oggetto TableAdapter associato. Ad esempio, se l'applicazione contiene un set di dati denominato `HRDataSet`, gli oggetti TableAdapter potrebbe trovarsi nel `HRDataSetTableAdapters` dello spazio dei nomi. (La convenzione di denominazione segue questo modello: DataSetName

Nell'esempio seguente si presuppone un oggetto TableAdapter denominato `CustomersTableAdapter`si trova in un progetto con `NorthwindDataSet`.

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Per creare una classe parziale per un oggetto TableAdapter

1.  Aggiungere una nuova classe al progetto selezionando il **Project** menu e selezionando **Aggiungi classe**.

2.  Assegnare alla classe il nome `CustomersTableAdapterExtended`.

3.  Selezionare **Aggiungi**.

4.  Sostituire il codice con il nome di classe parziale per il progetto e spazio dei nomi corretto come indicato di seguito:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>Vedere anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)