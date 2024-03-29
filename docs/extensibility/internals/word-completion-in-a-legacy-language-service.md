---
title: Completamento di parole in un servizio di linguaggio legacy | Microsoft Docs
description: Il completamento delle parole può essere supportato per un servizio di linguaggio legacy in Visual Studio SDK. Informazioni su come vengono implementati i servizi di linguaggio legacy in un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a9f32d6d99545f1daed9aed2c927c7987fe95dcd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711719"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Completamento delle parole in un servizio di linguaggio legacy
Il completamento della parola riempie i caratteri mancanti in una parola parzialmente digitata. Se è presente un solo possibile completamento, la parola viene completata quando viene immesso il carattere di completamento. Se la parola parziale corrisponde a più di una possibilità, viene visualizzato un elenco di possibili completamenti. Un carattere di completamento può essere qualsiasi carattere non usato per gli identificatori.

 I servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni, vedere [Estensione dell'editor e di Servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. In questo modo si miglioreranno le prestazioni del servizio di linguaggio e si potranno sfruttare le nuove funzionalità dell'editor.

## <a name="implementation-steps"></a>Passaggi di implementazione

1. Quando l'utente seleziona **Completa parola** dal menu **IntelliSense,** il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando viene inviato al servizio di linguaggio.

2. La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe intercetta il comando e chiama <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> il metodo con il motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> .

3. La <xref:Microsoft.VisualStudio.Package.Source> classe chiama quindi il metodo per ottenere <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> l'elenco dei possibili completamenti delle parole e quindi visualizza le parole in un elenco di descrizione comando usando la <xref:Microsoft.VisualStudio.Package.CompletionSet> classe .

    Se è presente una sola parola corrispondente, <xref:Microsoft.VisualStudio.Package.Source> la classe completa la parola.

   In alternativa, se lo scanner restituisce il valore del trigger quando viene digitato il primo carattere di un identificatore, la classe lo rileva e chiama il metodo con il motivo <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Source> di analisi di <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> . In questo caso il parser deve rilevare la presenza di un carattere di selezione dei membri e fornire un elenco di membri.

## <a name="enabling-support-for-the-complete-word"></a>Abilitazione del supporto per la parola completa
 Per abilitare il supporto per il completamento delle parole, impostare `CodeSense` il parametro denominato passato all'attributo utente associato al pacchetto di <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> linguaggio. In questo modo <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> la proprietà viene impostata nella classe <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

 Il parser deve restituire un elenco di dichiarazioni in risposta al valore del motivo di analisi , perché il completamento delle parole <xref:Microsoft.VisualStudio.Package.ParseReason> funzioni.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementazione della parola completa nel metodo ParseSource
 Per il completamento delle parole, la <xref:Microsoft.VisualStudio.Package.Source> classe chiama il metodo sulla classe per ottenere un elenco di possibili <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> corrispondenze di parole. È necessario implementare l'elenco in una classe derivata dalla <xref:Microsoft.VisualStudio.Package.Declarations> classe . Per informazioni <xref:Microsoft.VisualStudio.Package.Declarations> dettagliate sui metodi che è necessario implementare, vedere la classe .

 Se l'elenco contiene una sola parola, la classe inserisce automaticamente tale parola <xref:Microsoft.VisualStudio.Package.Source> al posto della parola parziale. Se l'elenco contiene più parole, la classe presenta un elenco di descrizione comando da cui l'utente <xref:Microsoft.VisualStudio.Package.Source> può selezionare la scelta appropriata.

 Esaminare anche l'esempio di <xref:Microsoft.VisualStudio.Package.Declarations> implementazione di una classe in [Completamento membri in un servizio di linguaggio legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
