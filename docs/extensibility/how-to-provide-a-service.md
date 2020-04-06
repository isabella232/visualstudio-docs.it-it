---
title: 'Procedura: Fornire un servizio Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60cae5e8048a0234114e1f9e7d97728e26ee40f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710777"
---
# <a name="how-to-provide-a-service"></a>Procedura: fornire un servizioHow to: Provide a service
Un pacchetto VSPackage può fornire servizi che altri VSPackage possono usare. Per fornire un servizio, un VSPackage deve registrare il servizio con Visual Studio e aggiungere il servizio.

 La <xref:Microsoft.VisualStudio.Shell.Package> classe <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementa <xref:System.ComponentModel.Design.IServiceContainer>sia e . <xref:System.ComponentModel.Design.IServiceContainer>contiene metodi di callback che forniscono servizi su richiesta.

 Per ulteriori informazioni sui servizi, vedere [Elementi essenziali del servizio](../extensibility/internals/service-essentials.md) .

> [!NOTE]
> Quando un vsPackage sta per essere scaricato, Visual Studio attende fino a quando tutte le richieste di servizi che un VSPackage fornisce sono stati recapitati. Non consente nuove richieste per questi servizi. Non è necessario <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> chiamare in modo esplicito il metodo per revocare un servizio durante lo scaricamento.

## <a name="implement-a-service"></a>Implementare un servizioImplement a service

1. Creare un progetto VSIX (**Progetto** > **nuovo** > **progetto** > di Visual**Cè** > **Extensibility** > Progetto**VSIX**).

2. Aggiungere un pacchetto VSPackage al progetto. Selezionare il nodo del progetto in **Esplora soluzioni** e fare clic su **Aggiungi** > **nuovo elemento** > **di estensibilità** > degli**elementi** > di**Visual**C

3. Per implementare un servizio, è necessario creare tre tipi:To implement a service, you need to create three types:

   - Interfaccia che descrive il servizio. Molte di queste interfacce sono vuote, ovvero non hanno metodi.

   - Interfaccia che descrive l'interfaccia del servizio. Questa interfaccia include i metodi da implementare.

   - Classe che implementa sia il servizio che l'interfaccia del servizio.

     Nell'esempio seguente viene illustrata un'implementazione di base dei tre tipi. Il costruttore della classe di servizio deve impostare il provider di servizi.

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

1. Per registrare un <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> servizio, aggiungere il al pacchetto VSPackage che fornisce il servizio. Esempio:

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Questo attributo `SMyService` viene registrato con Visual Studio.This attribute registers with Visual Studio.

    > [!NOTE]
    > Per registrare un servizio che sostituisce un <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>altro servizio con lo stesso nome, utilizzare il metodo . Si noti che è consentita una sola sostituzione di un servizio.

### <a name="add-a-service"></a>Aggiungere un servizio

1. Nell'inizializzatore VSPackage aggiungere il servizio e un metodo di callback per creare i servizi. Ecco la modifica da <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> apportare al metodo:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Implementare il metodo di callback, che deve creare e restituire il servizio o null se non può essere creato.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio può rifiutare una richiesta di fornire un servizio. Lo fa se un altro VSPackage fornisce già il servizio.

3. Ora è possibile ottenere il servizio e utilizzare i relativi metodi. L'esempio seguente mostra l'uso del servizio nell'inizializzatore, ma è possibile ottenere il servizio ovunque si desideri utilizzare il servizio.

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

     Il valore `helloString` di deve essere "Hello".

## <a name="see-also"></a>Vedere anche
- [Procedura: Ottenere un servizioHow to: Get a service](../extensibility/how-to-get-a-service.md)
- [Utilizzare e fornire servizi](../extensibility/using-and-providing-services.md)
- [Essenziali di servizio](../extensibility/internals/service-essentials.md)
