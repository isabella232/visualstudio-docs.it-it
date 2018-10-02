---
title: 'Procedura: fornire un servizio | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18cb5c28ab70b652b860d76fc6b7ad92e7262bf5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540823"
---
# <a name="how-to-provide-a-service"></a>Procedura: fornire un servizio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: fornire un servizio](https://docs.microsoft.com/visualstudio/extensibility/how-to-provide-a-service).  
  
Un pacchetto VSPackage può fornire servizi che è possibile usare altri pacchetti VSPackage. Per fornire un servizio, un pacchetto VSPackage deve registrare il servizio con Visual Studio e aggiungere il servizio.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Package> classe implementa entrambe <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> e <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> contiene i metodi di callback che forniscono servizi su richiesta.  
  
 Per altre informazioni sui servizi, vedere [nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Quando un pacchetto VSPackage sta per essere scaricati, Visual Studio attende fino a quando non sono state recapitate tutte le richieste per i servizi che offre un pacchetto VSPackage. Non consente nuove richieste per tali servizi. Non è necessario chiamare in modo esplicito il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodo revocare un servizio quando lo scaricamento.  
  
#### <a name="implementing-a-service"></a>Implementazione di un servizio  
  
1.  Creare un progetto VSIX (**File / nuovo / progetto / Visual c# / estendibilità / progetto VSIX**).  
  
2.  Aggiungere al progetto un pacchetto VSPackage. Selezionare il nodo del progetto nel **Esplora soluzioni** e fare clic su **Aggiungi / nuovo elemento / elementi di Visual c# / Extensibility / pacchetto di Visual Studio**.  
  
3.  Per implementare un servizio, è necessario creare tre tipi:  
  
    -   Interfaccia che descrive il servizio. Molte di queste interfacce sono vuote, vale a dire, non hanno nessun metodo.  
  
    -   Interfaccia che descrive l'interfaccia del servizio. Questa interfaccia include i metodi da implementare.  
  
    -   Una classe che implementa il servizio e l'interfaccia del servizio.  
  
     Nell'esempio seguente viene illustrata un'implementazione di base dei tre tipi. Il costruttore della classe del servizio deve impostare il provider del servizio.  
  
    ```csharp  
    public class MyService : SMyService, IMyService  
    {  
        private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
        private string myString;  
        public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
        {  
            Trace.WriteLine(  
                   "Constructing a new instance of MyService");  
            serviceProvider = sp;  
        }  
        public void Hello()  
        {  
            myString = "hello";  
        }  
        public string Goodbye()  
        {  
           return "goodbye";  
        }  
    }  
    public interface SMyService  
    {  
    }  
    public interface IMyService  
    {  
        void Hello();  
        string Goodbye();  
    }  
  
    ```  
  
### <a name="registering-a-service"></a>La registrazione di un servizio  
  
1.  Per registrare un servizio, aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> al pacchetto VSPackage che fornisce il servizio. Ecco un esempio:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Questo attributo registra `SMyService` con Visual Studio.  
  
    > [!NOTE]
    >  Per registrare un servizio che sostituisce un altro servizio con lo stesso nome, usare il <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Si noti che un solo eseguono l'override di un servizio è consentito.  
  
### <a name="adding-a-service"></a>Aggiunta di un servizio  
  
1.  1.  Nell'inizializzatore di VSPackage, aggiungere il servizio e aggiungere un metodo di callback per creare i servizi. Ecco la modifica da apportare al <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implementare il metodo di callback, che deve creare e restituire il servizio oppure null se non può essere creata.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio è possibile rifiutare una richiesta per fornire un servizio. Esegue l'operazione se un altro VSPackage fornisce già il servizio.  
  
3.  Ora è possibile ottenere il servizio e usarne i metodi. Come sarà illustrato nell'inizializzatore, ma è possibile ottenere in qualsiasi punto di servizio che si desidera utilizzare il servizio.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     Il valore di `helloString` deve essere "Hello".  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md)   
 [Uso e fornitura di servizi](../extensibility/using-and-providing-services.md)   
 [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)

