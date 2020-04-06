---
title: Completamento delle parole in un servizio di linguaggio Legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 948751cde5b6b710d911a30ca26a61e5411bba4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703167"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Completamento delle parole in un servizio di linguaggio legacy
Il completamento delle parole inserisce i caratteri mancanti in una parola parzialmente digitata. Se è presente un solo completamento possibile, la parola viene completata quando viene immesso il carattere di completamento. Se la parola parziale corrisponde a più di una possibilità, viene visualizzato un elenco di possibili completamenti. Un carattere di completamento può essere qualsiasi carattere non utilizzato per gli identificatori.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni, vedere [Estensione dell'editor e](../../extensibility/extending-the-editor-and-language-services.md)dei servizi di linguaggio .

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

## <a name="implementation-steps"></a>Passaggi di implementazione

1. Quando l'utente seleziona **Completa parola** dal <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> menu **IntelliSense,** il comando viene inviato al servizio di linguaggio.

2. La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe intercetta il comando <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> e chiama il <xref:Microsoft.VisualStudio.Package.ParseReason>metodo con il motivo di analisi di .

3. La <xref:Microsoft.VisualStudio.Package.Source> classe chiama <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> quindi il metodo per ottenere l'elenco dei possibili completamenti <xref:Microsoft.VisualStudio.Package.CompletionSet> delle parole e quindi visualizza le parole in un elenco di descrizioni comandi utilizzando la classe .

    Se è presente una sola <xref:Microsoft.VisualStudio.Package.Source> parola corrispondente, la classe completa la parola.

   In alternativa, se lo scanner <xref:Microsoft.VisualStudio.Package.TokenTriggers> restituisce il valore del trigger <xref:Microsoft.VisualStudio.Package.Source> quando viene digitato <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> il primo carattere <xref:Microsoft.VisualStudio.Package.ParseReason>di un identificatore, la classe rileva e chiama il metodo con il motivo di analisi di . In questo caso il parser deve rilevare la presenza di un carattere di selezione del membro e fornire un elenco di membri.

## <a name="enabling-support-for-the-complete-word"></a>Abilitazione del supporto per la parola completa
 Per abilitare il supporto `CodeSense` per il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> completamento delle parole, impostare il parametro denominato passato all'attributo utente associato al pacchetto di lingua. In questo <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> modo <xref:Microsoft.VisualStudio.Package.LanguagePreferences> viene impostata la proprietà nella classe .

 Il parser deve restituire un elenco di dichiarazioni <xref:Microsoft.VisualStudio.Package.ParseReason>in risposta al valore del motivo di analisi, affinché il completamento delle parole funzioni.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementazione di una parola completa nel metodo ParseSourceImplementing Complete Word in the ParseSource Method
 Per il completamento delle parole, la <xref:Microsoft.VisualStudio.Package.Source> classe chiama il <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodo sulla <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe per ottenere un elenco di possibili corrispondenze di parole. È necessario implementare l'elenco in <xref:Microsoft.VisualStudio.Package.Declarations> una classe derivata dalla classe . Vedere <xref:Microsoft.VisualStudio.Package.Declarations> la classe per informazioni dettagliate sui metodi che è necessario implementare.

 Se l'elenco contiene una sola <xref:Microsoft.VisualStudio.Package.Source> parola, la classe inserisce automaticamente tale parola al posto della parola parziale. Se l'elenco contiene più <xref:Microsoft.VisualStudio.Package.Source> di una parola, la classe presenta un elenco di descrizioni comandi da cui l'utente può selezionare la scelta appropriata.

 Esaminare anche l'esempio di implementazione di una <xref:Microsoft.VisualStudio.Package.Declarations> classe in Completamento membro in un servizio di [linguaggio Legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
