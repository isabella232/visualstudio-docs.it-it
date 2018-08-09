---
title: Hosting di IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28fc8ca212574c054add28e69a409fde4f58308a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638834"
---
# <a name="intellisense-hosting"></a>Hosting di IntelliSense
Visual Studio consente l'hosting di IntelliSense. IntellSense che ospita consente di fornire IntelliSense per codice che non è ospitato da editor di testo di Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Utilizzo di hosting di IntelliSense  
 In Visual Studio, qualsiasi codice che ha accesso a un buffer di testo e un set di completamenti può ottenere IntelliSense windows ovunque nell'interfaccia utente (UI). Alcuni scenari di questo esempio sono completamento nel **Watch** finestra o nel campo condizione di una finestra delle proprietà del punto di interruzione.  
  
### <a name="implementation-interfaces"></a>Interfacce di implementazione  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Qualsiasi componente dell'interfaccia utente che ospita le finestre popup IntelliSense deve supportare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaccia. La visualizzazione di testo dell'editor principale predefinito include un magazzino <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> implementazione per conservare le attuali funzionalità IntelliSense dell'interfaccia. Nella maggior parte, i metodi del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> rappresentano un sottoinsieme di ciò che è implementato nell'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia. Il subset include gestione IntelliSense UI, punto di inserimento e la modifica di selezione e funzionalità di sostituzione di testo semplice. Inoltre, il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaccia abilita separato IntelliSense "subject" e "contesto" in modo che IntelliSense può essere forniti per gli oggetti che non esistono direttamente nel buffer di testo che viene utilizzato per il contesto.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaccia provider deve implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> supporta metodo per consentire a un client determinare il tipo di IntelliSense per le funzionalità dell'host.  
  
 I flag host, definiti in [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), sono riepilogate di seguito.  
  
|Flag Host IntelliSense|Descrizione|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Impostando questo flag è il buffer del contesto sola lettura e la modifica si verifica solo all'interno del testo dell'oggetto.|  
|IHF_NOSEPERATESUBJECT|Impostando questo flag che non vi è nessun oggetto IntelliSense separato. L'oggetto esiste nel buffer del contesto, come nelle tradizionali <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sistema IntelliSense.|  
|IHF_SINGLELINESUBJECT|Impostando questo flag non è soggetto a più righe in grado di supportare, ad esempio in una modifica a riga singola nel **Watch** finestra.|  
|IHF_FORCECOMMITTOCONTEXT|Se questo flag è impostato e il buffer del contesto deve essere aggiornato, l'host Abilita i flag di sola lettura nel buffer del contesto deve essere ignorata e le modifiche per continuare.|  
|IHF_OVERTYPE|La modifica (nell'oggetto o al contesto) deve essere eseguita in modalità sovrascrittura.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit e IVsIntellisenseHost.AfterCompletorCommit  
 Questi metodi di callback vengono chiamati per la finestra di completamento prima e dopo che il testo viene eseguito il commit, per abilitare la pre-elaborazione e post-elaborazione.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> interfaccia è una versione generabile condivise della finestra completamento standard che viene usata dall'ambiente di sviluppo integrato (IDE). Qualsiasi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaccia possa implementare rapidamente IntelliSense usando l'interfaccia del completor.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop>