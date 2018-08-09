---
title: 'Procedura: fornire un servizio | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cbad09a19aeaf297505de215566b14df067c760a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639588"
---
# <a name="how-to-provide-a-service"></a>Procedura: fornire un servizio
Un pacchetto VSPackage può fornire servizi che è possibile usare altri pacchetti VSPackage. Per fornire un servizio, un pacchetto VSPackage deve registrare il servizio con Visual Studio e aggiungere il servizio.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Package> classe implementa entrambe <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> e <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> contiene i metodi di callback che forniscono servizi su richiesta.  
  
 Per altre informazioni sui servizi, vedere [Service essentials](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Quando un pacchetto VSPackage sta per essere scaricati, Visual Studio attende fino a quando non sono state recapitate tutte le richieste per i servizi che offre un pacchetto VSPackage. Non consente nuove richieste per tali servizi. Non è necessario chiamare in modo esplicito il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodo revocare un servizio quando lo scaricamento.  
  
## <a name="implement-a-service"></a>Implementare un servizio  
  
1.  Creare un progetto VSIX (**File** > **New** > **progetto** > **Visual C#**  >  **Estendibilità** > **progetto VSIX**).  
  
2.  Aggiungere al progetto un pacchetto VSPackage. Selezionare il nodo del progetto nel **Esplora soluzioni** e fare clic su **Add** > **nuovo elemento** > **Visual c# elementi**  >  **Estendibilità** > **pacchetto Visual Studio**.  
  
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
  
### <a name="register-a-service"></a>Registrare un servizio  
  
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
  
### <a name="add-a-service"></a>Aggiungere un servizio  
  
1.  Nell'inizializzatore di VSPackage, aggiungere il servizio e aggiungere un metodo di callback per creare i servizi. Ecco la modifica da apportare al <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implementare il metodo di callback, che deve creare e restituire il servizio oppure null se non può essere creata.  
  
    ```csharp  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new MyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio è possibile rifiutare una richiesta per fornire un servizio. Esegue l'operazione se un altro VSPackage fornisce già il servizio.  
  
3.  Ora è possibile ottenere il servizio e usarne i metodi. L'esempio seguente viene illustrato l'utilizzo del servizio nell'inizializzatore, ma è possibile ottenere in qualsiasi punto di servizio che si desidera utilizzare il servizio.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.Goodbye();  
  
        base.Initialize();  
    }  
    ```  
  
     Il valore di `helloString` deve essere "Hello".  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md)   
 [Usare e forniscono i servizi](../extensibility/using-and-providing-services.md)   
 [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)
