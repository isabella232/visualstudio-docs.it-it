---
title: Supporto per le proprietà di progetto e di configurazione . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c21d552e26add3a5159febd666c1f60573697535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704894"
---
# <a name="support-for-project-and-configuration-properties"></a>Supporto per le proprietà di configurazione e del progetto
La **Properties** finestra Proprietà [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nell'ambiente di sviluppo integrato (IDE) può visualizzare le proprietà di progetto e configurazione. È possibile fornire una pagina delle proprietà per il proprio tipo di progetto in modo che l'utente possa impostare le proprietà per l'applicazione.

 Selezionando un nodo di progetto in **Esplora soluzioni** e quindi scegliendo **proprietà** dal menu **progetto** , è possibile aprire una finestra di dialogo che include le proprietà di progetto e di configurazione. In [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]e , e i tipi di progetto derivati da questi linguaggi, questa finestra di dialogo viene visualizzata come pagina a schede in [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md). Per altre informazioni, vedere [Non nella compilazione: Procedura dettagliata: Esposizione delle proprietà](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)di progetto e di configurazione (C ) .

 Il Framework di pacchetto gestito per i progetti (MPFProj) fornisce classi helper per la creazione e la gestione di nuovo sistema di progetto. Il codice sorgente e le istruzioni di compilazione sono disponibili in [MPF for Projects - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Persistenza delle proprietà di progetto e configurazionePersistence of Project and Configuration Properties
 Le proprietà di progetto e di configurazione vengono mantenute in un file di progetto con qualsiasi estensione di file associata al tipo di progetto, ad esempio csproj, vbproj e .myproj. I progetti di linguaggio utilizzano in genere un file modello per generare il file di progetto. Tuttavia, esistono in realtà diversi modi per associare tipi di progetto e modelli. Per ulteriori informazioni, vedere [Descrizione della directory dei modelli (. Vsdir) Files](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Le proprietà di progetto e di configurazione vengono create aggiungendo elementi al file modello. Queste proprietà sono quindi disponibili per qualsiasi progetto creato utilizzando il tipo di progetto che utilizza questo modello. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]progetti e MPFProj utilizzano entrambi lo schema [Not in Build: MSBuild Overview](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) per i file di modello. Questi file hanno una sezione PropertyGroup per ogni configurazione. Le proprietà dei progetti vengono in genere mantenute nella prima sezione PropertyGroup, con un argomento Configuration impostato su una stringa null.

 Il codice seguente mostra l'inizio di un file di progetto MSBuild di base.

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

 In questo file `<Name>` `<SchemaVersion>` di progetto, `<Optimize>` e sono proprietà del progetto, ed è una proprietà di configurazione.

 È responsabilità del progetto rendere persistente le proprietà di progetto e di configurazione del file di progetto.

> [!NOTE]
> Un progetto può ottimizzare la persistenza persistente solo i valori di proprietà che differiscono dai valori predefiniti.

## <a name="support-for-project-and-configuration-properties"></a>Supporto per le proprietà di configurazione e del progetto
 La `Microsoft.VisualStudio.Package.SettingsPage` classe implementa le pagine delle proprietà di configurazione e di progetto. L'implementazione `SettingsPage` predefinita di offre proprietà pubbliche a un utente in una griglia delle proprietà generica. Il `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` metodo seleziona le `SettingsPage` classi derivate da per le griglie delle proprietà del progetto. Il `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` metodo seleziona le `SettingsPage` classi derivate da per le griglie delle proprietà di configurazione. Il tipo di progetto deve eseguire l'override di questi metodi per selezionare le pagine delle proprietà appropriate.

 La `SettingsPage` classe `Microsoft.VisualStudio.Package.ProjectNode` e la classe offrono questi metodi per rendere persistenti le proprietà di progetto e di configurazione:The class and the class offer these methods to persist project and configuration properties:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`e `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` rendere persistenti le proprietà del progetto.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`e `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` rendere persistenti le proprietà di configurazione.

  > [!NOTE]
  > Le implementazioni `Microsoft.VisualStudio.Package.SettingsPage` delle `Microsoft.VisualStudio.Package.ProjectNode` classi `Microsoft.Build.BuildEngine` e utilizzano i metodi (MSBuild) per ottenere e impostare le proprietà di progetto e di configurazione dal file di progetto.

  La classe da `SettingsPage` cui `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` si deriva deve implementare e per rendere persistenti le proprietà di progetto o di configurazione del file di progetto.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute e percorso del Registro di sistema
 Le classi `SettingsPage` derivate da sono progettate per essere condivise tra VSPackage.Classes derived from are designed to be shared across VSPackages. Per rendere possibile per un VSPackage creare `SettingsPage`una `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` classe derivata `Microsoft.VisualStudio.Shell.Package`da , aggiungere un a a una classe derivata da .

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 Il pacchetto VSPackage a cui è associato l'attributo non è importante. Quando un vsPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]viene registrato con , l'ID di classe (CLSID) di <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> qualsiasi oggetto che può essere creato viene registrato in modo che una chiamata a possa crearlo.

 Il percorso del Registro di sistema di <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>un oggetto che può essere creato viene determinato combinando , la parola , CLSID e il guid del tipo di oggetto. Se `MyProjectPropertyPage` la classe dispone di un guid di 3c693da2-5bca-49b3-bd95-ffe0a39dd723 e UserRegistryRoot è HKEY_CURRENT_USER Software , Software , Microsoft VisualStudio , 8.0Exp, e UserRegistryRoot\\è HKEY_CURRENT_USER Software , Microsoft VisualStudio , 8.0Exp, quindi il percorso del Registro di sistema sarà HKEY_CURRENT_USER .

## <a name="project-and-configuration-property-attributes-and-layout"></a>Attributi e layout delle proprietà di progetto e configurazioneProject and Configuration Property Attributes and Layout
 Gli <xref:System.ComponentModel.CategoryAttribute> <xref:System.ComponentModel.DisplayNameAttribute>attributi <xref:System.ComponentModel.DescriptionAttribute> , e determinano il layout, l'etichettatura e la descrizione delle proprietà di progetto e di configurazione in una pagina delle proprietà generica. Questi attributi determinano rispettivamente la categoria, il nome visualizzato e la descrizione dell'opzione.

> [!NOTE]
> Gli attributi equivalenti, SRCategory, LocDisplayName e SRDescription, utilizzano risorse stringa per la localizzazione e sono definiti in [MPF per progetti - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Si consideri il frammento di codice riportato di seguito.

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 La `MyConfigProp` proprietà di configurazione viene visualizzata nella pagina delle proprietà di configurazione come **Proprietà di configurazione personale** nella categoria Categoria My **Category**. Se l'opzione è selezionata, la descrizione, **Descrizione**personale , viene visualizzata nel riquadro della descrizione.

## <a name="see-also"></a>Vedere anche
- [Aggiunta e rimozione di pagine delle proprietà](../../extensibility/adding-and-removing-property-pages.md)
- [Progetti](../../extensibility/internals/projects.md)
- [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
