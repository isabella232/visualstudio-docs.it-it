---
title: Tramite la gestione di testo per monitorare le impostazioni globali | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3d7f93d0b736548f9ee815e0870a89dbd30ea21d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530506"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Tramite la gestione di testo per monitorare le impostazioni globali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [utilizzando la gestione di testo per le impostazioni globali di monitoraggio](https://docs.microsoft.com/visualstudio/extensibility/using-the-text-manager-to-monitor-global-settings).  
  
Se si implementa un editor di base, è necessario monitorare le modifiche apportate alle impostazioni globali, perché queste modifiche potrebbero influenzare l'istanza dell'editor. È possibile tenere traccia delle modifiche rimanendo in ascolto di eventi generati da Gestione testi. Ad esempio, quando si specifica una preferenza globale per l'aspetto o il comportamento di un componente nell'editor principale, ad esempio relativo oggetto dati del documento, la gestione di testo archivia le informazioni e comunica a tutti i client interessati.  
  
## <a name="text-manager-functions"></a>Funzioni di gestione di testo  
 Il gestore di testo genera eventi per una serie di impostazioni, incluse le seguenti:  
  
-   Indica se un buffer sia sotto il controllo del codice sorgente  
  
-   Come registrarsi per le notifiche di modifica di file  
  
-   Come tenere traccia di quali visualizzazioni sono associate alcuni buffer  
  
-   Preferenze di colorazione di testo  
  
-   Scheda e le preferenze di spazio  
  
 Le preferenze che sono univoche per una determinata lingua non gestite da Gestione testi. Queste impostazioni devono essere gestite da ogni servizio di linguaggio.  
  
 Notifica degli eventi per la gestione di testo viene fornita dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interfaccia. Implementare questa interfaccia nel client per gestire gli eventi oggetto generato il gestore di testo. Si registra per questi eventi tramite il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaccia nella gestione testi.  
  
## <a name="see-also"></a>Vedere anche  
 [All'interno l'Editor principale](../extensibility/inside-the-core-editor.md)   
 [Funzionalità dell'editor](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)

