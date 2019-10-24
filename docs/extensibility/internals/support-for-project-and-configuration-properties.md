---
title: Supporto per le proprietà di progetto e configurazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf0581eee4fade779d89143f4633f1b87d3ce0f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723163"
---
# <a name="support-for-project-and-configuration-properties"></a>Supporto per le proprietà di configurazione e del progetto
La finestra **Proprietà** nel Integrated Development Environment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) può visualizzare le proprietà di progetto e di configurazione. È possibile specificare una pagina delle proprietà per il proprio tipo di progetto in modo che l'utente possa impostare le proprietà per l'applicazione.

 Selezionando un nodo del progetto in **Esplora soluzioni** e scegliendo **Proprietà** dal menu **progetto** , è possibile aprire una finestra di dialogo che include proprietà di progetto e di configurazione. In [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e tipi di progetto derivati da questi linguaggi, questa finestra di dialogo viene visualizzata come pagina a schede nella finestra di [dialogo generale, ambiente, opzioni](../../ide/reference/general-environment-options-dialog-box.md). Per ulteriori informazioni, vedere [not in Build: Walkthrough: Esponeting Project and Configuration PropertiesC#()](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).

 Il Framework di pacchetto gestito per i progetti (MPFProj) fornisce classi helper per la creazione e la gestione di un nuovo sistema di progetto. È possibile trovare il codice sorgente e le istruzioni di compilazione in [MPF for Projects-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Persistenza delle proprietà di progetto e configurazione
 Le proprietà di progetto e di configurazione sono rese permanente in un file di progetto con qualsiasi estensione di file associata al tipo di progetto, ad esempio. csproj,. vbproj e. PROG. I progetti di linguaggio usano in genere un file modello per generare il file di progetto. Tuttavia, esistono in realtà diversi modi per associare i tipi di progetto e i modelli. Per ulteriori informazioni, vedere [Descrizione della directory dei modelli (. File VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Le proprietà di progetto e di configurazione vengono create aggiungendo elementi al file modello. Queste proprietà sono quindi disponibili per tutti i progetti creati usando il tipo di progetto che usa il modello. i progetti [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e MPFProj usano entrambi lo schema di [Panoramica not in Build: MSBuild](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) per i file modello. Questi file hanno una sezione PropertyGroup per ogni configurazione. Le proprietà dei progetti vengono in genere rese permanente nella prima sezione PropertyGroup, che include un argomento di configurazione impostato su una stringa null.

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
 La classe `Microsoft.VisualStudio.Package.SettingsPage` implementa le pagine delle proprietà di progetto e di configurazione. L'implementazione predefinita di `SettingsPage` offre proprietà pubbliche a un utente in una griglia di proprietà generica. Il metodo `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` seleziona le classi derivate da `SettingsPage` per le griglie delle proprietà del progetto. Il metodo `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` seleziona le classi derivate da `SettingsPage` per le griglie delle proprietà di configurazione. Il tipo di progetto deve eseguire l'override di questi metodi per selezionare le pagine delle proprietà appropriate.

 La classe `SettingsPage` e la classe `Microsoft.VisualStudio.Package.ProjectNode` offrono questi metodi per salvare in modo permanente le proprietà di progetto e di configurazione:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` e `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` salvare le proprietà del progetto.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` e `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` rende permanente le proprietà di configurazione.

  > [!NOTE]
  > Le implementazioni delle classi `Microsoft.VisualStudio.Package.SettingsPage` e `Microsoft.VisualStudio.Package.ProjectNode` utilizzano i metodi `Microsoft.Build.BuildEngine` (MSBuild) per ottenere e impostare le proprietà di progetto e di configurazione dal file di progetto.

  La classe derivata da `SettingsPage` deve implementare `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` e `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` per rendere permanente le proprietà del progetto o di configurazione del file di progetto.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute e percorso del registro di sistema
 Le classi derivate da `SettingsPage` sono progettate per essere condivise tra i pacchetti VSPackage. Per consentire a un VSPackage di creare una classe derivata da `SettingsPage`, aggiungere una `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` a una classe derivata da `Microsoft.VisualStudio.Shell.Package`.

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 Il VSPackage a cui è associato l'attributo non è importante. Quando un pacchetto VSPackage viene registrato con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], viene registrato l'ID di classe (CLSID) di qualsiasi oggetto che può essere creato in modo che una chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> possa crearla.

 Il percorso del registro di sistema di un oggetto che è possibile creare viene determinato combinando <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la parola, il CLSID e il GUID del tipo di oggetto. Se `MyProjectPropertyPage` classe ha un GUID di {3c693da2-5bca-49B3-bd95-ffe0a39dd723} e UserRegistryRoot è HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, il percorso del registro di sistema sarà HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\ 8.0 Exp \ CLSID \\ {3c693da2-5bca-49B3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Layout e attributi delle proprietà di progetto e configurazione
 Gli attributi <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute> e <xref:System.ComponentModel.DescriptionAttribute> determinano il layout, l'assegnazione di etichette e la descrizione delle proprietà di progetto e di configurazione in una pagina delle proprietà generica. Questi attributi determinano rispettivamente la categoria, il nome visualizzato e la descrizione dell'opzione.

> [!NOTE]
> Gli attributi equivalenti, SRCategory, LocDisplayName e SRDescription, usano le risorse di stringa per la localizzazione e sono definiti in [MPF per i progetti-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Si consideri il frammento di codice riportato di seguito.

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 La proprietà di configurazione `MyConfigProp` viene visualizzata nella pagina delle proprietà configurazione come **Proprietà** di configurazione nella categoria, **categoria**. Se l'opzione è selezionata, **la descrizione viene**visualizzata nel pannello Descrizione.

## <a name="see-also"></a>Vedere anche
- [Aggiunta e rimozione di pagine delle proprietà](../../extensibility/adding-and-removing-property-pages.md)
- [Progetti](../../extensibility/internals/projects.md)
- [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
