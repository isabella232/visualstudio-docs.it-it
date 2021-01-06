---
title: Servizi essenziali | Microsoft Docs
description: Informazioni sui servizi, che sono interfacce per l'utilizzo da un altro VSPackage. I servizi in un pacchetto VSPackage possono eseguire l'override di servizi incorporati o di altro.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 54d785d665122fd5c5fa1709aa9348777e3c730b
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875804"
---
# <a name="service-essentials"></a>Nozioni fondamentali sui servizi
Un servizio è un contratto tra due pacchetti VSPackage. Un pacchetto VSPackage fornisce un set specifico di interfacce per l'utilizzo da parte di un altro VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è a sua volta una raccolta di pacchetti VSPackage che fornisce servizi ad altri pacchetti VSPackage.

 Ad esempio, è possibile usare il servizio SVsActivityLog per ottenere un'interfaccia IVsActivityLog, che può essere usata per scrivere nel log attività. Per altre informazioni, vedere [procedura: usare il log attività](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce anche alcuni servizi predefiniti che non sono registrati. I pacchetti VSPackage possono sostituire i servizi predefiniti o altri fornendo un override del servizio. Per qualsiasi servizio è consentita una sola sostituzione del servizio.

 I servizi non hanno individuabilità. Pertanto, è necessario essere a conoscenza dell'identificatore del servizio (SID) di un servizio che si desidera utilizzare ed è necessario stabilire quali interfacce sono disponibili. La documentazione di riferimento per il servizio fornisce queste informazioni.

- I pacchetti VSPackage che forniscono servizi sono detti provider di servizi.

- I servizi forniti ad altri pacchetti VSPackage sono denominati servizi globali.

- I servizi disponibili solo per il pacchetto VSPackage che li implementa, o per qualsiasi oggetto creato, sono denominati servizi locali.

- I servizi che sostituiscono i servizi o i servizi predefiniti forniti da altri pacchetti sono detti override del servizio.

- I servizi o le sostituzioni dei servizi vengono caricati su richiesta, ovvero il provider di servizi viene caricato quando il servizio fornito viene richiesto da un altro pacchetto VSPackage.

- Per supportare il caricamento su richiesta, un provider di servizi registra i servizi globali con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Per altre informazioni, vedere [procedura: fornire un servizio](../../extensibility/how-to-provide-a-service.md).

- Dopo aver ottenuto un servizio, usare [QueryInterface](/cpp/atl/queryinterface) (codice non gestito) o eseguire il cast (codice gestito) per ottenere l'interfaccia desiderata, ad esempio:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Il codice gestito fa riferimento a un servizio in base al relativo tipo, mentre il codice non gestito fa riferimento a un servizio in base al relativo GUID.

- Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica un pacchetto VSPackage, passa un provider di servizi al pacchetto VSPackage per concedere all'accesso VSPackage ai servizi globali. Questa operazione è detta "Ubicazione" del pacchetto VSPackage.

- I pacchetti VSPackage possono essere provider di servizi per gli oggetti creati. Un modulo, ad esempio, potrebbe inviare una richiesta per un servizio color al relativo frame, che potrebbe passare la richiesta a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Gli oggetti gestiti che sono annidati in modo approfondito o che non sono in alcun sito possono chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per l'accesso diretto ai servizi globali.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Usare GetGlobalService

In alcuni casi potrebbe essere necessario ottenere un servizio da una finestra degli strumenti o da un contenitore di controlli che non è stato individuato, altrimenti è stato individuato con un provider di servizi che non è in grado di conoscere il servizio desiderato. Ad esempio, potrebbe essere necessario scrivere nel log attività dall'interno di un controllo. Per ulteriori informazioni su questi e altri scenari, vedere [procedura: risoluzione dei problemi relativi ai servizi](../../extensibility/how-to-troubleshoot-services.md).

È possibile ottenere la maggior parte dei servizi di Visual Studio chiamando il <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodo statico.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> si basa su un provider di servizi memorizzato nella cache inizializzato alla prima esecuzione di un pacchetto VSPackage derivato dal pacchetto. È necessario garantire che questa condizione sia soddisfatta o in caso contrario preparata per un servizio null.

Fortunatamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funziona in modo corretto nella maggior parte dei casi.

- Se un pacchetto VSPackage fornisce un servizio noto solo a un altro VSPackage, il pacchetto VSPackage che richiede il servizio viene inserito prima del caricamento del pacchetto VSPackage che fornisce il servizio.

- Se una finestra degli strumenti viene creata da un pacchetto VSPackage, il pacchetto VSPackage viene posto prima della creazione della finestra degli strumenti.

- Se un contenitore di controlli è ospitato da una finestra degli strumenti creata da un pacchetto VSPackage, il pacchetto VSPackage viene inserito prima della creazione del contenitore del controllo.

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

    Questo codice ottiene un servizio SVsActivityLog e ne esegue il cast a un'interfaccia IVsActivityLog, che può essere usata per scrivere nel log attività. Per un esempio, vedere [procedura: usare il log attività](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Vedi anche

- [Elenco di servizi disponibili](../../extensibility/internals/list-of-available-services.md)
- [Uso e offerta di servizi](../../extensibility/using-and-providing-services.md)
- [Cast e conversioni di tipi (C#)](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Cast](/cpp/cpp/casting)
