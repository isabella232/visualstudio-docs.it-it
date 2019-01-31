---
title: 'Procedura: Compilare un progetto con risorse | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b45d2dfedcc020a5b6206e4c419c0e4b7f9b0f02
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804001"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Procedura: Compilare un progetto con risorse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Se si stanno compilando le versioni localizzate di un progetto, tutti gli elementi dell'interfaccia utente devono essere separati in file di risorse per le diverse lingue. Se il progetto usa solo stringhe, i file di risorse possono usare file di testo. In alternativa, è possibile usare file RESX come file di risorse.  
  
## <a name="compiling-resources-with-msbuild"></a>Compilazione di risorse con MSBuild  
 La raccolta di attività comuni fornita con [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] include un'attività `GenerateResource` che è possibile usare per compilare le risorse in file di testo o RESX. Questa attività include il parametro `Sources` per specificare i file di risorse da compilare e il parametro `OutputResources` per specificare i nomi dei file di risorse di output. Per altre informazioni sull'attività `GenerateResource`, vedere [Attività GenerateResource](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Per compilare le risorse con MSBuild  
  
1.  Identificare i file di risorse del progetto e passarli all'attività `GenerateResource`, come elenchi di elementi o come nomi file.  
  
2.  Specificare il parametro `OutputResources` dell'attività `GenerateResource`, che consente di impostare i nomi dei file di risorse di output.  
  
3.  Usare l'elemento `Output` dell'attività per archiviare il valore del parametro `OutputResources` in un elemento.  
  
4.  Usare l'elemento creato dall'elemento `Output` come input per un'altra attività.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra come l'elemento `Output` specifica che l'attributo `OutputResources` dell'attività `GenerateResource` conterrà i file di risorse compilati `alpha.resources` e `beta.resources` e che questi due file verranno inseriti nell'elenco di elementi `Resources`. Identificando tali file con estensione resources come raccolta di elementi con lo stesso nome, è possibile usarli facilmente come input per un'altra attività, ad esempio l'attività [Csc](../msbuild/csc-task.md).  
  
 Questa attività equivale a usare l'opzione **/compile** per [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4):  
  
 `Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`  
  
```  
<GenerateResource  
    Sources="alpha.resx; beta.txt"  
    OutputResources="alpha.resources; beta.resources">  
    <Output TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
## <a name="example"></a>Esempio  
 Il progetto di esempio seguente contiene due attività: l'attività `GenerateResource` per compilare le risorse e l'attività `Csc` per compilare sia i file di codice sorgente che i file di risorse compilati. I file di risorse compilati dall'attività `GenerateResource` vengono archiviati nell'elemento `Resources` e passati all'attività `Csc`.  
  
```  
<Project DefaultTargets = "Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <Target Name="Resources">  
        <GenerateResource  
            Sources="alpha.resx; beta.txt"  
            OutputResources="alpha.resources; beta.resources">  
            <Output TaskParameter="OutputResources"  
                ItemName="Resources"/>  
        </GenerateResource>  
    </Target>  
  
    <Target Name="Build" DependsOnTargets="Resources">  
        <Csc Sources="hello.cs"  
                Resources="@(Resources)"  
                OutputAssembly="hello.exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
[MSBuild](msbuild.md)  
 [Attività GenerateResource](../msbuild/generateresource-task.md)   
 [Attività Csc](../msbuild/csc-task.md)   
 [Resgen.exe (generatore di file di risorse)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)
