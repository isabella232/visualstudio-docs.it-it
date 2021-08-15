---
title: 'Procedura: Usare il log attività | Microsoft Docs'
description: I pacchetti VSPackage possono scrivere messaggi nel log attività. Informazioni su come usare il log attività per il debug di VSPackage negli ambienti di vendita al dettaglio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: acf0e2d5cd5d72670b00e4cffa05a74c09f8f7e19604edeaabcc82ce834c0afe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401583"
---
# <a name="how-to-use-the-activity-log"></a>Procedura: Usare il log attività
I pacchetti VSPackage possono scrivere messaggi nel log attività. Questa funzionalità è particolarmente utile per il debug di VSPackage negli ambienti di vendita al dettaglio.

> [!TIP]
> Il log attività è sempre attivato. Visual Studio un buffer in sequenza delle ultime 100 voci e delle prime 10 voci, che hanno informazioni di configurazione generali.

## <a name="to-write-an-entry-to-the-activity-log"></a>Per scrivere una voce nel log attività

1. Inserire questo codice nel metodo o in qualsiasi altro metodo ad <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> eccezione del costruttore VSPackage:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Questo codice ottiene il <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> servizio e lo esegue il cast a un'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> scrive una voce in formato informativo nel log attività usando il contesto culturale corrente.

2. Quando il pacchetto VSPackage viene caricato (in genere quando viene richiamato un comando o viene aperta una finestra), il testo viene scritto nel log attività.

## <a name="to-examine-the-activity-log"></a>Per esaminare il log attività

1. Eseguire Visual Studio con l'opzione della riga [di comando /Log](../ide/reference/log-devenv-exe.md) per scrivere ActivityLog.xml su disco durante la sessione.

2. Dopo aver Visual Studio, trovare il log attività nella sottocartella per Visual Studio dati:

   <em> *%AppData%</em>\Microsoft\VisualStudio \\ \<version>\ActivityLog.xml*.

3. Aprire il log attività con qualsiasi editor di testo. Ecco una voce tipica:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Programmazione efficiente

Poiché il log attività è un servizio, il log attività non è disponibile nel costruttore VSPackage.

È necessario ottenere il log attività subito prima di scrivervi. Non memorizzare nella cache o salvare il log attività per un uso futuro.

## <a name="see-also"></a>Vedi anche

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Risoluzione dei problemi relativi ai pacchetti VSPackage](../extensibility/troubleshooting-vspackages.md)
- [VSPackages](../extensibility/internals/vspackages.md)
