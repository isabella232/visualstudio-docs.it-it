---
title: Salvare un set di dati come XML
description: Salvare un set di dati come XML. Accedere ai dati XML in un set di dati chiamando i metodi XML disponibili nel set di dati, ad esempio GetXml o WriteXml.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 144412b8e738391e1c0122efaef3dee658010422556541987f09b2ca31881697
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346934"
---
# <a name="save-a-dataset-as-xml"></a>Salvare un set di dati come XML

Accedere ai dati XML in un set di dati chiamando i metodi XML disponibili nel set di dati. Per salvare i dati in formato XML, è possibile chiamare il metodo <xref:System.Data.DataSet.GetXml%2A> o il metodo di un oggetto <xref:System.Data.DataSet.WriteXml%2A> <xref:System.Data.DataSet> .

La chiamata al metodo restituisce una stringa contenente i dati di tutte le tabelle dati nel set di dati <xref:System.Data.DataSet.GetXml%2A> formattato come XML.

La chiamata <xref:System.Data.DataSet.WriteXml%2A> al metodo invia i dati in formato XML a un file specificato dall'utente.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Per salvare i dati in un set di dati come XML in una variabile

- Il metodo <xref:System.Data.DataSet.GetXml%2A> restituisce un oggetto <xref:System.String>. Dichiarare una variabile di <xref:System.String> tipo e assegnarle i risultati del <xref:System.Data.DataSet.GetXml%2A> metodo .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet12":::

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Per salvare i dati in un set di dati come XML in un file

- Il <xref:System.Data.DataSet.WriteXml%2A> metodo dispone di diversi overload. Dichiarare una variabile e assegnarle un percorso valido in cui salvare il file. Il codice seguente illustra come salvare i dati in un file:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet13":::

## <a name="see-also"></a>Vedi anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
