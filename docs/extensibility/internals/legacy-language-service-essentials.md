---
title: Informazioni di base sul servizio di linguaggio | Microsoft Docs
description: Informazioni sulle funzionalità essenziali disponibili nei servizi di linguaggio legacy che consentono di integrare un linguaggio di programmazione in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: dda53c2ea5c282e67b3ed0ec86112a2a69d64cab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049909"
---
# <a name="legacy-language-service-essentials"></a>Nozioni fondamentali sui servizi di linguaggio legacy
È necessario fornire un servizio di linguaggio per integrare un linguaggio di programmazione in Visual Studio. In questo argomento vengono illustrate le funzionalità disponibili nei servizi di linguaggio legacy.

 I servizi di linguaggio legacy vengono implementati come parte di un PACCHETTO VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni sul nuovo modo di implementare un servizio di linguaggio, vedere [Editor and Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare le nuove funzionalità dell'editor.

 I servizi di linguaggio legacy offrono le funzionalità seguenti:

|Funzionalità|Descrizione|
|-------------|-----------------|
|Colorazione della sintassi|Determina la visualizzazione dell'editor per visualizzare colori e stili del carattere diversi per i diversi elementi di un linguaggio. Questa differenziazione può semplificare la lettura e la modifica dei file.<br /><br /> Per informazioni generali, vedere [Colorazione della sintassi in un servizio di linguaggio legacy.](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)<br /><br /> Per informazioni su questa funzionalità in Managed Package Framework (MPF), vedere Colorazione della sintassi [in un servizio di linguaggio legacy.](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)|
|Completamento istruzioni|Completa un'istruzione o una parola chiave che l'utente ha iniziato a digitare. Il completamento delle istruzioni consente agli utenti di immettere istruzioni difficili più facilmente, con meno digitazione e meno probabilità di errore.<br /><br /> Per informazioni generali, vedere [Completamento delle istruzioni in un servizio di linguaggio legacy.](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)<br /><br /> Per informazioni su questa funzionalità in MPF, vedere [Completamento parole in un servizio di linguaggio legacy.](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)|
|Corrispondenza parentesi graffe|Evidenzia i caratteri associati, ad esempio le parentesi graffe. Quando l'utente specifica un carattere di chiusura, ad esempio "}", la corrispondenza delle parentesi graffe evidenzia il carattere di apertura corrispondente, ad esempio "{". Quando sono presenti diversi livelli di caratteri di inclusione, questa funzionalità consente agli utenti di verificare che i caratteri di inclusione siano associati correttamente.<br /><br /> Per informazioni su questa funzionalità in MPF, vedere Corrispondenza delle parentesi [graffe in un servizio di linguaggio legacy.](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)|
|Descrizioni comando delle informazioni sui parametri|Visualizza un elenco di firme possibili per il metodo di overload attualmente digitato dall'utente.<br /><br /> Per informazioni generali, vedere [Informazioni sui parametri in un servizio di linguaggio legacy.](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)<br /><br /> Per informazioni su questa funzionalità in MPF, vedere [Informazioni sui parametri in un servizio di linguaggio legacy.](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)|
|Marcatori di errore|Visualizza una sottolineatura rossa ondulata, nota anche come ondulata, sotto un testo sintatticamente errato. I marcatori di errore vengono in genere usati per intuire gli utenti di parole chiave con errori di ortografia, parentesi non chiuse, caratteri non validi ed errori simili.<br /><br /> Nelle classi MPF i marcatori di errore vengono gestiti automaticamente nel <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metodo della <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe .|

 Molte di queste funzionalità richiedono al servizio di linguaggio di analizzare il codice sorgente. È spesso possibile riutilizzare il codice di tokenizzazione e analisi per il compilatore o l'interprete.

 Le funzionalità seguenti sono correlate al supporto per i linguaggi di programmazione, ma non fanno parte dei servizi di linguaggio:

| Funzionalità | Descrizione |
|-----------------------| - |
| Analizzatori di espressioni | Supporta il debugger convalidando i punti di interruzione e fornendo un elenco di espressioni da visualizzare nella [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **finestra di** debug Auto.<br /><br /> Per altre informazioni, vedere [Supporto del servizio di linguaggio per il debug.](../../extensibility/internals/language-service-support-for-debugging.md) |
| Strumenti per l'esplorazione dei simboli | Supporta **Visualizzatore oggetti**, **Visualizzazione classi**, **Visualizzatore chiamate** e Risultati **ricerca simboli**. |
