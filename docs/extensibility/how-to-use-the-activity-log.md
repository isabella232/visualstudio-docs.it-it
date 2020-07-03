---
title: 'Procedura: usare il log attività | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 824feee64f928dc837a379aeb539daaa5ba0d1db
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905580"
---
# <a name="how-to-use-the-activity-log"></a>Procedura: usare il log attività
I pacchetti VSPackage possono scrivere messaggi nel log attività. Questa funzionalità è particolarmente utile per il debug dei pacchetti VSPackage negli ambienti di vendita al dettaglio.

> [!TIP]
> Il log attività è sempre attivato. Visual Studio mantiene un buffer in sequenza delle ultime 100 voci, nonché le prime 10 voci, che hanno informazioni di configurazione generali.

## <a name="to-write-an-entry-to-the-activity-log"></a>Per scrivere una voce nel log attività

1. Inserire questo codice nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo o in qualsiasi altro metodo eccetto il costruttore VSPackage:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Questo codice ottiene il <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> servizio e ne esegue il cast a un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>scrive una voce informativa nel log attività usando il contesto culturale corrente.

2. Quando il pacchetto VSPackage viene caricato (in genere quando viene richiamato un comando o viene aperta una finestra), il testo viene scritto nel log attività.

## <a name="to-examine-the-activity-log"></a>Per esaminare il log attività

1. Eseguire Visual Studio con l'opzione della riga di comando [/log](../ide/reference/log-devenv-exe.md) per scrivere ActivityLog.xml su disco durante la sessione.

2. Dopo la chiusura di Visual Studio, trovare il log attività nella sottocartella per i dati di Visual Studio:

   <em> *% AppData%</em>\Microsoft\VisualStudio \\ \<version>\ActivityLog.xml*.

3. Aprire il log attività con qualsiasi editor di testo. Ecco una voce tipica:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Programmazione efficiente

Poiché il log attività è un servizio, il log attività non è disponibile nel costruttore VSPackage.

È necessario ottenere il log attività immediatamente prima di scrivervi. Non memorizzare nella cache o salvare il log attività per un uso futuro.

## <a name="see-also"></a>Vedere anche

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Risoluzione dei problemi relativi ai pacchetti VSPackage](../extensibility/troubleshooting-vspackages.md)
- [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
