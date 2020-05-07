---
title: 'Procedura: fornire un servizio di Visual Studio asincrono | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65362e465beec5465903083beca069104a48166b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710761"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Procedura: fornire un servizio di Visual Studio asincrono
Se si desidera ottenere un servizio senza bloccare il thread dell'interfaccia utente, è necessario creare un servizio asincrono e caricare il pacchetto in un thread in background. A questo scopo, è possibile usare <xref:Microsoft.VisualStudio.Shell.AsyncPackage> un anziché un <xref:Microsoft.VisualStudio.Shell.Package>e aggiungere il servizio con i metodi asincroni speciali del pacchetto asincrono.

 Per informazioni su come fornire servizi sincroni di Visual Studio, vedere [procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementare un servizio asincrono

1. Creare un progetto VSIX (**file** > **nuovo** > **Project** > progetto**Visual C#** > **estendibilità** > **VSIX**). Denominare il progetto **TestAsync**.

2. Aggiungere un pacchetto VSPackage al progetto. Selezionare il nodo del progetto nella **Esplora soluzioni** e fare clic su **Aggiungi** > **nuovo elemento** > **Visual C# elementi** > **estensibilità** > **pacchetto di Visual Studio**. Assegnare al file il nome *TestAsyncPackage.cs*.

3. In *TestAsyncPackage.cs*modificare il pacchetto in modo da ereditare `AsyncPackage` da `Package`anziché:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Per implementare un servizio, è necessario creare tre tipi:

    - Interfaccia che identifica il servizio. Molte di queste interfacce sono vuote, ovvero non hanno metodi perché vengono usate solo per eseguire query sul servizio.

    - Interfaccia che descrive l'interfaccia del servizio. Questa interfaccia include i metodi da implementare.

    - Classe che implementa sia il servizio che l'interfaccia del servizio.

5. Nell'esempio seguente viene illustrata un'implementazione molto semplice dei tre tipi. Il costruttore della classe del servizio deve impostare il provider di servizi. In questo esempio si aggiungerà semplicemente il servizio al file di codice del pacchetto.

6. Aggiungere le seguenti direttive using al file del pacchetto:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Di seguito è illustrata l'implementazione asincrona del servizio. Si noti che è necessario impostare il provider di servizi asincroni anziché il provider di servizi sincroni nel costruttore:

    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private IAsyncServiceProvider asyncServiceProvider;

        public TextWriterService(IAsyncServiceProvider provider)
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;
        }

        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }

        public async Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
    }

    public interface STextWriterService
    {
    }

    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
    }
    ```

## <a name="register-a-service"></a>Registrare un servizio
 Per registrare un servizio, aggiungere <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> al pacchetto che fornisce il servizio. Diversamente dalla registrazione di un servizio sincrono, è necessario assicurarsi che il pacchetto e il servizio supportino il caricamento asincrono:

- È necessario aggiungere il campo **AllowsBackgroundLoading = true** a <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> per verificare che il pacchetto possa essere inizializzato in modo asincrono per ulteriori informazioni su PackageRegistrationAttribute, vedere [registrare e annullare la registrazione di pacchetti VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

- È necessario aggiungere il campo **IsAsyncQueryable = true** a per <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> assicurarsi che l'istanza del servizio possa essere inizializzata in modo asincrono.

  Di seguito è riportato un esempio `AsyncPackage` di con una registrazione asincrona del servizio:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Aggiungere un servizio

1. In *TestAsyncPackage.cs*rimuovere il `Initialize()` metodo ed eseguire l'override `InitializeAsync()` del metodo. Aggiungere il servizio e aggiungere un metodo di callback per creare i servizi. Di seguito è riportato un esempio dell'inizializzatore asincrono che aggiunge un servizio:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Per rendere il servizio visibile all'esterno del pacchetto, impostare il valore di innalzamento di livello su *true* come ultimo parametro:`this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Aggiungere un riferimento a *Microsoft. VisualStudio. Shell. Interop. 14.0. DesignTime. dll*.

3. Implementare il metodo di callback come metodo asincrono che crea e restituisce il servizio.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Usare un servizio
 A questo punto è possibile ottenere il servizio e utilizzarne i metodi.

1. Questo verrà visualizzato nell'inizializzatore, ma è possibile ottenere il servizio in qualsiasi punto in cui si vuole usare il servizio.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     Non dimenticare di passare `userpath` a un nome file e un percorso sensato nel computer.

2. Compilare ed eseguire il codice. Quando viene visualizzata l'istanza sperimentale di Visual Studio, aprire una soluzione. In questo modo `AsyncPackage` l'oggetto viene caricato automaticamente. Quando l'inizializzatore è in esecuzione, dovrebbe essere presente un file nel percorso specificato.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Usare un servizio asincrono in un gestore di comandi
 Di seguito è riportato un esempio di come usare un servizio asincrono in un comando di menu. È possibile utilizzare la procedura illustrata di seguito per utilizzare il servizio in altri metodi non asincroni.

1. Aggiungere un comando di menu al progetto. Nella **Esplora soluzioni**selezionare il nodo del progetto, fare clic con il pulsante destro del mouse e scegliere **Aggiungi** > **nuovo elemento** > **estendibile** > **comando personalizzato**. Denominare il file di comando *TestAsyncCommand.cs*.

2. Il modello di comando personalizzato aggiunge nuovamente il `Initialize()` metodo al file *TestAsyncPackage.cs* per inizializzare il comando. Nel `Initialize()` metodo copiare la riga che inizializza il comando. L'aspetto dovrebbe risultare simile al seguente:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Spostare questa riga nel `InitializeAsync()` metodo del file *AsyncPackageForService.cs* . Poiché si tratta di un'inizializzazione asincrona, è necessario passare al thread principale prima di inizializzare il comando <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>utilizzando. L'aspetto dovrebbe risultare simile al seguente:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Eliminare il `Initialize()` metodo.

4. Nel file *TestAsyncCommand.cs* trovare il `MenuItemCallback()` metodo. Eliminare il corpo del metodo.

5. Aggiungere una direttiva using:

    ```csharp
    using System.IO;
    ```

6. Aggiungere un metodo asincrono denominato `UseTextWriterAsync()`, che ottiene il servizio e utilizza i relativi metodi:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. Chiamare questo metodo dal `MenuItemCallback()` metodo:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Compilare la soluzione e avviare il debug. Quando viene visualizzata l'istanza sperimentale di Visual Studio, andare al menu **strumenti** e cercare la voce di menu **richiama TestAsyncCommand** . Quando si fa clic su di esso, il TextWriterService scrive nel file specificato. Non è necessario aprire una soluzione, perché richiamare il comando causa anche il caricamento del pacchetto.

## <a name="see-also"></a>Vedere anche
- [Usare e fornire servizi](../extensibility/using-and-providing-services.md)
