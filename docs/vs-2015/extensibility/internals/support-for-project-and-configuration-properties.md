---
title: Supporto per il progetto e le proprietà di configurazione | Microsoft Docs
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
ms.openlocfilehash: ae770d36c0f030a060eccfe86bc3939dad9622d8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691877"
---
# <a name="support-for-project-and-configuration-properties"></a>Supporto per le proprietà di configurazione e del progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il **delle proprietà** finestra nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente di sviluppo integrato (IDE) può visualizzare le proprietà di configurazione e progetto. È possibile fornire una pagina delle proprietà per il proprio tipo di progetto in modo che l'utente può impostare le proprietà dell'applicazione.  
  
 Selezionando un nodo del progetto in **Esplora soluzioni** e quindi facendo clic su **delle proprietà** sul **progetto** menu, è possibile aprire una finestra di dialogo che include configurazione e progetto proprietà. Nelle [!INCLUDE[csprcs](../../includes/csprcs-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]e tipi derivati da questi linguaggi, questa finestra di dialogo viene visualizzata come una pagina a schede nel progetto di [General, Environment, Options Dialog Box](../../ide/reference/general-environment-options-dialog-box.md). Per altre informazioni, vedere [non incluso nella Build: Procedura dettagliata: Esposizione di proprietà di configurazione e progetto (C#)](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Il Framework di pacchetto gestito per progetti (MPFProj) fornisce classi helper per la creazione e la gestione di nuovo sistema di progetto. È possibile trovare l'origine istruzioni di compilazione e codice in [MPF per i progetti - Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Persistenza del progetto e le proprietà di configurazione  
 Le proprietà di configurazione e progetto sono persistenti in un file di progetto che ha un'estensione di file associato al tipo di progetto, ad esempio, con estensione csproj, vbproj e .myproj. Progetti di linguaggio usano in genere un file di modello per generare il file di progetto. Tuttavia, esistono effettivamente diversi modi per associare tipi di progetto e modelli. Per altre informazioni, vedere [NIB: Modelli di Visual Studio](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041) e [Descrizione Directory del modello (. File VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Le proprietà di configurazione e progetto vengono create aggiungendo elementi al file del modello. Queste proprietà sono quindi disponibili per eventuali progetti creati con il tipo di progetto che usa questo modello. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] progetti e MPFProj usano entrambi il [non incluso nella Build: Cenni preliminari su MSBuild](https://msdn.microsoft.com/b588fd73-a45b-4706-908f-cc131bccfbde) dello schema per i file di modello. Questi file è presente una sezione PropertyGroup per ogni configurazione. Le proprietà dei progetti vengono in genere rese persistenti nella prima sezione PropertyGroup, che dispone di un argomento Configuration impostato su una stringa null.  
  
 Il codice seguente mostra l'inizio di un file di progetto MSBuild base.  
  
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
  
 In questo file di progetto `<Name>` e `<SchemaVersion>` sono di proprietà del progetto e `<Optimize>` è una proprietà di configurazione.  
  
 È responsabilità del progetto per rendere persistenti le proprietà di progetto e la configurazione del file di progetto.  
  
> [!NOTE]
> Un progetto può ottimizzare la persistenza per salvare in modo permanente solo valori di proprietà che differiscono dai valori predefiniti.  
  
## <a name="support-for-project-and-configuration-properties"></a>Supporto per le proprietà di configurazione e del progetto  
 Il `Microsoft.VisualStudio.Package.SettingsPage` classe implementa le pagine delle proprietà di configurazione e progetto. L'implementazione predefinita di `SettingsPage` offre proprietà pubbliche per un utente in una griglia delle proprietà generiche. Il `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` metodo consente di selezionare le classi derivate da `SettingsPage` per griglie di proprietà di progetto. Il `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` metodo consente di selezionare le classi derivate da `SettingsPage` per griglie di proprietà di configurazione. Il tipo di progetto deve eseguire l'override di questi metodi per selezionare le pagine delle proprietà appropriata.  
  
 Il `SettingsPage` classi e `Microsoft.VisualStudio.Package.ProjectNode` classe offrono questi metodi per rendere persistenti le proprietà di configurazione e progetto:  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` e `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` rendere persistenti le proprietà del progetto.  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` e `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` rendere persistenti le proprietà di configurazione.  
  
  > [!NOTE]
  > Le implementazioni del `Microsoft.VisualStudio.Package.SettingsPage` e `Microsoft.VisualStudio.Package.ProjectNode` classi di uso di `Microsoft.Build.BuildEngine` metodi (MSBuild) per ottenere e impostare le proprietà di progetto e la configurazione dal file di progetto.  
  
  La classe di derivazione `SettingsPage` deve implementare `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` e `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` per rendere persistenti le proprietà di configurazione di progetto o del file di progetto.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute e il percorso del Registro di sistema  
 Le classi derivate da `SettingsPage` sono progettati per essere condivisi tra pacchetti VSPackage. Per rendere possibile per un pacchetto VSPackage creare una classe derivata da `SettingsPage`, aggiungere un' `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` a una classe derivata da `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs#1)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb#1)]  
  
 Il pacchetto VSPackage a cui è associato l'attributo non è importante. Quando un pacchetto VSPackage è registrato con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], viene registrato l'id di classe (CLSID) di qualsiasi oggetto che può essere creato in modo che una chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> può essere creato.  
  
 Il percorso del Registro di sistema di un oggetto che può essere creato è determinato dalla combinazione <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la parola, CLSID e il guid del tipo di oggetto. Se `MyProjectPropertyPage` classe ha un guid di {3c693da2-5bca-49b3-bd95-ffe0a39dd723} e il UserRegistryRoot è HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, quindi il percorso del Registro di sistema sarebbe HKEY_CURRENT_USER\Software\Microsoft\VisualStudio \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Progetto e gli attributi delle proprietà di configurazione e il Layout  
 Il <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, e <xref:System.ComponentModel.DescriptionAttribute> attributi determinano il layout, l'assegnazione di etichette e descrizione delle proprietà di configurazione e progetto in una pagina delle proprietà generiche. Questi attributi determinano la categoria, il nome visualizzato e descrizione dell'opzione, rispettivamente.  
  
> [!NOTE]
> Attributi equivalenti, SRCategory, LocDisplayName e SRDescription, usare le risorse stringa per la localizzazione e sono definiti in [MPF per i progetti - Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Si consideri il frammento di codice riportato di seguito.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs#2)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb#2)]  
  
 Il `MyConfigProp` proprietà di configurazione viene visualizzata nella pagina delle proprietà di configurazione come **proprietà di configurazione My** nella categoria **My Category**. Se l'opzione è selezionata, la descrizione **My Description**, viene visualizzato nel Pannello di descrizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Non incluso nella Build: Procedura dettagliata: Esposizione di proprietà di configurazione e progetto (C#)](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Aggiunta e rimozione di pagine delle proprietà](../../extensibility/adding-and-removing-property-pages.md)   
 [Lo stato del VSPackage](../../misc/vspackage-state.md)   
 [Progetti](../../extensibility/internals/projects.md)   
 [NIB: Modelli di Visual Studio](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041)   
 [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
