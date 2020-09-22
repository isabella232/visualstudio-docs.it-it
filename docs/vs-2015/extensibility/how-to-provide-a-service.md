---
title: 'Procedura: fornire un servizio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 565a8a91797c826b6419dc5a8488d7d3baf9cddc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839648"
---
# <a name="how-to-provide-a-service"></a>Procedura: Fornire un servizio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un pacchetto VSPackage può fornire servizi che altri pacchetti VSPackage possono usare. Per fornire un servizio, un pacchetto VSPackage deve registrare il servizio con Visual Studio e aggiungere il servizio.  
  
 La <xref:Microsoft.VisualStudio.Shell.Package> classe implementa sia <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> che <xref:System.ComponentModel.Design.IServiceContainer> . <xref:System.ComponentModel.Design.IServiceContainer> contiene metodi di callback che forniscono servizi su richiesta.  
  
 Per altre informazioni sui servizi, vedere [Service Essentials](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
> Quando un pacchetto VSPackage sta per essere scaricato, Visual Studio attende finché non vengono recapitate tutte le richieste per i servizi forniti da un pacchetto VSPackage. Non sono consentite nuove richieste per questi servizi. Non chiamare in modo esplicito il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodo per revocare un servizio durante lo scaricamento.  
  
#### <a name="implementing-a-service"></a>Implementazione di un servizio  
  
1. Creare un progetto VSIX (**file/nuovo/progetto/Visual C#/estendibilità/progetto VSIX**).  
  
2. Aggiungere un pacchetto VSPackage al progetto. Selezionare il nodo del progetto nella **Esplora soluzioni** e fare clic su **Aggiungi/nuovo elemento/Visual C# Items/Extensibility/pacchetto di Visual Studio**.  
  
3. Per implementare un servizio, è necessario creare tre tipi:  
  
   - Interfaccia che descrive il servizio. Molte di queste interfacce sono vuote, ovvero non hanno metodi.  
  
   - Interfaccia che descrive l'interfaccia del servizio. Questa interfaccia include i metodi da implementare.  
  
   - Classe che implementa sia il servizio che l'interfaccia del servizio.  
  
     Nell'esempio seguente viene illustrata un'implementazione molto semplice dei tre tipi. Il costruttore della classe del servizio deve impostare il provider di servizi.  
  
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
  
### <a name="registering-a-service"></a>Registrazione di un servizio  
  
1. Per registrare un servizio, aggiungere al <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> pacchetto VSPackage che fornisce il servizio. Esempio:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Questo attributo viene registrato `SMyService` con Visual Studio.  
  
    > [!NOTE]
    > Per registrare un servizio che sostituisce un altro servizio con lo stesso nome, usare <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> . Si noti che è consentito un solo override di un servizio.  
  
### <a name="adding-a-service"></a>Aggiunta di un servizio  
  
1. 1.  Nell'inizializzatore VSPackage aggiungere il servizio e aggiungere un metodo di callback per creare i servizi. Ecco la modifica da apportare al <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Metodo:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2. Implementare il metodo di callback, che deve creare e restituire il servizio, oppure null se non è possibile crearlo.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    > Visual Studio può rifiutare una richiesta di fornire un servizio. Questa operazione viene eseguita se un altro pacchetto VSPackage fornisce già il servizio.  
  
3. A questo punto è possibile ottenere il servizio e utilizzarne i metodi. Questo verrà visualizzato nell'inizializzatore, ma è possibile ottenere il servizio in qualsiasi punto in cui si vuole usare il servizio.  
  
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
