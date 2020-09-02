---
title: 'Procedura: ottenere un servizio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46ef86b8cde506aad3e00aa6b5dbc6470c0087de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204184"
---
# <a name="how-to-get-a-service"></a>Procedura: Ottenere un servizio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spesso è necessario ottenere i servizi di Visual Studio per accedere a diverse funzionalità. In generale, un servizio di Visual Studio fornisce una o più interfacce che è possibile usare. È possibile ottenere la maggior parte dei servizi da un pacchetto VSPackage.  
  
 Tutti i pacchetti VSPackage che derivano da <xref:Microsoft.VisualStudio.Shell.Package> e che sono stati correttamente inseriti in un sito possono richiedere un servizio globale. Poiché la classe del pacchetto implementa <xref:System.IServiceProvider> , anche tutti i pacchetti VSPackage che derivano dal pacchetto sono un provider di servizi.  
  
 Quando Visual Studio carica un <xref:Microsoft.VisualStudio.Shell.Package> oggetto, passa un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> oggetto al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodo durante l'inizializzazione. Questa operazione viene chiamata *Ubicazione* del pacchetto VSPackage. La classe del pacchetto esegue il wrapping del provider di servizi e fornisce il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodo per ottenere i servizi.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Recupero di un servizio da un VSPackage inizializzato  
  
1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] progetto VSIX denominato `GetServiceExtension` . Il modello di progetto VSIX è reperibile nella finestra di dialogo **nuovo progetto** in **Visual C#/extensibility**.  
  
2. A questo punto aggiungere un modello di elemento di comando personalizzato denominato **GetServiceCommand**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a **Visual C#/extensibility** e selezionare **comando personalizzato**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file di comando in **GetServiceCommand.cs**. Per ulteriori informazioni su come creare un comando personalizzato, [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3. In GetServiceCommand.cs rimuovere il corpo del metodo MenuItemCommand e aggiungere il codice seguente:  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Questo codice ottiene un servizio SVsActivityLog e ne esegue il cast a un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia, che può essere usata per scrivere nel log attività. Per un esempio, vedere [procedura: usare il log attività](../extensibility/how-to-use-the-activity-log.md).  
  
4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.  
  
5. Nel menu strumenti dell'istanza sperimentale, trovare il pulsante **richiama GetServiceCommand** . Quando si fa clic su questo pulsante, viene visualizzata una finestra di messaggio che indica che **il servizio log attività è stato trovato.**  
  
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
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md)   
 [Uso e fornitura di servizi](../extensibility/using-and-providing-services.md)   
 [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)
