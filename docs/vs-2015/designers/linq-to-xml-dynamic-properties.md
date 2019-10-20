---
title: Proprietà dinamiche in LINQ to XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ff0b31512711b8888b05fcfde191c8cb5c47d99
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664257"
---
# <a name="linq-to-xml-dynamic-properties"></a>Proprietà dinamiche in LINQ to XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contenuto della sezione vengono fornite informazioni di riferimento relative alle proprietà dinamiche di LINQ to XML. In particolare, queste proprietà vengono esposte dalle classi <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement>, incluse nello spazio dei nomi <xref:System.Xml.Linq>.

 Come illustrato nell'argomento [Panoramica del data binding di WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), ogni proprietà dinamica è equivalente a una proprietà o a un metodo pubblico della stessa classe. Questi membri standard devono essere usati per la maggior parte degli scopi. Le proprietà dinamiche vengono fornite specificamente per gli scenari di associazione dati LINQ to XML. Per altre informazioni sui membri standard di queste classi, vedere gli argomenti di riferimento <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement>.

 Relativamente ai valori risolti, le proprietà dinamiche descritte in questa sezione rientrano in due categorie:

- Proprietà semplici, ad esempio le proprietà `Value` nelle classi <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement>, che vengono risolte in un singolo valore.

- Valori indicizzati, ad esempio le proprietà [Elements](../designers/elements-xelement-dynamic-property.md) e [Descendants](../designers/descendants-xelement-dynamic-property.md) di <xref:System.Xml.Linq.XElement>, che vengono risolti in un tipo di indicizzatore. Affinché i tipi di indicizzatori vengano risolti nel valore o nella raccolta desiderata, è necessario passare un parametro di nome espanso.

  Tutte le proprietà dinamiche che restituiscono un valore indicizzato di tipo <xref:System.Collections.Generic.IEnumerable%601> usano l'esecuzione posticipata. Per altre informazioni sull'esecuzione posticipata, vedere [Introduzione alle query LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).

## <a name="in-this-section"></a>Contenuto della sezione

|Argomento|Descrizione|
|-----------|-----------------|
|[Proprietà dinamiche della classe XAttribute](../designers/xattribute-class-dynamic-properties.md)|Vengono forniti dettagli sulle proprietà dinamiche esposte dalla classe <xref:System.Xml.Linq.XAttribute>.|
|[Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)|Vengono forniti dettagli sulle proprietà dinamiche esposte dalla classe <xref:System.Xml.Linq.XElement>.|

## <a name="reference"></a>Reference
 <xref:System.Xml.Linq>

 <xref:System.Xml.Linq.XElement?displayProperty=fullName>

 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Vedere anche
 [Data Binding WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md) [data binding WPF con LINQ to XML Panoramica](../designers/wpf-data-binding-with-linq-to-xml-overview.md) [introduttiva alle query LINQC#()](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)
