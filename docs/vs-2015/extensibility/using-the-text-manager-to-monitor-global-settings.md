---
title: Utilizzo di gestione testo per il monitoraggio delle impostazioni globali | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ece51450b8344ae4715a912399ec538171a26a5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695460"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Uso della gestione testi per monitorare le impostazioni globali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si implementa un editor principale, è necessario monitorare le modifiche apportate alle impostazioni globali, in quanto tali modifiche possono influire sull'istanza dell'editor. È possibile tenere traccia delle modifiche ascoltando gli eventi generati dalla gestione del testo. Ad esempio, quando si specifica una preferenza globale per l'aspetto o il comportamento di un componente nell'editor principale, ad esempio il relativo oggetto dati del documento, gestione testo archivia tali informazioni e le comunica a tutti i client interessati.  
  
## <a name="text-manager-functions"></a>Funzioni di gestione del testo  
 Gestione testo genera eventi per diverse impostazioni, incluse le seguenti:  
  
- Indica se un buffer è sotto il controllo del codice sorgente  
  
- Come eseguire la registrazione per le notifiche di modifica di file  
  
- Come tenere traccia delle visualizzazioni associate a determinati buffer  
  
- Preferenze di colorazione del testo  
  
- Preferenze di tabulazione e spazio  
  
  Le preferenze univoche per una determinata lingua non vengono gestite dalla gestione del testo. Queste impostazioni devono essere gestite da ogni servizio di linguaggio.  
  
  La notifica degli eventi per gestione testo viene fornita dall' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interfaccia. Implementare questa interfaccia nell'oggetto client per gestire gli eventi che hanno generato la gestione del testo. Per eseguire la registrazione di questi eventi, è possibile usare l' <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaccia di gestione testo.  
  
## <a name="see-also"></a>Vedere anche  
 [All'interno dell'editor principale](../extensibility/inside-the-core-editor.md)   
 [Funzionalità dell'editor](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
