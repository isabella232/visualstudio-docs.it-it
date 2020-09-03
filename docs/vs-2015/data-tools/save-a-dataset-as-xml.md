---
title: Salvare un set di dati come XML | Microsoft Docs
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
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e64c3c17934e5cdc5d6ca1f510c7164b86a77c1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652855"
---
# <a name="save-a-dataset-as-xml"></a>Salvare un set di dati come XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile accedere ai dati XML in un DataSet chiamando i metodi XML disponibili nel DataSet. Per salvare i dati in formato XML, è possibile chiamare il <xref:System.Data.DataSet.GetXml%2A> metodo o il <xref:System.Data.DataSet.WriteXml%2A> metodo di un oggetto <xref:System.Data.DataSet> .

 La chiamata al <xref:System.Data.DataSet.GetXml%2A> metodo restituisce una stringa che contiene i dati di tutte le tabelle di dati nel DataSet formattato come XML.

 La chiamata al <xref:System.Data.DataSet.WriteXml%2A> metodo invia i dati in formato XML a un file specificato.

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Per salvare i dati in un DataSet come XML in una variabile

- Il <xref:System.Data.DataSet.GetXml%2A> metodo restituisce un oggetto <xref:System.String> . Ciò significa che si dichiara una variabile di tipo <xref:System.String> e si assegnano i risultati del <xref:System.Data.DataSet.GetXml%2A> metodo.

     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Per salvare i dati in un set di dati come XML in un file

- Il <xref:System.Data.DataSet.WriteXml%2A> metodo dispone di diversi overload. Nel codice seguente viene illustrato come salvare i dati in un file. Dichiarare una variabile e assegnarle un percorso valido in cui salvare il file.

     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]

## <a name="see-also"></a>Vedere anche
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
