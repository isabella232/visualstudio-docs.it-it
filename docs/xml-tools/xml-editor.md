---
title: Editor XML
description: Informazioni sull'editor XML in Visual Studio che si basa sull'editor di testo e include supporto aggiuntivo per i linguaggi XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: c796cedd457db405fe3d12a9ed0881881ddfee6b8f333adc1f9379d962650e24
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121350966"
---
# <a name="xml-editor"></a>Editor XML

L'editor XML in Visual Studio è basato sull'editor di testo e include supporto aggiuntivo per i linguaggi XML. Quando si apre un file XML in Visual Studio, viene aperto nell'editor XML.

L'editor XML include le funzionalità seguenti:

- Verifica della sintassi XML 1.0.

- Convalida dello schema durante la digitazione.

- Supporto dei frammenti di codice XML, inclusi i frammenti generati da uno schema.

- Supporto per la DTD (Document Type Definition).

- Supporto per lo schema del linguaggio XSD (XML Schema Definition Language).

- Creazione di uno schema XML da un documento di istanza XML.

- Conversione di una DTD o di uno schema XDR (XML-Data Reduced) in uno schema XML.

- Controllo della sintassi XSLT.

- Strutturazione del documento per consentire l'espansione e la compressione degli elementi.

- Integrazione con [XML Schema Explorer.](../xml-tools/xml-schema-explorer.md) In questo modo viene fornita una visualizzazione gerarchia di XML Schema.

L'editor XML viene richiamato per estensioni di file note, ad esempio *.xml*, *xsd,* *xsl* *e.config*. Viene inoltre richiamato su qualsiasi estensione di file sconosciuta se il file sembra contenere XML.

## <a name="xslt-intellisense"></a>XSLT IntelliSense

[XSLT IntelliSense consente](../xml-tools/xml-editor-intellisense-features.md) di completare automaticamente i nomi dei set di attributi, le modalità e i nomi dei modelli e i nomi dei parametri per una modalità specificata o un modello denominato specificato.

## <a name="xslt-profiler"></a>Profiler XSLT

Il [profiler XSLT crea](../xml-tools/xslt-profiler.md) report dettagliati sulle prestazioni XSLT che consentono di misurare, valutare e risolvere i problemi correlati alle prestazioni nel codice XSLT. XSLT Profiler include anche suggerimenti utili per le ottimizzazioni dei fogli di stile XSL e XSLT.

## <a name="xslt-hierarchy"></a>Gerarchia XSLT

Lo [strumento di gerarchia XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md) consente di aggiungere punti di interruzione nei fogli di stile inclusi e/o nelle regole del modello predefinite.

## <a name="see-also"></a>Vedi anche

- [Opzioni dell'editor XML - formattazione](../ide/reference/options-text-editor-xml-formatting.md)
- [Opzioni dell'editor XML - Varie](../ide/reference/options-text-editor-xml-miscellaneous.md)
- [Funzionalità dell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)
- [Informazioni di riferimento per gli standard XML](/previous-versions/dotnet/netframework-4.0/ms256177(v=vs.100))
- [Strumenti XML in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)