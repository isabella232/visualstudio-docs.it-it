---
title: Nozioni di base sul servizio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e2947cb4cd6a347d8e010340f8689eb1907a28a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705492"
---
# <a name="service-essentials"></a>Nozioni fondamentali sui servizi
A service is a contract between two VSPackages. Un pacchetto VSPackage fornisce un set specifico di interfacce per un altro VSPackage da utilizzare. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]è essa stessa una raccolta di vsPackage che fornisce servizi ad altri package VS.

 Ad esempio, è possibile usare il servizio SVsActivityLog per ottenere un'interfaccia IVsActivityLog, che è possibile usare per scrivere nel log attività. Per ulteriori informazioni, vedere [Procedura: utilizzare il log attività](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce anche alcuni servizi incorporati che non sono registrati. VSPackage possono sostituire built-in o altri servizi fornendo un override del servizio. Per qualsiasi servizio è consentita una sola sostituzione del servizio.

 I servizi non hanno alcuna individuabilità. Pertanto, è necessario conoscere l'identificatore del servizio (SID) di un servizio che si desidera utilizzare ed è necessario conoscere le interfacce che fornisce. La documentazione di riferimento per il servizio fornisce queste informazioni.

- VsPackage che forniscono servizi sono chiamati provider di servizi.

- I servizi forniti ad altri package VS sono denominati servizi globali.

- I servizi disponibili solo per il pacchetto VSPackage che li implementa o per qualsiasi oggetto creato, sono chiamati servizi locali.

- I servizi che sostituiscono i servizi incorporati o i servizi forniti da altri pacchetti sono denominati sostituzioni dei servizi.

- I servizi, o sostituzioni di servizio, vengono caricati su richiesta, ovvero il provider di servizi viene caricato quando il servizio fornito viene richiesto da un altro VSPackage.Services, or service overrides, are loaded on demand, that is, the service provider is loaded when the service it provides is requested by another VSPackage.

- Per supportare il caricamento su richiesta, un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]provider di servizi registra i propri servizi globali con . Per ulteriori informazioni, vedere [Procedura: fornire un servizio](../../extensibility/how-to-provide-a-service.md).

- Dopo aver ottenuto un servizio, usare QueryInterface (codice non gestito) o eseguire il cast (codice gestito) per ottenere l'interfaccia desiderata, ad esempio:After you obtain a service, use [QueryInterface](/cpp/atl/queryinterface) (unmanaged code) or casting (managed code) to get the desired interface, for example:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Il codice gestito fa riferimento a un servizio in base al tipo, mentre il codice non gestito fa riferimento a un servizio tramite il relativo GUID.

- Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica un pacchetto VSPackage, passa un provider di servizi per il pacchetto VSPackage per fornire il pacchetto VSPackage l'accesso ai servizi globali. Questa operazione viene definita "siting" del pacchetto VSPackage.

- I pacchetti VSPackage possono essere provider di servizi per gli oggetti creati. Ad esempio, un form potrebbe inviare una richiesta per un servizio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]colore al relativo frame, che potrebbe passare la richiesta a .

- Gli oggetti gestiti che sono annidati in profondità o che non si trovano affatto possono richiedere <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> l'accesso diretto ai servizi globali.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Usare GetGlobalServiceUse GetGlobalService

In alcuni stati potrebbe essere necessario ottenere un servizio da una finestra degli strumenti o da un contenitore di controlli che non è stato individuato oppure è stato individuato con un provider di servizi che non conosce il servizio desiderato. Ad esempio, è possibile scrivere nel log attività dall'interno di un controllo. Per ulteriori informazioni su questi e altri scenari, vedere [Procedura: risolvere i problemi relativi ai servizi](../../extensibility/how-to-troubleshoot-services.md).

È possibile ottenere la maggior parte <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> dei servizi di Visual Studio chiamando il metodo statico.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>si basa su un provider di servizi memorizzati nella cache che viene inizializzato la prima volta che viene individuato qualsiasi VSPackage derivato da Package. È necessario garantire che questa condizione sia soddisfatta oppure essere preparati per un servizio null.

Fortunatamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funziona correttamente la maggior parte del tempo.

- Se un pacchetto VSPackage fornisce un servizio noto solo a un altro VSPackage, il pacchetto VSPackage che richiede il servizio viene individuato prima che venga caricato il pacchetto VSPackage che fornisce il servizio.

- Se una finestra degli strumenti viene creata da un VSPackage, il pacchetto VSPackage viene individuato prima che venga creata la finestra degli strumenti.

- Se un contenitore di controlli è ospitato da una finestra degli strumenti creata da un VSPackage, il pacchetto VSPackage viene individuato prima che venga creato il contenitore di controlli.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Per ottenere un servizio dall'interno di una finestra degli strumenti o di un contenitore di controlliTo get a service from within a tool window or control container

- Inserire questo codice nel costruttore, nella finestra degli strumenti o nel contenitore dei controlli:Insert this code in the constructor, tool window, or control container:

    ```csharp
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```

    ```vb
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```

    Questo codice ottiene un servizio SVsActivityLog ed esegue il cast a un IVsActivityLog interfaccia, che può essere utilizzata per scrivere nel log attività. Per un esempio, vedere [Procedura: utilizzare il log attività](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Vedere anche

- [Elenco di servizi disponibili](../../extensibility/internals/list-of-available-services.md)
- [Uso e offerta di servizi](../../extensibility/using-and-providing-services.md)
- [Cast e conversioni di tipi (C#)](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Cast](/cpp/cpp/casting)
