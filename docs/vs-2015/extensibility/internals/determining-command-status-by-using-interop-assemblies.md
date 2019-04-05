---
title: Determinazione dello stato del comando con gli assembly di interoperabilità | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc67123e082258932ab5df6613941f869d6049a6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969608"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Determinazione dello stato dei comandi in base agli assembly di interoperabilità
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un pacchetto VSPackage deve tenere traccia dello stato dei comandi che possono essere gestite. L'ambiente non è possibile determinare quando un comando gestito all'interno del pacchetto VSPackage diventa abilitato o disabilitato. È responsabilità del pacchetto VSPackage per informare l'ambiente sugli stati dei comandi, ad esempio, lo stato di general comandi, ad esempio **tagliare**, **copia**, e **Incolla**.  
  
## <a name="status-notification-sources"></a>Origini di notifica di stato  
 L'ambiente riceve le informazioni sui comandi tramite VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo, che fa parte dell'implementazione di VSPackage del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. L'ambiente chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo del pacchetto VSPackage in due condizioni:  
  
- Quando un utente apre un menu principale o un menu di scelta rapida (pulsante destro del mouse), l'ambiente esegue il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo su tutti i comandi nel menu corrispondente per determinare il proprio stato.  
  
- Quando il pacchetto VSPackage richiede che l'ambiente di aggiornare l'interfaccia utente (UI). Questo errore si verifica come i comandi che sono attualmente visibili all'utente, ad esempio la **tagliare**, **copia**, e **Incolla** sulla barra degli strumenti standard di raggruppamento, diventare abilitato e disabilitato in risposta alle azioni dell'utente e di contesto.  
  
  Poiché la shell ospita più pacchetti VSPackage, le prestazioni della shell sarebbero eccessivamente peggiorare se sono stati necessario per eseguire il polling ogni VSPackage per determinare lo stato del comando. Al contrario, il pacchetto VSPackage deve attivamente notificare l'ambiente quando viene modificato al momento della modifica dell'interfaccia utente. Per altre informazioni sulla notifica di aggiornamento, vedere [aggiornamento dell'interfaccia utente](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Errore di notifica di stato  
 Errore del pacchetto VSPackage per notificare l'ambiente di una modifica dello stato del comando è possibile inserire l'interfaccia utente in uno stato incoerente. Tenere presente che qualsiasi i comandi di menu di scelta rapida o menu può essere inserito su una barra degli strumenti dall'utente. Pertanto, l'aggiornamento dell'interfaccia utente solo quando si apre un menu di scelta rapida o menu non è sufficiente.  
  
## <a name="see-also"></a>Vedere anche  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementazione](../../extensibility/internals/command-implementation.md)
