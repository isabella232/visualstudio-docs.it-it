---
title: 'Procedura: utilizzare AsyncPackage per caricare VSPackage in background. Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 77690a1947f82f97c4aa12809a80ea61335d216d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710624"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Procedura: utilizzare AsyncPackage per caricare VSPackage in backgroundHow to: Use AsyncPackage to load VSPackages in the background
Il caricamento e l'inizializzazione di un pacchetto VS possono comportare l'I/O del disco. Se tale I/O si verifica nel thread dell'interfaccia utente, può causare problemi di velocità di risposta. Per risolvere questo problema, Visual Studio <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 2015 ha introdotto la classe che consente il caricamento del pacchetto in un thread in background.

## <a name="create-an-asyncpackage"></a>Creare un AsyncPackageCreate an AsyncPackage
 È possibile iniziare creando un progetto VSIX (**Progetto** > **nuovo** > **progetto** > **Visual Cè** > Progetto**VSIX**) e aggiungendo un VSPackage al progetto (fare clic con il pulsante destro del mouse sul progetto e **aggiungere** > **nuovo elemento** > **in c'è** > **extensibility** > **Extensibility** > **Visual Studio Package**). È quindi possibile creare i servizi e aggiungerli al pacchetto.

1. Derivare il <xref:Microsoft.VisualStudio.Shell.AsyncPackage>pacchetto da .

2. Se si forniscono servizi la cui query può causare il caricamento del pacchetto:If you are providing services whose querying may cause your package to load:

    Per indicare a Visual Studio che il pacchetto è sicuro <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> per il caricamento in background e per optare per questo comportamento, è necessario impostare **AllowsBackgroundLoading** proprietà true nel costruttore dell'attributo.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Per indicare a Visual Studio che è sicuro creare un'istanza <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> del servizio <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> in un thread in background, è necessario impostare la proprietà su true nel costruttore.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Se si esegue il caricamento tramite contesti dell'interfaccia utente, <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> è necessario specificare **PackageAutoLoadFlags.BackgroundLoad** per OR il valore (0x2) nei flag scritti come valore della voce di caricamento automatico del pacchetto.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Se si dispone di operazioni di <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>inizializzazione asincrona da eseguire, è necessario eseguire l'override di . Rimuovere `Initialize()` il metodo fornito dal modello VSIX. (Il `Initialize()` metodo in **AsyncPackage** è sealed). È possibile utilizzare <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> uno qualsiasi dei metodi per aggiungere servizi asincroni al pacchetto.

    NOTA: `base.InitializeAsync()`per chiamare , è possibile modificare il codice sorgente in:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. È necessario fare attenzione a NON effettuare RPC (chiamata di procedura remota) dal codice di inizializzazione asincrona (in **InitializeAsync**). Questi possono verificarsi <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> quando si chiama direttamente o indirettamente.  Quando sono necessari caricamenti di sincronizzazione, il thread dell'interfaccia utente si bloccherà utilizzando <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Il modello di blocco predefinito disabilita le RPC. Ciò significa che se si tenta di utilizzare una chiamata RPC dalle attività asincrone, si eseguirà un deadlock se il thread dell'interfaccia utente è in attesa del caricamento del pacchetto. L'alternativa generale consiste nel eseguire il marshalling del codice nel <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> thread dell'interfaccia utente, se necessario, usando qualcosa come **Joinable Task Factory**o un altro meccanismo che non utilizza una chiamata RPC.  NON utilizzare **ThreadHelper.Generic.Invoke** o in genere bloccare il thread chiamante in attesa di arrivare al thread dell'interfaccia utente.

    NOTA: è consigliabile evitare di `InitializeAsync` utilizzare **GetService** o **QueryService** nel metodo. Se è necessario utilizzarli, è necessario passare prima al thread dell'interfaccia utente. L'alternativa consiste <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> nell'utilizzare da **AsyncPackage** (eseguendo il cast a <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)

   C:: Creare un AsyncPackage:

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

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Convertire un pacchetto VSPackage esistente in AsyncPackageConvert an existing VSPackage to AsyncPackage
 La maggior parte del lavoro è uguale alla creazione di un nuovo **AsyncPackage**. Seguire i passaggi da 1 a 5 descritti in precedenza. È inoltre necessario prestare particolare attenzione con le seguenti raccomandazioni:

1. Ricordarsi di `Initialize` rimuovere la sostituzione presente nel pacchetto.

2. Evitare deadlock: potrebbero essere presenti RPC nascoste nel codice. che ora avvengono su un thread in background. Assicurarsi che se si sta effettuando una RPC (ad esempio, **GetService**), è necessario (1) passare al thread principale o (2) utilizzare la versione asincrona dell'API, se presente (ad esempio, **GetServiceAsync**).

3. Non passare da un thread all'altro troppo frequentemente. Provare a localizzare il lavoro che può verificarsi in un thread in background per ridurre il tempo di caricamento.

## <a name="querying-services-from-asyncpackage"></a>Esecuzione di query sui servizi da AsyncPackageQuerying services from AsyncPackage
 Un **AsyncPackage** può o non può caricare in modo asincrono a seconda del chiamante. Ad esempio,

- Se il chiamante ha chiamato **GetService** o **QueryService** (entrambe le API sincrone) o

- Se il chiamante ha chiamato **IVsShell::LoadPackage** (o **IVsShell5::LoadPackageWithContext**) o

- Il caricamento viene attivato da un contesto dell'interfaccia utente, ma non è stato specificato il meccanismo di contesto dell'interfaccia utente in grado di caricare in modo asincrono

  quindi il pacchetto verrà caricato in modo sincrono.

  Il pacchetto ha ancora l'opportunità (nella fase di inizializzazione asincrona) di eseguire operazioni dal thread dell'interfaccia utente, anche se il thread dell'interfaccia utente verrà bloccato per il completamento di tale lavoro. Se il chiamante usa **IAsyncServiceProvider** per eseguire query in modo asincrono per il servizio, il caricamento e l'inizializzazione verranno eseguiti in modo asincrono presupponendo che non si blocchino immediatamente sull'oggetto attività risultante.

  In c'è: Come eseguire query sul servizio in modo asincrono:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
