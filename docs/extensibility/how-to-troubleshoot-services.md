---
title: 'Procedura: Risolvere i problemi relativi ai servizi | Microsoft Docs'
description: Informazioni su come risolvere diversi problemi comuni che possono verificarsi quando si tenta di ottenere un servizio in Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d84e178f8dd3c7006dd3213fdb60eea9b96dac24
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124854"
---
# <a name="how-to-troubleshoot-services"></a>Procedura: Risolvere i problemi dei servizi
Quando si tenta di ottenere un servizio, possono verificarsi diversi problemi comuni:

- Il servizio non è registrato con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Il servizio è richiesto dal tipo di interfaccia e non dal tipo di servizio.

- Il pacchetto VSPackage che richiede il servizio non è stato sito.

- Viene usato il provider di servizi errato.

  Se non è possibile ottenere il servizio richiesto, la chiamata a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> restituisce null. Dopo aver richiesto un servizio, è consigliabile verificare sempre la proprietà Null:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Per risolvere i problemi relativi a un servizio

1. Esaminare il Registro di sistema per verificare se il servizio è stato registrato correttamente. Per altre informazioni, vedere [Procedura: Fornire un servizio](../extensibility/how-to-provide-a-service.md).

    Il *frammento di* file reg seguente mostra come registrare il servizio SVsTextManager:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    Nell'esempio precedente il numero di versione è la versione di , ad esempio [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 12.0 o 14.0, la chiave {F5E7E71D-1401-11d1-883B-0000F87579D2} è l'identificatore di servizio (SID) del servizio, SVsTextManager e il valore predefinito {F5E7E720-1401-11d1-883B-0000F87579D2} è il GUID del pacchetto VSPackage di gestione testo, che fornisce il servizio.

2. Usare il tipo di servizio e non il tipo di interfaccia quando si chiama GetService. Quando si richiede un servizio da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , <xref:Microsoft.VisualStudio.Shell.Package> estrae il GUID dal tipo . Un servizio non verrà trovato se sono presenti le condizioni seguenti:

   1. Un tipo di interfaccia viene passato a GetService anziché al tipo di servizio.

   2. Nessun GUID viene assegnato in modo esplicito all'interfaccia. Di conseguenza, il sistema crea un GUID predefinito per un oggetto in base alle esigenze.

3. Assicurarsi che il pacchetto VSPackage che richiede il servizio sia stato sito. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea un pacchetto VSPackage dopo la costruzione e prima di chiamare <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

    Se in un costruttore VSPackage è presente codice che richiede un servizio, spostarlo nel `Initialize` metodo .

4. Assicurarsi di usare il provider di servizi corretto.

    Non tutti i provider di servizi sono uguali. Il provider di servizi che passa a una finestra degli strumenti è diverso da quello passato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a un vspackage. Il provider di servizi della finestra degli strumenti conosce <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> , ma non conosce <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . È possibile chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per ottenere un provider di servizi VSPackage dall'interno di una finestra degli strumenti.

    Se una finestra degli strumenti ospita un controllo utente o qualsiasi altro contenitore di controlli, il contenitore verrà creato dal modello di componente Windows e non avrà accesso ad alcun [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] servizio. È possibile chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per ottenere un provider di servizi VSPackage dall'interno di un contenitore di controlli.

## <a name="see-also"></a>Vedi anche
- [Elenco dei servizi disponibili](../extensibility/internals/list-of-available-services.md)
- [Usare e fornire servizi](../extensibility/using-and-providing-services.md)
- [Informazioni di base sul servizio](../extensibility/internals/service-essentials.md)
- [Visual Studio risoluzione dei problemi](/troubleshoot/visualstudio/welcome-visual-studio/)