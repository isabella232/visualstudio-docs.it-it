---
title: Usare AsyncPackage per caricare i pacchetti VSPackage in background
description: Informazioni su come usare la classe AsyncPackage che consente il caricamento dei pacchetti in un thread in background, che può impedire problemi di velocità di risposta dall'I/O del disco.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: leslierichardson95
ms.author: lerich
ms.workload:
- vssdk
ms.openlocfilehash: 32017e3755a85142876f9616f45f300e323b6752affa1773db5bcdd548b1ef1f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359897"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Procedura: Usare AsyncPackage per caricare pacchetti VSPackage in background
Il caricamento e l'inizializzazione di un pacchetto di Visual Studio possono comportare operazioni di I/O su disco. Se tale I/O si verifica nel thread dell'interfaccia utente, può causare problemi di velocità di risposta. Per risolvere questo problema, Visual Studio 2015 ha introdotto la classe che consente il caricamento <xref:Microsoft.VisualStudio.Shell.AsyncPackage> dei pacchetti in un thread in background.

## <a name="create-an-asyncpackage"></a>Creare un AsyncPackage
 Per iniziare, è possibile creare un progetto VSIX (**File** New  >    >  **Project**  >  **Visual C#**  >  **Extensibility** VSIX Project ) e aggiungere un VSPackage al progetto (fare clic con il pulsante destro del mouse sul progetto e scegliere Aggiungi nuovo elemento  >     >    >  **C#**  >  **Extensibility**  >  **Visual Studio Package**). È quindi possibile creare i servizi e aggiungerli al pacchetto.

1. Derivare il pacchetto da <xref:Microsoft.VisualStudio.Shell.AsyncPackage> .

2. Se si forniscono servizi le cui query possono causare il caricamento del pacchetto:

    Per indicare Visual Studio che il pacchetto è sicuro per il caricamento in background e per acconsentire esplicitamente a questo comportamento, è necessario impostare la proprietà <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> **AllowsBackgroundLoading** su true nel costruttore dell'attributo.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Per indicare Visual Studio che è sicuro creare un'istanza del servizio in un thread in background, è necessario impostare la proprietà <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> su true nel <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> costruttore.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Se si sta caricando tramite contesti dell'interfaccia utente, è necessario specificare **PackageAutoLoadFlags.BackgroundLoad** per OR il valore (0x2) nei flag scritti come valore della voce di caricamento automatico del <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> pacchetto.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Se è necessario eseguire operazioni di inizializzazione asincrona, è necessario eseguire l'override di <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> . Rimuovere il `Initialize()` metodo fornito dal modello VSIX. Il `Initialize()` metodo in **AsyncPackage è** sealed. È possibile usare uno qualsiasi dei <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> metodi per aggiungere servizi asincroni al pacchetto.

    NOTA: per chiamare `base.InitializeAsync()` , è possibile modificare il codice sorgente in:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. È necessario fare attenzione a NON eseguire RPC (Remote Procedure Call) dal codice di inizializzazione asincrona (in **InitializeAsync).** Possono verificarsi quando si chiama <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> direttamente o indirettamente.  Quando sono necessari caricamenti di sincronizzazione, il thread dell'interfaccia utente si blocca usando <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . Il modello di blocco predefinito disabilita le RPC. Ciò significa che se si tenta di usare una rpc dalle attività asincrone, si verifica un deadlock se il thread dell'interfaccia utente è in attesa del caricamento del pacchetto. L'alternativa generale consiste nel effettuare il marshalling del codice al thread dell'interfaccia utente, se necessario, usando un meccanismo come **joinable Task Factory** o un altro meccanismo che non <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> usa una RPC.  NON usare **ThreadHelper.Generic.Invoke o** in genere bloccare il thread chiamante in attesa di ottenere il thread dell'interfaccia utente.

    NOTA: è consigliabile evitare di **usare GetService** **o QueryService** nel `InitializeAsync` metodo . Se è necessario usarli, è necessario passare prima al thread dell'interfaccia utente. L'alternativa consiste <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> nell'usare da **AsyncPackage** (eseguendo il cast a <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> ).

   C#: creare un AsyncPackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]
public sealed class TestPackage : AsyncPackage
{
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(SMyTestService), CreateService, true);
        return Task.FromResult<object>(null);
    }
}
```

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Convertire un VSPackage esistente in AsyncPackage
 La maggior parte del lavoro è identica alla creazione di un nuovo **oggetto AsyncPackage.** Seguire i passaggi da 1 a 5 precedenti. È anche necessario prestare particolare attenzione con le raccomandazioni seguenti:

1. Ricordarsi di rimuovere `Initialize` la sostituzione presente nel pacchetto.

2. Evitare deadlock: potrebbero essere presenti RPC nascoste nel codice. che ora si verificano in un thread in background. Assicurarsi che se si sta effettuando una chiamata RPC (ad esempio, **GetService**), è necessario (1) passare al thread principale o (2) usare la versione asincrona dell'API, se presente (ad esempio, **GetServiceAsync).**

3. Non passare troppo spesso da un thread all'altro. Provare a localizzare il lavoro che può verificarsi in un thread in background per ridurre il tempo di caricamento.

## <a name="querying-services-from-asyncpackage"></a>Esecuzione di query su servizi da AsyncPackage
 Un **AsyncPackage può** essere caricato o meno in modo asincrono a seconda del chiamante. Ad esempio,

- Se il **chiamante ha chiamato GetService** o **QueryService** (entrambe LE API sincrone) o

- Se il chiamante **ha chiamato IVsShell::LoadPackage** (o **IVsShell5::LoadPackageWithContext**) o

- Il caricamento viene attivato da un contesto dell'interfaccia utente, ma non è stato specificato il meccanismo del contesto dell'interfaccia utente che può essere caricato in modo asincrono

  il pacchetto verrà caricato in modo sincrono.

  Il pacchetto ha ancora la possibilità (nella fase di inizializzazione asincrona) di eseguire operazioni fuori dal thread dell'interfaccia utente, anche se il thread dell'interfaccia utente verrà bloccato per il completamento di tale operazione. Se il chiamante usa **IAsyncServiceProvider** per eseguire query in modo asincrono per il servizio, il caricamento e l'inizializzazione verranno evasi in modo asincrono presupponendo che non si blocchino immediatamente nell'oggetto attività risultante.

  C#: Come eseguire query sul servizio in modo asincrono:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
