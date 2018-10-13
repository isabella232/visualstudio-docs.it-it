---
title: T4 Direttiva Assembly | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44949749-ce3c-4fb5-8690-a17f1564ac2f
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3ede2e84ac644fc8e1438873ea561ef3010f670c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301004"
---
# <a name="t4-assembly-directive"></a>Direttiva assembly T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un modello di testo della fase di progettazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], la direttiva `assembly` carica un assembly in modo che il codice del modello possa utilizzarne i tipi. L'effetto è simile all'aggiunta di un riferimento all'assembly in un progetto di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Per una panoramica generale della scrittura di modelli di testo, vedere [scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  La direttiva `assembly` in un modello di testo (pre-elaborato) della fase di esecuzione non è necessaria. Aggiungere invece gli assembly necessari per il **riferimenti** del [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] progetto.  
  
## <a name="using-the-assembly-directive"></a>Utilizzo della direttiva Assembly  
 La sintassi della direttiva è la seguente:  
  
```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 Il nome dell'assembly deve essere uno dei seguenti:  
  
-   Il nome sicuro dell'assembly nella GAC, quale `System.Xml.dll`. È inoltre possibile utilizzare la forma estesa, quale `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Per altre informazioni, vedere <xref:System.Reflection.AssemblyName>.  
  
-   Il percorso assoluto dell'assembly  
  
 È possibile utilizzare anche la sintassi `$(variableName)` per fare riferimento alle variabili [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], quali `$(SolutionDir)` e `%VariableName%` per fare riferimento alle variabili di ambiente. Ad esempio:  
  
```  
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>  
```  
  
 La direttiva dell'assembly non ha alcun effetto in un modello di testo pre-elaborato. Invece, includere i riferimenti necessari nella **riferimenti** sezione del [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] progetto. Per altre informazioni, vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="standard-assemblies"></a>Assembly standard  
 Gli assembly seguenti vengono caricati automaticamente, in modo che non sia necessario scrivere per essi direttive dell'assembly:  
  
-   `Microsoft.VisualStudio.TextTemplating.1*.dll`  
  
-   `System.dll`  
  
-   `WindowsBase.dll`  
  
 Se si utilizza una direttiva personalizzata, il processore di direttiva potrebbe caricare assembly aggiuntivi. Ad esempio, se si scrivono modelli per un linguaggio DSL, non è necessario scrivere direttive dell'assembly per gli assembly seguenti:  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`  
  
-   `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`  
  
-   Assembly contenente il modello DSL.  
  
##  <a name="msbuild"></a> Usando le proprietà del progetto in MSBuild e Visual Studio  
 Le macro di Visual Studio, ad esempio $(SolutionDir), non funzionano in MSBuild. Se si desidera trasformare i modelli nel computer di compilazione, è necessario utilizzare le proprietà del progetto.  
  
 Modificare il file con estensione csproj o vbproj per definire una proprietà del progetto. In questo esempio viene definita una proprietà denominata `myLibFolder`:  
  
```xml  
<!-- Define a project property, myLibFolder: -->  
<PropertyGroup>  
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myLibFolder">  
      <Value>$(myLibFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 È ora possibile usare la proprietà del progetto nei modelli di testo, che si trasformano correttamente in Visual Studio e in MSBuild:  
  
```  
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Direttiva include T4](../modeling/t4-include-directive.md)



