---
title: Editor XML e Progettazione schemi
description: Informazioni sugli strumenti in Visual Studio per l'uso di XML, XSLT e XML Schema, tra cui l'editor XML, Progettazione XML Schema e il debugger XSLT.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
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
- XML [Visual Studio], .NET classes
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 4ff3edfedecc3598ba2571723f4757a60ffc8c45
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633531"
---
# <a name="overview-of-xml-tools-in-visual-studio"></a>Panoramica degli strumenti XML in Visual Studio

*Extensible Markup Language (XML)* è un linguaggio di markup che fornisce un formato per la descrizione dei dati. XML separa i dati e la relativa presentazione usando fogli di stile associati, ad esempio Extensible Stylesheet Language (XSL) e CSS (Cascading Style Sheets). Visual Studio comprende strumenti e funzionalità che semplificano l'uso del codice XML, XSLT e degli schemi XML.

## <a name="xml-editor"></a>Editor XML

[L'editor XML](xml-editor.md) viene utilizzato per modificare i documenti XML. Fornisce il controllo completo della sintassi XML, la convalida dello schema durante la digitazione, la codifica a colori e IntelliSense. Se viene fornita una definizione dello schema o del tipo di documento, essa verrà usata da IntelliSense per elencare gli elementi e gli attributi disponibili.

Le altre funzionalità includono:

- Supporto di frammenti XML, inclusi frammenti generati da schema

- Struttura del documento in modo che gli elementi possano essere espansi e compressi

- Possibilità di eseguire trasformazioni XSLT e di visualizzare i risultati come testo, XML o HTML

- Possibilità di generare schemi XSD (XML Schema Definition Language) dal documento dell'istanza XML

- Supporto per la modifica di fogli di stile XSLT, incluso il supporto intelliSense

- XML Schema Explorer

## <a name="xml-schema-designer"></a>Progettazione XML Schema

Progettazione [XML Schema è](xml-schema-designer.md) integrato con Visual Studio e l'editor XML per consentire l'utilizzo di schemi XSD (XML Schema Definition Language).

## <a name="xslt-debugging"></a>Debug XSLT

Visual Studio supporta il [debug di fogli di stile XSLT.](../xml-tools/debugging-xslt.md) Usando il debugger, è possibile impostare i punti di interruzione in un foglio di stile XSLT, eseguire l'istruzione del codice di un foglio di stile XSLT e così via.

> [!NOTE]
> Il debugger XSLT è disponibile solo nell'Enterprise di Visual Studio.

## <a name="see-also"></a>Vedi anche

- <xref:System.Xml?displayProperty=fullName>
- [Trasformazioni XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Elaborare dati XML usando il modello di dati XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [XML DOM (Document Object Model)](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [SOM (Schema Object Model) XML](/dotnet/standard/data/xml/xml-schema-object-model-som)
