---
title: 'Procedura: risoluzione dei problemi relativi ai servizi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 588396f3f152222c4e79b03a1d733524a8ff3ca9
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905721"
---
# <a name="how-to-troubleshoot-services"></a>Procedura: risolvere i problemi relativi ai servizi
Quando si tenta di ottenere un servizio, è possibile che si verifichino molti problemi comuni:

- Il servizio non è registrato con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Il servizio è richiesto dal tipo di interfaccia e non dal tipo di servizio.

- Il pacchetto VSPackage che richiede il servizio non è stato sito.

- Viene utilizzato il provider di servizi errato.

  Se non è possibile ottenere il servizio richiesto, la chiamata a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> restituisce null. È consigliabile testare sempre per null dopo la richiesta di un servizio:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Per risolvere i problemi relativi a un servizio

1. Esaminare il registro di sistema per verificare se il servizio è stato registrato correttamente. Per altre informazioni, vedere [procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md).

    Il frammento di file *reg* seguente mostra come potrebbe essere registrato il servizio SVsTextManager:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    Nell'esempio precedente, il numero di versione è la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , ad esempio 12,0 o 14,0, la chiave {F5E7E71D-1401-11D1-883B-0000F87579D2} è l'identificatore del servizio (SID) del servizio, SVsTextManager, e il valore predefinito {F5E7E720-1401-11D1-883B-0000F87579D2} è il GUID del pacchetto del pacchetto VSPackage di gestione del testo, che fornisce il servizio.

2. Usare il tipo di servizio e non il tipo di interfaccia quando si chiama GetService. Quando si richiede un servizio da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , <xref:Microsoft.VisualStudio.Shell.Package> estrae il GUID dal tipo. Un servizio non verrà trovato se sussistono le condizioni seguenti:

   1. Un tipo di interfaccia viene passato a GetService invece che al tipo di servizio.

   2. Nessun GUID viene assegnato in modo esplicito all'interfaccia. Pertanto, il sistema crea un GUID predefinito per un oggetto in base alle esigenze.

3. Verificare che il pacchetto VSPackage che richiede il servizio sia stato sito. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]siti un pacchetto VSPackage dopo la relativa costruzione e prima della chiamata a <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

    Se si dispone di codice in un costruttore VSPackage che necessita di un servizio, spostarlo nel `Initialize` metodo.

4. Assicurarsi di usare il provider di servizi corretto.

    Non tutti i provider di servizi sono uguali. Il provider di servizi che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passa a una finestra degli strumenti è diverso da quello che passa a un VSPackage. Il provider di servizi della finestra degli strumenti è a conoscenza di <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> , ma non è a conoscenza di <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . È possibile chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per ottenere un provider di servizi VSPackage dall'interno di una finestra degli strumenti.

    Se una finestra degli strumenti ospita un controllo utente o qualsiasi altro contenitore di controlli, il contenitore verrà ospitato dal modello di componenti di Windows e non potrà accedere ai [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] servizi. È possibile chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per ottenere un provider di servizi VSPackage dall'interno di un contenitore di controlli.

## <a name="see-also"></a>Vedere anche
- [Elenco dei servizi disponibili](../extensibility/internals/list-of-available-services.md)
- [Usare e fornire servizi](../extensibility/using-and-providing-services.md)
- [Essentials servizio](../extensibility/internals/service-essentials.md)
