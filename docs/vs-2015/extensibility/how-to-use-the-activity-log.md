---
title: 'Procedura: Usare il Log attività | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 812862c3eaf99b7459bb422e174f8fe155ea384a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042587"
---
# <a name="how-to-use-the-activity-log"></a>Procedura: Usare il log attività
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I pacchetti VSPackage possono scrivere messaggi nel log attività. Questa funzionalità è particolarmente utile per il debug di pacchetti VSPackage negli ambienti delle vendite al dettaglio.  
  
> [!TIP]
>  Il log attività è sempre attivato. Visual Studio consente di mantenere un buffer in sequenza delle ultime 100 voci, nonché le prime dieci voci, che dispone di informazioni di configurazione generale.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Per scrivere una voce nel log attività  
  
1. Inserire questo codice nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo o in qualsiasi altro metodo, ad eccezione del costruttore VSPackage:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Questo codice ottiene la <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> del servizio e ne esegue il cast a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Scrive una voce informativo nel log attività usando il contesto relative alla lingua corrente.  
  
2. Quando viene caricato il pacchetto VSPackage (in genere quando un comando viene richiamato o viene aperta una finestra), il testo venga scritto nel log attività.  
  
### <a name="to-examine-the-activity-log"></a>Per esaminare il log attività  
  
1. Trovare il log attività nella sottocartella per i dati di Visual Studio: *% AppData %* \Microsoft\VisualStudio\14.0\ActivityLog.XML...  
  
2. Aprire il log attività con qualsiasi editor di testo. Di seguito è una voce tipica:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Poiché il log attività è un servizio, il log attività non è disponibile nel costruttore di VSPackage.  
  
 Prima di scriverci dentro, si dovrebbe ottenere il log attività. Non memorizzare nella cache o salvare il log attività per un uso futuro.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Risoluzione dei problemi relativi a pacchetti VSPackage](../extensibility/troubleshooting-vspackages.md)   
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
