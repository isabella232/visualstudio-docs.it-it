---
title: 'Procedura: usare ClickOnce per distribuire applicazioni eseguibili in più versioni di .NET Framework | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 7a5262814f6ccfb28ba796140e52175e2fe940a9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842768"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Procedura: usare ClickOnce per distribuire applicazioni eseguibili in più versioni di .NET framework
È possibile distribuire un'applicazione destinata a più versioni di .NET Framework tramite la tecnologia di distribuzione ClickOnce. Ciò richiede di generare e aggiornare i manifesti dell'applicazione e della distribuzione.  
  
> [!NOTE]
>  Prima di modificare l'applicazione a più versioni di .NET Framework di destinazione, è necessario assicurarsi che l'applicazione viene eseguita con più versioni di .NET Framework. Versione common language runtime è diverso tra [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] rispetto a .NET Framework 2.0, .NET Framework 3.0 e .NET Framework 3.5.  
  
 Questo processo sono necessari i passaggi seguenti:  
  
1.  Generare i manifesti dell'applicazione e distribuzione.  
  
2.  Modificare il manifesto di distribuzione per visualizzare un elenco di più versioni di .NET Framework.  
  
3.  Modifica il *app. config* file per elencare le versioni di runtime di .NET Framework compatibili.  
  
4.  Modificare il manifesto dell'applicazione per contrassegnare gli assembly dipendenti degli assembly di .NET Framework.  
  
5.  Firmare il manifesto dell'applicazione.  
  
6.  Aggiornare e firmare il manifesto della distribuzione.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Per generare i manifesti dell'applicazione e distribuzione  
  
-   Usare la procedura guidata di pubblicazione o la pagina di pubblicazione di creazione progetti per pubblicare l'applicazione e generare l'applicazione e i file manifesto di distribuzione. Per altre informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) oppure [pubblicare Page, Project Designer](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Per modificare il manifesto di distribuzione per visualizzare un elenco di più versioni di .NET Framework  
  
1.  Nella directory di pubblicazione, aprire il manifesto di distribuzione usando l'Editor XML in Visual Studio. Il manifesto di distribuzione con il *Application* estensione del nome file.  
  
2.  Sostituire il codice XML tra i `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` e `</compatibleFrameworks>` elementi con il codice XML che elenca le versioni di .NET Framework supportate per l'applicazione.  
  
     Nella tabella seguente vengono illustrate alcune delle versioni di .NET Framework disponibili e il codice XML corrispondente che è possibile aggiungere al manifesto della distribuzione.  
  
    |Versione di .NET Framework|XML|  
    |----------------------------|---------|  
    |Client 4|\<Framework targetVersion = "4.0" profile = supportedRuntime "Client" = "4.0.30319" / >|  
    |Full 4|\<Framework targetVersion = "4.0" profile = supportedRuntime "Completo" = "4.0.30319" / >|  
    |3.5 client|\<Framework targetVersion = "3.5" profile = supportedRuntime "Client" = "2.0.50727" / >|  
    |3.5 completo|\<Framework targetVersion = "3.5" profile = supportedRuntime "Completo" = "2.0.50727" / >|  
    |3.0|\<Framework targetVersion = supportedRuntime "3.0" = "2.0.50727" / >|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Per modificare il file app. config per elencare le versioni di runtime di .NET Framework compatibili  
  
1.  In Esplora soluzioni aprire il *app. config* file usando l'Editor XML in Visual Studio.  
  
2.  Sostituire (o aggiungere) il codice XML tra i `<startup>` e `</startup>` elementi con il codice XML che elenca i runtime di .NET Framework supportati per l'applicazione.  
  
     Nella tabella seguente vengono illustrate alcune delle versioni di .NET Framework disponibili e il codice XML corrispondente che è possibile aggiungere al manifesto della distribuzione.  
  
    |Versione di runtime di .NET framework|XML|  
    |------------------------------------|---------|  
    |Client 4|\<versione supportedRuntime = sku "v4.0.30319" = ". NETFramework, versione = v4.0, profilo = Client "/ >|  
    |Full 4|\<versione supportedRuntime = sku "v4.0.30319" = ". NETFramework, versione = v4.0 "/ >|  
    |3.5 completo|\<version="v2.0.50727"/ supportedRuntime >|  
    |3.5 client|\<versione supportedRuntime = sku "v2.0.50727" = "Client" / >|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Per modificare il manifesto dell'applicazione per contrassegnare gli assembly dipendenti degli assembly di .NET Framework  
  
1. Nella directory di pubblicazione, aprire il manifesto dell'applicazione utilizzando l'Editor XML in Visual Studio. Il manifesto di distribuzione con il *manifest* estensione del nome file.  
  
2. Aggiungere `group="framework"` per il XML della dipendenza per gli assembly di sentinel (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, e `System.Data.Entity`). Ad esempio, il codice XML dovrebbe essere simile al seguente:  
  
   ```xml  
   <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
   ```  
  
3. Aggiornare il numero di versione il `<assemblyIdentity>` elemento per Microsoft.Windows.CommonLanguageRuntime sul numero di versione di .NET Framework che è il minimo comune denominatore. Ad esempio, se l'applicazione è destinata a .NET Framework 3.5 e [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)], utilizzare il 2.0.50727.0 numero di versione e il codice XML dovrebbe essere simile al seguente:  
  
   ```xml  
   <dependency>  
     <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
       <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
     </dependentAssembly>  
   </dependency>  
   ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Per aggiornare e firmare nuovamente l'applicazione e distribuzione di manifesti  
  
-   Aggiornare e firmare nuovamente i manifesti dell'applicazione e distribuzione. Per altre informazioni, vedere [procedura: firmare manifesti dell'applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Vedere anche  
 [La pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks > elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<dipendenza > elemento](../deployment/dependency-element-clickonce-application.md)   
 [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Schema dei file di configurazione](/dotnet/framework/configure-apps/file-schema/index)