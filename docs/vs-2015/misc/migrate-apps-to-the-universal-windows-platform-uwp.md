---
title: La migrazione di App per la piattaforma Windows universale (UWP) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: d59ccac2ef8f91fae9bede5951ff42ec5a43be0e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848553"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Migrare le app alla piattaforma UWP (Universal Windows Platform)
Apportare le modifiche manuali necessarie ai file di progetto esistenti per le app di Windows Store 8.1, di Windows Phone 8.1 o di Windows universale create con Visual Studio 2015 RC, in modo da consentirne l'uso con Visual Studio 2015 RTM. Se è presente un'app universale di Windows 8.1 con un progetto di app di Windows e un progetto di Windows Phone, è necessario seguire la procedura per la migrazione dei singoli progetti.  
  
 La piattaforma UWP (Universal Windows Platform) consente ora di scegliere come destinazione dell'app una o più famiglie di dispositivi. Per altre informazioni sulle app di Windows universale, vedere questa [Guida della piattaforma](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).  
  
- [Migrare le app esistenti di Windows Store 8.1 o Windows Phone 8.1 C#/VB](#MigrateCSharp) per usare la piattaforma UWP.  
  
- [Migrare le app esistenti di Windows Store 8.1 o Windows Phone 8.1 C++](#MigrateCPlusPlus) per usare la piattaforma UWP.  
  
- [Modifiche richieste per le app di Windows universale esistenti create con Visual Studio 2015 RC](#PreviousVersions).  
  
- [Modifiche richieste per i progetti di unit test esistenti per le app di Windows universale create con Visual Studio 2015 RC](#MigrateUnitTest).  
  
  Se non si vogliono apportare tutte queste modifiche, vedere le informazioni su come [convertire le app esistenti](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) in un nuovo progetto di Windows universale.  
  
##  <a name="MigrateCSharp"></a> Eseguire la migrazione di App C# /VB Windows Store 8.1 o Windows Phone 8.1 per utilizzare la piattaforma Windows universale  
  
#### <a name="migrate-your-cvb-project-files"></a>Migrare i file di progetto C#/VB  
  
1.  Per trovare il tipo di piattaforma UWP (Universal Windows Platform) installato, aprire la cartella **\Program Files (x86)\Windows Kits\10\Platforms\UAP**, che contiene un elenco di cartelle per ogni piattaforma UWP installata. Il nome della cartella è la versione della piattaforma UWP installata. Ad esempio, in questo dispositivo Windows 10 è installata la versione 10.0.10240.0 della piattaforma UWP (Universal Windows Platform).  
  
     ![Aprire la cartella per visualizzare le versioni installate](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     È possibile installare più versioni della piattaforma UWP. Si consiglia di usare la versione più recente disponibile per l'app.  
  
2.  In Esplora File passare alla cartella in cui è archiviato il progetto UWP. In questa cartella creare un file con estensione json. Assegnare al file il nome project.json e quindi aggiungere il contenuto seguente al file:  
  
    ```json  
    {  
      "dependencies": {  
        "Microsoft.ApplicationInsights": "1.0.0",  
        "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",  
        "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",  
        "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"  
      },  
      "frameworks": {  
        "uap10.0": {}  
      },  
      "runtimes": {  
        "win10-arm": {},  
        "win10-arm-aot": {},  
        "win10-x86": {},  
        "win10-x86-aot": {},  
        "win10-x64": {},  
        "win10-x64-aot": {}  
      }  
    }  
  
    ```  
  
3.  Creare un file denominato default.rd.xml con i contenuti seguenti. Se si ha un progetto VB, aggiungere questo file alla directory Progetto del progetto. Se si ha un progetto C#, aggiungere questo file alla directory Proprietà del progetto.  
  
    ```xml  
    <?xml version="1.0"?>  
    <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> -->  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application>  
    <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. -->  
    <Assembly Dynamic="Required All" Name="*Application*"/>  
    <!-- Add your application specific runtime directives here. -->  
    </Application></Directives>  
    ```  
  
4.  Aprire la soluzione che contiene le app esistenti di Windows Store 8.1 o Windows Phone 8.1 in Visual Studio.  
  
5.  Fare clic con il pulsante destro del mouse sul progetto esistente per l'app in Esplora soluzioni e quindi scegliere **Scarica progetto**. Dopo aver scaricato il progetto, fare di nuovo clic con il pulsante destro del mouse sul file di progetto e scegliere di modificare il file con estensione csproj o vbproj.  
  
     ![Fare clic con il pulsante destro del progetto e scegliere Modifica](../misc/media/uap-editproject.png "UAP_EditProject")  
  
6.  Trovare il \<PropertyGroup > elemento che contiene il \<TargetPlatformVersion > elemento con un valore 8.1. Attenersi alla procedura seguente per questo \<PropertyGroup > elemento:  
  
    1.  Impostare il valore della \<piattaforma > elemento da: **x86**.  
  
    2.  Aggiungere un \<TargetPlatformIdentifier > elemento e impostarne il valore: **UAP**.  
  
    3.  Modificare il valore esistente del \<TargetPlatformVersion > elemento come valore della versione (Universal Windows Platform) installato. Aggiungere anche un \<TargetPlatformMinVersion > elemento e assegnargli lo stesso valore.  
  
    4.  Modificare il valore della \<MinimumVisualStudioVersion > elemento da: **14**.  
  
    5.  Sostituire il \<ProjectTypeGuids > come illustrato di seguito:  
  
         Per C#:  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
        ```  
  
         Per VB:  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        ```  
  
    6.  Aggiungere un \<EnableDotNetNativeCompatibleProfile > elemento e impostarne il valore: **true**.  
  
    7.  La dimensione predefinita per le risorse nelle app di Windows universale è 200. Se il progetto include risorse con dimensione non 200, è necessario aggiungere un \<UapDefaultAssetScale > elemento con il valore della scala degli asset a questo elemento PropertyGroup. Altre informazioni su [asset e scale](http://msdn.microsoft.com/library/jj679352.aspx).  
  
         A questo punto il \<PropertyGroup > elemento dovrebbe essere simile a questo esempio:  
  
        ```xml  
        <PropertyGroup>  
            …  
             <Platform Condition=" '$(Platform)' == '' ">x86</Platform>  
             <TargetPlatformVersion>10.0.10240.0</TargetPlatformVersion>  
             <TargetPlatformMinVersion>10.0.10240.0</TargetPlatformMinVersion>  
             <TargetPlatformIdentifier>UAP</TargetPlatformIdentifier>  
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>  
             <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
             <UapDefaultAssetScale>100</UapDefaultAssetScale>  
             …  
        </PropertyGroup>  
        ```  
  
7.  Sostituire le istanze di 12.0 con 14.0 per riflettere la versione di Visual Studio in uso. Ad esempio, le istanze seguenti:  
  
    ```xml  
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ```  
  
    ```  
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' ">  
        <VisualStudioVersion>14.0</VisualStudioVersion>  
    ```  
  
8.  Trovare \<PropertyGroup > gli elementi che sono configurati per la piattaforma AnyCPU come parte dell'attributo Condition. Rimuovere questi elementi e i relativi elementi figlio. L'elemento AnyCPU non è supportato per le app di Windows 10 in Visual Studio 2015. Ad esempio, è necessario rimuovere \<PropertyGroup > elementi quali quelli riportati:  
  
    ```xml  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <PlatformTarget>AnyCPU</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <PlatformTarget>AnyCPU</PlatformTarget>  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
    ```  
  
9. Per ognuna delle restanti \<PropertyGroup > element, controllare se l'elemento ha un attributo Condition con una configurazione rilascio. Se accade, ma non contiene un \<UseDotNetNativeToolchain > elemento, quindi aggiungerne uno. Impostare il valore per il \<UseDotNetNativeToolchain > elemento su true, simile al seguente:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|x64'">  
        <OutputPath>bin\x64\Release\</OutputPath>  
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <Optimize>true</Optimize>  
        <NoWarn>;2008</NoWarn>  
        <DebugType>pdbonly</DebugType>  
        <PlatformTarget>x64</PlatformTarget>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
        <ErrorReport>prompt</ErrorReport>  
        <Prefer32Bit>true</Prefer32Bit>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
    ```  
  
10. Per Windows Phone progetti rimuovere solo il \<PropertyGroup > elemento contenente un \<TargetPlatformIdentifier > elemento con un valore windowsphoneapp. Rimuovere anche gli elementi figlio di questo elemento:  
  
    ```xml  
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">  
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>  
    </PropertyGroup>  
    ```  
  
11. Trovare il \<ItemGroup > elemento che contiene il \<AppxManifest > elemento. Aggiungere il codice seguente \<None > come figlio dell'elemento di \<ItemGroup > elemento:  
  
    ```xml  
    <None Include="project.json" />  
    ```  
  
12. Trovare il \<ItemGroup > elemento che contiene altre risorse che vengono aggiunti al progetto, ad esempio file con estensione png del logo (\<Include="Assets\Logo.scale-100.png contenuto" / >). Aggiungere il codice seguente \<Content > elemento figlio a questa \<ItemGroup > elemento:  
  
     **Per c#:**  
  
    ```xml  
    <Content Include="Properties\default.rd.xml" />  
    ```  
  
     **Per VB:**  
  
    ```xml  
    <Content Include="My Project\default.rd.xml" />  
    ```  
  
13. Trovare il \<ItemGroup > che include \<riferimento > gli elementi figlio ai pacchetti NuGet. Prendere nota dei pacchetti NuGet usati, perché sarà necessario scaricarli con Gestione pacchetti NuGet dopo che il progetto è stato ricaricato. Rimuovere questo \<ItemGroup > insieme ai relativi elementi figlio. Ad esempio, un progetto UWP può includere i pacchetti NuGet seguenti che devono essere rimossi:  
  
    ```xml  
    <ItemGroup>  
        <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
      </ItemGroup>  
    ```  
  
14. Salvare le modifiche.  
  
15. Chiudere il file con estensione csproj o vbproj.  
  
16. Fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere Ricarica progetto dal menu di scelta rapida. A questo punto, tutti i file nel progetto dovrebbero essere visualizzati in Esplora soluzioni.  
  
17. Usare Gestione NuGet per aggiungere di nuovo i pacchetti eliminati in un passaggio precedente.  
  
     Seguire quindi la procedura per [aggiornare i file manifesto del pacchetto](#PackageManifest) per tutti i progetti Windows Store 8.1 o Windows Phone 8.1.  
  
##  <a name="MigrateCPlusPlus"></a> Migrare le app Windows Store 8.1 o Windows Phone 8.1 C++ per usare la piattaforma Windows universale  
  
#### <a name="migrate-your-c-project-files"></a>Migrare i file di progetto C++  
  
1.  Per trovare il tipo di piattaforma UWP (Universal Windows Platform) installato, aprire la cartella **\Program Files (x86)\Windows Kits\10\Platforms\UAP**, che contiene un elenco di cartelle per ogni piattaforma UWP installata. Il nome della cartella è la versione della piattaforma UWP installata. Ad esempio, in questo dispositivo Windows 10 è installata la versione 10.0.10240.0 della piattaforma UWP (Universal Windows Platform).  
  
     ![Aprire la cartella per visualizzare le versioni installate](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     È possibile installare più versioni della piattaforma UWP. Si consiglia di usare la versione più recente disponibile per l'app.  
  
2.  Aprire la soluzione che contiene le app esistenti di Windows Store 8.1 o Windows Phone 8.1 C++ in Visual Studio.  
  
     Fare clic con il pulsante destro del mouse sul progetto esistente in Esplora soluzioni, quindi selezionare **Scarica progetto**. Dopo aver scaricato il progetto, fare di nuovo clic con il pulsante destro del mouse sul file di progetto e scegliere di modificare il file con estensione vcxproj.  
  
     ![Destra&#45;fare clic sul file di progetto e scegliere di modificarlo](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")  
  
3.  Trovare il \<PropertyGroup > elemento che contiene il \<ApplicationTypeRevision > elemento con un valore 8.1. Attenersi alla procedura seguente per questo \<PropertyGroup > elemento:  
  
    1.  Aggiungere un \<WindowsTargetPlatformVersion > elemento e un \<WindowsTargetPlatformMinVersion > elemento e fornire loro il valore della versione (Universal Windows Platform) installato.  
  
    2.  Aggiornare il valore dell'elemento ApplicationTypeRevision da 8.1 a 10.0.  
  
    3.  Modificare il valore della \<MinimumVisualStudioVersion > elemento: 14.  
  
    4.  Aggiungere un \<EnableDotNetNativeCompatibleProfile > elemento e impostarne il valore: true.  
  
    5.  La dimensione predefinita per le risorse nelle app di Windows universale è 200. Se il progetto include risorse con dimensione non 200, è necessario aggiungere un \<UapDefaultAssetScale > elemento con il valore della scala degli asset a questo elemento PropertyGroup. Altre informazioni su [asset e scale](http://msdn.microsoft.com/library/jj679352.aspx).  
  
    6.  Per Windows Phone progetti solo, modificare il valore di \<ApplicationType > da Windows Phone a Windows Store.  
  
         A questo punto il \<PropertyGroup > elemento dovrebbe essere simile a questo esempio:  
  
        ```xml  
        <PropertyGroup>  
            …  
                  <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>  
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>  
             <ApplicationType>Windows Store</ApplicationType>  
             <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>  
             <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
             <UapDefaultAssetScale>100</UapDefaultAssetScale>  
             …  
        </PropertyGroup>  
        ```  
  
4.  Modificare tutte le istanze del \<PlatformToolset > elemento abbiano il valore v140. Ad esempio:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
    ```  
  
5.  Per ognuna delle restanti \<PropertyGroup > element, controllare se l'elemento ha un attributo Condition con una configurazione rilascio. Se accade, ma non contiene un \<UseDotNetNativeToolchain > elemento, quindi aggiungerne uno. Impostare il valore per il \<UseDotNetNativeToolchain > elemento su true, simile al seguente:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
  
    ```  
  
6.  Salvare le modifiche. Quindi, chiudere il file di progetto.  
  
7.  Fare clic con il pulsante destro del mouse sul file di progetto in Esplora soluzioni e scegliere Ricarica progetto dal menu di scelta rapida. A questo punto, tutti i file nel progetto dovrebbero essere visualizzati in Esplora soluzioni.  
  
     Seguire quindi la procedura per [aggiornare i file manifesto del pacchetto](#PackageManifest) per tutti i progetti Windows Store 8.1 o Windows Phone 8.1.  
  
##  <a name="PackageManifest"></a> Aggiornare il file manifesto di pacchetto per i progetti di tutti i Windows Store 8.1 o Windows Phone 8.1  
 È necessario aggiornare il file manifesto del pacchetto per ogni progetto nella soluzione.  
  
#### <a name="update-your-package-manifest-file"></a>Aggiornare il file manifesto del pacchetto  
  
1. Aprire il file Package.appxmanifest nel progetto. È necessario modificare il file Package.AppxManifest per tutti i progetti Windows Store e Windows Phone.  
  
2. È necessario aggiornare il \<pacchetto > elemento con i nuovi schemi in base al tipo di progetto esistente. Rimuovere prima gli schemi seguenti in base al tipo di progetto in uso, Windows Store o Windows Phone.  
  
    **PRECEDENTE per il progetto Windows Store:** il \<pacchetto > elemento avrà un aspetto simile al seguente.  
  
   ```xml  
   <Package  
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"     
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">  
  
   ```  
  
    **PRECEDENTE per il progetto Windows Phone:** il \<pacchetto > elemento avrà un aspetto simile al seguente.  
  
   ```xml  
   <Package  
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"     
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"  
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"  
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">  
   ```  
  
    **Novità per la piattaforma Windows universale:** aggiungere gli schemi sotto il \<pacchetto > elemento. Rimuovere i prefissi dell'identificatore dello spazio dei nomi associato dagli elementi per gli schemi appena rimossi. Aggiornare la proprietà IgnorableNamespaces su: uap mp. Il nuovo \<pacchetto > elemento dovrebbe essere simile alla seguente.  
  
   ```xml  
   <Package  
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"  
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"  
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"  
      IgnorableNamespaces= "uap mp">  
  
   ```  
  
3. Aggiungere un \<dipendenze > elemento figlio di \<pacchetto > elemento. Aggiungere quindi una \<TargetDeviceFamily > elemento figlio a questa \<dipendenze > elemento con gli attributi Name, MinVersion e MaxVersionTested. Assegnare all'attributo Name il valore: Windows.Universal. Assegnare a MinVersion e MaxVersionTested il valore della versione della piattaforma UWP installata. Questo elemento dovrebbe essere simile al seguente:  
  
   ```xml  
   <Dependencies>  
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />  
   </Dependencies>  
   ```  
  
4. **Per Windows Store solo:** è necessario aggiungere un' \<MP: phoneidentity > elemento figlio di \<pacchetto > elemento. Aggiungere un attributo PhoneProductId e un attributo PhonePublisherId. Impostare phoneproductid in modo che hanno lo stesso valore di attributo Name nel \<identità > elemento. Impostare il valore PhonePublishedId su: 00000000-0000-0000-0000-000000000000, analogamente a quanto segue:  
  
   ```xml  
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />   
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>  
   ```  
  
5. Trovare il \<prerequisiti > elemento ed eliminare questo elemento e gli eventuali elementi figlio presente.  
  
6. Aggiungere il **uap** dello spazio dei nomi al seguente \<risorsa > elementi: Scale, DXFeatureLevel. Ad esempio:  
  
   ```xml  
   <Resources>  
     <Resource Language="en-us"/>  
    <Resource uap:Scale="180"/>  
    <Resource uap:DXFeatureLevel="dx11"/>  
   </Resources>  
  
   ```  
  
7. Aggiungere il **uap** dello spazio dei nomi al seguente \<funzionalità > elementi: documentsLibrary, picturesLibrary, videosLibrary, musicLibrary, enterpriseAuthentication, sharedUserCertificates, removableStorage, Appointments e contacts. Ad esempio:  
  
   ```xml  
   <Capabilities>  
     <uap:Capability Name="documentsLibrary"/>  
     <uap:Capability Name="removableStorage"/>  
   </Capabilities>  
  
   ```  
  
8. Aggiungere il **uap** dello spazio dei nomi per il \<VisualElements > elemento e ai relativi elementi figlio. Ad esempio:  
  
   ```xml  
   <uap:VisualElements  
       DisplayName="My WWA App"  
       Square150x150Logo="images/150x150.png"  
       Square44x44Logo="images/44x44.png"  
       Description="My WWA App"  
       BackgroundColor="#777777">  
     <uap:SplashScreen Image="images/splash.png"/>  
   </uap:VisualElements>  
  
   ```  
  
    **Solo per Windows Store:** i nomi delle dimensioni riquadro sono stati modificati. Modificare gli attributi nel \<VisualElements > dimensioni riquadro con convergenza di elemento per riflettere la nuova. 70x70 diventa 71x71 e 30x30 diventa 44x44.  
  
    **PRECEDENTE:** nomi delle dimensioni riquadro  
  
   ```xml  
   <m2:VisualElements  
       …  
       Square30x30Logo="Assets\SmallLogo.png"  
       …>  
    <m2:DefaultTile  
         …  
         Square70x70Logo="images/70x70.png">  
   </m2:VisualElements>  
  
   ```  
  
    **NUOVO:** nomi delle dimensioni riquadro  
  
   ```xml  
   <uap:VisualElements  
       …  
       Square44x44Logo="Assets\SmallLogo.png"  
       …>  
    <uap:DefaultTile  
         …  
         Square71x71Logo="images/70x70.png">  
   </uap:VisualElements>  
  
   ```  
  
9. Aggiungere il **uap** dello spazio dei nomi per il \<ApplicationContentUriRules > e tutti i relativi elementi figlio. Ad esempio:  
  
    ```xml  
    <uap:ApplicationContentUriRules>  
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>  
      <uap:Rule Type="exclude" Match="*.pdf"/>  
    </uap:ApplicationContentUriRules>  
  
    ```  
  
10. Aggiungere il **uap** dello spazio dei nomi al seguente \<estensione > elementi e i relativi elementi figlio: windows.accountPictureProvide, windows.alarm, windows.autoPlayContent windows.appointmentsProvider,  windows.autoPlayDevice, windows.cachedFileUpdate, windows.cameraSettings, windows.fileOpenPicker, windows.fileTypeAssociation, windows.fileSavePicke, windows.lockScreenCall, windows.printTaskSettings, windows.protocol, windows.search, Windows. sharetarget. Ad esempio:  
  
    ```xml  
    <Extensions>  
      <uap:Extension Category="windows.alarm"/>  
      <uap:Extension Category="windows.search" EntryPoint="MyActivateableClassId.baz"/>  
      <uap:Extension Category="windows.protocol">  
        <uap:Protocol Name="mailto" DesiredView="useHalf">  
         <uap:DisplayName>MailTo Protocol</uap:DisplayName>  
        </uap:Protocol>  
      </uap:Extension>  
    </Extensions>  
  
    ```  
  
11. Aggiungere lo spazio dei nomi **uap** alle attività in background di tipo chatMessageNotification. Ad esempio:  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
     <BackgroundTasks ServerName="MyBackgroundTasks">  
        <uap:Task Type="chatMessageNotification"/>  
      </BackgroundTasks>  
    </Extension>  
  
    ```  
  
12. Modificare le dipendenze framework. Aggiungere un nome dell'editore a tutti \<PackageDependency > elementi, e specificare MinVersion se non è già stato specificato.  
  
     **PRECEDENTE:** \<PackageDependency > elemento  
  
    ```xml  
    <Dependencies>  
     <PackageDependency Name="Microsoft.VCLibs.120.00" />  
    </Dependencies>  
  
    ```  
  
     **Novità:** \<PackageDependency > elemento  
  
    ```xml  
    <Dependencies>  
     <PackageDependency  
          Name="Microsoft.VCLibs.120.00"  
          Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"  
          MinVersion="12.0.30113.0" />  
    </Dependencies>  
  
    ```  
  
     Usare i valori Publisher e MinVersion appropriati per il framework che si sta effettivamente usando. Tenere presente che questi nomi possono essere diversi per Windows 10.  
  
13. Sostituire le attività di tipo background gattCharacteristicNotification e rfcommConnection con un'attività di tipo Bluetooth. Ad esempio:  
  
     **PRECEDENTE:**  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
    <BackgroundTasks ServerName="MyBackgroundTasks">  
                <Task Type="rfcommConnection"/>  
               <Task Type="gattCharacteristicNotification"/>  
    </BackgroundTasks>  
    </Extension>  
    ```  
  
     **NUOVO:** sostituito con l'attività di tipo Bluetooth.  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
    <BackgroundTasks ServerName="MyBackgroundTasks">  
               <Task Type="bluetooth"/>  
    </BackgroundTasks>  
    </Extension>  
    ```  
  
14. Sostituire le capacità del dispositivo Bluetooth bluetooth.rfcomm e bluetooth.genericAttributeProfile con una capacità Bluetooth generica. Ad esempio:  
  
     **PRECEDENTE:**  
  
    ```xml  
    <Capabilities>  
      <m2:DeviceCapability Name="bluetooth.rfcomm">  
        <m2:Device Id="any">  
         <m2:Function Type="serviceId:34B1CF4D-1069-4AD6-89B6-E161D79BE4D8"/>  
        </m2:Device>  
      </m2:DeviceCapability>  
      <m2:DeviceCapability Name="bluetooth.genericAttributeProfile">  
        <m2:Device Id="any">  
         <m2:Function Type="name:heartRate"/>  
        </m2:Device>  
      </m2:DeviceCapability>  
    </Capabilities>  
    ```  
  
     **NUOVO:** sostituito con una capacità Bluetooth generica.  
  
    ```xml  
    <Capabilities>  
      <uap:DeviceCapability Name="bluetooth"/>  
    </Capabilities>  
  
    ```  
  
15. Rimuovere tutti gli elementi deprecati.  
  
    1. Questi attributi per \<VisualElements > sono deprecati e devono essere rimossi:  
  
       - Il \<VisualElements > attributi: ForegroundText, ToastCapable  
  
       - Il \<DefaultTile > attributo DefaultSize di  
  
       - Il \<ApplicationView > elemento  
  
         Ad esempio:  
  
       ```xml  
       <m2:VisualElements  
           …  
           ForegroundText="dark"  
           ToastCapable="true">  
       <m2:DefaultTile DefaultSize="square150x150Logo"/>  
         <m2:ApplicationView MinWidth="width320"/>  
       </m2:VisualElements>  
  
       ```  
  
    2. Rimuovere le estensioni Windows.contact e windows.contactPicker e tutti gli elementi contenuti.  
  
16. Salvare il file Package.appxmanifest. Quindi, chiudere Visual Studio.  
  
17. È necessario rimuovere alcuni file nascosti prima di riaprire la soluzione.  
  
    1.  Aprire Esplora file, fare clic su **Visualizza** nella barra degli strumenti e selezionare **Elementi nascosti** ed **Estensioni di file**. Aprire la cartella nel computer: \<percorso per il percorso della soluzione >\\VS\\\v14 {nome progetto}. Se esiste un file con estensione suo, eliminarlo.  
  
    2.  Tornare alla cartella in cui si trova la soluzione. Aprire le cartelle per i progetti presenti nella soluzione. Se nelle cartelle del progetto esiste un file con estensione csproj.user o vbproj.user, eliminarlo.  
  
         Ora è possibile riaprire la soluzione in Visual Studio. A questo punto è possibile codificare, compilare ed eseguire il debug dell'app con la piattaforma UWP.  
  
         Informazioni su come [adattare il codice](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) per sfruttare le nuove caratteristiche della piattaforma UWP.  
  
##  <a name="PreviousVersions"></a> Modifiche richieste per le app di Windows universale esistenti create con Visual Studio 2015 RC  
 Se sono state create app universali di Windows 10 con Visual Studio 2015 RC, è necessario modificare la destinazione del progetto in modo da usare la versione della piattaforma UWP (Universal Windows Platform) installata con la versione più recente di Visual Studio 2015. Le versioni precedenti non sono supportate. Le modifiche richieste dipendono dal linguaggio usato per creare l'app:  
  
-   [App C# /VB](#RCUpdate10CSharp)  
  
-   [App C++](#RCUpdate10CPlusPlus)  
  
###  <a name="RCUpdate10CSharp"></a> Aggiornare i progetti C# /VB per usare la piattaforma più recente di Windows universale  
 Quando si apre la soluzione per l'app esistente, viene indicato che è necessario un aggiornamento per l'app:  
  
 ![Visualizzazione del progetto in Esplora soluzioni](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")  
  
 Se si sceglie di ricaricare il progetto da Esplora soluzioni, verrà visualizzata la finestra di dialogo seguente:  
  
 ![Ridestinare l'app per usare il SDK corretto](../misc/media/missingsdkforuap.png "MissingSDKforUAP")  
  
 Poiché l'SDK della piattaforma UWP per il progetto non è supportato, non sarà possibile installarlo. Fare clic su OK e seguire la procedura descritta di seguito.  
  
##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>Aggiornare i progetti C#/VB in modo che usino la piattaforma UWP più recente  
  
1. Per trovare il tipo di piattaforma UWP (Universal Windows Platform) installato, aprire la cartella **\Program Files (x86)\Windows Kits\10\Platforms\UAP**, che contiene un elenco di cartelle per ogni piattaforma UWP installata. Il nome della cartella è la versione della piattaforma UWP installata. Ad esempio, in questo dispositivo Windows 10 è installata la versione 10.0.10240.0 della piattaforma UWP (Universal Windows Platform).  
  
    ![Aprire la cartella per visualizzare le versioni installate](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
    È possibile installare più versioni della piattaforma UWP. Si consiglia di usare la versione più recente disponibile per l'app.  
  
2. In Esplora File passare alla cartella in cui è archiviato il progetto UWP. Eliminare il file packages.config e creare un nuovo file con estensione json in questa cartella. Assegnare al file il nome project.json e quindi aggiungere il contenuto seguente al file:  
  
   ```json  
  
   {  
     "dependencies": {  
       "Microsoft.ApplicationInsights": "1.0.0",  
       "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",  
       "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",  
       "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"  
     },  
     "frameworks": {  
       "uap10.0": {}  
     },  
     "runtimes": {  
       "win10-arm": {},  
       "win10-arm-aot": {},  
       "win10-x86": {},  
       "win10-x86-aot": {},  
       "win10-x64": {},  
       "win10-x64-aot": {}  
     }  
   }  
  
   ```  
  
3. Con Visual Studio aprire la soluzione contenente l'app di Windows universale C#/VB. Sarà necessario aggiornare il file di progetto (con estensione csproj o vbproj). Fare clic con il pulsante destro del mouse sul file di progetto e scegliere di modificarlo.  
  
    ![Fare clic con il pulsante destro del progetto e scegliere Modifica](../misc/media/uap-editproject.png "UAP_EditProject")  
  
4. Trovare il \<PropertyGroup > elemento che contiene il \<TargetPlatformVersion > e \<TargetPlatformMinVersion > elementi. Modificare il valore esistente del \<TargetPlatformVersion > e \<TargetPlatformMinVersion > elementi che possono essere la stessa versione della piattaforma Windows universale installata.  
  
    La dimensione predefinita per le risorse nelle app di Windows universale è 200. I progetti creati con risorse di Visual Studio 2015 RC includono con dimensione 100, è necessario aggiungere un \<UapDefaultAssetScale > elemento con un valore pari a 100 all'elemento PropertyGroup. Altre informazioni su [asset e scale](http://msdn.microsoft.com/library/jj679352.aspx).  
  
5. Se sono stati aggiunti riferimenti a SDK di estensione della piattaforma UWP (Universal Windows Platform), ad esempio Windows Mobile SDK, sarà necessario aggiornare la versione dell'SDK. Ad esempio questo \<SDKReference > elemento:  
  
   ```xml  
   <SDKReference Include="WindowsMobile, Version=10.0.0.1">  
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>  
   </SDKReference>  
  
   ```  
  
    Deve essere modificato in:  
  
   ```xml  
   <SDKReference Include="WindowsMobile, Version=10.0.10240.0">  
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>  
   </SDKReference>  
  
   ```  
  
6. Trovare il \<destinazione > elemento con un attributo di nome con il valore: sia EnsureNuGetPackageBuildImports. Eliminare questo elemento e tutti i relativi elementi figlio.  
  
   ```xml  
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">  
       <PropertyGroup>  
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>  
       </PropertyGroup>  
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />  
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />  
   </Target>  
   ```  
  
7. Trovare ed eliminare il \<Import > gli elementi con attributi Project e Condition che fanno riferimento Microsoft.Diagnostics.Tracing.EventSource e Microsoft. applicationinsights, simile al seguente:  
  
   ```xml  
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />  
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />  
  
   ```  
  
8. Trovare il \<ItemGroup > che ha \<riferimento > gli elementi figlio ai pacchetti NuGet. Prendere nota dei pacchetti NuGet a cui viene fatto riferimento, perché queste informazioni saranno necessarie per un passaggio successivo. Una differenza significativa nel formato di progetto Windows 10 tra Visual Studio 2015 RC e Visual Studio 2015 RTM è rappresentata dal fatto che il formato RTM usa [NuGet](http://docs.nuget.org/) versione 3.  
  
    Rimuovere il \<ItemGroup > e tutti i relativi elementi figlio. Ad esempio, un progetto UWP creato con Visual Studio RC includerà i pacchetti NuGet seguenti che devono essere rimossi:  
  
   ```xml  
   <ItemGroup>  
       <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
         <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
       <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
         <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
       <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
         <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
       <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
       <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
     </ItemGroup>  
  
   ```  
  
9. Trovare il \<ItemGroup > elemento contenente un \<AppxManifest > elemento. Se è presente un \<None > elemento con un attributo di inclusione impostata su: Packages. config, eliminarlo. Aggiungere anche un \<None > elemento con un file di inclusione dell'attributo e impostarne il valore su: Project. JSON.  
  
10. Salvare le modifiche. Quindi, chiudere il file di progetto.  
  
11. Fare clic con il pulsante destro del mouse sul file di progetto in Esplora soluzioni e scegliere Ricarica progetto dal menu di scelta rapida. A questo punto, tutti i file nel progetto dovrebbero essere visualizzati in Esplora soluzioni.  
  
12. Selezionare il file ApplicationInsights.config in Esplora soluzioni e aprire le relative proprietà. Impostare la proprietà Azione di compilazione su "Contenuto" e la proprietà Copia in directory di output su "Copia se più recente".  
  
13. Aprire il file Package.appxmanifest nel progetto.  
  
    1.  Trovare il \<TargetDeviceFamily > elemento. Modificare gli attributi MinVersion e MaxVersionTested in modo che corrispondano alla versione della piattaforma UWP (Universal Windows Platform) installata, analogamente a quanto segue:  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  Salvare le modifiche.  
  
14. Usare Gestione NuGet per aggiungere i pacchetti eliminati nel passaggio precedente. Una differenza significativa nel formato di progetto Windows 10 tra Visual Studio 2015 RC e Visual Studio 2015 RTM è rappresentata dal fatto che il formato RTM usa [NuGet](http://docs.nuget.org/) versione 3.  
  
    Ora è possibile codificare, compilare ed eseguire il debug dell'app.  
  
    Se si hanno progetti di unit test per le app di Windows universale, è necessario seguire anche [questi passaggi](#MigrateUnitTest).  
  
###  <a name="RCUpdate10CPlusPlus"></a> Aggiornare i progetti C++ per usare la piattaforma più recente di Windows universale  
  
1.  Per trovare il tipo di piattaforma UWP (Universal Windows Platform) installato, aprire la cartella **\Program Files (x86)\Windows Kits\10\Platforms\UAP**, che contiene un elenco di cartelle per ogni piattaforma UWP installata. Il nome della cartella è la versione della piattaforma UWP installata. Ad esempio, in questo dispositivo Windows 10 è installata la versione 10.0.10240.0 della piattaforma UWP (Universal Windows Platform).  
  
     ![Aprire la cartella per visualizzare le versioni installate](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     È possibile installare più versioni della piattaforma UWP. Si consiglia di usare la versione più recente disponibile per l'app.  
  
2.  Aprire la soluzione che contiene l'app di Windows C++ universale. Fare clic con il pulsante destro del mouse sul file con estensione vcxproj del progetto e scegliere di scaricare il file di progetto. Dopo aver scaricato il progetto, fare di nuovo clic con il pulsante destro del mouse sul file di progetto e scegliere di modificarlo.  
  
     ![Scaricare il progetto, quindi modificare il file di progetto](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")  
  
3.  Trovare eventuali \<PropertyGroup > gli elementi che non contengono un attributo Condition ma contengono un \<ApplicationTypeRevision > elemento. Aggiornare il valore di ApplicationTypeRevision da 8.2 a 10.0. Aggiungere un \<WindowsTargetPlatformVersion > e un \<WindowsTargetPlatformMinVersion > elemento e impostare i relativi valori come il valore della versione (Universal Windows Platform) installato.  
  
     Aggiungere un \<EnableDotNetNativeCompatibleProfile > elemento e impostarne il valore su true se l'elemento non esiste già.  
  
     La dimensione predefinita per le risorse nelle app di Windows universale è 200. I progetti creati con risorse di Visual Studio 2015 RC includono con dimensione 100, è necessario aggiungere un \<UapDefaultAssetScale > elemento con un valore pari a 100 all'elemento PropertyGroup. Altre informazioni su [asset e scale](http://msdn.microsoft.com/library/jj679352.aspx).  
  
     Pertanto, questo \<PropertyGroup > elemento ora sarà simile al seguente:  
  
    ```xml  
    <PropertyGroup Label="Globals">  
        …  
        <MinimumVisualStudioVersion>14.0</MinimumVisualStudioVersion>  
        <ApplicationType>Windows Store</ApplicationType>  
        <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
        <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>  
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>  
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
        <UapDefaultAssetScale>100</UapDefaultAssetScale>  
      </PropertyGroup>  
  
    ```  
  
4.  Per ognuna delle restanti \<PropertyGroup > element, controllare se l'elemento ha un attributo Condition con una configurazione rilascio. Se accade, ma non contiene un \<UseDotNetNativeToolchain > elemento, quindi aggiungerne uno. Impostare il valore per il \<UseDotNetNativeToolchain > elemento su true, simile al seguente:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
  
    ```  
  
5.  È necessario aggiornare il \<EnableDotNetNativeCompatibleProfile > elemento e il \<UseDotNetNativeToolchain > elemento per abilitare .NET Native, ma .NET Native non è abilitato nei modelli C++.  
  
     Salvare le modifiche. Quindi, chiudere il file di progetto.  
  
6.  Fare clic con il pulsante destro del mouse sul file di progetto in Esplora soluzioni e scegliere Ricarica progetto dal menu di scelta rapida. A questo punto, tutti i file nel progetto dovrebbero essere visualizzati in Esplora soluzioni.  
  
7.  Aprire il file Package.appxmanifest nel progetto.  
  
    1.  Trovare il \<TargetDeviceFamily > elemento. Modificare gli attributi MinVersion e MaxVersionTested in modo che corrispondano alla versione della piattaforma UWP (Universal Windows Platform) installata, analogamente a quanto segue:  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  Salvare le modifiche.  
  
         Ora è possibile codificare, compilare ed eseguire il debug dell'app.  
  
         Se si hanno progetti di unit test per le app di Windows universale, è necessario seguire anche [questi passaggi](#MigrateUnitTest).  
  
##  <a name="MigrateUnitTest"></a> Modifiche richieste per i progetti di test unità esistenti per le app di Windows universale create con Visual Studio 2015 RC  
 Se sono stati creati progetti di unit test per app universali di Windows 10 con Visual Studio 2015 RC, è necessario apportare queste ulteriori modifiche ai file di progetto, per poter usare questi progetti di test con la versione più recente di Visual Studio 2015. Le modifiche richieste dipendono dal linguaggio usato per creare l'app:  
  
-   [App C# /VB](#UnitTestRCUpdate10CSharp)  
  
-   [App C++](#UnitTestRCUpdate10CPlusPlus)  
  
###  <a name="UnitTestRCUpdate10CSharp"></a> Aggiornare i progetti di test unità di C# /VB  
  
1. Con Visual Studio aprire la soluzione contenente il progetto di unit test C#/VB. Modificare il valore della \<OuttputType > elemento: AppContainerExe.  
  
   ```xml  
  
   <OutputType>AppContainerExe</OutputType>  
  
   ```  
  
2. Sostituire l'elemento \<EnableCoreRuntime > false\</EnableCoreRuntime > con l'elemento seguente:  
  
   ```xml  
  
   <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
  
   ```  
  
3. Rimuovere le righe seguenti:  
  
   ```xml  
  
   <PropertyGroup>  
       <AppXPackage>True</AppXPackage>  
       <AppxPackageIncludePrivateSymbols>true</AppxPackageIncludePrivateSymbols>  
    </PropertyGroup>  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
    <PlatformTarget>AnyCPU</PlatformTarget>  
    <DebugSymbols>true</DebugSymbols>  
    <DebugType>full</DebugType>  
    <Optimize>false</Optimize>  
    <OutputPath>bin\Debug\</OutputPath>  
    <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
    <ErrorReport>prompt</ErrorReport>  
    <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
       <PlatformTarget>AnyCPU</PlatformTarget>  
       <DebugType>pdbonly</DebugType>  
       <Optimize>true</Optimize>  
       <OutputPath>bin\Release\</OutputPath>  
       <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
       <ErrorReport>prompt</ErrorReport>  
       <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
  
   ```  
  
4. Aggiungere l'elemento \<UseDotNetNativeToolchain > true\</UseDotNetNativeToolchain > come elemento figlio a questi gruppi di proprietà:  
  
   ```xml  
  
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">  
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">  
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">  
  
   ```  
  
5. Eliminare gli oggetti seguenti \<ItemGroup > elementi:  
  
   ```xml  
  
   <ItemGroup>  
      <Compile Include="Properties\AssemblyInfo.cs" />  
      <Compile Include="UnitTest.cs" />  
   </ItemGroup>  
   <ItemGroup>  
      <AppxManifest Include="Package.appxmanifest">  
         <SubType>Designer</SubType>  
      </AppxManifest>  
      <None Include="packages.config" />  
      <None Include="UnitTestProject1_TemporaryKey.pfx" />  
   </ItemGroup>  
   <ItemGroup>  
      <Content Include="Properties\Default.rd.xml" />  
      <Content Include="Assets\Logo.scale-240.png" />  
      <Content Include="Assets\SmallLogo.scale-240.png" />  
      <Content Include="Assets\SplashScreen.scale-240.png" />  
      <Content Include="Assets\Square71x71Logo.scale-240.png" />  
      <Content Include="Assets\StoreLogo.scale-240.png" />  
      <Content Include="Assets\WideLogo.scale-240.png" />  
   </ItemGroup>  
  
   ```  
  
    Sostituirli con questi elementi:  
  
   ```xml  
  
   <ItemGroup>  
      <Compile Include="Properties\AssemblyInfo.cs" />  
      <Compile Include="UnitTestApp.xaml.cs">  
         <DependentUpon>UnitTestApp.xaml</DependentUpon>  
      </Compile>  
      <Compile Include="UnitTest.cs" />  
   </ItemGroup>  
   <ItemGroup>  
      <ApplicationDefinition Include="UnitTestApp.xaml">  
         <Generator>MSBuild:Compile</Generator>  
         <SubType>Designer</SubType>  
      </ApplicationDefinition>  
   </ItemGroup>  
   <ItemGroup>  
      <AppxManifest Include="Package.appxmanifest">  
         <SubType>Designer</SubType>  
      </AppxManifest>  
      <None Include="UnitTestProject1_TemporaryKey.pfx" />  
   </ItemGroup>  
   <ItemGroup>  
      <Content Include="Properties\UnitTestApp.rd.xml" />  
      <Content Include="Assets\LockScreenLogo.scale-200.png" />  
      <Content Include="Assets\SplashScreen.scale-200.png" />  
      <Content Include="Assets\Square150x150Logo.scale-200.png" />  
      <Content Include="Assets\Square44x44Logo.scale-200.png" />  
      <Content Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />  
      <Content Include="Assets\StoreLogo.png" />  
      <Content Include="Assets\Wide310x150Logo.scale-200.png" />  
   </ItemGroup>  
   ```  
  
6. Creare un nuovo progetto di unit test e copiare i file UnitTestApp.xaml e UnitTestApp.xaml.cs dal nuovo progetto al progetto di unit test esistente che si sta aggiornando.  
  
7. Copiare il file UnitTestApp.rd.xml dalla cartella Properties del nuovo progetto di unit test alla cartella Properties del progetto di unit test esistente che si sta aggiornando.  
  
8. Aprire il file Package.appxmanifest nel progetto. Eliminare quindi dal file gli elementi seguenti:  
  
   ```xml  
  
   <Applications>  
      <Application Id="vstest.executionengine.universal.App"  
            Executable="vstest.executionengine.appcontainer.uap.exe"  
            EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">  
         <uap:VisualElements  
            DisplayName="UnitTestProject1"  
            Square150x150Logo="Assets\Logo.png"  
            Square44x44Logo="Assets\SmallLogo.png"  
            Description="UnitTestProject1"  
            BackgroundColor="#464646">  
            <uap:SplashScreen Image="Assets\SplashScreen.png" />  
         </uap:VisualElements>  
      </Application>  
   </Applications>  
   <Capabilities>  
      <Capability Name="internetClientServer" />  
   </Capabilities>  
   ```  
  
    Sostituire gli elementi eliminati con gli elementi seguenti. Usare il valore appropriato per ProjectName in base al nome del progetto, al posto di UnitTestProject1 negli elementi seguenti:  
  
   ```xml  
  
   <Applications>  
      <Application Id="vstest.executionengine.universal.App"   
            Executable="$targetnametoken$.exe"  
            EntryPoint="UnitTestProject1.App">  
         <uap:VisualElements  
               DisplayName="UnitTestProject1"  
               Square150x150Logo="Assets\Square150x150Logo.png"  
               Square44x44Logo="Assets\Square44x44Logo.png"  
               Description="UnitTestProject1"  
               BackgroundColor="transparent">  
            <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>  
            <uap:SplashScreen Image="Assets\SplashScreen.png" />  
         </uap:VisualElements>  
      </Application>  
   </Applications>  
   <Capabilities>  
      <Capability Name="internetClient" />  
   </Capabilities>  
   ```  
  
   Ora è possibile eseguire gli unit test.  
  
###  <a name="UnitTestRCUpdate10CPlusPlus"></a> Aggiornare i progetti C++ per usare la piattaforma più recente di Windows universale  
  
1.  Con Visual Studio aprire la soluzione contenente il progetto di unit test C++. Rimuovere gli elementi seguenti:  
  
    ```xml  
  
    <TestApplication>true</TestApplication>  
    <AppxPackage>True</AppxPackage>  
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>  
    <EnableCoreRuntime>false</EnableCoreRuntime>  
  
    ```  
  
2.  Aggiungere il codice seguente \<ProjectConfiguration > elementi di sotto di questo elemento \<ItemGroup Label = "ProjectConfigurations" > Se non sono già nel file:  
  
    ```xml  
  
    <ProjectConfiguration Include="Debug|x64">  
       <Configuration>Debug</Configuration>  
       <Platform>x64</Platform>  
    </ProjectConfiguration>  
    <ProjectConfiguration Include="Release|x64">  
       <Configuration>Release</Configuration>  
       <Platform>x64</Platform>  
    </ProjectConfiguration>  
  
    ```  
  
3.  Sostituire ogni occorrenza di questo elemento:  
  
    ```xml  
  
    <ConfigurationType>DynamicLibrary</ConfigurationType>  
  
    ```  
  
     Con il seguente:  
  
    ```xml  
  
    <ConfigurationType>Application</ConfigurationType>  
  
    ```  
  
4.  Aggiungere queste \<PropertyGroup > elementi se non sono già nel file:  
  
    ```xml  
  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'" Label="Configuration">  
       <ConfigurationType>Application</ConfigurationType>  
       <UseDebugLibraries>true</UseDebugLibraries>  
       <PlatformToolset>v140</PlatformToolset>  
    </PropertyGroup>  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'" Label="Configuration">  
       <ConfigurationType>Application</ConfigurationType>  
       <UseDebugLibraries>false</UseDebugLibraries>  
       <WholeProgramOptimization>true</WholeProgramOptimization>  
       <PlatformToolset>v140</PlatformToolset>  
       <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
    </PropertyGroup>  
  
    ```  
  
5.  Sostituire ogni occorrenza di questo elemento:  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
    ```  
  
     Con il seguente:  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
  
    ```  
  
6.  Sostituire ogni occorrenza di questo elemento:  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
     Con il seguente:  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
7.  Aggiungere queste \<ItemDefinitionGroup > elementi nella sezione che già contiene altri \<ItemDefinitionGroup > elementi:  
  
    ```xml  
  
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">  
       <ClCompile>  
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>  
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>  
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%     (AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
       </ClCompile>  
    <Link>  
       <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
    </Link>  
    </ItemDefinitionGroup>  
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'">  
       <ClCompile>  
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>  
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>  
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
       </ClCompile>  
       <Link>  
          <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
       </Link>  
    </ItemDefinitionGroup>  
  
    ```  
  
8.  Eliminare gli oggetti seguenti \< ItemGroup > elemento:  
  
    ```xml  
  
    <ItemGroup>  
       <Image Include="Assets\Logo.scale-100.png" />  
       <Image Include="Assets\SmallLogo.scale-100.png" />  
       <Image Include="Assets\StoreLogo.scale-100.png" />  
       <Image Include="Assets\SplashScreen.scale-100.png" />  
       <Image Include="Assets\WideLogo.scale-100.png" />  
    </ItemGroup>  
  
    ```  
  
     Sostituirlo con questo \<ItemGroup > elemento:  
  
    ```xml  
  
    <ItemGroup>  
       <Image Include="Assets\LockScreenLogo.scale-200.png" />  
       <Image Include="Assets\SplashScreen.scale-200.png" />  
       <Image Include="Assets\Square44x44Logo.scale-200.png" />  
       <Image Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />  
       <Image Include="Assets\Square150x150Logo.scale-200.png" />  
       <Image Include="Assets\StoreLogo.png" />  
       <Image Include="Assets\Wide310x150Logo.scale-200.png" />  
    </ItemGroup>  
  
    ```  
  
9. Eliminare gli oggetti seguenti \< ItemGroup > elemento:  
  
    ```xml  
  
    <ItemGroup>  
       <ClInclude Include="pch.h" />  
    </ItemGroup>  
    ```  
  
     Sostituirlo con questi \<ItemGroup > elementi:  
  
    ```xml  
  
    <ItemGroup>  
       <ClInclude Include="pch.h" />  
       <ClInclude Include="UnitTestApp.xaml.h">  
          <DependentUpon>UnitTestApp.xaml</DependentUpon>  
       </ClInclude>  
    </ItemGroup>  
    <ItemGroup>  
       <ApplicationDefinition Include="UnitTestApp.xaml">  
          <SubType>Designer</SubType>  
       </ApplicationDefinition>  
    </ItemGroup>  
  
    ```  
  
10. Eliminare l'elemento seguente:  
  
    ```xml  
    <ClCompile Include="UnitTest.cpp"/>  
    ```  
  
     Sostituirlo con questi \<CICompile > elementi:  
  
    ```xml  
  
    <ClCompile Include="UnitTestApp.xaml.cpp">  
       <DependentUpon>UnitTestApp.xaml</DependentUpon>  
    </ClCompile>  
    <ClCompile Include="UnitTest.cpp"/>  
  
    ```  
  
11. Aggiungere questo elemento:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />  
    ```  
  
     Sopra l'elemento seguente nel file:  
  
    ```xml  
  
    <ItemGroup>  
       <Xml Include="UnitTestApp.rd.xml" />  
    </ItemGroup>  
    ```  
  
12. Creare un nuovo progetto di unit test C++ e copiare i file UnitTestApp.xaml, UnitTestApp.xaml.cpp, UnitTestApp.xaml.h e UnitTestApp.rd.xml da tale progetto al progetto esistente che si sta aggiornando.  
  
13. Aprire il file Package.appxmanifest nel progetto. Eliminare quindi dal file gli elementi seguenti:  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"  
             Executable="vstest.executionengine.appcontainer.uap.exe"  
             EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">  
          <uap:VisualElements  
             DisplayName="UnitTestProject1"  
             Square150x150Logo="Assets\Logo.png"  
             Square44x44Logo="Assets\SmallLogo.png"  
             Description="UnitTestProject1"  
             BackgroundColor="#464646">  
             <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClientServer" />  
    </Capabilities>  
  
    ```  
  
     Sostituire gli elementi eliminati con gli elementi seguenti. Usare il valore appropriato per ProjectName in base al nome del progetto, al posto di UnitTestProject1 negli elementi seguenti:  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"   
                Executable="$targetnametoken$.exe"  
                EntryPoint="UnitTestProject1.App">  
          <uap:VisualElements  
                DisplayName="UnitTestProject1"  
                Square150x150Logo="Assets\Square150x150Logo.png"  
                Square44x44Logo="Assets\Square44x44Logo.png"  
                Description="UnitTestProject1"  
                BackgroundColor="transparent">  
                <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>  
                <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClient" />  
    </Capabilities>  
  
    ```