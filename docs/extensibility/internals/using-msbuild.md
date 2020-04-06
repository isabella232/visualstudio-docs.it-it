---
title: Uso di MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f961249ff584f7767dc2505bb20b1fb0961b7dd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704293"
---
# <a name="using-msbuild"></a>Uso di MSBuild
MSBuild fornisce un formato XML estensibile ben definito per la creazione di file di progetto che descrivono completamente gli elementi di progetto da compilare, le attività di compilazione e le configurazioni di compilazione.

## <a name="general-msbuild-considerations"></a>Considerazioni generali su MSBuildGeneral MSBuild Considerations
 I file di progetto [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] MSBuild, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ad esempio i file con estensione csproj e vbproj, contengono dati utilizzati in fase di compilazione, ma possono anche contenere dati utilizzati in fase di progettazione. I dati della fase di compilazione vengono archiviati utilizzando le primitive MSBuild, inclusi [l'elemento Item (MSBuild)](../../msbuild/item-element-msbuild.md) e [l'elemento proprietà (MSBuild)](../../msbuild/property-element-msbuild.md). I dati della fase di progettazione, ovvero i dati specifici del tipo di progetto e di tutti i sottotipi di progetto correlati, vengono archiviati in formato XML in formato libero riservato.

 MSBuild non dispone del supporto nativo per gli oggetti di configurazione, ma fornisce attributi condizionali per specificare dati specifici della configurazione. Ad esempio:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Per ulteriori informazioni sugli attributi condizionali, vedere [Costrutti condizionali](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Estensione di MSBuild per il tipo di progettoExtending MSBuild for Your Project Type
 Le interfacce e le API MSBuild sono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]soggette a modifiche nelle versioni future di . Pertanto, è consigliabile utilizzare le classi di framework di pacchetto gestito (MPF) perché forniscono la schermatura dalle modifiche.

 Il Framework di pacchetto gestito per i progetti (MPFProj) fornisce classi helper per la creazione e la gestione di nuovo sistema di progetto. Il codice sorgente e le istruzioni di compilazione sono disponibili in [MPF for Projects - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Le classi MPF specifiche del progetto sono le seguenti:

|Classe|Implementazione|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement`class è un wrapper per gli elementi MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Generatori di file singoli e attività MSBuildSingle File Generators vs.
 I generatori di file singoli sono accessibili solo in fase di progettazione, ma le attività MSBuild possono essere usate in fase di progettazione e in fase di compilazione. Per la massima flessibilità, pertanto, utilizzare le attività MSBuild per trasformare e generare codice. Per ulteriori informazioni, vedere [Strumenti personalizzati](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento su MSBuild](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Strumenti personalizzati](../../extensibility/internals/custom-tools.md)
