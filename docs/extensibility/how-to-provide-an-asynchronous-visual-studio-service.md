---
title: 'Procedura: Fornire un servizio Visual Studio asincrono | Microsoft Docs'
description: Informazioni su come fornire un servizio Visual Studio asincrono. Questo approccio consente di ottenere un servizio senza bloccare il thread dell'interfaccia utente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 41777f9b04060928799c621de8262d50d027014aaa4a2831ad0a6656bfa0b9c1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401713"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Procedura: Fornire un servizio Visual Studio asincrono
Se si vuole ottenere un servizio senza bloccare il thread dell'interfaccia utente, è necessario creare un servizio asincrono e caricare il pacchetto in un thread in background. A questo scopo è possibile usare un anziché un e aggiungere il servizio con i metodi asincroni speciali <xref:Microsoft.VisualStudio.Shell.AsyncPackage> <xref:Microsoft.VisualStudio.Shell.Package> del pacchetto asincrono.

 Per informazioni su come fornire servizi Visual Studio sincroni, vedere [Procedura: Fornire un servizio](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementare un servizio asincrono

1. Creare un progetto VSIX (**File**  >  **New**  >  **Project**  >  **Visual C#**  >  **Extensiblity**  >  **VSIX Project**). Assegnare al progetto il **nome TestAsync**.

2. Aggiungere un VSPackage al progetto. Selezionare il nodo del progetto nel **Esplora soluzioni** e fare clic **su** Aggiungi nuovo elemento  >    >  **Visual C# Items**  >  **Extensibility**  >  **Visual Studio Package**. Assegnare a questo file *il nome TestAsyncPackage.cs*.

3. In *TestAsyncPackage.cs* modificare il pacchetto in modo che erediti da `AsyncPackage` anziché da `Package` :

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Per implementare un servizio, è necessario creare tre tipi:

    - Interfaccia che identifica il servizio. Molte di queste interfacce sono vuote, cio' non hanno metodi perché vengono usate solo per l'esecuzione di query sul servizio.

    - Interfaccia che descrive l'interfaccia del servizio. Questa interfaccia include i metodi da implementazione.

    - Classe che implementa sia il servizio che l'interfaccia del servizio.

5. L'esempio seguente illustra un'implementazione molto semplice dei tre tipi. Il costruttore della classe del servizio deve impostare il provider di servizi. In questo esempio si aggiungerà semplicemente il servizio al file di codice del pacchetto.

6. Aggiungere le direttive using seguenti al file di pacchetto:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Ecco l'implementazione asincrona del servizio. Si noti che è necessario impostare il provider di servizi asincroni anziché il provider di servizi sincrono nel costruttore :

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
 Per registrare un servizio, aggiungere <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> al pacchetto che fornisce il servizio. Diversamente dalla registrazione di un servizio sincrono, è necessario assicurarsi che sia il pacchetto che il servizio supportino il caricamento asincrono:

- È necessario aggiungere il campo **AllowsBackgroundLoading = true** a per assicurarsi che il pacchetto possa essere inizializzato in modo asincrono Per altre informazioni su PackageRegistrationAttribute, vedere Registrare e annullare la registrazione di <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> [VSPackage.](../extensibility/registering-and-unregistering-vspackages.md)

- È necessario aggiungere il **campo IsAsyncQueryable = true** a per assicurarsi che l'istanza del servizio possa essere <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> inizializzata in modo asincrono.

  Di seguito è riportato un esempio di `AsyncPackage` con una registrazione asincrona del servizio:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Aggiungere un servizio

1. In *TestAsyncPackage.cs* rimuovere il `Initialize()` metodo ed eseguire l'override del metodo `InitializeAsync()` . Aggiungere il servizio e aggiungere un metodo di callback per creare i servizi. Di seguito è riportato un esempio dell'inizializzatore asincrono che aggiunge un servizio:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Per rendere visibile questo servizio all'esterno di questo pacchetto, impostare il valore del flag di innalzamento di livello su *true* come ultimo parametro:  `this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Aggiungere un riferimento a *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

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
 È ora possibile ottenere il servizio e usare i relativi metodi.

1. Questo verrà illustrato nell'inizializzatore, ma è possibile ottenere il servizio ovunque si vuole usare il servizio.

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

     Non dimenticare di passare a un nome file e a un percorso che `userpath` ha senso nel computer.

2. Compilare ed eseguire il codice. Quando viene visualizzata l'istanza sperimentale Visual Studio, aprire una soluzione. In questo modo, `AsyncPackage` l'oggetto viene ricaricato automaticamente. Al termine dell'esecuzione dell'inizializzatore, è necessario trovare un file nel percorso specificato.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Usare un servizio asincrono in un gestore comandi
 Ecco un esempio di come usare un servizio asincrono in un comando di menu. È possibile usare la procedura illustrata di seguito per usare il servizio in altri metodi non asincroni.

1. Aggiungere un comando di menu al progetto. Nell'elenco **Esplora soluzioni** selezionare il nodo del progetto, fare clic con il pulsante destro del mouse e scegliere **Aggiungi**  >  **Nuovo elemento**  >  **Estendibilità**  >  **Comando personalizzato**. Assegnare al file di *comando il nome TestAsyncCommand.cs*.

2. Il modello di comando personalizzato aggiunge nuovamente il `Initialize()` metodo al file *TestAsyncPackage.cs* per inizializzare il comando. Nel metodo `Initialize()` copiare la riga che inizializza il comando. Avrà un aspetto simile al seguente:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Sposta al metodo `InitializeAsync()` nel file *AsyncPackageForService.cs.* Poiché si tratta di un'inizializzazione asincrona, è necessario passare al thread principale prima di inizializzare il comando usando <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . L'aspetto dovrebbe risultare simile al seguente:

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

3. Eliminare il `Initialize()` metodo .

4. Nel file *TestAsyncCommand.cs* trovare il `MenuItemCallback()` metodo . Eliminare il corpo del metodo.

5. Aggiungere una direttiva using:

    ```csharp
    using System.IO;
    ```

6. Aggiungere un metodo asincrono denominato `UseTextWriterAsync()` , che ottiene il servizio e usa i relativi metodi:

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

7. Chiamare questo metodo dal `MenuItemCallback()` metodo :

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Compilare la soluzione e avviare il debug. Quando viene visualizzata l'istanza sperimentale di Visual Studio, passare al **menu** Strumenti e cercare la voce di menu **Richiama TestAsyncCommand.** Quando si fa clic su di esso, TextWriterService scrive nel file specificato. Non è necessario aprire una soluzione, perché richiamando il comando viene caricato anche il pacchetto.

## <a name="see-also"></a>Vedi anche
- [Usare e fornire servizi](../extensibility/using-and-providing-services.md)
