---
title: 'Procedura: Fornire un servizio asincrono di Visual Studio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9a03c4282fb7c2719f0f408759be972ead0f866
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62862940"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Procedura: Fornire un servizio asincrono di Visual Studio
Se si vuole ottenere un servizio senza bloccare il thread dell'interfaccia utente, è necessario creare un servizio asincrono e caricare il pacchetto in un thread in background. A tale scopo è possibile usare un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> anziché un <xref:Microsoft.VisualStudio.Shell.Package>, aggiungere il servizio con metodi asincroni speciale del pacchetto asincrona.

 Per informazioni su come fornire servizi di Visual Studio sincroni, vedere [come: Fornire un servizio](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementare un servizio asincrono

1. Creare un progetto VSIX (**File** > **New** > **progetto** > **Visual C#**  >  **Estendibilità** > **progetto VSIX**). Denominare il progetto **TestAsync**.

2. Aggiungere al progetto un pacchetto VSPackage. Selezionare il nodo del progetto nel **Esplora soluzioni** e fare clic su **Add** > **nuovo elemento** > **Visual c# elementi**  >  **Estendibilità** > **pacchetto Visual Studio**. Nome del file *TestAsyncPackage.cs*.

3. Nelle *TestAsyncPackage.cs*, modificare il pacchetto da cui ereditare `AsyncPackage` anziché `Package`:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Per implementare un servizio, è necessario creare tre tipi:

    - Interfaccia che identifica il servizio. Molte di queste interfacce sono vuote, vale a dire, non hanno metodi come vengono usati solo per le query del servizio.

    - Interfaccia che descrive l'interfaccia del servizio. Questa interfaccia include i metodi da implementare.

    - Una classe che implementa il servizio e l'interfaccia del servizio.

5. Nell'esempio seguente viene illustrata un'implementazione di base dei tre tipi. Il costruttore della classe del servizio deve impostare il provider del servizio. In questo esempio si aggiungerà solo il servizio al file di codice del pacchetto.

6. Aggiungere le seguenti istruzioni using al file del pacchetto:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Ecco l'implementazione del servizio asincrona. Si noti che è necessario impostare il provider del servizio asincrone anziché il provider del servizio sincrone nel costruttore:

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

            await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
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
 Per registrare un servizio, aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> al pacchetto che fornisce il servizio. Diversi per la registrazione di un servizio sincrone, è necessario assicurarsi che sia il pacchetto di servizio supporta il caricamento asincrono:

- È necessario aggiungere il **AllowsBackgroundLoading = true** campo le <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> per garantire pacchetto può essere inizializzato in modo asincrono per ulteriori informazioni sul PackageRegistrationAttribute, vedere [registrare e annullare la registrazione di pacchetti VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

- È necessario aggiungere il **IsAsyncQueryable = true** campo il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> per assicurarsi che l'istanza del servizio può essere inizializzato in modo asincrono.

  Di seguito è riportato un esempio di un `AsyncPackage` con una registrazione servizio asincrone:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Aggiungere un servizio

1. Nelle *TestAsyncPackage.cs*, rimuovere il `Initialize()` ed eseguire l'override di `InitializeAsync()` (metodo). Aggiungere il servizio e aggiungere un metodo di callback per creare i servizi. Di seguito è riportato un esempio dell'inizializzatore asincrona aggiunta di un servizio:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```

2. Aggiungere un riferimento a *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

3. Implementare il metodo di callback come un metodo asincrono che crea e restituisce il servizio.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Usare un servizio
 Ora è possibile ottenere il servizio e usarne i metodi.

1. Come sarà illustrato nell'inizializzatore, ma è possibile ottenere in qualsiasi punto di servizio che si desidera utilizzare il servizio.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await textService.WriteLineAsync(<userpath>), "this is a test");
    }

    ```

     Non dimenticare di modificare  *\<userpath >* a un nome e il percorso appropriato nel computer.

2. Compilare ed eseguire il codice. Quando viene visualizzata l'istanza sperimentale di Visual Studio, aprire una soluzione. In questo modo, il `AsyncPackage` per caricare automaticamente. Quando si è eseguito l'inizializzatore, si deve trovare un file nel percorso specificato.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Usare un servizio asincrono in un gestore comando
 Ecco un esempio di come usare un servizio asincrono in un comando di menu. È possibile usare la procedura illustrata in questo caso usare il servizio in altri metodi non asincrona.

1. Aggiungere un comando di menu al progetto. (Nelle **Esplora soluzioni**, selezionare il nodo del progetto, pulsante destro del mouse e selezionare **Add** > **nuovo elemento**  >   **Estendibilità** > **comando personalizzato**.) Denominare il file di comando *TestAsyncCommand.cs*.

2. Il modello di comando personalizzato aggiunge nuovamente il `Initialize()` metodo per il *TestAsyncPackage.cs* file per inizializzare il comando. Nel `Initialize()` (metodo), copiare la riga che inizializza il comando. Il codice dovrebbe essere simile al seguente:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Spostare la riga per il `InitializeAsync()` metodo nel *AsyncPackageForService.cs* file. Poiché si tratta di un'inizializzazione asincrona, è necessario passare al thread principale prima di inizializzare il comando usando <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Ora dovrebbe essere simile al seguente:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await textService.WriteLineAsync((<userpath>, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Eliminare il `Initialize()` (metodo).

4. Nel *TestAsyncCommand.cs* del file, trovare il `MenuItemCallback()` (metodo). Eliminare il corpo del metodo.

5. Aggiungere un'istruzione using:

    ```csharp
    using System.IO;
    ```

6. Aggiungere un metodo asincrono denominato `UseTextWriterAsync()`, che ottiene il servizio e Usa i metodi:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        // don't forget to change <userpath> to a local path
        await textService.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7. Chiamare questo metodo dalla `MenuItemCallback()` metodo:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Compilare la soluzione e avviare il debug. Quando viene visualizzata l'istanza sperimentale di Visual Studio, passare al **degli strumenti** menu e cercare il **TestAsyncCommand richiamare** voce di menu. Quando si fa clic, il TextWriterService scrive il file specificato. (Non occorre aprire una soluzione, poiché il comando richiamato anche fa sì che il pacchetto da caricare.)

## <a name="see-also"></a>Vedere anche
- [Usare e forniscono i servizi](../extensibility/using-and-providing-services.md)
