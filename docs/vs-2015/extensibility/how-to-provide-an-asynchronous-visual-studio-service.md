---
title: 'Procedura: fornire un servizio asincrono | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c58b0be10bf10a21b783a48d52806bf769381ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204107"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Procedura: Fornire un servizio asincrono di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si desidera ottenere un servizio senza bloccare il thread dell'interfaccia utente, è necessario creare un servizio asincrono e caricare il pacchetto in un thread in background. A questo scopo è possibile usare un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> anziché un <xref:Microsoft.VisualStudio.Shell.Package> e aggiungere il servizio con i metodi asincroni speciali del pacchetto asincrono

 Per informazioni su come fornire servizi sincroni di Visual Studio, vedere [procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md).

## <a name="implementing-an-asynchronous-service"></a>Implementazione di un servizio asincrono

1. Creare un progetto VSIX (**file/nuovo/progetto/Visual C#/estendibilità/progetto VSIX**). Denominare il progetto **TestAsync**.

2. Aggiungere un pacchetto VSPackage al progetto. Selezionare il nodo del progetto nella **Esplora soluzioni** e fare clic su **Aggiungi/nuovo elemento/Visual C# Items/Extensibility/pacchetto di Visual Studio**. Assegnare al file il nome **TestAsyncPackage.cs**.

3. In TestAsyncPackage.cs modificare il pacchetto in modo da ereditare da AsyncPackage anziché da Package:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Per implementare un servizio, è necessario creare tre tipi:

    - Interfaccia che descrive il servizio. Molte di queste interfacce sono vuote, ovvero non hanno metodi.

    - Interfaccia che descrive l'interfaccia del servizio. Questa interfaccia include i metodi da implementare.

    - Classe che implementa sia il servizio che l'interfaccia del servizio.

5. Nell'esempio seguente viene illustrata un'implementazione molto semplice dei tre tipi. Il costruttore della classe del servizio deve impostare il provider di servizi. In questo esempio si aggiungerà semplicemente il servizio al file di codice del pacchetto.

6. Aggiungere le istruzioni using seguenti al file del pacchetto:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7. Di seguito è illustrata l'implementazione asincrona del servizio. Si noti che è necessario impostare il provider di servizi asincroni anziché il provider di servizi sincroni nel costruttore:

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

## <a name="registering-a-service"></a>Registrazione di un servizio
 Per registrare un servizio, aggiungere al <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> pacchetto che fornisce il servizio. La registrazione di un servizio sincrono presenta due differenze:

- Se si sta caricando il pacchetto, è necessario aggiungere il <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> valore BackgroundLoad all'attributo. Per altre informazioni sul caricamento automatici dei pacchetti VSPackage, vedere [caricamento dei pacchetti VSPackage](../extensibility/loading-vspackages.md).

- È necessario aggiungere il campo **AllowsBackgroundLoading = true** a <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> . Per altre informazioni su PackageRegistrationAttribute, vedere [registrazione e annullamento della registrazione di pacchetti VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

  Di seguito è riportato un esempio di AsyncPackage con una registrazione asincrona del servizio:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="adding-a-service"></a>Aggiunta di un servizio

1. In TestAsyncPackage.cs rimuovere il `Initialize()` Metodo ed eseguire l'override del `InitializeAsync()` metodo. Aggiungere il servizio e aggiungere un metodo di callback per creare i servizi. Di seguito è riportato un esempio dell'inizializzatore asincrono che aggiunge un servizio:

    ```
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

2. Aggiungere un riferimento a Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.

3. Implementare il metodo di callback come metodo asincrono che crea e restituisce il servizio.

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

## <a name="using-a-service"></a>Uso di un servizio
 A questo punto è possibile ottenere il servizio e utilizzarne i metodi.

1. Questo verrà visualizzato nell'inizializzatore, ma è possibile ottenere il servizio in qualsiasi punto in cui si vuole usare il servizio.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     Non dimenticare di passare *\<userpath>* a un nome file e un percorso sensato nel computer.

2. Compilare ed eseguire il codice. Quando viene visualizzata l'istanza sperimentale di Visual Studio, aprire una soluzione. In questo modo, il AsyncPackage viene caricato automaticamente. Quando l'inizializzatore è in esecuzione, dovrebbe essere presente un file nel percorso specificato.

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Uso di un servizio asincrono in un gestore di comandi
 Di seguito è riportato un esempio di come usare un servizio asincrono in un comando di menu. È possibile utilizzare la procedura illustrata di seguito per utilizzare il servizio in altri metodi non asincroni.

1. Aggiungere un comando di menu al progetto. Nella **Esplora soluzioni**selezionare il nodo del progetto, fare clic con il pulsante destro del mouse e scegliere **Aggiungi/nuovo elemento/estendibilità/comando personalizzato**. Denominare il file di comando **TestAsyncCommand.cs.**

2. Il modello di comando personalizzato aggiunge nuovamente il `Initialize()` metodo al file TestAsyncPackage.cs per inizializzare il comando. Nel metodo Initialize () copiare la riga che inizializza il comando. Avrà un aspetto simile al seguente:

    ```
    TestAsyncCommand.Initialize(this);
    ```

     Spostare questa riga `InitializeAsync()` nel metodo del file AsyncPackageForService.cs. Poiché si tratta di un'inizializzazione asincrona, è necessario passare al thread principale prima di inizializzare il comando utilizzando <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . L'aspetto dovrebbe risultare simile al seguente:

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

3. Eliminare il `Initialize()` metodo.

4. Nel file TestAsyncCommand.cs trovare il `MenuItemCallback()` metodo. Eliminare il corpo del metodo.

5. Aggiungere un'istruzione using:

    ```
    using System.IO;
    ```

6. Aggiungere un metodo asincrono denominato `GetAsyncService()` , che ottiene il servizio e utilizza i relativi metodi:

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

7. Chiamare questo metodo dal `MenuItemCallback()` Metodo:

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8. Compilare la soluzione e avviare il debug. Quando viene visualizzata l'istanza sperimentale di Visual Studio, andare al menu **strumenti** e cercare la voce di menu **richiama TestAsyncCommand** . Quando si fa clic su di esso, il TextWriterService scrive nel file specificato. Non è necessario aprire una soluzione, perché richiamare il comando causa anche il caricamento del pacchetto.

## <a name="see-also"></a>Vedere anche
 [Uso e offerta di servizi](../extensibility/using-and-providing-services.md)
