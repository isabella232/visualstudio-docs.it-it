---
title: File con estensione targets di MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bab229a3246ac91eaa652be67e98a68aab40e820
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839808"
---
# <a name="msbuild-targets-files"></a>File con estensione targets di MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] include più file con estensione targets che contengono elementi, proprietà, destinazioni e attività per gli scenari comuni. Questi file vengono automaticamente importati nella maggior parte dei file di progetto di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per semplificare la manutenzione e la leggibilità.  
  
 I progetti importano generalmente uno o più file con estensione TARGETS per definire il processo di compilazione. Ad esempio, un progetto di [!INCLUDE[csprcs](../includes/csprcs-md.md)] creato da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] importerà Microsoft.CSharp.targets che importa Microsoft.Common.targets. Il progetto stesso di [!INCLUDE[csprcs](../includes/csprcs-md.md)] definirà gli elementi e le proprietà specifici di tale progetto, ma le regole di compilazione standard per un progetto di [!INCLUDE[csprcs](../includes/csprcs-md.md)] vengono definite nei file con estensione targets importati.  
  
 Il valore `$(MSBuildToolsPath)` specifica il percorso di questi file con destinazione .targets comuni. Se `ToolsVersion` è 4.0, i file sono nel percorso seguente: `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  
  
> [!NOTE]
> Per informazioni su come creare destinazioni personalizzate, vedere [Destinazioni](../msbuild/msbuild-targets.md). Per informazioni su come usare l' `Import` elemento per inserire un file di progetto in un altro file di progetto, vedere [elemento Import (MSBuild)](../msbuild/import-element-msbuild.md) e [procedura: usare la stessa destinazione in più file di progetto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  
  
## <a name="common-targets-files"></a>File con estensione targets comuni  
  
|File con estensione targets|Descrizione|  
|-------------------|-----------------|  
|Microsoft.Common.targets|Definisce i passaggi nel processo di compilazione standard per i progetti di [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] e [!INCLUDE[csprcs](../includes/csprcs-md.md)].<br /><br /> Importato dai file Microsoft.CSharp.targets e Microsoft.VisualBasic.targets, che includono l'istruzione seguente: `<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|Definisce i passaggi nel processo di compilazione standard per i progetti di Visual C#.<br /><br /> Importato dai file di progetto di Visual C# (con estensione csproj), che includono l'istruzione seguente: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|Definisce i passaggi nel processo di compilazione standard per i progetti di Visual Basic.<br /><br /> Importato dai file di progetto di Visual Basic (con estensione vbproj), che includono l'istruzione seguente: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)
