---
title: Estendere la funzionalità di un TableAdapter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19367f812a87d6aa585e123100f1d08144c57ff9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672366"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Estendere la funzionalità di un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile estendere la funzionalità di un TableAdapter aggiungendo codice al file di classe parziale del TableAdapter.

 Il codice che definisce un TableAdapter viene rigenerato quando vengono apportate modifiche a TableAdapter nell' **Progettazione DataSet**o quando una procedura guidata modifica la configurazione di un TableAdapter. Per impedire l'eliminazione del codice durante la rigenerazione di un TableAdapter, aggiungere il codice al file di classe parziale del TableAdapter.

 Le classi parziali consentono di dividere il codice per una classe specifica tra più file fisici. Per ulteriori informazioni, vedere [partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) o [partial (Type)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

## <a name="locate-tableadapters-in-code"></a>Individuare gli oggetti TableAdapter nel codice
 Sebbene i TableAdapter siano progettati con la **Progettazione DataSet**, le classi TableAdapter generate non sono classi annidate di <xref:System.Data.DataSet> . Gli oggetti TableAdapter si trovano in uno spazio dei nomi in base al nome del set di dati associato del TableAdapter. Se, ad esempio, l'applicazione contiene un set di dati denominato `HRDataSet` , gli oggetti TableAdapter si troveranno `HRDataSetTableAdapters` nello spazio dei nomi. La convenzione di denominazione segue questo modello: *DataSetName*  +  `TableAdapters` .

 Nell'esempio seguente si presuppone che un oggetto TableAdapter denominato `CustomersTableAdapter` si trovi in un progetto con `NorthwindDataSet` .

#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Per creare una classe parziale per un TableAdapter

1. Aggiungere una nuova classe al progetto passando al menu **progetto** e selezionando**Aggiungi classe**.

2. Denominare la classe `CustomersTableAdapterExtended`.

3. Selezionare **Aggiungi**.

4. Sostituire il codice con lo spazio dei nomi corretto e il nome della classe parziale per il progetto come indicato di seguito:

     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]

## <a name="see-also"></a>Vedere anche
 [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
