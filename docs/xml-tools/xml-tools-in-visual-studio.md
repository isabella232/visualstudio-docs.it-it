---
title: Strumenti XML in Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 350908d2d21a30985e624ff9526c22d6e5cf9bb1
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349413"
---
# <a name="xml-tools-in-visual-studio"></a>Strumenti XML in Visual Studio

*Extensible Markup Language (XML)* è un linguaggio di markup che fornisce un formato per descrivere i dati. Offre una maggiore precisione per le dichiarazioni del contenuto e risultati di ricerca più significativi tra più piattaforme. Il linguaggio XML consente inoltre di separare la presentazione dai dati. Ad esempio, in HTML si usano i tag per indicare al browser di visualizzare i dati in grassetto o corsivo. In XML invece si usano i tag solo per descrivere i dati, ad esempio nome della città, temperatura e pressione barometrica. Nel XML, fogli di stile, ad esempio fogli di stile XSL (Extensible Language) e fogli di stile (CSS) vengono utilizzati per presentare i dati in un browser. XML separa i dati dalla presentazione e dall'elaborazione. In questo modo è possibile presentare ed elaborare i dati come si vuole, applicando fogli di stile e applicazioni diversi.

XML è un sottoinsieme di SGML ottimizzato per la distribuzione sul Web. È definito dal World Wide Web Consortium (W3C) Questa standardizzazione garantisce che i dati strutturati siano uniformi e indipendenti da applicazioni o fornitori.

XML è alla base di molte funzionalità di Visual Studio e .NET Framework. Nell'elenco di articolo seguente descrive gli strumenti e funzionalità correlate a XML disponibili in Visual Studio e .NET Framework.

Per altre informazioni, vedere il <xref:System.Xml?displayProperty=fullName> documentazione.

## <a name="reference"></a>Riferimenti

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) espone il [Editor XML](http://go.microsoft.com/fwlink/?LinkId=228249) analizzato albero tramite [perché](http://go.microsoft.com/fwlink/?LinkId=228250) per tutti i documenti XML.

[Riferimento agli standard XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) fornisce informazioni sulle tecnologie XML, tra cui XML, definizione DTD (Document Type Definition), il linguaggio XML Schema definition (XSD) e XSLT.

<xref:System.Xml?displayProperty=fullName> Descrive le classi e altri elementi che costituiscono il <xref:System.Xml> dello spazio dei nomi e vengono forniti collegamenti a informazioni più dettagliate su ogni elemento.

<xref:System.Xml.Serialization?displayProperty=fullName> Descrive le classi e altri elementi che costituiscono il <xref:System.Xml.Serialization> dello spazio dei nomi e vengono forniti collegamenti a informazioni più dettagliate su ogni elemento.

## <a name="related-sections"></a>Sezioni correlate

[Oggetto del modello DOM (Document XML)](/dotnet/standard/data/xml/xml-document-object-model-dom) descrive il modo in cui il <xref:System.Xml.XmlDocument> e le relative classi associate conformano a W3C Document Object Model (Core) livello 1 e specifiche per il supporto dello spazio dei nomi di livello 2.

[L'elaborazione dati XML con XmlReader e XmlWriter](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc189001\(v\=vs.95\))

[Trasformazioni XSLT](/dotnet/standard/data/xml/xslt-transformations) descrive il modo in cui il <xref:System.Xml.Xsl.XslCompiledTransform> classe implementa la raccomandazione XSLT 1.0.

[Elaborare dati XML utilizzando il modello di dati XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model) descrive il modo in cui il <xref:System.Xml.XPath.XPathNavigator> classe può elaborare dati XML archiviati in un <xref:System.Xml.XPath.XPathDocument> o un <xref:System.Xml.XmlDocument> oggetto. La classe <xref:System.Xml.XPath.XPathNavigator> è basata sul modello di dati XQuery 1.0 e XPath 2.0 e può essere usata per spostarsi tra i dati XML e per modificarli.

[Modello SOM (Schema Object Model) XML](/dotnet/standard/data/xml/xml-schema-object-model-som) descrive le classi usate per la creazione e modifica di schemi XML, fornendo un <xref:System.Xml.Schema.XmlSchema> classe per caricare e modificare uno schema.