---
title: 'Procedura: Usare caratteri XML riservati nei file di progetto | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: "14"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eb747b60c575aa1e49b559d3cf4a73b649808041
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Procedura: utilizzare caratteri XML riservati nei file di progetto
Quando si creano file di progetto, potrebbe essere necessario usare caratteri XML riservati, ad esempio, nei valori della proprietà o nei valori del parametro di un'attività. Alcuni caratteri riservati tuttavia devono essere sostituiti da un'entità denominata in modo che il file di progetto possa essere analizzato.  
  
## <a name="using-reserved-characters"></a>Uso di caratteri riservati  
 La tabella seguente descrive i caratteri XML riservati che devono essere sostituiti dall'entità denominata corrispondente in modo che il file di progetto possa essere analizzato.  
  
|Carattere riservato|Entità denominata|  
|------------------------|------------------|  
|\<|&amp;lt;|  
|>|&amp;gt;|  
|&|&amp;amp;|  
|"|&amp;quot;|  
|'|&amp;apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Per usare le virgolette doppie in un file di progetto  
  
-   Sostituire le virgolette doppie con l'entità denominata corrispondente, &amp;quot;. Ad esempio, per racchiudere tra virgolette doppie l'elenco di elementi `EXEFile`, digitare:  
  
    ```xml  
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>  
    ```  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente le virgolette doppie vengono usate per evidenziare il nome file nel messaggio restituito dal file di progetto.  
  
```xml  
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
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)    
 [MSBuild](../msbuild/msbuild.md)    
