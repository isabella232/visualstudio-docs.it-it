---
title: Funzionalità legacy del servizio di linguaggio1 | Microsoft Docs
description: Informazioni sulle funzionalità Visual Studio supportate in un servizio di linguaggio MPF (Managed Package Framework).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 94099df26da9d9fcd62db62ad440820056775a81
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042283"
---
# <a name="legacy-language-service-features-1"></a>Funzionalità del servizio di linguaggio legacy 1
Un servizio di linguaggio MPF (Managed Package Framework) può supportare una o più funzionalità, ad esempio l'evidenziazione della sintassi, IntelliSense e la convalida [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dei punti di interruzione. Ogni funzionalità può essere implementata indipendentemente dalle altre, ma tutte richiedono un parser e uno scanner, ad eccezione dell'evidenziazione della sintassi, che richiede solo uno scanner.

## <a name="in-this-section"></a>Contenuto della sezione
- [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Descrive ciò che è necessario per supportare la corrispondenza delle coppie di lingue, nota anche come corrispondenza delle parentesi graffe.

- [Aggiunta di commenti al codice in un servizio di linguaggio legacy](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Descrive gli elementi necessari per supportare l'applicazione di commenti e rimozione del commento del codice selezionato.

- [Proprietà personalizzate dei documenti in un servizio di linguaggio legacy](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Descrive gli elementi necessari per supportare le proprietà del documento incorporate in un file di origine.

- [Struttura in un servizio di linguaggio legacy](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Descrive gli elementi necessari per supportare la struttura tramite l'implementazione di aree nascoste.

- [Riformattazione del codice in un servizio di linguaggio legacy](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Descrive gli elementi necessari per supportare la riformattazione del codice.

- [Supporto per i frammenti di codice in un servizio di linguaggio legacy](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Descrive gli elementi necessari per supportare frammenti di codice, ovvero segmenti di codice inseriti e modificabili.

- [Informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Descrive gli elementi necessari per supportare l'operazione IntelliSense Parameter Info per la visualizzazione di una firma del metodo durante la digitazione del metodo.

- [Informazioni rapide in un servizio di linguaggio legacy](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Descrive gli elementi necessari per supportare l'operazione informazioni rapide di IntelliSense per la visualizzazione di informazioni su un identificatore.

- [Completamento dei membri in un servizio di linguaggio legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Descrive gli elementi necessari per supportare l'operazione di completamento dei membri IntelliSense per la selezione di un membro di uno spazio dei nomi da un elenco.

- [Completamento delle parole in un servizio di linguaggio legacy](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Descrive gli elementi necessari per supportare l'operazione IntelliSense Complete Word per il completamento di parole parzialmente digitate.

- [Supporto per la finestra Auto in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Descrive le operazioni che un servizio di linguaggio può eseguire per supportare la **finestra Auto durante** il debug.

- [Supporto per la barra di spostamento in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Viene descritto come usare la barra **di** spostamento nella parte superiore della visualizzazione dell'editor per consentire lo spostamento rapido a qualsiasi tipo o membro nel file visualizzato in tale visualizzazione.

- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Descrive gli elementi necessari per supportare l'evidenziazione della sintassi del codice sorgente.

- [Convalida dei punti di interruzione in un servizio di linguaggio legacy](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Descrive le operazioni che un servizio di linguaggio può eseguire per supportare la convalida dei punti di interruzione all'esterno di un debugger.

## <a name="related-sections"></a>Sezioni correlate
- [Scanner e parser dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Descrive il parser e lo scanner necessari per implementare tutte le funzionalità di un servizio di linguaggio che usa il framework del pacchetto gestito.

- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Descrive gli elementi necessari per implementare un servizio di linguaggio tramite MPF.

- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Descrive i passaggi necessari per registrare un servizio di linguaggio basato su MPF con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Uso di IntelliSense](../../ide/using-intellisense.md)

 Viene illustrato come IntelliSense semplifica l'accesso ai riferimenti al linguaggio.

- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Fornisce informazioni su come usare managed package framework (MPF) per implementare un servizio di linguaggio completo nel codice gestito.
