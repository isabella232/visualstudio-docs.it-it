---
title: 'Procedura: Risolvere i problemi di servizi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 681564b2148fb9554e80105c2e18b1d220bb37ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62862846"
---
# <a name="how-to-troubleshoot-services"></a>Procedura: Risolvere i problemi di servizi
Esistono alcuni problemi comuni che possono verificarsi quando si prova a ottenere un servizio:

- Il servizio non è registrato con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Il servizio è richiesto dal tipo di interfaccia e non per tipo di servizio.

- Il pacchetto VSPackage che richiede il servizio non è stato individuato.

- Viene utilizzato il provider del servizio non corretto.

  Se non è possibile ottenere il servizio richiesto, la chiamata a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> restituisce null. È necessario verificare sempre i valori null dopo la richiesta di un servizio:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Per risolvere i problemi di un servizio

1. Esaminare il Registro di sistema per vedere se il servizio è stato registrato correttamente. Per altre informazioni, vedere [Procedura: Fornire un servizio](../extensibility/how-to-provide-a-service.md).

    Quanto segue *reg* frammento del file Mostra come potrebbe essere registrato il servizio SVsTextManager:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    Nell'esempio precedente, numero di versione è la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ad esempio 12.0 o 14.0, la chiave {F5E7E71D-1401-11d1-883B-0000F87579D2} è l'identificatore di servizio (SID) del servizio, SVsTextManager e le {il valore predefinito F5E7E720-1401-11D1-883B-0000F87579D2} è il GUID della gestione testo VSPackage, che fornisce il servizio del pacchetto.

2. Quando si chiama GetService, usare il tipo di servizio e non il tipo di interfaccia. Quando si richiede un servizio dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> estrae il GUID dal tipo. Un servizio non verrà trovato se sussistono le condizioni seguenti:

   1. Un tipo di interfaccia viene passato al metodo GetService anziché il tipo di servizio.

   2. Nessun GUID in modo esplicito viene assegnato all'interfaccia. Di conseguenza, il sistema crea un GUID predefinito per un oggetto in base alle esigenze.

3. Assicurarsi che il pacchetto VSPackage che richiede il servizio è stato individuato. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un pacchetto VSPackage di siti al termine della creazione e prima di chiamare <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.

    Se si dispone di codice in un costruttore di VSPackage che necessita di un servizio, spostare il `Initialize` (metodo).

4. Assicurarsi che si usa il provider del servizio corretto.

    Non tutti i provider di servizi sono uguali. Il provider di servizi che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passa a una finestra degli strumenti è diversa da quella passa a un pacchetto VSPackage. Il provider di servizio finestra degli strumenti è a conoscenza <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, ma non conosce <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. È possibile chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per ottenere un provider di servizi di VSPackage all'interno di una finestra degli strumenti.

    Se una finestra degli strumenti ospita un controllo utente o qualsiasi altro contenitore di controllo, il contenitore verrà individuato dal modello di componente di Windows e non sarà possibile accedere a qualsiasi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] servizi. È possibile chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per ottenere un provider di servizi di VSPackage all'interno di un contenitore di controlli.

## <a name="see-also"></a>Vedere anche
- [Elenco dei servizi disponibili](../extensibility/internals/list-of-available-services.md)
- [Usare e forniscono i servizi](../extensibility/using-and-providing-services.md)
- [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)