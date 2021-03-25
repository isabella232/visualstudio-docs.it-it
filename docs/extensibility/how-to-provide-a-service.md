---
title: 'Procedura: fornire un servizio | Microsoft Docs'
description: Un pacchetto VSPackage può fornire servizi che altri pacchetti VSPackage possono usare. Informazioni su come un pacchetto VSPackage registra un servizio con Visual Studio e aggiunge il servizio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8391d6d08214f915d136f80130cf9167573c14eb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069894"
---
# <a name="how-to-provide-a-service"></a>Procedura: fornire un servizio
Un pacchetto VSPackage può fornire servizi che altri pacchetti VSPackage possono usare. Per fornire un servizio, un pacchetto VSPackage deve registrare il servizio con Visual Studio e aggiungere il servizio.

 La <xref:Microsoft.VisualStudio.Shell.Package> classe implementa sia <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> che <xref:System.ComponentModel.Design.IServiceContainer> . <xref:System.ComponentModel.Design.IServiceContainer> contiene metodi di callback che forniscono servizi su richiesta.

 Per altre informazioni sui servizi, vedere [Service Essentials](../extensibility/internals/service-essentials.md) .

> [!NOTE]
> Quando un pacchetto VSPackage sta per essere scaricato, Visual Studio attende finché non vengono recapitate tutte le richieste per i servizi forniti da un pacchetto VSPackage. Non sono consentite nuove richieste per questi servizi. Non chiamare in modo esplicito il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodo per revocare un servizio durante lo scaricamento.

## <a name="implement-a-service"></a>Implementare un servizio

1. Creare un progetto VSIX (**file**  >  **New**  >  **Project**  >  **Visual C#**  >  **Extensibility**  >  **progetto VSIX**).

2. Aggiungere un pacchetto VSPackage al progetto. Selezionare il nodo del progetto nella **Esplora soluzioni** e fare clic su **Aggiungi**  >  **nuovo elemento**  >  **Visual C# elementi**  >  **estensibilità**  >  **pacchetto di Visual Studio**.

3. Per implementare un servizio, è necessario creare tre tipi:

   - Interfaccia che descrive il servizio. Molte di queste interfacce sono vuote, ovvero non hanno metodi.

   - Interfaccia che descrive l'interfaccia del servizio. Questa interfaccia include i metodi da implementare.

   - Classe che implementa sia il servizio che l'interfaccia del servizio.

     Nell'esempio seguente viene illustrata un'implementazione di base dei tre tipi. Il costruttore della classe del servizio deve impostare il provider di servizi.

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

1. Per registrare un servizio, aggiungere al <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> pacchetto VSPackage che fornisce il servizio. Ecco un esempio:

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

### <a name="add-a-service"></a>Aggiungere un servizio

1. Nell'inizializzatore VSPackage aggiungere il servizio e aggiungere un metodo di callback per creare i servizi. Ecco la modifica da apportare al <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Metodo:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Implementare il metodo di callback, che deve creare e restituire il servizio, oppure null se non è possibile crearlo.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio può rifiutare una richiesta di fornire un servizio. Questa operazione viene eseguita se un altro pacchetto VSPackage fornisce già il servizio.

3. A questo punto è possibile ottenere il servizio e utilizzarne i metodi. Nell'esempio seguente viene illustrato l'utilizzo del servizio nell'inizializzatore, ma è possibile ottenere il servizio in qualsiasi punto in cui si desidera utilizzare il servizio.

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

## <a name="see-also"></a>Vedi anche
- [Procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md)
- [Usare e fornire servizi](../extensibility/using-and-providing-services.md)
- [Essentials servizio](../extensibility/internals/service-essentials.md)
