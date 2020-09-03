---
title: Determinazione dello stato del comando mediante gli assembly di interoperabilità | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196780"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Determinazione dello stato dei comandi in base agli assembly di interoperabilità
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un pacchetto VSPackage deve tenere traccia dello stato dei comandi che è in grado di gestire. L'ambiente non è in grado di determinare quando un comando gestito all'interno del pacchetto VSPackage viene abilitato o disabilitato. È responsabilità del VSPackage informare l'ambiente sugli stati dei comandi, ad esempio lo stato dei comandi generali come **taglia**, **copia**e **Incolla**.  
  
## <a name="status-notification-sources"></a>Origini notifiche di stato  
 L'ambiente riceve informazioni sui comandi tramite il metodo VSPackages <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> , che fa parte dell'implementazione di VSPackage dell' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. L'ambiente chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo del pacchetto VSPackage in due condizioni:  
  
- Quando un utente apre un menu principale o un menu di scelta rapida (facendo clic con il pulsante destro del mouse), l'ambiente esegue il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo su tutti i comandi di tale menu per determinarne lo stato.  
  
- Quando il pacchetto VSPackage richiede che l'ambiente aggiorni l'interfaccia utente corrente (UI). Questa situazione si verifica in quanto i comandi attualmente visibili all'utente, ad esempio il raggruppamento **taglia**, **copia**e **Incolla** sulla barra degli strumenti standard, diventano abilitati e disabilitati in risposta a azioni utente e di contesto.  
  
  Poiché la shell ospita più VSPackage, le prestazioni della shell potrebbero risultare inaccettabili se fosse necessario eseguire il polling di ogni VSPackage per determinare lo stato del comando. Al contrario, il pacchetto VSPackage deve informare attivamente l'ambiente quando l'interfaccia utente cambia al momento della modifica. Per ulteriori informazioni sulla notifica di aggiornamento, vedere [aggiornamento dell'interfaccia utente](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Errore di notifica di stato  
 Un errore del pacchetto VSPackage per notificare all'ambiente la modifica dello stato di un comando può inserire l'interfaccia utente in uno stato incoerente. Tenere presente che qualsiasi comando di menu o menu di scelta rapida può essere inserito su una barra degli strumenti dall'utente. Pertanto, l'aggiornamento dell'interfaccia utente solo quando si apre un menu o un menu di scelta rapida non è sufficiente.  
  
## <a name="see-also"></a>Vedere anche  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementazione](../../extensibility/internals/command-implementation.md)
