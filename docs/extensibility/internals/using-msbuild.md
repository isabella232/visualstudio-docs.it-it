---
title: Uso di MSBuild | Microsoft Docs
description: MSBuild un formato XML estendibile per la creazione di file di progetto che descrivono completamente gli elementi di progetto da compilare, le attività di compilazione e le configurazioni di compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 47a6d8298b8ddcbeb3878f81beee8f00881be74c84c097b68e6a2563fd810546
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375699"
---
# <a name="using-msbuild"></a>Uso di MSBuild
MSBuild fornisce un formato XML ben definito ed estendibile per la creazione di file di progetto che descrivono completamente gli elementi di progetto da compilare, le attività di compilazione e le configurazioni di compilazione.

## <a name="general-msbuild-considerations"></a>Considerazioni MSBuild generali
 MSBuild file di progetto, ad esempio file con estensione csproj e vbproj, contengono dati usati in fase di compilazione, ma possono anche contenere dati usati in fase [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] di progettazione. I dati in fase di compilazione vengono archiviati usando MSBuild primitive, tra cui [l'elemento Item (MSBuild)](../../msbuild/item-element-msbuild.md) e [l'elemento Property (MSBuild).](../../msbuild/property-element-msbuild.md) I dati in fase di progettazione, che sono dati specifici del tipo di progetto e di eventuali sottotipi di progetto correlati, vengono archiviati in codice XML in formato libero riservato.

 MSBuild non dispone del supporto nativo per gli oggetti di configurazione, ma fornisce attributi condizionali per specificare dati specifici della configurazione. Esempio:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Per altre informazioni sugli attributi condizionali, vedere [Costrutti condizionali](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Estensione MSBuild per il tipo di Project
 MSBuild interfacce e API sono soggette a modifiche nelle versioni future di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Pertanto, è bene usare le classi MPF (Managed Package Framework) perché forniscono la schermatura dalle modifiche.

 Managed Package Framework for Projects (MPFProj) fornisce classi helper per la creazione e la gestione di un nuovo sistema di progetto. Il codice sorgente e le istruzioni di compilazione sono disponibili in [MPF for Projects - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Le classi MPF specifiche del progetto sono le seguenti:

|Classe|Implementazione|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement`class è un wrapper per MSBuild elementi.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Generatori di file singolo e attività MSBuild file
 I generatori di file singoli sono accessibili solo in fase di progettazione, ma MSBuild attività possono essere usate in fase di progettazione e di compilazione. Per la massima flessibilità, usare quindi MSBuild attività per trasformare e generare codice. Per altre informazioni, vedere [Strumenti personalizzati](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Vedi anche
- [MSBuild Riferimento](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Strumenti personalizzati](../../extensibility/internals/custom-tools.md)
