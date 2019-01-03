---
title: Tramite la gestione di testo per monitorare le impostazioni globali | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 43b4f1c2de4862b30dd5822931b02292b942c50f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877549"
---
# <a name="use-the-text-manager-to-monitor-global-settings"></a>Usare la gestione di testo per monitorare le impostazioni globali
Se si implementa un editor di base, è necessario monitorare le modifiche apportate alle impostazioni globali, perché queste modifiche potrebbero influenzare l'istanza dell'editor. È possibile tenere traccia delle modifiche rimanendo in ascolto di eventi generati da Gestione testi. Ad esempio, quando si specifica una preferenza globale per l'aspetto o il comportamento di un componente nell'editor principale, ad esempio relativo oggetto dati del documento, la gestione di testo archivia le informazioni e comunica a tutti i client interessati.  
  
## <a name="text-manager-functions"></a>Funzioni di gestione di testo  
 Il gestore di testo genera eventi per una serie di impostazioni, incluse le seguenti:  
  
- Indica se un buffer sia sotto il controllo del codice sorgente  
  
- Come registrarsi per le notifiche di modifica di file  
  
- Come tenere traccia di quali visualizzazioni sono associate alcuni buffer  
  
- Preferenze di colorazione di testo  
  
- Scheda e le preferenze di spazio  
  
  Le preferenze che sono univoche per una determinata lingua non gestite da Gestione testi. Queste impostazioni devono essere gestite da ogni servizio di linguaggio.  
  
  Notifica degli eventi per la gestione di testo viene fornita dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interfaccia. Implementare questa interfaccia nel client per gestire gli eventi oggetto generato il gestore di testo. Si registra per questi eventi tramite il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaccia nella gestione testi.  
  
## <a name="see-also"></a>Vedere anche  
 [All'interno dell'editor di base](../extensibility/inside-the-core-editor.md)   
 [Funzionalità dell'editor](https://msdn.microsoft.com/library/bdac940d-1f14-4019-a01f-fd0bb3dc7198)