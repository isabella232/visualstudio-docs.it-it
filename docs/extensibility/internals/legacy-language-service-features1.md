---
title: Features1 servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2a1eea79b0ac2d80fb2b75043d4462e73928798
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909554"
---
# <a name="legacy-language-service-features"></a>Funzionalità del servizio di linguaggio legacy
Un servizio di linguaggio managed package framework (MPF) può supportare uno o più [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funzionalità, ad esempio l'evidenziazione della sintassi, IntelliSense e convalida di punto di interruzione. Ogni funzionalità possono essere implementata indipendente dagli altri, ma tutti richiedono un parser e uno scanner tranne l'evidenziazione della sintassi, che richiede solo uno scanner.

## <a name="in-this-section"></a>In questa sezione
- [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Vengono descritte le funzionalità necessarie per supportare la coppia di linguaggi corrispondenti, noto anche come corrispondenza parentesi graffe.

- [Aggiunta di commenti al codice in un servizio di linguaggio legacy](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Vengono descritte le funzionalità necessarie per supportare l'aggiunta di commenti e rimozione di commenti del codice selezionato.

- [Proprietà personalizzate dei documenti in un servizio di linguaggio legacy](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Vengono descritte le funzionalità necessarie per supportare le proprietà del documento sono incorporate in un file di origine.

- [Definizione della struttura in un servizio di linguaggio legacy](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Vengono descritte le funzionalità necessarie per supportare la struttura tramite l'implementazione di aree nascoste.

- [Riformattazione del codice in un servizio di linguaggio legacy](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Vengono descritte le funzionalità necessari per supportare codice riformattazione.

- [Supporto per i frammenti di codice in un servizio di linguaggio legacy](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Vengono descritte le funzionalità necessarie per supportare i frammenti di codice, ovvero i segmenti di codice inserite e che possono essere modificati.

- [Informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Vengono descritte le funzionalità necessarie per supportare l'operazione di informazioni sul parametro di IntelliSense per la visualizzazione di una firma del metodo com'è digitato il metodo.

- [Informazioni rapide in un servizio di linguaggio legacy](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Vengono descritte le funzionalità necessarie per supportare l'operazione di informazioni rapide di IntelliSense per la visualizzazione di informazioni su un identificatore.

- [Completamento dei membri in un servizio di linguaggio legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Descrive la procedura necessaria per supportare l'operazione di completamento IntelliSense dei membri per la selezione di un membro di uno spazio dei nomi da un elenco.

- [Completamento delle parole in un servizio di linguaggio legacy](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Vengono descritte le funzionalità necessarie per supportare l'operazione completa parola di IntelliSense per il completamento delle parole digitate parzialmente.

- [Supporto per la finestra Auto in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Descrive le operazioni possa eseguire un servizio di linguaggio per supportare le **Auto** finestra durante il debug.

- [Supporto per la barra di spostamento in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Viene descritto come utilizzare il **sulla barra di navigazione** nella parte superiore della visualizzazione dell'editor per consentire la navigazione rapida in qualsiasi tipo o membro nel file in tale visualizzazione...

- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Vengono descritte le funzionalità necessarie per supportare l'evidenziazione della sintassi del codice sorgente.

- [Convalida dei punti di interruzione in un servizio di linguaggio legacy](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Viene descritto cosa può fare un servizio di linguaggio per supportare i punti di interruzione durante la convalida di fuori di un debugger.

## <a name="related-sections"></a>Sezioni correlate
- [Scanner e parser dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Viene descritto il parser e analisi che sono necessari per implementare tutte le funzionalità di un servizio di linguaggio che usa il framework di pacchetto gestito.

- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Descrive cosa è necessaria implementare un servizio di linguaggio tramite MPF.

- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Vengono descritti i passaggi necessari per registrare un servizio di linguaggio basato su MPF con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Utilizzo di IntelliSense](../../ide/using-intellisense.md)

 Spiega come IntelliSense rende più semplice l'accesso ai riferimenti al linguaggio.

- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Fornisce informazioni su come usare il framework di pacchetto gestito (MPF) per implementare un servizio di linguaggio completo nel codice gestito.