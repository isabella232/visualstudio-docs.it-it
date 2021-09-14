---
title: 'Procedura: Ottenere un servizio | Microsoft Docs'
description: Informazioni su come ottenere i Visual Studio per accedere a funzionalità diverse. È possibile ottenere la maggior parte dei servizi usando un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 810211f79bd04bcba9b59dcf60e16e14d19bc702
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626255"
---
# <a name="how-to-get-a-service"></a>Procedura: Ottenere un servizio

Spesso è necessario ottenere Visual Studio per accedere a funzionalità diverse. In generale, un Visual Studio fornisce una o più interfacce che è possibile usare. È possibile ottenere la maggior parte dei servizi da un VSPackage.

Qualsiasi VSPackage che deriva da e che è stato correttamente configurato può <xref:Microsoft.VisualStudio.Shell.Package> richiedere qualsiasi servizio globale. Poiché la `Package` classe implementa , anche qualsiasi <xref:System.IServiceProvider> VSPackage che deriva da è un `Package` provider di servizi.

Quando Visual Studio carica <xref:Microsoft.VisualStudio.Shell.Package> un oggetto , passa un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> oggetto al metodo durante <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> l'inizializzazione. Questa operazione è *denominata siting* del pacchetto VSPackage. La `Package` classe esegue il wrapping di questo provider di servizi e fornisce il metodo per ottenere i <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> servizi.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Recupero di un servizio da un VSPackage inizializzato

1. Ogni Visual Studio'estensione inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `GetServiceExtension` . È possibile trovare il modello di progetto VSIX nella finestra **di dialogo Project** nuovo progetto cercando "vsix".

2. Aggiungere ora un modello di elemento di comando personalizzato **denominato GetServiceCommand.** Nella finestra **di dialogo Aggiungi nuovo** elemento passare a **Estendibilità di Visual C#**  >   e selezionare **Comando personalizzato.** Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in *GetServiceCommand.cs*. Per altre informazioni su come creare un comando personalizzato, vedere [Creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

3. In *GetServiceCommand.cs* rimuovere il corpo del `MenuItemCommand` metodo e aggiungere il codice seguente:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Questo codice ottiene un servizio SVsActivityLog ed esegue il cast a un'interfaccia , che può essere usata per <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> scrivere nel log attività. Per un esempio, [vedere Procedura: Usare il log attività](../extensibility/how-to-use-the-activity-log.md).

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

5. Nel menu **Strumenti** dell'istanza sperimentale trovare il **pulsante Invoke GetServiceCommand (Richiama GetServiceCommand).** Quando si fa clic su questo pulsante, viene visualizzata una finestra di messaggio che indica **Trovato il servizio log attività.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Recupero di un servizio da una finestra degli strumenti o da un contenitore di controlli

In alcuni casi può essere necessario ottenere un servizio da una finestra degli strumenti o da un contenitore di controlli che non è stato sito oppure è stato sito con un provider di servizi che non conosce il servizio desiderato. Ad esempio, è possibile scrivere nel log attività dall'interno di un controllo .

Il metodo statico si basa su un provider di servizi memorizzato nella cache che viene inizializzato la prima volta che viene sito un <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> VSPackage <xref:Microsoft.VisualStudio.Shell.Package> derivato da .

Poiché il costruttore VSPackage viene chiamato prima del sito del VSPackage, i servizi globali non sono in genere disponibili all'interno del costruttore VSPackage. Per [una soluzione alternativa, vedere Procedura: Risolvere i](../extensibility/how-to-troubleshoot-services.md) problemi relativi ai servizi.

Ecco un esempio di come ottenere un servizio in una finestra degli strumenti o in un altro elemento non VSPackage.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Recupero di un servizio dall'oggetto DTE

È anche possibile ottenere servizi <xref:EnvDTE.DTEClass> dall'oggetto . Tuttavia, è necessario ottenere l'oggetto DTE come servizio da un VSPackage o chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> statico .

L'oggetto DTE implementa <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> , che è possibile usare per eseguire una query per un servizio tramite <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> .

Ecco come ottenere un servizio dall'oggetto DTE.

```csharp
// Start with the DTE object, for example: 
// using EnvDTE;
// DTE dte = (DTE)GetService(typeof(DTE));

ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
if (sp != null)
{
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log != null)
    {
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");
    }
}
```

## <a name="see-also"></a>Vedi anche

- [Procedura: Fornire un servizio](../extensibility/how-to-provide-a-service.md)
- [Usare e fornire servizi](../extensibility/using-and-providing-services.md)
- [Informazioni di base sul servizio](../extensibility/internals/service-essentials.md)
