---
title: Uso di MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f27d3c5c7465314a7e9005972dec1349c1b9d89f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902231"
---
# <a name="using-msbuild"></a>Uso di MSBuild
MSBuild fornisce un formato XML ben definito ed estendibile per la creazione di file di progetto che descrivono gli elementi di progetto per essere compilato, attività di compilazione e le configurazioni della build.  
  
## <a name="general-msbuild-considerations"></a>Considerazioni generali MSBuild  
 File di progetto MSBuild, ad esempio, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] file con estensione csproj e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] file con estensione vbproj, contengono dati che viene usati in fase di compilazione, ma possono anche contenere dati che viene usati in fase di progettazione. Dati in fase di compilazione vengono archiviati utilizzando le primitive di MSBuild, incluso [elemento Item (MSBuild)](../../msbuild/item-element-msbuild.md) e [elemento Property (MSBuild)](../../msbuild/property-element-msbuild.md). Dati Design-time, ovvero i dati specifici per il tipo di progetto e qualsiasi sottotipi di progetto correlate, sono archiviati in XML Freeform riservate per il servizio.  
  
 MSBuild non include il supporto nativo per gli oggetti di configurazione, ma fornire attributi condizionali per specificare i dati specifici della configurazione. Ad esempio:  
  
```xml  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Per altre informazioni sugli attributi condizionali, vedere [costrutti condizionali](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>MSBuild per l'estensione per il tipo di progetto  
 Interfacce di MSBuild e le API sono soggetti a modifiche nelle versioni future di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pertanto, è consigliabile usare le classi di framework (MPF) di pacchetto gestito, perché forniscono la schermatura dalle modifiche.  
  
 Il Framework di pacchetto gestito per progetti (MPFProj) fornisce classi helper per la creazione e la gestione di nuovo sistema di progetto. È possibile trovare l'origine istruzioni di compilazione e codice in [MPF per i progetti - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).  
  
 Le classi MPF di progetti specifici sono i seguenti:  
  
|Classe|Implementazione|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` classe è un wrapper per gli elementi di MSBuild.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Visual Studio di generatori di File singoli. Attività MSBuild  
 Singolo file i generatori sono accessibili in fase di progettazione solo, ma le attività di MSBuild possono essere utilizzate in fase di progettazione e in fase di compilazione. Per la massima flessibilità, pertanto, utilizzare le attività di MSBuild per trasformare e generare il codice. Per altre informazioni, vedere [strumenti personalizzati](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild](../../msbuild/msbuild-reference.md)   
 [MSBuild](../../msbuild/msbuild.md)   
 [Strumenti personalizzati](../../extensibility/internals/custom-tools.md)