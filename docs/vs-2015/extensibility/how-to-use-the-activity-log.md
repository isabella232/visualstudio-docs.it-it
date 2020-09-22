---
title: 'Procedura: usare il log attività | Microsoft Docs'
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
ms.openlocfilehash: d450e02d23159f186fd85bf1b687a2fb2c18e82a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840032"
---
# <a name="how-to-use-the-activity-log"></a>Procedura: Usare il log attività
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I pacchetti VSPackage possono scrivere messaggi nel log attività. Questa funzionalità è particolarmente utile per il debug dei pacchetti VSPackage negli ambienti di vendita al dettaglio.  
  
> [!TIP]
> Il log attività è sempre attivato. Visual Studio mantiene un buffer in sequenza delle ultime 100 voci, oltre alle prime dieci voci, che hanno informazioni di configurazione generali.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Per scrivere una voce nel log attività  
  
1. Inserire questo codice nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo o in qualsiasi altro metodo eccetto il costruttore VSPackage:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Questo codice ottiene il <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> servizio e ne esegue il cast a un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> scrive una voce informativa nel log attività usando il contesto culturale corrente.  
  
2. Quando il pacchetto VSPackage viene caricato (in genere quando viene richiamato un comando o viene aperta una finestra), il testo viene scritto nel log attività.  
  
### <a name="to-examine-the-activity-log"></a>Per esaminare il log attività  
  
1. Trovare il log attività nella sottocartella per i dati di Visual Studio: *% AppData%* \Microsoft\VisualStudio\14.0\ActivityLog.XML..  
  
2. Aprire il log attività con qualsiasi editor di testo. Ecco una voce tipica:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Poiché il log attività è un servizio, il log attività non è disponibile nel costruttore VSPackage.  
  
 È necessario ottenere il log attività immediatamente prima di scrivervi. Non memorizzare nella cache o salvare il log attività per un uso futuro.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Risoluzione dei problemi relativi ai pacchetti VSPackage](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
