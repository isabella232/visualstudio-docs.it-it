---
title: 'Procedura: Ottenere un servizio Documenti Microsoft'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8e6f20eaa08d6bb7aaa0cc9e560856daa5959e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710962"
---
# <a name="how-to-get-a-service"></a>Procedura: Ottenere un servizioHow to: Get a service

Spesso è necessario ottenere i servizi di Visual Studio per accedere a funzionalità diverse. In generale, un servizio di Visual Studio fornisce una o più interfacce che è possibile usare. È possibile ottenere la maggior parte dei servizi da un pacchetto VSPackage.You can get most services from a VSPackage.

Qualsiasi VSPackage che <xref:Microsoft.VisualStudio.Shell.Package> deriva da e che è stato individuato correttamente può richiedere qualsiasi servizio globale. Poiché `Package` la <xref:System.IServiceProvider>classe implementa , qualsiasi `Package` VSPackage che deriva da è anche un provider di servizi.

Quando Visual Studio <xref:Microsoft.VisualStudio.Shell.Package>carica un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> , passa un oggetto al metodo durante l'inizializzazione. Questo è chiamato *sipario* del pacchetto VSPackage. La `Package` classe esegue il wrapping <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> di questo provider di servizi e fornisce il metodo per ottenere i servizi.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Recupero di un servizio da un pacchetto VSPackage inizializzatoGetting a service from an initialized VSPackage

1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un progetto `GetServiceExtension`VSIX denominato . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **Nuovo progetto** cercando "vsix".

2. Aggiungere ora un modello di elemento di comando personalizzato denominato **GetServiceCommand**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a**Estensibilità** **di Visual C,** > quindi selezionare **Comando personalizzato**. Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in *GetServiceCommand.cs*. Per altre informazioni su come creare un comando personalizzato, [creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md) di menuFor more information about how to create a custom command, Create an extension with a menu command

3. In *GetServiceCommand.cs*, rimuovere `MenuItemCommand` il corpo del metodo e aggiungere il codice seguente:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Questo codice ottiene un servizio SVsActivityLog <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> e ne esegue il cast a un'interfaccia, che può essere usata per scrivere nel log attività. Per un esempio, vedere [Procedura: Utilizzare il registro attività](../extensibility/how-to-use-the-activity-log.md).

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

5. Nel menu **Strumenti** dell'istanza sperimentale individuare il pulsante **Invoke GetServiceCommand.** Quando si fa clic su questo pulsante, verrà visualizzata una finestra di messaggio che indica **Trovato il servizio registro attività.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Recupero di un servizio da una finestra degli strumenti o da un contenitore di controlliGetting a service from a tool window or control container

In alcuni stati potrebbe essere necessario ottenere un servizio da una finestra degli strumenti o da un contenitore di controlli che non è stato individuato oppure è stato individuato con un provider di servizi che non conosce il servizio desiderato. Ad esempio, è possibile scrivere nel log attività dall'interno di un controllo.

Il <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodo statico si basa su un provider di servizi memorizzati <xref:Microsoft.VisualStudio.Shell.Package> nella cache che viene inizializzato la prima volta che viene individuato qualsiasi VSPackage derivato da.

Poiché il costruttore VSPackage viene chiamato prima che il pacchetto VSPackage viene individuato, i servizi globali sono in genere non disponibili all'interno del costruttore VSPackage. Per una soluzione alternativa, vedere [Procedura: Risolvere i problemi relativi ai servizi.](../extensibility/how-to-troubleshoot-services.md)

Ecco un esempio del modo per ottenere un servizio in una finestra degli strumenti o un altro elemento non VSPackage.Here's an example of the way to get a service in a tool window or other non-VSPackage element.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Recupero di un servizio dall'oggetto DTE

È inoltre possibile <xref:EnvDTE.DTEClass> ottenere servizi dall'oggetto. Tuttavia, è necessario ottenere l'oggetto DTE come servizio <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> da un VSPackage o chiamando il metodo statico.

L'oggetto <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>DTE implementa , che è possibile <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>utilizzare per eseguire una query per un servizio utilizzando .

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

## <a name="see-also"></a>Vedere anche

- [Procedura: fornire un servizioHow to: Provide a service](../extensibility/how-to-provide-a-service.md)
- [Utilizzare e fornire servizi](../extensibility/using-and-providing-services.md)
- [Essenziali di servizio](../extensibility/internals/service-essentials.md)
