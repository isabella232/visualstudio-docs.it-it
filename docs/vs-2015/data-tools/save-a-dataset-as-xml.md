---
title: Salvare un set di dati in formato XML | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2e4331b59c532e681c7e10ab8e43b953e9f72b18
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059695"
---
# <a name="save-a-dataset-as-xml"></a>Salvare un set di dati come XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I dati XML in un set di dati sono accessibili chiamando i metodi XML disponibili nel set di dati. Per salvare i dati in formato XML, è possibile chiamare il <xref:System.Data.DataSet.GetXml%2A> metodo o il <xref:System.Data.DataSet.WriteXml%2A> metodo di un <xref:System.Data.DataSet>.  
  
 La chiamata di <xref:System.Data.DataSet.GetXml%2A> metodo restituisce una stringa che contiene i dati da tutte le tabelle di dati nel set di dati in formato XML.  
  
 La chiamata di <xref:System.Data.DataSet.WriteXml%2A> metodo invia i dati in formato XML in un file specificato.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Per salvare i dati in un set di dati in formato XML a una variabile  
  
- Il <xref:System.Data.DataSet.GetXml%2A> metodo restituisce un <xref:System.String>. Ciò significa che si dichiara una variabile di tipo <xref:System.String> e assegnare i risultati del <xref:System.Data.DataSet.GetXml%2A> (metodo).  
  
     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Per salvare i dati in un set di dati come XML in un file  
  
- Il <xref:System.Data.DataSet.WriteXml%2A> metodo dispone di diversi overload. Il codice seguente viene illustrato come salvare i dati in un file. Dichiarare una variabile e assegnarla a un percorso valido per salvare il file.  
  
     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
