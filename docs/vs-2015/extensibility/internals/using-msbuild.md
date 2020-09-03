---
title: Uso di MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a1ad59e6d8f4cb88004629b0dfd2cdf0631a7824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297675"
---
# <a name="using-msbuild"></a>Uso di MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

MSBuild fornisce un formato XML estendibile e ben definito per la creazione di file di progetto che descrivono completamente gli elementi di progetto da compilare, le attività di compilazione e le configurazioni di compilazione.  
  
 Per un esempio end-to-end di un sistema di progetto di linguaggio basato su MSBuild, vedere l'approfondimento di esempio di IronPython negli[esempi di VSSDK](../../misc/vssdk-samples.md).  
  
## <a name="general-msbuild-considerations"></a>Considerazioni generali su MSBuild  
 I file di progetto MSBuild, ad esempio [!INCLUDE[csprcs](../../includes/csprcs-md.md)] i file con estensione csproj e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] VBPROJ, contengono dati usati in fase di compilazione, ma possono anche contenere dati usati in fase di progettazione. I dati in fase di compilazione vengono archiviati usando le primitive MSBuild, inclusi elemento [Item (MSBuild)](../../msbuild/item-element-msbuild.md) ed [elemento Property (MSBuild)](../../msbuild/property-element-msbuild.md). I dati della fase di progettazione, ovvero i dati specifici per il tipo di progetto e gli eventuali sottotipi di progetto correlati, vengono archiviati in un file XML in formato libero riservato.  
  
 MSBuild non dispone del supporto nativo per gli oggetti di configurazione, ma fornisce attributi condizionali per la specifica di dati specifici della configurazione. Ad esempio:  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Per altre informazioni sugli attributi condizionali, vedere [costrutti condizionali](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Estensione di MSBuild per il tipo di progetto  
 Le interfacce e le API di MSBuild sono soggette a modifiche nelle versioni future di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Pertanto, è consigliabile utilizzare le classi del Framework di pacchetto gestito (MPF) perché forniscono la schermatura dalle modifiche.  
  
 Il Framework di pacchetto gestito per i progetti (MPFProj) fornisce classi helper per la creazione e la gestione di un nuovo sistema di progetto. È possibile trovare il codice sorgente e le istruzioni di compilazione in [MPF for Projects-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
 Di seguito sono riportate le classi MPF specifiche del progetto:  
  
|Classe|Implementazione|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` la classe è un wrapper per gli elementi MSBuild.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Generatori di file singoli e attività MSBuild  
 I generatori di file singoli sono accessibili solo in fase di progettazione, ma le attività di MSBuild possono essere utilizzate in fase di progettazione e di compilazione. Per garantire la massima flessibilità, utilizzare le attività MSBuild per trasformare e generare codice. Per ulteriori informazioni, vedere [strumenti personalizzati](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti a MSBuild](../../msbuild/msbuild-reference.md)   
 [MSBuild](https://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [Strumenti personalizzati](../../extensibility/internals/custom-tools.md)
