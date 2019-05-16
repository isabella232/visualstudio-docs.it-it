---
title: Estendere le funzionalità di un oggetto TableAdapter | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7e14acedeab457df10cc011a94f96d7202972eea
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697890"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Estendere la funzionalità di un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile estendere la funzionalità di un oggetto TableAdapter aggiungendo codice al file di classe parziale dell'oggetto TableAdapter.  
  
 Il codice che definisce un oggetto TableAdapter viene rigenerato quando vengono apportate modifiche all'oggetto TableAdapter nel **Progettazione Dataset**, o quando una procedura guidata modifica la configurazione di un oggetto TableAdapter. Per evitare che il codice in corso l'eliminazione durante la rigenerazione di un oggetto TableAdapter, aggiungere codice al file di classe parziale dell'oggetto TableAdapter.  
  
 Le classi parziali consentono di codice per una classe specifica da dividere tra più file fisici. Per altre informazioni, vedere [parziali](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) oppure [parziale (tipo)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
## <a name="locate-tableadapters-in-code"></a>Individuare gli oggetti TableAdapter nel codice  
 Anche se gli oggetti TableAdapter sono progettati con la **Progettazione Dataset**, le classi TableAdapter generate non sono classi annidate di <xref:System.Data.DataSet>. Gli oggetti TableAdapter si trovano in uno spazio dei nomi basato sul nome del set di dati dell'oggetto TableAdapter associato. Ad esempio, se l'applicazione contiene un set di dati denominato `HRDataSet`, gli oggetti TableAdapter potrebbe trovarsi nel `HRDataSetTableAdapters` dello spazio dei nomi. (La convenzione di denominazione segue questo modello: *DatasetName* + `TableAdapters`).  
  
 Nell'esempio seguente si presuppone un oggetto TableAdapter denominato `CustomersTableAdapter`si trova in un progetto con `NorthwindDataSet`.  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Per creare una classe parziale per un oggetto TableAdapter  
  
1. Aggiungere una nuova classe al progetto selezionando il **Project** menu e selezionando**Aggiungi classe**.  
  
2. Assegnare alla classe il nome `CustomersTableAdapterExtended`.  
  
3. Selezionare **Aggiungi**.  
  
4. Sostituire il codice con il nome di classe parziale per il progetto e spazio dei nomi corretto come indicato di seguito:  
  
     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]  
  
## <a name="see-also"></a>Vedere anche  
 [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
