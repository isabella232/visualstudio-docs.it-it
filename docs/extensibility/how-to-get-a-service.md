---
title: 'Procedura: ottenere un servizio | Microsoft Docs'
description: Informazioni su come ottenere i servizi di Visual Studio per accedere a diverse funzionalità. È possibile ottenere la maggior parte dei servizi usando un pacchetto VSPackage.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9096250f72e6bf64b2c6b76eeaa313ee7769dd51
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070089"
---
# <a name="how-to-get-a-service"></a>Procedura: ottenere un servizio

Spesso è necessario ottenere i servizi di Visual Studio per accedere a diverse funzionalità. In generale, un servizio di Visual Studio fornisce una o più interfacce che è possibile usare. È possibile ottenere la maggior parte dei servizi da un pacchetto VSPackage.

Tutti i pacchetti VSPackage che derivano da <xref:Microsoft.VisualStudio.Shell.Package> e che sono stati correttamente inseriti in un sito possono richiedere un servizio globale. Poiché la `Package` classe implementa <xref:System.IServiceProvider> , anche tutti i pacchetti VSPackage che deriva da `Package` sono un provider di servizi.

Quando Visual Studio carica un <xref:Microsoft.VisualStudio.Shell.Package> oggetto, passa un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> oggetto al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodo durante l'inizializzazione. Questa operazione viene chiamata *Ubicazione* del pacchetto VSPackage. La `Package` classe esegue il wrapping del provider di servizi e fornisce il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodo per ottenere i servizi.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Recupero di un servizio da un VSPackage inizializzato

1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `GetServiceExtension` . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **nuovo progetto** cercando "VSIX".

2. A questo punto aggiungere un modello di elemento di comando personalizzato denominato **GetServiceCommand**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a   >  **estensibilità** di Visual C# e selezionare **comando personalizzato**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file di comando in *GetServiceCommand. cs*. Per ulteriori informazioni su come creare un comando personalizzato, [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

3. In *GetServiceCommand. cs* rimuovere il corpo del `MenuItemCommand` metodo e aggiungere il codice seguente:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Questo codice ottiene un servizio SVsActivityLog e ne esegue il cast a un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia, che può essere usata per scrivere nel log attività. Per un esempio, vedere [procedura: usare il log attività](../extensibility/how-to-use-the-activity-log.md).

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

5. Nel menu **strumenti** dell'istanza sperimentale, trovare il pulsante **richiama GetServiceCommand** . Quando si fa clic su questo pulsante, viene visualizzata una finestra di messaggio che indica che **il servizio log attività è stato trovato.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Recupero di un servizio da una finestra degli strumenti o da un contenitore di controlli

In alcuni casi potrebbe essere necessario ottenere un servizio da una finestra degli strumenti o da un contenitore di controlli che non è stato individuato, altrimenti è stato individuato con un provider di servizi che non è in grado di conoscere il servizio desiderato. Ad esempio, potrebbe essere necessario scrivere nel log attività dall'interno di un controllo.

Il metodo statico si <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> basa su un provider di servizi memorizzato nella cache che viene inizializzato alla prima esecuzione di un VSPackage derivato da <xref:Microsoft.VisualStudio.Shell.Package> .

Poiché il costruttore VSPackage viene chiamato prima che il pacchetto VSPackage sia situato, i servizi globali non sono in genere disponibili all'interno del costruttore VSPackage. Vedere [procedura: risolvere i problemi relativi ai servizi](../extensibility/how-to-troubleshoot-services.md) per una soluzione alternativa.

Di seguito è riportato un esempio di come ottenere un servizio in una finestra degli strumenti o in un altro elemento non VSPackage.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Recupero di un servizio dall'oggetto DTE

È anche possibile ottenere i servizi da un <xref:EnvDTE.DTEClass> oggetto. Tuttavia, è necessario ottenere l'oggetto DTE come servizio da un VSPackage o chiamando il <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodo statico.

L'oggetto DTE implementa <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> , che è possibile utilizzare per eseguire una query per un servizio utilizzando <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> .

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

- [Procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md)
- [Usare e fornire servizi](../extensibility/using-and-providing-services.md)
- [Essentials servizio](../extensibility/internals/service-essentials.md)
