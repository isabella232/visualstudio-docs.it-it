---
title: 'Procedura: Risolvere i problemi relativi ai servizi Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49560acdf57f5dad2c57f2a8e4649f194d6d8298
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710755"
---
# <a name="how-to-troubleshoot-services"></a>Procedura: Risolvere i problemi relativi ai serviziHow to: Troubleshoot services
Esistono diversi problemi comuni che possono verificarsi quando si tenta di ottenere un servizio:There are several common problems that can occur when you try to get a service:

- Il servizio non [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]è registrato con .

- Il servizio è richiesto dal tipo di interfaccia e non dal tipo di servizio.

- Il pacchetto VSPackage che richiede il servizio non è stato individuato.

- Viene utilizzato il provider di servizi errato.

  Se non è possibile ottenere il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> servizio richiesto, la chiamata a restituisce null. È sempre necessario verificare la proprietà null dopo aver richiesto un servizio:You should always test for null after requesting a service:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Per risolvere i problemi di un servizioTo troubleshoot a service

1. Esaminare il Registro di sistema per verificare se il servizio è stato registrato correttamente. Per ulteriori informazioni, vedere [Procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md).

    Il frammento di file *reg* seguente mostra come potrebbe essere registrato il servizio SVsTextManager:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    Nell'esempio precedente, il numero [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]di versione è la versione di , ad esempio 12.0 o 14.0, la chiave "F5E7E71D-1401-11d1-883B-0000F87579D2" è l'identificatore del servizio (SID) del servizio, SVsTextManager e il valore predefinito , F5E7E720-1401-11d1-883B-0000F87579D2, è il GUID del pacchetto del gestore di testo VSPackage, che fornisce il servizio.

2. Utilizzare il tipo di servizio e non il tipo di interfaccia quando si chiama GetService.Use the service type and not the interface type when you call GetService. Quando si richiede [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]un <xref:Microsoft.VisualStudio.Shell.Package> servizio da , estrae il GUID dal tipo. Un servizio non verrà trovato se esistono le seguenti condizioni:

   1. Un tipo di interfaccia viene passato a GetService anziché al tipo di servizio.

   2. Nessun GUID viene assegnato in modo esplicito all'interfaccia. Pertanto, il sistema crea un GUID predefinito per un oggetto in base alle esigenze.

3. Assicurarsi che il pacchetto VSPackage che richiede il servizio è stato individuato. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]siti un VSPackage dopo la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>costruzione e prima di chiamare .

    Se si dispone di codice in un costruttore VSPackage che richiede un servizio, spostarlo nel `Initialize` metodo .

4. Assicurarsi di utilizzare il provider di servizi corretto.

    Non tutti i fornitori di servizi sono uguali. Il provider [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di servizi che passa a una finestra degli strumenti è diverso da quello che passa a un vsPackage.The service provider that passes to a tool window differs from the one it passes to a VSPackage. Il provider di servizi <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>della finestra degli <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>strumenti conosce , ma non conosce . È possibile <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> chiamare per ottenere un provider di servizi VSPackage dall'interno di una finestra degli strumenti.

    Se una finestra degli strumenti ospita un controllo utente o qualsiasi altro contenitore di controlli, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] il contenitore verrà individuato dal modello di componente di Windows e non avrà accesso ad alcun servizio. È possibile <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> chiamare per ottenere un provider di servizi VSPackage dall'interno di un contenitore di controlli.

## <a name="see-also"></a>Vedere anche
- [Elenco dei servizi disponibili](../extensibility/internals/list-of-available-services.md)
- [Utilizzare e fornire servizi](../extensibility/using-and-providing-services.md)
- [Essenziali di servizio](../extensibility/internals/service-essentials.md)
