---
title: Service Essentials | Microsoft Docs
description: Informazioni sui servizi, ovvero interfacce che possono essere utilizzate da un altro VSPackage. I servizi in un VSPackage possono eseguire l'override di servizi predefiniti o di altro tipo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 66b5689c2212104608361ccc07a799051e4627eb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627335"
---
# <a name="service-essentials"></a>Nozioni fondamentali sui servizi
Un servizio è un contratto tra due VSPackage. Un VSPackage fornisce un set specifico di interfacce che un altro VSPackage può usare. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è di per sé una raccolta di VSPackage che fornisce servizi ad altri VSPackage.

 Ad esempio, è possibile usare il servizio SVsActivityLog per ottenere un'interfaccia IVsActivityLog, che è possibile usare per scrivere nel log attività. Per altre informazioni, vedere [Procedura: Usare il log attività](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce anche alcuni servizi predefiniti che non sono registrati. I pacchetti VSPackage possono sostituire i servizi predefiniti o altri fornendo un override del servizio. Per qualsiasi servizio è consentita una sola sostituzione del servizio.

 I servizi non sono individuabili. Pertanto, è necessario conoscere l'identificatore di servizio (SID) di un servizio che si desidera utilizzare ed è necessario conoscere le interfacce fornite. La documentazione di riferimento per il servizio fornisce queste informazioni.

- I pacchetti VSPackage che forniscono servizi sono denominati provider di servizi.

- I servizi forniti ad altri VSPackage sono detti servizi globali.

- I servizi disponibili solo per il pacchetto VSPackage che li implementa o per qualsiasi oggetto creato sono denominati servizi locali.

- I servizi che sostituiscono i servizi predefiniti o i servizi forniti da altri pacchetti sono detti override del servizio.

- I servizi o le sostituzioni del servizio vengono caricati su richiesta, cio' il provider di servizi viene caricato quando il servizio fornito viene richiesto da un altro VSPackage.

- Per supportare il caricamento su richiesta, un provider di servizi registra i servizi globali con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Per altre informazioni, vedere [Procedura: Fornire un servizio](../../extensibility/how-to-provide-a-service.md).

- Dopo aver ottenuto un servizio, usare [QueryInterface](/cpp/atl/queryinterface) (codice non gestito) o il cast (codice gestito) per ottenere l'interfaccia desiderata, ad esempio:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Il codice gestito fa riferimento a un servizio in base al tipo, mentre il codice non gestito fa riferimento a un servizio tramite il relativo GUID.

- Quando carica un VSPackage, passa un provider di servizi al pacchetto VSPackage per concedere al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pacchetto VSPackage l'accesso ai servizi globali. Questa operazione viene definita "siting" del pacchetto VSPackage.

- I pacchetti VSPackage possono essere provider di servizi per gli oggetti creati. Ad esempio, un modulo potrebbe inviare una richiesta per un servizio colori al relativo frame, che potrebbe passare la richiesta a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Gli oggetti gestiti annidati o non presenti nel sito possono richiedere <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> l'accesso diretto ai servizi globali.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Usare GetGlobalService

In alcuni casi può essere necessario ottenere un servizio da una finestra degli strumenti o da un contenitore di controllo che non è stato sito oppure è stato utilizzato un provider di servizi che non conosce il servizio desiderato. Ad esempio, è possibile scrivere nel log attività dall'interno di un controllo . Per altre informazioni su questi e altri scenari, vedere [Procedura: Risolvere i problemi dei servizi](../../extensibility/how-to-troubleshoot-services.md).

È possibile ottenere la maggior Visual Studio chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> statico .

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> si basa su un provider di servizi memorizzato nella cache inizializzato la prima volta che si trova un vspackage derivato da Package. È necessario garantire che questa condizione sia soddisfatta oppure prepararsi per un servizio Null.

Fortunatamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funziona correttamente nella maggior parte dei casi.

- Se un VSPackage fornisce un servizio noto solo a un altro VSPackage, il pacchetto VSPackage che richiede il servizio viene caricato prima del pacchetto VSPackage che fornisce il servizio.

- Se una finestra degli strumenti viene creata da un VSPackage, il pacchetto VSPackage viene creato prima della creazione della finestra degli strumenti.

- Se un contenitore di controlli è ospitato da una finestra degli strumenti creata da un VSPackage, il pacchetto VSPackage viene ospitato prima della creazione del contenitore di controlli.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Per ottenere un servizio dall'interno di una finestra degli strumenti o di un contenitore di controlli

- Inserire questo codice nel costruttore, nella finestra degli strumenti o nel contenitore di controlli:

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

    Questo codice ottiene un servizio SVsActivityLog ed esegue il cast a un'interfaccia IVsActivityLog, che può essere usata per scrivere nel log attività. Per un esempio, vedere [Procedura: Usare il log attività](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Vedi anche

- [Elenco di servizi disponibili](../../extensibility/internals/list-of-available-services.md)
- [Uso e offerta di servizi](../../extensibility/using-and-providing-services.md)
- [Cast e conversioni di tipi (C#)](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Cast](/cpp/cpp/casting)
