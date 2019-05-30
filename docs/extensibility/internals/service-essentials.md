---
title: Servizio Essentials | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8817ca48ff0a3f44a973986a173e647ce89c662c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318693"
---
# <a name="service-essentials"></a>Nozioni fondamentali sui servizi
Un servizio è un contratto tra due pacchetti VSPackage. Un pacchetto VSPackage fornisce un set specifico di interfacce per un altro VSPackage da utilizzare. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è a sua volta una raccolta di VSPackage che fornisce servizi per gli altri pacchetti VSPackage.

 Ad esempio, è possibile utilizzare il servizio SVsActivityLog per ottenere un'interfaccia IVsActivityLog, che è possibile usare per scrivere nel log attività. Per altre informazioni, vedere [Procedura: Usare il Log attività](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce anche alcuni servizi predefiniti che non sono registrati. Pacchetti VSPackage possono sostituire incorporati o altri servizi, fornendo un override del servizio. Sostituzione di un solo servizio è consentito per qualsiasi servizio.

 Servizi non dispongono di alcuna esposizione al rilevamento. Pertanto, è necessario conoscere l'ID di servizio (SID) di un servizio che si desidera utilizzare, ed è necessario conoscere quali interfacce offre. La documentazione di riferimento per il servizio fornisce queste informazioni.

- Pacchetti VSPackage che forniscono servizi vengono chiamati i provider di servizi.

- I servizi forniti da altri pacchetti VSPackage sono denominati servizi globali.

- Servizi sono disponibili solo per il pacchetto VSPackage che li implementa o per tutti gli oggetti che vengono creati, sono denominati servizi locali.

- I servizi che sostituiscono i servizi incorporati o i servizi forniti da altri pacchetti, vengono chiamati servizio esegue l'override.

- I servizi o le sostituzioni di servizio, vengono caricate su richiesta, vale a dire, il provider del servizio viene caricato quando il servizio che fornisce è richiesto da un altro pacchetto VSPackage.

- Per supportare il caricamento su richiesta, un provider del servizio registra i suoi servizi globali con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Per altre informazioni, vedere [Procedura: Fornire un servizio](../../extensibility/how-to-provide-a-service.md).

- Dopo aver ottenuto un servizio, usare [QueryInterface](/cpp/atl/queryinterface) (codice non gestito) o al cast (codice gestito) per ottenere l'interfaccia desiderata, ad esempio:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Codice gestito fa riferimento a un servizio in base al tipo, mentre il codice non gestito si riferisce a un servizio con il relativo GUID.

- Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica un pacchetto VSPackage, passa un provider di servizi a VSPackage per consentire l'accesso a VSPackage per servizi globali. Ciò è detto "posizione" il pacchetto VSPackage.

- I VSPackage possono essere i provider di servizi per gli oggetti creati. Ad esempio, un modulo potrebbe inviare una richiesta per un servizio di colore per il frame, che potrà passare alla richiesta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- Gli oggetti gestiti che sono molto annidati, o non individuati affatto, possono chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per l'accesso diretto ai servizi globali.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Usare GetGlobalService

In alcuni casi potrebbe essere necessario ottenere un servizio da una finestra degli strumenti o controllo contenitore che non è stato individuato, altrimenti è stato individuato con un provider di servizi che non conosce il servizio desiderato. Ad esempio, è possibile scrivere nel log attività all'interno di un controllo. Per altre informazioni su questi e altri scenari, vedere [come: Risolvere i problemi di servizi](../../extensibility/how-to-troubleshoot-services.md).

È possibile ottenere la maggior parte dei servizi di Visual Studio tramite la chiamata al metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> (metodo).

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> si basa su un servizio memorizzato nella cache viene individuato provider che viene inizializzata la prima volta che un pacchetto VSPackage derivato dal pacchetto. È necessario garantire che questa condizione viene soddisfatta, altrimenti essere preparata per un servizio null.

Fortunatamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funziona correttamente la maggior parte dei casi.

- Se un pacchetto VSPackage fornisce un servizio noto solo a un altro VSPackage, il pacchetto VSPackage che richiede il servizio viene individuato prima il pacchetto VSPackage che fornisce che il servizio sia caricato.

- Se una finestra degli strumenti viene creata da un pacchetto VSPackage, il pacchetto VSPackage è collocato prima che venga creata la finestra degli strumenti.

- Se un contenitore di controlli è ospitato da una finestra degli strumenti creata da un pacchetto VSPackage, il pacchetto VSPackage è collocato prima che venga creato il contenitore del controllo.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Per ottenere un servizio dall'interno di un contenitore di controllo o finestra degli strumenti

- Inserire questo codice nel costruttore, finestra degli strumenti o contenitore di controlli:

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

    Questo codice ottiene un servizio SVsActivityLog e ne esegue il cast a un'interfaccia IVsActivityLog, che può essere usata per scrivere nel log attività. Per un esempio, vedere [Procedura: Usare il Log attività](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Vedere anche

- [Elenco di servizi disponibili](../../extensibility/internals/list-of-available-services.md)
- [Uso e fornitura di servizi](../../extensibility/using-and-providing-services.md)
- [Cast e conversioni di tipi](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Cast](/cpp/cpp/casting)