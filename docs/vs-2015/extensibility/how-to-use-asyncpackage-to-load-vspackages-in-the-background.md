---
title: 'Procedura: usare AsyncPackage per caricare i pacchetti VSPackage in background | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 9
ms.author: gregvanl
ms.openlocfilehash: f59838913ed3f9bc6679336393f6db9181291e3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204030"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Procedura: Usare AsyncPackage per caricare pacchetti VSPackage in background
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il caricamento e l'inizializzazione di un pacchetto Visual Studio possono comportare l'I/O del disco. Se si verificano operazioni di I/O sul thread dell'interfaccia utente, possono verificarsi problemi di velocità di risposta. Per risolvere questo problema, in Visual Studio 2015 è stata introdotta la  <xref:Microsoft.VisualStudio.Shell.AsyncPackage> classe che consente il caricamento dei pacchetti in un thread in background.  
  
## <a name="creating-an-asyncpackage"></a>Creazione di un AsyncPackage  
 È possibile iniziare creando un progetto VSIX (**file/nuovo/progetto/Visual C#/extensibility/progetto VSIX**) e aggiungendo un pacchetto VSPackage al progetto (fare clic con il pulsante destro del mouse sul progetto e **aggiungere/nuovo elemento/elemento C#/estendibilità/pacchetto di Visual Studio**). È quindi possibile creare i servizi e aggiungere tali servizi al pacchetto.  
  
1. Derivare il pacchetto da <xref:Microsoft.VisualStudio.Shell.AsyncPackage> .  
  
2. Se si forniscono servizi le cui query possono causare il caricamento del pacchetto:  
  
    Per indicare a Visual Studio che il pacchetto è sicuro per il caricamento in background e per acconsentire esplicitamente a questo comportamento, è <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> necessario impostare la proprietà **AllowsBackgroundLoading** su true nel costruttore dell'attributo.  
  
   ```csharp  
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
   ```  
  
    Per indicare a Visual Studio che è sicuro creare un'istanza del servizio in un thread in background, è necessario impostare la <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> proprietà su true nel <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> costruttore.  
  
   ```csharp  
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
   ```  
  
3. Se si esegue il caricamento tramite contesti dell'interfaccia utente, è necessario specificare **PackageAutoLoadFlags. BackgroundLoad** per <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> o il valore (0x2) nei flag scritti come valore della voce di caricamento automatico del pacchetto.  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
   ```  
  
4. Se è necessario eseguire operazioni di inizializzazione asincrona, è necessario eseguire l'override di <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> . Rimuovere il metodo **Initialize ()** fornito dal modello VSIX. (Il metodo **Initialize ()** in **AsyncPackage** è sealed). È possibile utilizzare uno dei <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> metodi per aggiungere servizi asincroni al pacchetto.  
  
    Nota: per chiamare **base.InitializeAsync ()**, è possibile modificare il codice sorgente in:  
  
   ```csharp  
   await base.InitializeAsync(cancellationToken, progress);  
   ```  
  
5. È necessario prestare attenzione a non eseguire RPC (Remove procedure call) dal codice di inizializzazione asincrona (in **InitializeAsync**). Questi possono verificarsi quando si chiama <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> direttamente o indirettamente.  Quando sono necessari carichi di sincronizzazione, il thread dell'interfaccia utente si bloccherà usando <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . Il modello di blocco predefinito Disabilita le chiamate RPC. Ciò significa che se si tenta di utilizzare una RPC dalle attività asincrone, si verifica un deadlock se il thread dell'interfaccia utente è in attesa del caricamento del pacchetto. L'alternativa generale consiste nel effettuare il marshalling del codice al thread dell'interfaccia utente, se necessario, usando una **Factory delle attività di joinable** <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> o un altro meccanismo che non usa una chiamata RPC.  Non usare **ThreadHelper. Generic. Invoke** o bloccare in genere il thread chiamante in attesa di raggiungere il thread dell'interfaccia utente.  
  
    Nota: è consigliabile evitare di usare **GetService** o **QueryService** nel metodo **InitializeAsync** . Se è necessario usarli, sarà necessario passare prima al thread dell'interfaccia utente. L'alternativa consiste nell'usare <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> da **AsyncPackage** (eseguendo il cast a <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> .)  
  
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
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Converte un VSPackage esistente in AsyncPackage  
 La maggior parte del lavoro è la stessa della creazione di un nuovo **AsyncPackage**. È necessario seguire i passaggi da 1 a 5 precedenti. È anche necessario prestare particolare attenzione agli elementi seguenti:  
  
1. Ricordarsi di rimuovere l'override di **inizializzazione** presente nel pacchetto.  
  
2. Evitare i deadlock: nel codice potrebbero essere presenti RPC nascoste che ora si verificano in un thread in background. È necessario assicurarsi che se si esegue una chiamata RPC (ad esempio, **GetService**), è necessario (1) passare al thread principale o (2) usare la versione asincrona dell'API se ne esiste una (ad esempio, **GetServiceAsync**).  
  
3. Non spostarsi troppo spesso tra i thread. Provare a localizzare il lavoro che può verificarsi in un thread in background. In questo modo si riduce il tempo di caricamento.  
  
## <a name="querying-services-from-asyncpackage"></a>Esecuzione di query sui servizi da AsyncPackage  
 Un **AsyncPackage** può o non può essere caricato in modo asincrono a seconda del chiamante. Ad esempio,  
  
- Se il chiamante ha chiamato **GetService** o **QueryService** (entrambe API sincrone) o  
  
- Se il chiamante ha chiamato **IVsShell:: LoadPackage** (o **IVsShell5:: LoadPackageWithContext**) o  
  
- Il carico viene attivato da un contesto dell'interfaccia utente, ma non è stato specificato il meccanismo del contesto dell'interfaccia utente che può essere caricato in modo asincrono  
  
  il pacchetto verrà quindi caricato in modo sincrono.  
  
  Si noti che il pacchetto ha ancora un'opportunità (nella fase di inizializzazione asincrona) per eseguire il lavoro sul thread dell'interfaccia utente, anche se il thread dell'interfaccia utente verrà bloccato per il completamento di tale operazione. Se il chiamante usa **IAsyncServiceProvider** per eseguire query in modo asincrono per il servizio, il caricamento e l'inizializzazione verranno eseguiti in modo asincrono presumendo che non si blocchino immediatamente sull'oggetto attività risultante.  
  
  C#: come eseguire una query del servizio in modo asincrono:  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
