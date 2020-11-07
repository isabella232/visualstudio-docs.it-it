---
title: Usare ClickOnce per distribuire app multitarget
description: Informazioni su come distribuire un'applicazione destinata a più versioni del .NET Framework tramite la tecnologia di distribuzione ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67dcee1fac0b5ec082a7f92285c6c0ac2523800a
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349516"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Procedura: Usare ClickOnce per distribuire applicazioni eseguibili in più versioni di .NET Framework
È possibile distribuire un'applicazione destinata a più versioni del .NET Framework tramite la tecnologia di distribuzione ClickOnce. A tale scopo, è necessario generare e aggiornare i manifesti dell'applicazione e della distribuzione.

> [!NOTE]
> Prima di modificare l'applicazione in modo che sia destinata a più versioni del .NET Framework, è necessario assicurarsi che l'applicazione venga eseguita con più versioni del .NET Framework. La versione Common Language Runtime è diversa .NET Framework 4 rispetto a .NET Framework 2,0, .NET Framework 3,0 e .NET Framework 3,5.

 Per questo processo sono richiesti i passaggi seguenti:

1. Generare i manifesti dell'applicazione e della distribuzione.

2. Modificare il manifesto di distribuzione per elencare le versioni di più .NET Framework.

3. Modificare il file di *app.config* per elencare le versioni di .NET Framework Runtime compatibili.

4. Modificare il manifesto dell'applicazione per contrassegnare gli assembly dipendenti come assembly .NET Framework.

5. Firmare il manifesto dell'applicazione.

6. Aggiornare e firmare il manifesto della distribuzione.

### <a name="to-generate-the-application-and-deployment-manifests"></a>Per generare i manifesti dell'applicazione e della distribuzione

- Usare la pubblicazione guidata o la pagina pubblica di progettazione progetti per pubblicare l'applicazione e generare i file manifesto dell'applicazione e della distribuzione. Per altre informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) o la [pagina pubblica, Progettazione progetti](../ide/reference/publish-page-project-designer.md).

### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Per modificare il manifesto di distribuzione per elencare le versioni di più .NET Framework

1. Nella directory publish aprire il manifesto di distribuzione usando l'editor XML in Visual Studio. Il manifesto di distribuzione ha l'estensione del nome file *. Application* .

2. Sostituire il codice XML tra gli `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` `</compatibleFrameworks>` elementi e con XML che elenca le versioni di .NET Framework supportate per l'applicazione.

     Nella tabella seguente vengono illustrate alcune delle versioni di .NET Framework disponibili e il codice XML corrispondente che è possibile aggiungere al manifesto della distribuzione.

    |Versione di .NET Framework|XML|
    |----------------------------|---------|
    |4 Client|\<framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />|
    |4 Completo|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|
    |3.5 Client|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|
    |3.5 Completo|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|

### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Per modificare il file di app.config per elencare le versioni compatibili di .NET Framework Runtime

1. In Esplora soluzioni aprire il file di *app.config* utilizzando l'editor XML in Visual Studio.

2. Sostituire (o aggiungere) il codice XML tra gli `<startup>` `</startup>` elementi e con XML che elenca i runtime di .NET Framework supportati per l'applicazione.

     Nella tabella seguente vengono illustrate alcune delle versioni di .NET Framework disponibili e il codice XML corrispondente che è possibile aggiungere al manifesto della distribuzione.

    |.NET Framework versione runtime|XML|
    |------------------------------------|---------|
    |4 Client|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0,Profile=Client" />|
    |4 Completo|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|
    |3.5 Completo|\<supportedRuntime version="v2.0.50727"/>|
    |3.5 Client|\<supportedRuntime version="v2.0.50727" sku="Client"/>|

### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Per modificare il manifesto dell'applicazione per contrassegnare gli assembly dipendenti come assembly .NET Framework

1. Nella directory publish (pubblica) aprire il manifesto dell'applicazione usando l'editor XML in Visual Studio. Il manifesto di distribuzione ha l'estensione del nome file *. manifest* .

2. Aggiungere `group="framework"` al file XML di dipendenza per gli assembly Sentinel ( `System.Core` ,, `WindowsBase` `Sentinel.v3.5Client` e `System.Data.Entity` ). Ad esempio, il codice XML dovrebbe essere simile al seguente:

   ```xml
   <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">
   ```

3. Aggiornare il numero di versione dell' `<assemblyIdentity>` elemento per Microsoft. Windows. CommonLanguageRuntime al numero di versione per il .NET Framework che è il denominatore comune più basso. Ad esempio, se l'applicazione è destinata a .NET Framework 3,5 e .NET Framework 4, usare il numero di versione di 2.0.50727.0 e il codice XML dovrebbe essere simile al seguente:

   ```xml
   <dependency>
     <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
       <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />
     </dependentAssembly>
   </dependency>
   ```

### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Per aggiornare e firmare nuovamente i manifesti dell'applicazione e della distribuzione

- Aggiornare e firmare nuovamente i manifesti dell'applicazione e della distribuzione. Per altre informazioni, vedere [Procedura: Firmare nuovamente manifesti di applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Vedere anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [\<compatibleFrameworks> elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [\<dependency> elemento](../deployment/dependency-element-clickonce-application.md)
- [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Schema dei file di configurazione](/dotnet/framework/configure-apps/file-schema/index)
