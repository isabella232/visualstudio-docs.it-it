---
title: Hosting di IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c378aec6822a436de0d8fc2656fcac7be4149f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203905"
---
# <a name="intellisense-hosting"></a>Hosting IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Abilita l'hosting di IntelliSense. IntellSense hosting consente di fornire IntelliSense per il codice non ospitato dall'editor di testo di Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Utilizzo dell'hosting IntelliSense  
 In Visual Studio qualsiasi codice che ha accesso a un set di completamenti e a un buffer di testo può ottenere Windows IntelliSense da qualsiasi punto dell'interfaccia utente (UI). Alcuni scenari di esempio sono il completamento nella finestra **espressioni di controllo** o nel campo condizione della finestra Proprietà punto di interruzione.  
  
### <a name="implementation-interfaces"></a>Interfacce di implementazione  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Qualsiasi componente dell'interfaccia utente che ospita le finestre popup di IntelliSense deve supportare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaccia. La visualizzazione di testo dell'editor principale predefinito include un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> implementazione dell'interfaccia di azione per conservare la funzionalità IntelliSense corrente. Nella maggior parte dei casi, i metodi dell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaccia rappresentano un subset degli elementi implementati nell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia. Il subset include la gestione dell'interfaccia utente di IntelliSense, la manipolazione del cursore e della selezione e la semplice funzionalità di sostituzione del testo. Inoltre, l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaccia consente l'utilizzo di IntelliSense separato "Subject" e "context", in modo che sia possibile fornire IntelliSense per gli oggetti che non esistono direttamente nel buffer di testo utilizzato per il contesto.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> provider di interfaccia deve implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> metodo per consentire a un client di determinare il tipo di funzionalità di IntelliSense supportate dall'host.  
  
 I flag host, definiti in [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), sono riepilogati di seguito.  
  
|Flag host IntelliSense|Descrizione|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|L'impostazione di questo flag indica che il buffer del contesto è di sola lettura e la modifica avviene solo all'interno del testo dell'oggetto.|  
|IHF_NOSEPERATESUBJECT|L'impostazione di questo flag indica che non è presente alcun oggetto IntelliSense separato. L'oggetto è presente nel buffer del contesto, ad esempio nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sistema IntelliSense tradizionale.|  
|IHF_SINGLELINESUBJECT|L'impostazione di questo flag indica che l'oggetto non è in grado di supportare più righe, ad esempio in un'unica modifica della riga nella finestra **espressioni di controllo** .|  
|IHF_FORCECOMMITTOCONTEXT|Se questo flag è impostato e il buffer del contesto deve essere aggiornato, l'host Abilita il flag di sola lettura sul buffer del contesto da ignorare e modifica per continuare.|  
|IHF_OVERTYPE|La modifica (in oggetto o contesto) deve essere eseguita in modalità sovratipo.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost. BeforeCompletorCommit e IVsIntellisenseHost. AfterCompletorCommit  
 Questi metodi di callback vengono chiamati dalla finestra di completamento prima e dopo il commit del testo, per consentire la pre-elaborazione e la post-elaborazione.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 L' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> interfaccia è una versione co-creabile della finestra di completamento standard utilizzata dalla Integrated Development Environment (IDE). Qualsiasi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaccia può implementare rapidamente IntelliSense utilizzando questa interfaccia Completor.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
