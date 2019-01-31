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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: c1eff1b80807b040bd50d7e4e5f2045c73c46929
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011819"
---
# <a name="save-a-dataset-as-xml"></a>Salvare un set di dati come XML

Accedere ai dati XML in un set di dati chiamando i metodi XML disponibili nel set di dati. Per salvare i dati in formato XML, è possibile chiamare il <xref:System.Data.DataSet.GetXml%2A> metodo o il <xref:System.Data.DataSet.WriteXml%2A> metodo di un <xref:System.Data.DataSet>.

La chiamata di <xref:System.Data.DataSet.GetXml%2A> metodo restituisce una stringa che contiene i dati da tutte le tabelle di dati nel set di dati in formato XML.

La chiamata di <xref:System.Data.DataSet.WriteXml%2A> metodo invia i dati in formato XML in un file specificato.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Per salvare i dati in un set di dati in formato XML a una variabile

- Il metodo <xref:System.Data.DataSet.GetXml%2A> restituisce un tipo <xref:System.String>. Dichiarare una variabile di tipo <xref:System.String> e assegnare i risultati del <xref:System.Data.DataSet.GetXml%2A> (metodo).

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Per salvare i dati in un set di dati come XML in un file

- Il <xref:System.Data.DataSet.WriteXml%2A> metodo dispone di diversi overload. Dichiarare una variabile e assegnarla a un percorso valido per salvare il file. Il codice seguente viene illustrato come salvare i dati in un file:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)