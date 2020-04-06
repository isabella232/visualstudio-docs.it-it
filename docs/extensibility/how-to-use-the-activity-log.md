---
title: 'Procedura: Utilizzare il log attività . Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64986be303370cf8c9048612ff3d44e82e96805a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710575"
---
# <a name="how-to-use-the-activity-log"></a>Procedura: utilizzare il log attivitàHow to: Use the activity log
VSPackage possono scrivere messaggi nel log attività. Questa funzionalità è particolarmente utile per il debug di VSPackage in ambienti di vendita al dettaglio.

> [!TIP]
> Il registro attività è sempre attivato. Visual Studio mantiene un buffer in sequenza delle ultime 100 voci, nonché le prime 10 voci, che dispongono di informazioni di configurazione generali.

## <a name="to-write-an-entry-to-the-activity-log"></a>Per scrivere una voce nel log attività

1. Inserire questo codice <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> nel metodo o in qualsiasi altro metodo ad eccezione del costruttore VSPackage:Insert this code in the method or in any other method except the VSPackage constructor:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Questo codice <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> ottiene il servizio ed <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> esegue il cast a un'interfaccia. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>scrive una voce informativa nel registro attività utilizzando il contesto culturale corrente.

2. Quando il pacchetto VSPackage viene caricato (in genere quando viene richiamato un comando o viene aperta una finestra), il testo viene scritto nel log attività.

## <a name="to-examine-the-activity-log"></a>Per esaminare il registro attività

1. Eseguire Visual Studio con l'opzione della riga di comando [/Log](../ide/reference/log-devenv-exe.md) per scrivere ActivityLog.xml su disco durante la sessione.

2. Dopo aver chiuso Visual Studio, trovare il log attività nella sottocartella per i dati di Visual Studio:After closing Visual Studio, find the activity log in the subfolder for Visual Studio data:

   <em> *%AppData%</em>: versione\\\<di VisualStudio> ActivityLog.xml*.

3. Aprire il registro attività con qualsiasi editor di testo. Ecco una voce tipica:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Programmazione efficiente

Poiché il log attività è un servizio, il log attività non è disponibile nel costruttore VSPackage.Because the activity log is a service, the activity log is unavailable in the VSPackage constructor.

È necessario ottenere il log attività appena prima di scrivervi. Non memorizzare nella cache o salvare il registro attività per un utilizzo futuro.

## <a name="see-also"></a>Vedere anche

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Risoluzione dei problemi relativi ai pacchetti VSPackage](../extensibility/troubleshooting-vspackages.md)
- [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
