---
title: Completamento delle parole in un servizio di linguaggio Legacy | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 591967bd9ac61b611b1b062a006a5069fc94d114
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285298"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Completamento delle parole in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Completa parola inserisce i caratteri mancanti in una parola parziale digitata. Se è presente un solo termine possibili, la parola viene completata quando viene immesso il carattere di completamento. Se la parola parziale corrisponde a più possibilità, viene visualizzato un elenco di completamenti possibili. Un carattere di completamento può essere qualsiasi carattere che non viene utilizzato per gli identificatori.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni, vedere [estensione dell'Editor e servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="implementation-steps"></a>Passaggi di implementazione  
  
1.  Quando l'utente seleziona **completa parola** dalle **IntelliSense** dal menu di <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando viene inviato al servizio di linguaggio.  
  
2.  Il <xref:Microsoft.VisualStudio.Package.ViewFilter> classe intercetta le chiamate di <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo con il motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  Il <xref:Microsoft.VisualStudio.Package.Source> classe quindi chiamate le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo per ottenere l'elenco di completamenti di parole possibili e visualizza quindi le parole in una descrizione comando elencate mediante il <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.  
  
     Se è presente un solo parola corrispondente, il <xref:Microsoft.VisualStudio.Package.Source> classe completa parola.  
  
 In alternativa, se lo scanner restituisce il valore trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando viene inserito il primo carattere di un identificatore, il <xref:Microsoft.VisualStudio.Package.Source> classe lo rileva e chiama le <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo con il motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>. In questo caso il parser deve rilevare la presenza di un carattere di selezione membro e fornire un elenco di membri.  
  
## <a name="enabling-support-for-the-complete-word"></a>Abilitazione del supporto per la parola completa  
 Per abilitare il supporto per set di completamenti word il `CodeSense` passato al parametro denominato il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo utente associato al pacchetto di linguaggio. Consente di impostare il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> proprietà di <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 Il parser deve restituire un elenco delle dichiarazioni in risposta al valore di motivo analisi <xref:Microsoft.VisualStudio.Package.ParseReason>, per il completamento delle parole per il funzionamento.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementazione completa parola nel metodo ParseSource  
 Per il completamento delle parole, il <xref:Microsoft.VisualStudio.Package.Source> classe chiama il <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodo sul <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe per ottenere un elenco di corrispondenze possibili word. È necessario implementare l'elenco in una classe derivata dal <xref:Microsoft.VisualStudio.Package.Declarations> classe. Vedere il <xref:Microsoft.VisualStudio.Package.Declarations> classe per informazioni dettagliate sui metodi di cui è necessario implementare.  
  
 Se l'elenco contiene solo una singola parola, il <xref:Microsoft.VisualStudio.Package.Source> classe inserisce automaticamente tale parola al posto di parole parziali. Se l'elenco contiene più di una parola, il <xref:Microsoft.VisualStudio.Package.Source> classe presenta un elenco di suggerimento dello strumento da cui l'utente può selezionare la scelta più appropriata.  
  
 Anche esaminare l'esempio di un <xref:Microsoft.VisualStudio.Package.Declarations> implementazione della classe nel [completamento dei membri in un servizio di linguaggio Legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).

