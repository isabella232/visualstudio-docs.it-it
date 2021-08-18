---
title: Supporto per Project proprietà di configurazione | Microsoft Docs
description: Informazioni su come fornire una pagina delle proprietà per il proprio tipo di progetto nell'IDE di Visual Studio, che può visualizzare le proprietà estese del progetto e della configurazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5d29e1d4b280454f8f5724dce207a6cf527b2c0d79b95b8ce799b88c8a7bf34e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121337786"
---
# <a name="support-for-project-and-configuration-properties"></a>Supporto per le proprietà di configurazione e del progetto
La **finestra Proprietà** nell'ambiente di sviluppo integrato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) può visualizzare le proprietà di progetto e configurazione. È possibile specificare una pagina delle proprietà per il proprio tipo di progetto in modo che l'utente possa impostare le proprietà per l'applicazione.

 Selezionando un nodo di progetto in **Esplora soluzioni** e quindi scegliendo Proprietà dal menu **Project,** è possibile aprire una finestra di dialogo che include le proprietà di progetto e configurazione.  In e e nei tipi di progetto derivati da questi linguaggi, questa finestra di dialogo viene visualizzata come pagina a schede nella finestra di dialogo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [Generale, Ambiente, Opzioni](../../ide/reference/general-environment-options-dialog-box.md). Per altre informazioni, vedere [Not in Build: Walkthrough: Exposing Project and Configuration Properties (C#) .](/previous-versions/bb166517(v=vs.100))

 Managed Package Framework for Projects (MPFProj) fornisce classi helper per la creazione e la gestione di un nuovo sistema di progetto. È possibile trovare il codice sorgente e le istruzioni di compilazione in [MPF for Projects - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Persistenza delle Project e di configurazione
 Project e le proprietà di configurazione vengono rese persistenti in un file di progetto con qualsiasi estensione di file associata al tipo di progetto, ad esempio csproj, vbproj e myproj. I progetti di linguaggio usano in genere un file modello per generare il file di progetto. Esistono tuttavia diversi modi per associare tipi di progetto e modelli. Per altre informazioni, vedere [Descrizione della directory dei modelli (. Vsdir) File](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Project e le proprietà di configurazione vengono create aggiungendo elementi al file modello. Queste proprietà sono quindi disponibili per qualsiasi progetto creato usando il tipo di progetto che usa questo modello. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]I progetti e MPFProj usano entrambi lo schema [Not in Build: MSBuild Overview](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) per i file modello. Questi file hanno una sezione PropertyGroup per ogni configurazione. Le proprietà dei progetti vengono in genere rese persistenti nella prima sezione PropertyGroup, che ha un argomento Configuration impostato su una stringa Null.

 Il codice seguente illustra l'inizio di un file di MSBuild di base.

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

 In questo file di progetto `<Name>` e sono proprietà del progetto ed è una proprietà di `<SchemaVersion>` `<Optimize>` configurazione.

 È responsabilità del progetto rendere persistenti le proprietà di progetto e di configurazione del file di progetto.

> [!NOTE]
> Un progetto può ottimizzare la persistenza tramite la persistenza solo dei valori di proprietà che differiscono dai valori predefiniti.

## <a name="support-for-project-and-configuration-properties"></a>Supporto per le proprietà di configurazione e del progetto
 La `Microsoft.VisualStudio.Package.SettingsPage` classe implementa le pagine delle proprietà di configurazione e di progetto. L'implementazione predefinita `SettingsPage` di offre proprietà pubbliche a un utente in una griglia delle proprietà generica. Il `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` metodo seleziona le classi derivate da per le `SettingsPage` griglie delle proprietà del progetto. Il `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` metodo seleziona le classi derivate da per le `SettingsPage` griglie delle proprietà di configurazione. Il tipo di progetto deve eseguire l'override di questi metodi per selezionare le pagine delle proprietà appropriate.

 La `SettingsPage` classe e la classe offrono questi metodi per rendere `Microsoft.VisualStudio.Package.ProjectNode` persistenti le proprietà di progetto e configurazione:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` e `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` rendere persistenti le proprietà del progetto.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` e `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` rendere persistenti le proprietà di configurazione.

  > [!NOTE]
  > Le implementazioni delle classi e usano i `Microsoft.VisualStudio.Package.SettingsPage` metodi (MSBuild) per ottenere e impostare le proprietà di progetto e `Microsoft.VisualStudio.Package.ProjectNode` configurazione dal file di `Microsoft.Build.BuildEngine` progetto.

  La classe da cui si deriva `SettingsPage` deve implementare `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` e per `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` rendere persistenti le proprietà di progetto o di configurazione del file di progetto.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute e percorso del Registro di sistema
 Le classi `SettingsPage` derivate da sono progettate per essere condivise tra vspackage. Per fare in modo che un VSPackage crei una classe derivata da `SettingsPage` , aggiungere un oggetto a una classe derivata da `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` `Microsoft.VisualStudio.Shell.Package` .

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs" id="Snippet1":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb" id="Snippet1":::

 Il PACCHETTO VSPackage a cui è collegato l'attributo non è importante. Quando un VSPackage viene registrato con , l'ID di classe (CLSID) di qualsiasi oggetto che può essere creato viene registrato in modo che una chiamata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> possa crearlo.

 Il percorso del Registro di sistema di un oggetto che può essere creato è determinato dalla combinazione di <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> , parola, CLSID e GUID del tipo di oggetto. Se la classe ha il `MyProjectPropertyPage` GUID {3c693da2-5bca-49b3-bd95-ffe0a39dd723} e UserRegistryRoot è HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, il percorso del Registro di sistema sarà HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\CLSID\\ {3c693da2-5bca-49b3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Project attributi e layout delle proprietà di configurazione e di configurazione
 Gli <xref:System.ComponentModel.CategoryAttribute> attributi , e <xref:System.ComponentModel.DisplayNameAttribute> <xref:System.ComponentModel.DescriptionAttribute> determinano il layout, l'etichettatura e la descrizione delle proprietà di progetto e configurazione in una pagina delle proprietà generica. Questi attributi determinano rispettivamente la categoria, il nome visualizzato e la descrizione dell'opzione.

> [!NOTE]
> Gli attributi equivalenti, SRCategory, LocDisplayName e SRDescription, usano le risorse stringa per la localizzazione e sono definiti in [MPF per i progetti - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Si consideri il frammento di codice riportato di seguito.

 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb" id="Snippet2":::
 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs" id="Snippet2":::

 La proprietà di configurazione viene visualizzata nella pagina delle proprietà di configurazione come `MyConfigProp` My Config **Property** nella categoria **My Category**. Se l'opzione è selezionata, nel pannello della descrizione viene visualizzata la descrizione **My Description**( Descrizione).

## <a name="see-also"></a>Vedi anche
- [Aggiunta e rimozione di pagine delle proprietà](../../extensibility/adding-and-removing-property-pages.md)
- [Progetti](../../extensibility/internals/projects.md)
- [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)