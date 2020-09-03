---
title: Supporto per le proprietà di progetto e configurazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b03bc04b1d5b87219110aa65bee53c4a4a8f77e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "74301074"
---
# <a name="support-for-project-and-configuration-properties"></a>Supporto per le proprietà di configurazione e del progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nella finestra **Proprietà** del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrated Development Environment (IDE) è possibile visualizzare le proprietà di progetto e di configurazione. È possibile specificare una pagina delle proprietà per il proprio tipo di progetto in modo che l'utente possa impostare le proprietà per l'applicazione.  
  
 Selezionando un nodo del progetto in **Esplora soluzioni** e scegliendo **Proprietà** dal menu **progetto** , è possibile aprire una finestra di dialogo che include proprietà di progetto e di configurazione. In [!INCLUDE[csprcs](../../includes/csprcs-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , e i tipi di progetto derivati da questi linguaggi, questa finestra di dialogo viene visualizzata come pagina a schede nella finestra di [dialogo generale, ambiente, opzioni](../../ide/reference/general-environment-options-dialog-box.md). Per ulteriori informazioni, vedere [not in Build: Walkthrough: Esponeting Project and Configuration Properties (C#)](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Il Framework di pacchetto gestito per i progetti (MPFProj) fornisce classi helper per la creazione e la gestione di un nuovo sistema di progetto. È possibile trovare il codice sorgente e le istruzioni di compilazione in [MPF for Projects-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Persistenza delle proprietà di progetto e configurazione  
 Le proprietà di progetto e configurazione sono rese disponibili in un file di progetto con estensione di file associata al tipo di progetto, ad esempio. csproj,. vbproj e. PROG. I progetti di linguaggio usano in genere un file modello per generare il file di progetto. Tuttavia, esistono in realtà diversi modi per associare i tipi di progetto e i modelli. Per ulteriori informazioni, vedere la descrizione del modello di [Visual Studio](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041) e della directory dei modelli [(. File VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Le proprietà di progetto e di configurazione vengono create aggiungendo elementi al file modello. Queste proprietà sono quindi disponibili per tutti i progetti creati usando il tipo di progetto che usa il modello. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] i progetti e MPFProj usano entrambi lo schema di [Panoramica not in Build: MSBuild](https://msdn.microsoft.com/b588fd73-a45b-4706-908f-cc131bccfbde) per i file modello. Questi file hanno una sezione PropertyGroup per ogni configurazione. Le proprietà dei progetti vengono in genere rese permanente nella prima sezione PropertyGroup, che include un argomento di configurazione impostato su una stringa null.  
  
 Il codice seguente illustra l'inizio di un file di progetto MSBuild di base.  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 In questo file di progetto `<Name>` e `<SchemaVersion>` sono proprietà del progetto e `<Optimize>` è una proprietà di configurazione.  
  
 È responsabilità del progetto salvare in modo permanente il progetto e le proprietà di configurazione del file di progetto.  
  
> [!NOTE]
> Un progetto può ottimizzare la persistenza salvando in modo permanente solo i valori delle proprietà che differiscono dai valori predefiniti.  
  
## <a name="support-for-project-and-configuration-properties"></a>Supporto per le proprietà di configurazione e del progetto  
 La `Microsoft.VisualStudio.Package.SettingsPage` classe implementa le pagine delle proprietà di progetto e di configurazione. L'implementazione predefinita di `SettingsPage` offre proprietà pubbliche a un utente in una griglia di proprietà generica. Il `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` metodo seleziona le classi derivate da `SettingsPage` per le griglie delle proprietà del progetto. Il `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` metodo seleziona le classi derivate da `SettingsPage` per le griglie delle proprietà di configurazione. Il tipo di progetto deve eseguire l'override di questi metodi per selezionare le pagine delle proprietà appropriate.  
  
 La `SettingsPage` classe e la `Microsoft.VisualStudio.Package.ProjectNode` classe offrono questi metodi per salvare in modo permanente le proprietà di progetto e di configurazione:  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` e rendono `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` permanente le proprietà del progetto.  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` e rendono `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` permanente le proprietà di configurazione.  
  
  > [!NOTE]
  > Le implementazioni delle `Microsoft.VisualStudio.Package.SettingsPage` classi e `Microsoft.VisualStudio.Package.ProjectNode` usano i `Microsoft.Build.BuildEngine` metodi (MSBuild) per ottenere e impostare le proprietà di progetto e configurazione dal file di progetto.  
  
  La classe da cui deriva `SettingsPage` deve implementare `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` e `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` per rendere permanente le proprietà del progetto o di configurazione del file di progetto.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute e percorso del registro di sistema  
 Le classi derivate da `SettingsPage` sono progettate per essere condivise tra i pacchetti VSPackage. Per consentire a un VSPackage di creare una classe derivata da `SettingsPage` , aggiungere un oggetto `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` a una classe derivata da `Microsoft.VisualStudio.Shell.Package` .  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs#1)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb#1)]  
  
 Il VSPackage a cui è associato l'attributo non è importante. Quando un pacchetto VSPackage viene registrato con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , viene registrato l'ID di classe (CLSID) di qualsiasi oggetto che può essere creato, in modo che una chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> possa crearla.  
  
 Il percorso del registro di sistema di un oggetto che è possibile creare viene determinato combinando <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> , la parola, il CLSID e il GUID del tipo di oggetto. Se `MyProjectPropertyPage` la classe ha un GUID di {3c693da2-5bca-49B3-bd95-ffe0a39dd723} e UserRegistryRoot è HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp, il percorso del registro di sistema sarà HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0exp\clsid \\ {3c693da2-5bca-49B3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Layout e attributi delle proprietà di progetto e configurazione  
 Gli <xref:System.ComponentModel.CategoryAttribute> <xref:System.ComponentModel.DisplayNameAttribute> attributi, e <xref:System.ComponentModel.DescriptionAttribute> determinano il layout, l'assegnazione di etichette e la descrizione delle proprietà di progetto e di configurazione in una pagina delle proprietà generica. Questi attributi determinano rispettivamente la categoria, il nome visualizzato e la descrizione dell'opzione.  
  
> [!NOTE]
> Gli attributi equivalenti, SRCategory, LocDisplayName e SRDescription, usano le risorse di stringa per la localizzazione e sono definiti in [MPF per i progetti-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
 Si consideri il frammento di codice riportato di seguito.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs#2)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb#2)]  
  
 La `MyConfigProp` proprietà di configurazione viene visualizzata nella pagina delle proprietà configurazione come **Proprietà** di configurazione nella categoria, **categoria**. Se l'opzione è selezionata, **la descrizione viene**visualizzata nel pannello Descrizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Not in Build: procedura dettagliata: esposizione delle proprietà di progetto e di configurazione (C#)](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Aggiunta e rimozione di pagine delle proprietà](../../extensibility/adding-and-removing-property-pages.md)   
 [Stato VSPackage](../../misc/vspackage-state.md)   
 [Progetti](../../extensibility/internals/projects.md)   
 [PENNINI: modelli di Visual Studio](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041)   
 [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
