---
title: Editor XML e progettazione schema
ms.date: 11/04/2016
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9412d89ee7d9ad1412f0eaf9fe9341e336a65e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668714"
---
# <a name="xml-tools-in-visual-studio"></a>Strumenti XML in Visual Studio

*Extensible Markup Language (XML)* è un linguaggio di markup che fornisce un formato per la descrizione dei dati. XML separa i dati e la relativa presentazione usando i fogli di stile associati, ad esempio Extensible Stylesheet Language (XSL) e fogli di stile CSS. Visual Studio comprende strumenti e funzionalità che semplificano l'uso del codice XML, XSLT e degli schemi XML.

## <a name="xml-editor"></a>Editor XML

L' [editor XML](xml-editor.md) viene utilizzato per modificare i documenti XML. Fornisce il controllo completo della sintassi XML, la convalida dello schema durante la digitazione, la codifica a colori e IntelliSense. Se viene fornita una definizione dello schema o del tipo di documento, essa verrà usata da IntelliSense per elencare gli elementi e gli attributi disponibili.

Le funzionalità aggiuntive comprendono:

- Supporto per i frammenti di codice XML, inclusi i frammenti generati dallo schema

- Struttura del documento in modo che sia possibile espandere e comprimere gli elementi

- Possibilità di eseguire trasformazioni XSLT e visualizzare i risultati come testo, XML o HTML

- Possibilità di generare schemi XSD (XML Schema Definition Language) dal documento di istanza XML

- Supporto per la modifica dei fogli di stile XSLT, incluso il supporto IntelliSense

- XML Schema Explorer

## <a name="xml-schema-designer"></a>Progettazione XML Schema

[Progettazione XML Schema](xml-schema-designer.md) è integrato con Visual Studio e l'editor XML per consentire l'utilizzo di schemi di XML Schema Definition Language (XSD).

## <a name="xslt-debugging"></a>Debug XSLT

Visual Studio supporta il [debug di fogli di stile XSLT](../xml-tools/debugging-xslt.md). Usando il debugger, è possibile impostare i punti di interruzione in un foglio di stile XSLT, eseguire l'istruzione del codice di un foglio di stile XSLT e così via.

> [!NOTE]
> Il debugger XSLT è disponibile solo nell'edizione Enterprise di Visual Studio.

## <a name="see-also"></a>Vedere anche

- <xref:System.Xml?displayProperty=fullName>
- [Trasformazioni XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Elaborare dati XML utilizzando il modello di dati XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [Modello DOM (Document Object Mode) XML](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [SOM (Schema Object Model) XML](/dotnet/standard/data/xml/xml-schema-object-model-som)