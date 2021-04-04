---
title: Supporto per le proprietà di progetto e configurazione | Microsoft Docs
description: Informazioni su come fornire una pagina delle proprietà per il proprio tipo di progetto nell'IDE di Visual Studio, in cui è possibile visualizzare le proprietà estese del progetto e della configurazione.
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
ms.workload:
- vssdk
ms.openlocfilehash: 6f3932658442774ad6f54bd5e6243fe73679b38f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214031"
---
# <a name="support-for-project-and-configuration-properties"></a>Supporto per le proprietà di configurazione e del progetto
Nella finestra **Proprietà** del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE) è possibile visualizzare le proprietà di progetto e di configurazione. È possibile specificare una pagina delle proprietà per il proprio tipo di progetto in modo che l'utente possa impostare le proprietà per l'applicazione.

 Selezionando un nodo del progetto in **Esplora soluzioni** e scegliendo **Proprietà** dal menu **progetto** , è possibile aprire una finestra di dialogo che include proprietà di progetto e di configurazione. In [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] , e i tipi di progetto derivati da questi linguaggi, questa finestra di dialogo viene visualizzata come pagina a schede nella finestra di [dialogo generale, ambiente, opzioni](../../ide/reference/general-environment-options-dialog-box.md). Per ulteriori informazioni, vedere [not in Build: Walkthrough: Esponeting Project and Configuration Properties (C#)](/previous-versions/bb166517(v=vs.100)).

 Il Framework di pacchetto gestito per i progetti (MPFProj) fornisce classi helper per la creazione e la gestione di un nuovo sistema di progetto. È possibile trovare il codice sorgente e le istruzioni di compilazione in [MPF for Projects-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Persistenza delle proprietà di progetto e configurazione
 Le proprietà di progetto e di configurazione sono rese permanente in un file di progetto con qualsiasi estensione di file associata al tipo di progetto, ad esempio. csproj,. vbproj e. PROG. I progetti di linguaggio usano in genere un file modello per generare il file di progetto. Tuttavia, esistono in realtà diversi modi per associare i tipi di progetto e i modelli. Per ulteriori informazioni, vedere [Descrizione della directory dei modelli (. File VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Le proprietà di progetto e di configurazione vengono create aggiungendo elementi al file modello. Queste proprietà sono quindi disponibili per tutti i progetti creati usando il tipo di progetto che usa il modello. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i progetti e MPFProj usano entrambi lo schema di [Panoramica not in Build: MSBuild](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) per i file modello. Questi file hanno una sezione PropertyGroup per ogni configurazione. Le proprietà dei progetti vengono in genere rese permanente nella prima sezione PropertyGroup, che include un argomento di configurazione impostato su una stringa null.

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

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs" id="Snippet1":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb" id="Snippet1":::

 Il VSPackage a cui è associato l'attributo non è importante. Quando un pacchetto VSPackage viene registrato con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , viene registrato l'ID di classe (CLSID) di qualsiasi oggetto che può essere creato, in modo che una chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> possa crearla.

 Il percorso del registro di sistema di un oggetto che è possibile creare viene determinato combinando <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> , la parola, il CLSID e il GUID del tipo di oggetto. Se `MyProjectPropertyPage` la classe ha un GUID di {3c693da2-5bca-49B3-bd95-ffe0a39dd723} e UserRegistryRoot è HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, il percorso del registro di sistema sarà HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\CLSID\\ {3c693da2-5bca-49B3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Layout e attributi delle proprietà di progetto e configurazione
 Gli <xref:System.ComponentModel.CategoryAttribute> <xref:System.ComponentModel.DisplayNameAttribute> attributi, e <xref:System.ComponentModel.DescriptionAttribute> determinano il layout, l'assegnazione di etichette e la descrizione delle proprietà di progetto e di configurazione in una pagina delle proprietà generica. Questi attributi determinano rispettivamente la categoria, il nome visualizzato e la descrizione dell'opzione.

> [!NOTE]
> Gli attributi equivalenti, SRCategory, LocDisplayName e SRDescription, usano le risorse di stringa per la localizzazione e sono definiti in [MPF per i progetti-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Si consideri il frammento di codice riportato di seguito.

 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb" id="Snippet2":::
 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs" id="Snippet2":::

 La `MyConfigProp` proprietà di configurazione viene visualizzata nella pagina delle proprietà configurazione come **Proprietà** di configurazione nella categoria, **categoria**. Se l'opzione è selezionata, **la descrizione viene** visualizzata nel pannello Descrizione.

## <a name="see-also"></a>Vedi anche
- [Aggiunta e rimozione di pagine delle proprietà](../../extensibility/adding-and-removing-property-pages.md)
- [Progetti](../../extensibility/internals/projects.md)
- [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)