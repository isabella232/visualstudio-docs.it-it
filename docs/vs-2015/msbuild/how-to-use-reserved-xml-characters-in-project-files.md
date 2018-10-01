---
title: 'Procedura: Usare caratteri XML riservati nei file di progetto | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f045195a4e934fcb6e140da68528ca43f104136d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525665"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Procedura: utilizzare caratteri XML riservati nei file di progetto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: usare caratteri XML riservati nei file di progetto](https://docs.microsoft.com/visualstudio/msbuild/how-to-use-reserved-xml-characters-in-project-files).  
  
  
Quando si creano file di progetto, potrebbe essere necessario usare caratteri XML riservati, ad esempio, nei valori della proprietà o nei valori del parametro di un'attività. Alcuni caratteri riservati tuttavia devono essere sostituiti da un'entità denominata in modo che il file di progetto possa essere analizzato.  
  
## <a name="using-reserved-characters"></a>Uso di caratteri riservati  
 La tabella seguente descrive i caratteri XML riservati che devono essere sostituiti dall'entità denominata corrispondente in modo che il file di progetto possa essere analizzato.  
  
|Carattere riservato|Entità denominata|  
|------------------------|------------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|"|&quot;|  
|'|&apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Per usare le virgolette doppie in un file di progetto  
  
-   Sostituire le virgolette doppie con l'entità denominata corrispondente, &quot;. Ad esempio, per racchiudere tra virgolette doppie l'elenco di elementi `EXEFile`, digitare:  
  
    ```  
    <Message Text="The output file is "@(EXEFile)"."/>  
    ```  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente le virgolette doppie vengono usate per evidenziare il nome file nel messaggio restituito dal file di progetto.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is "@(EXEFile)"."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md) [MSBuild](msbuild.md)


