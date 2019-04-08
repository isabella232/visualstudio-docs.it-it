---
title: 'Procedura: Usare AsyncPackage per caricare pacchetti VSPackage in Background | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 9
ms.author: gregvanl
ms.openlocfilehash: 7de79fbbd5221a75bec1e168c22e687ddc9c7ffa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965695"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Procedura: Usare AsyncPackage per caricare pacchetti VSPackage in background
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il caricamento e l'inizializzazione di un pacchetto di Visual Studio può comportare i/o disco. Se questo tipo i/o si verifica nel thread UI, può causare problemi di velocità di risposta. Per risolvere questo problema, Visual Studio 2015 è stato introdotto il <xref:Microsoft.VisualStudio.Shell.AsyncPackage> classe che consente il caricamento del pacchetto in un thread in background.  
  
## <a name="creating-an-asyncpackage"></a>Creazione di un AsyncPackage  
 È possibile iniziare creando un progetto VSIX (**File / nuovo / progetto / Visual C# / Extensibility / progetto VSIX**) e l'aggiunta di un pacchetto VSPackage per il progetto (fare clic con il pulsante destro sul progetto e **Aggiungi/nuovo elemento / C# elemento/estendibilità/Visual Il pacchetto di Studio**). È quindi possibile creare i servizi e aggiungere tali servizi per il pacchetto.  
  
1. Derivare il pacchetto da <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2. Se si desidera fornire servizi a cui l'esecuzione di query può causare il pacchetto da caricare:  
  
    Per indicare a Visual Studio che il pacchetto è sicuro per il caricamento in background e per applicare questo comportamento, il <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> devono impostare **AllowsBackgroundLoading** proprietà su true nel costruttore dell'attributo.  
  
   ```csharp  
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
   ```  
  
    Per indicare a Visual Studio che è possibile creare un'istanza del servizio in un thread in background, è consigliabile impostare il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> impostata su true la <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> costruttore.  
  
   ```csharp  
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
   ```  
  
3. Se si sta caricando tramite contesti dell'interfaccia utente, quindi è necessario specificare **PackageAutoLoadFlags.BackgroundLoad** per il <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> o il valore (0x2) nei flag scritto come valore della voce di auto-caricamento del pacchetto.  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
   ```  
  
4. Se si devono di operazioni di inizializzazione asincrona da eseguire, è necessario eseguire l'override <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Rimuovere il **Initialize ()** metodo fornito dal modello di progetto VSIX. (Il **Initialize ()** metodo nella **AsyncPackage** è sealed). È possibile usare uno qualsiasi del <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> metodi per aggiungere servizi asincroni per il pacchetto.  
  
    NOTA: Per chiamare **base. InitializeAsync()**, è possibile modificare il codice sorgente per:  
  
   ```csharp  
   await base.InitializeAsync(cancellationToken, progress);  
   ```  
  
5. È necessario prestare attenzione a non effettuare le chiamate RPC (rimuovere Procedure Call) dal proprio codice di inizializzazione asincrona (in **InitializeAsync**). Questi possono verificarsi quando si chiama <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> direttamente o indirettamente.  Quando carichi sync sono necessarie, il thread dell'interfaccia utente verrà bloccato tramite <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Il modello di blocco predefinita disabilita chiamate RPC. Ciò significa che se si prova a usare una chiamata RPC dalle attività asincrone, verrà generato un deadlock se il thread dell'interfaccia utente è a sua volta il pacchetto da caricare in attesa. L'alternativa generale consiste nell'effettuare il marshalling del codice per il thread dell'interfaccia utente, se necessario usando uno strumento come **Factory delle attività Joinable**del <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> o un altro meccanismo che non usa una chiamata RPC.  Non utilizzare **ThreadHelper.Generic.Invoke** o in genere blocca il thread chiamante in attesa di ottenere al thread dell'interfaccia utente.  
  
    NOTA: È consigliabile evitare di usare **GetService** oppure **QueryService** nel **InitializeAsync** (metodo). Se si dispone di usarli, è necessario passare al thread dell'interfaccia utente prima di tutto. L'alternativa consiste nell'usare <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> dalle **AsyncPackage** (eseguendo il cast a <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)  
  
   C#: Creare un AsyncPackage:  
  
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
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Convertire un pacchetto VSPackage esistente in AsyncPackage  
 La maggior parte del lavoro è analoga alla creazione di una nuova **AsyncPackage**. È necessario seguire i passaggi da 1 a 5 precedenti. È anche necessario richiedere particolare attenzione in quanto segue:  
  
1.  Ricordarsi di rimuovere il **inizializzare** override nel pacchetto.  
  
2.  Evitare i deadlock: Possono essere nascosti RPC nel codice che si verificano in un thread in background. È necessario assicurarsi che se si effettua una chiamata RPC (ad esempio **GetService**), è necessario uno (1) passare al thread principale o (2) usare la versione dell'API in presenza di una asincrona esiste (ad esempio **GetServiceAsync**).  
  
3.  Non passare tra i thread troppo frequentemente. Provare a localizzare il lavoro che può essere eseguita in un thread in background. In questo modo si riduce il tempo di caricamento.  
  
## <a name="querying-services-from-asyncpackage"></a>Esecuzione di query su servizi da AsyncPackage  
 Un' **AsyncPackage** può o potrebbe non essere caricato in modo asincrono in base al chiamante. Ad esempio,  
  
- Se viene chiamato al chiamante **GetService** oppure **QueryService** (entrambe le API sincrone) o  
  
- Se viene chiamato al chiamante **IVsShell::LoadPackage** (o **IVsShell5::LoadPackageWithContext**) o  
  
- Il carico viene attivato da un contesto dell'interfaccia utente, ma non è stato specificato che carica in modo asincrono è il meccanismo del contesto dell'interfaccia utente  
  
  quindi il pacchetto verrà caricato in modo sincrono.  
  
  Si noti che il pacchetto comunque ha la possibilità (in fase di inizializzazione asincrona) per svolgere il lavoro esterno del thread dell'interfaccia utente, anche se il thread dell'interfaccia utente verrà bloccato per il completamento del lavoro. Se il chiamante Usa **IAsyncServiceProvider** a query in modo asincrono per il servizio, quindi il caricamento e inizializzazione verrà effettuati in modo asincrono presupponendo che non bloccare immediatamente nell'oggetto attività risultante.  
  
  C#: Come eseguire una query del servizio in modo asincrono:  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
