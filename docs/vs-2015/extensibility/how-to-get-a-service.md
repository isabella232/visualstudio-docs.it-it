---
title: 'Procedura: ottenere un servizio | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea5f3be4f5792213c5625e4c287195161eb1dd62
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785066"
---
# <a name="how-to-get-a-service"></a>Procedura: ottenere un servizio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È spesso necessario ottenere i servizi di Visual Studio per accedere alle funzionalità diverse. In generale, un servizio di Visual Studio fornisce una o più interfacce che è possibile usare. È possibile ottenere la maggior parte dei servizi da un pacchetto VSPackage.  
  
 Qualsiasi pacchetto VSPackage che deriva da <xref:Microsoft.VisualStudio.Shell.Package> e che è stato individuato correttamente può richiedere qualsiasi servizio globale. Dal momento che implementa la classe del pacchetto <xref:System.IServiceProvider>, qualsiasi pacchetto VSPackage che deriva da pacchetto è anche un provider di servizi.  
  
 Quando Visual Studio carica una <xref:Microsoft.VisualStudio.Shell.Package>, passa una <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> dell'oggetto per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodo durante l'inizializzazione. Questa operazione viene definita *posa* il pacchetto VSPackage. La classe del pacchetto esegue il wrapping di questo provider di servizi e fornisce il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodo per i servizi.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Recupero di un servizio da un pacchetto VSPackage inizializzato  
  
1.  Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX che contiene gli asset di estensione. Creare un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] progetto VSIX denominato `GetServiceExtension`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# / Extensibility**.  
  
2.  A questo punto aggiungere un modello di elemento di comando personalizzato denominato **GetServiceCommand**. Nel **Aggiungi nuovo elemento** finestra di dialogo passa alla **Visual c# / Extensibility** e selezionare **comando personalizzato**. Nel **Name** campo nella parte inferiore della finestra, modificare il nome di file di comando da **GetServiceCommand.cs**. Per altre informazioni su come creare un comando personalizzato, [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  In GetServiceCommand.cs, rimuovere il corpo del metodo MenuItemCommand e aggiungere il codice seguente:  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Questo codice ottiene un servizio SVsActivityLog e ne esegue il cast a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia, che può essere usato per scrivere nel log attività. Per un esempio, vedere [procedura: usare il Log attività](../extensibility/how-to-use-the-activity-log.md).  
  
4.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.  
  
5.  Nel menu Strumenti dell'istanza sperimentale, trovare il **richiamare GetServiceCommand** pulsante. Quando si fa clic su questo pulsante, si dovrebbe essere una finestra di messaggio con la dicitura **individuato il servizio di log attività.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Recupero di un servizio da un contenitore di controllo o finestra degli strumenti  
 In alcuni casi potrebbe essere necessario ottenere un servizio da una finestra degli strumenti o controllo contenitore che non è stato individuato, altrimenti è stato individuato con un provider di servizi che non conosce il servizio desiderato. Ad esempio, è possibile scrivere nel log attività all'interno di un controllo.  
  
 Il metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodo si basa su un provider di servizi memorizzato nella cache che viene inizializzato al primo qualsiasi pacchetto VSPackage è derivato da <xref:Microsoft.VisualStudio.Shell.Package> viene individuato.  
  
 Poiché il costruttore di VSPackage viene chiamato prima che il VSPackage viene individuato, servizi globali vengono in genere non sono disponibili all'interno del costruttore di VSPackage. Visualizzare [procedura: risolvere i problemi di servizi](../extensibility/how-to-troubleshoot-services.md) per una soluzione alternativa.  
  
 Di seguito è riportato un esempio della modalità per ottenere un servizio in una finestra degli strumenti o un altro elemento non VSPackage.  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>Recupero di un servizio dall'oggetto DTE  
 È anche possibile ottenere servizi da <xref:EnvDTE.DTEClass> oggetto. Tuttavia, è necessario ottenere l'oggetto DTE come un servizio da un pacchetto VSPackage o chiamando il metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> (metodo).  
  
 Implementa l'oggetto DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, che è possibile usare per eseguire query per un servizio utilizzando <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
 Di seguito viene illustrato come ottenere un servizio dall'oggetto DTE.  
  
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

