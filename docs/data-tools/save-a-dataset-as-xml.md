---
title: Salvare un set di dati come XML
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3198b94b1248f20b178e85e9e75a2765e6191c28
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586302"
---
# <a name="save-a-dataset-as-xml"></a>Salvare un set di dati come XML

Accedere ai dati XML in un DataSet chiamando i metodi XML disponibili nel DataSet. Per salvare i dati in formato XML, è possibile chiamare il metodo <xref:System.Data.DataSet.GetXml%2A> o il metodo <xref:System.Data.DataSet.WriteXml%2A> di un <xref:System.Data.DataSet>.

La chiamata al metodo <xref:System.Data.DataSet.GetXml%2A> restituisce una stringa che contiene i dati di tutte le tabelle di dati nel DataSet formattato come XML.

La chiamata al metodo <xref:System.Data.DataSet.WriteXml%2A> invia i dati in formato XML a un file specificato.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Per salvare i dati in un DataSet come XML in una variabile

- Il metodo <xref:System.Data.DataSet.GetXml%2A> restituisce un tipo <xref:System.String>. Dichiarare una variabile di tipo <xref:System.String> e assegnargli i risultati del metodo <xref:System.Data.DataSet.GetXml%2A>.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Per salvare i dati in un set di dati come XML in un file

- Il metodo <xref:System.Data.DataSet.WriteXml%2A> dispone di diversi overload. Dichiarare una variabile e assegnarle un percorso valido in cui salvare il file. Il codice seguente illustra come salvare i dati in un file:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
