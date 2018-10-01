---
title: 'Procedura: fornire un servizio asincrono di Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4a58d249c68a0b28158edb92428d1470973cc094
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518580"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Procedura: fornire un servizio asincrono di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: fornire un servizio asincrono di Visual Studio](https://docs.microsoft.com/visualstudio/extensibility/how-to-provide-an-asynchronous-visual-studio-service).  
  
Se si vuole ottenere un servizio senza bloccare il thread dell'interfaccia utente, è necessario creare un servizio asincrono e caricare il pacchetto in un thread in background. A tale scopo è possibile usare un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> anziché un <xref:Microsoft.VisualStudio.Shell.Package>, aggiungere il servizio con metodi asincroni speciale del pacchetto asincrona  
  
 Per informazioni su come fornire servizi di Visual Studio sincroni, vedere [procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implementing-an-asynchronous-service"></a>Implementazione di un servizio asincrono  
  
1.  Creare un progetto VSIX (**File / nuovo / progetto / Visual c# / estendibilità / progetto VSIX**). Denominare il progetto **TestAsync**.  
  
2.  Aggiungere al progetto un pacchetto VSPackage. Selezionare il nodo del progetto nel **Esplora soluzioni** e fare clic su **Aggiungi / nuovo elemento / elementi di Visual c# / Extensibility / pacchetto di Visual Studio**. Nome del file **TestAsyncPackage.cs**.  
  
3.  In TestAsyncPackage.cs, modificare il pacchetto da cui ereditare AsyncPackage anziché pacchetto seguenti:  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Per implementare un servizio, è necessario creare tre tipi:  
  
    -   Interfaccia che descrive il servizio. Molte di queste interfacce sono vuote, vale a dire, non hanno nessun metodo.  
  
    -   Interfaccia che descrive l'interfaccia del servizio. Questa interfaccia include i metodi da implementare.  
  
    -   Una classe che implementa il servizio e l'interfaccia del servizio.  
  
5.  Nell'esempio seguente viene illustrata un'implementazione di base dei tre tipi. Il costruttore della classe del servizio deve impostare il provider del servizio. In questo esempio si aggiungerà solo il servizio al file di codice del pacchetto.  
  
6.  Aggiungere le seguenti istruzioni using al file del pacchetto:  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  Ecco l'implementazione del servizio asincrona. Si noti che è necessario impostare il provider del servizio asincrone anziché il provider del servizio sincrone nel costruttore:  
  
    ```  
    public class TextWriterService : STextWriterService, ITextWriterService  
    {  
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;  
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)  
        {  
            serviceProvider = provider;  
        }  
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)  
        {  
            StreamWriter writer = new StreamWriter(path);  
            await writer.WriteLineAsync(line);  
            writer.Close();  
        }  
        public TaskAwaiter GetAwaiter()  
        {  
            return new TaskAwaiter();  
        }  
    }  
    public interface STextWriterService  
    {  
    }  
    public interface ITextWriterService   
    {  
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);  
        TaskAwaiter GetAwaiter();  
    }  
    ```  
  
## <a name="registering-a-service"></a>La registrazione di un servizio  
 Per registrare un servizio, aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> al pacchetto che fornisce il servizio. Vi sono due differenze tramite la registrazione di un servizio sincrone:  
  
-   Se si è il caricamento automatico il pacchetto, è necessario aggiungere il <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> valore BackgroundLoad all'attributo. Per altre informazioni sui pacchetti VSPackage di caricamento automatico, vedere [caricamento di VSPackage](../extensibility/loading-vspackages.md).  
  
-   È necessario aggiungere il **AllowsBackgroundLoading = true** campo il <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Per altre informazioni sul PackageRegistrationAttribute, vedere [la registrazione e annullamento della registrazione dei pacchetti VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Di seguito è riportato un esempio di un AsyncPackage con una registrazione servizio asincrone::  
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="adding-a-service"></a>Aggiunta di un servizio  
  
1.  In TestAsyncPackage.cs, rimuovere il `Initialize()` ed eseguire l'override di `InitializeAsync()` (metodo). Aggiungere il servizio e aggiungere un metodo di callback per creare i servizi. Di seguito è riportato un esempio dell'inizializzatore asincrona aggiunta di un servizio:  
  
    ```  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  Aggiungere un riferimento a Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Implementare il metodo di callback come un metodo asincrono che crea e restituisce il servizio.  
  
    ```csharp  
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        STextWriterService service = null;  
        await System.Threading.Tasks.Task.Run(() => {  
                    service = new TextWriterService(this);  
             });  
  
        return service;  
    }  
  
    ```  
  
## <a name="using-a-service"></a>Utilizzo di un servizio  
 Ora è possibile ottenere il servizio e usarne i metodi.  
  
1.  Come sarà illustrato nell'inizializzatore, ma è possibile ottenere in qualsiasi punto di servizio che si desidera utilizzare il servizio.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     Non dimenticare di modificare  *\<userpath >* a un nome e il percorso appropriato nel computer.  
  
2.  Compilare ed eseguire il codice. Quando viene visualizzata l'istanza sperimentale di Visual Studio, aprire una soluzione. In questo modo il AsyncPackage per caricare automaticamente. Quando si è eseguito l'inizializzatore, si deve trovare un file nel percorso specificato.  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Usando un servizio asincrono in un gestore comando  
 Ecco un esempio di come usare un servizio asincrono in un comando di menu. È possibile usare la procedura illustrata in questo caso usare il servizio in altri metodi non asincrona.  
  
1.  Aggiungere un comando di menu al progetto. (Nelle **Esplora soluzioni**, selezionare il nodo del progetto, pulsante destro del mouse e selezionare **Aggiungi / nuovo elemento / Extensibility / comando personalizzato**.) Denominare il file di comando **TestAsyncCommand.cs.**  
  
2.  Il modello di comando personalizzato aggiunge nuovamente il `Initialize()` metodo al file TestAsyncPackage.cs per inizializzare il comando. Nel metodo Initialize (), copiare la riga che inizializza il comando. Il codice dovrebbe essere simile al seguente:  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Spostare la riga per il `InitializeAsync()` metodo nel file AsyncPackageForService.cs. Poiché si tratta di un'inizializzazione asincrona, è necessario passare al thread principale prima di inizializzare il comando usando <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Ora dovrebbe essere simile al seguente:  
  
    ```csharp  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        TestAsyncCommand.Initialize(this);    
  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync((<userpath>, "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
3.  Eliminare il `Initialize()` (metodo).  
  
4.  Nel file TestAsyncCommand.cs, trovare il `MenuItemCallback()` (metodo). Eliminare il corpo del metodo.  
  
5.  Aggiungere un'istruzione using:  
  
    ```  
    using System.IO;  
    ```  
  
6.  Aggiungere un metodo asincrono denominato `GetAsyncService()`, che ottiene il servizio e Usa i metodi:  
  
    ```csharp  
    private async System.Threading.Tasks.Task GetAsyncService()  
    {  
        ITextWriterService textService =   
           this.ServiceProvider.GetService(typeof(STextWriterService))  
              as ITextWriterService;  
        // don’t forget to change <userpath> to a local path  
        await writer.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Chiamare questo metodo dalla `MenuItemCallback()` metodo:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        GetAsyncService();  
    }  
  
    ```  
  
8.  Compilare la soluzione e avviare il debug. Quando viene visualizzata l'istanza sperimentale di Visual Studio, passare al **degli strumenti** menu e cercare il **TestAsyncCommand richiamare** voce di menu. Quando si fa clic, il TextWriterService scrive il file specificato. (Non occorre aprire una soluzione, poiché il comando richiamato anche fa sì che il pacchetto da caricare.)  
  
## <a name="see-also"></a>Vedere anche  
 [Uso e fornitura di servizi](../extensibility/using-and-providing-services.md)

