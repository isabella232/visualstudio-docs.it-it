---
title: 'Procedura: Fare riferimento al nome o al percorso del file di progetto | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b54a63b135f844ff20b45ffac430662c4df1f19
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633837"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Procedura: Fare riferimento al nome o al percorso del file di progetto

È possibile usare il nome o il percorso del progetto nel file di progetto senza dover creare una proprietà. MSBuild fornisce proprietà riservate che fanno riferimento al nome del file di progetto e altre proprietà correlate al progetto. Per altre informazioni sulle proprietà riservate, vedere [Proprietà di MSBuild riservate e note](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="use-the-project-properties"></a>Usare le proprietà del progetto

 MSBuild fornisce alcune proprietà riservate che è possibile utilizzare nei file di progetto senza definirle ogni volta. La proprietà riservata `MSBuildProjectName`, ad esempio, fornisce un riferimento al nome file di progetto. La proprietà riservata `MSBuildProjectDirectory` specifica un riferimento al percorso del file di progetto.

#### <a name="to-use-the-project-properties"></a>Per usare le proprietà di progetto

- Fare riferimento alla proprietà nel file di progetto con la notazione $(), come per qualsiasi altra proprietà. Ad esempio:

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  Uno dei vantaggi dell'uso di una proprietà riservata è che eventuali modifiche apportate al nome file di progetto vengono incorporate automaticamente. La volta successiva in cui si compila il progetto, il file di output assumerà il nuovo nome senza nessuna altra azione da parte dell'utente.

  Per altre info sull'uso di caratteri speciali nei riferimenti a file o progetti, vedi [Caratteri speciali MSBuild](../msbuild/msbuild-special-characters.md).

> [!NOTE]
> Le proprietà riservate non possono essere ridefinite nel file di progetto.

## <a name="example"></a>Esempio

 Il file di progetto di esempio seguente fa riferimento al nome del progetto come proprietà riservata per specificare il nome per l'output.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    DefaultTargets = "Compile">

    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
     </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using
        input files of type CSFile -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(MSBuildProjectName).exe" >
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the project -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example"></a>Esempio

 Il file di progetto di esempio seguente usa la proprietà `MSBuildProjectDirectory` riservata per creare il percorso completo a un file del percorso del file di progetto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

Nell'esempio viene utilizzata la sintassi della <xref:System.IO.Path.Combine*?displayProperty=fullName>funzione [Property](property-functions.md) per chiamare il metodo statico .NET Framework .

## <a name="see-also"></a>Vedere anche

- [MSBuild](../msbuild/msbuild.md)
- [Proprietà di MSBuild riservate e note](../msbuild/msbuild-reserved-and-well-known-properties.md)
