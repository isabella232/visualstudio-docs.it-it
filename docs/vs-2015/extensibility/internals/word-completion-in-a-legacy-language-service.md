---
title: Completamento delle parole in un servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8b4449a30119d925b167213141c3ba577ce42609
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839619"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Completamento delle parole in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il completamento delle parole compila i caratteri mancanti in una parola parzialmente tipizzata. Se è presente solo un possibile completamento, la parola viene completata quando viene immesso il carattere di completamento. Se la parola parziale corrisponde a più di una possibilità, viene visualizzato un elenco di possibili completamenti. Un carattere di completamento può essere qualsiasi carattere non utilizzato per gli identificatori.  
  
 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni, vedere [estensione dei servizi di editor e di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.  
  
## <a name="implementation-steps"></a>Passaggi di implementazione  
  
1. Quando l'utente seleziona **completa parola** dal menu **IntelliSense** , il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando viene inviato al servizio di linguaggio.  
  
2. La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe intercetta il comando e chiama il <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo con il motivo dell'analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> .  
  
3. La <xref:Microsoft.VisualStudio.Package.Source> classe chiama quindi il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo per ottenere l'elenco dei completamenti di parole possibili, quindi Visualizza le parole in un elenco di descrizioni comandi usando la <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.  
  
    Se è presente una sola parola corrispondente, la <xref:Microsoft.VisualStudio.Package.Source> classe completa la parola.  
  
   In alternativa, se lo scanner restituisce il valore del trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando il primo carattere di un identificatore viene digitato, la <xref:Microsoft.VisualStudio.Package.Source> classe rileva questo oggetto e chiama il <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo con il motivo dell'analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> . In questo caso il parser deve rilevare la presenza di un carattere di selezione dei membri e fornire un elenco di membri.  
  
## <a name="enabling-support-for-the-complete-word"></a>Abilitazione del supporto per la parola completa  
 Per abilitare il supporto per il completamento delle parole, impostare il `CodeSense` parametro denominato passato all' <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo utente associato al pacchetto di linguaggio. Viene impostata la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> proprietà sulla <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 Il parser deve restituire un elenco di dichiarazioni in risposta al valore del motivo dell'analisi <xref:Microsoft.VisualStudio.Package.ParseReason> , per il corretto funzionamento del completamento delle parole.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementazione di una parola completa nel Metodo ParseSource  
 Per il completamento delle parole, la <xref:Microsoft.VisualStudio.Package.Source> classe chiama il <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> Metodo sulla <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe per ottenere un elenco di possibili corrispondenze di Word. È necessario implementare l'elenco in una classe derivata dalla <xref:Microsoft.VisualStudio.Package.Declarations> classe. <xref:Microsoft.VisualStudio.Package.Declarations>Per informazioni dettagliate sui metodi che è necessario implementare, vedere la classe.  
  
 Se l'elenco contiene una sola parola, la <xref:Microsoft.VisualStudio.Package.Source> classe inserisce automaticamente tale parola al posto della parola parziale. Se l'elenco contiene più di una parola, la <xref:Microsoft.VisualStudio.Package.Source> classe presenta un elenco di descrizioni comandi da cui l'utente può selezionare la scelta appropriata.  
  
 Esaminare inoltre l'esempio di implementazione di una <xref:Microsoft.VisualStudio.Package.Declarations> classe nel [completamento dei membri in un servizio di linguaggio legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
