---
title: Strumenti XML
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9a46523c4c856367e77c345c7e44d0dbc87508f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845981"
---
# <a name="xml-tools-in-visual-studio"></a>Strumenti XML in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extensible Markup Language (XML) * è un linguaggio di markup che fornisce un formato per la descrizione dei dati. Offre una maggiore precisione per le dichiarazioni del contenuto e risultati di ricerca più significativi tra più piattaforme. Il linguaggio XML consente inoltre di separare la presentazione dai dati. Ad esempio, in HTML si usano i tag per indicare al browser di visualizzare i dati in grassetto o corsivo. In XML invece si usano i tag solo per descrivere i dati, ad esempio nome della città, temperatura e pressione barometrica. In XML si usano i fogli di stile, ad esempio XSL (Extensible Stylesheet Language) e CSS (Cascading Style Sheet) per presentare i dati in un browser. XML separa i dati dalla presentazione e dall'elaborazione. In questo modo è possibile presentare ed elaborare i dati come si vuole, applicando fogli di stile e applicazioni diversi.

 XML è un sottoinsieme di SGML ottimizzato per la distribuzione sul Web. È definito dal World Wide Web Consortium (W3C) Questa standardizzazione garantisce che i dati strutturati siano uniformi e indipendenti da applicazioni o fornitori.

 Molte funzionalità di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sono basate su XML. L'argomento seguente descrive gli strumenti e le funzionalità relativi a XML disponibili in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Per ulteriori informazioni, vedere il [centro](https://msdn.microsoft.com/data/bb190600.aspx)per sviluppatori XML, che fornisce la documentazione più recente, informazioni tecniche, download, newsgroup e altre risorse per gli sviluppatori XML.

## <a name="in-this-section"></a>Contenuto della sezione
 [Utilizzo di dati XML](../xml-tools/working-with-xml-data.md) Viene illustrato il ruolo del codice XML nel modo in cui vengono gestiti i dati [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 [Debug di XSLT](../xml-tools/debugging-xslt.md) Fornisce collegamenti ad argomenti sull'uso del debugger di Visual Studio per eseguire il debug di XSLT.

## <a name="reference"></a>Informazioni di riferimento
 [ EditorMicrosoft.VisualStudio.Xml](https://msdn.microsoft.com/library/microsoft.visualstudio.xmleditor.aspx) Espone l'albero di analisi dell' [editor XML](https://msdn.microsoft.com/library/ms255810.aspx) tramite [System.Xml. LINQ](https://msdn.microsoft.com/library/system.xml.linq.aspx) per qualsiasi documento XML.

 [Riferimento agli standard XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) Vengono fornite informazioni sulle tecnologie XML, tra cui XML, DTD (Document Type Definition), XSD (XML Schema Definition Language) e XSLT.

 <xref:System.Xml?displayProperty=fullName> Descrive le classi e altri elementi che costituiscono lo <xref:System.Xml> spazio dei nomi e fornisce collegamenti a informazioni più dettagliate su ogni elemento.

 <xref:System.Xml.Serialization?displayProperty=fullName> Descrive le classi e altri elementi che costituiscono lo <xref:System.Xml.Serialization> spazio dei nomi e fornisce collegamenti a informazioni più dettagliate su ogni elemento.

## <a name="related-sections"></a>Sezioni correlate
 [Document Object Model XML (Dom)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) Viene descritto in che modo le <xref:System.Xml.XmlDocument> classi e le classi associate sono conformi alle specifiche di supporto dello spazio dei nomi W3C Document Object Model (Core) Level 1 e Level 2.

 [Lettura di XML con XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) Viene descritto il modo in cui l'oggetto <xref:System.Xml.XmlReader> fornisce l'accesso di sola lettura non memorizzato nella cache ai dati XML tramite un flusso XML.

 [Scrittura di XML con XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) Viene descritto il <xref:System.Xml.XmlWriter> modo in cui il fornisce la modalità di generazione dei flussi XML non memorizzata nella cache e di sola trasmissione e consente di compilare documenti XML conformi allo standard W3C.

 [Trasformazioni XSLT](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) Viene descritto il modo in cui la <xref:System.Xml.Xsl.XslCompiledTransform> classe implementa la raccomandazione XSLT 1,0.

 [Elaborare dati XML utilizzando il modello di dati XPath](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) Viene descritto in che modo la <xref:System.Xml.XPath.XPathNavigator> classe può elaborare i dati XML archiviati in un <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> oggetto o. La classe <xref:System.Xml.XPath.XPathNavigator> è basata sul modello di dati XQuery 1.0 e XPath 2.0 e può essere usata per spostarsi tra i dati XML e per modificarli.

 [Modello SOM (XML Schema Object Model)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) Vengono descritte le classi utilizzate per la creazione e la modifica di XML Schema, fornendo una <xref:System.Xml.Schema.XmlSchema> classe per caricare e modificare uno schema.
