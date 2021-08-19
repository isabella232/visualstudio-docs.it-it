---
title: Fare riferimento al nome o al percorso del file di progetto
description: Informazioni su come usare MSBuild riservate per fare riferimento al nome o al percorso del file di progetto senza dover creare proprietà personalizzate.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 06ff5cb50453557eff20b2b1ec287d4b03012abf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085039"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Procedura: Fare riferimento al nome o al percorso del file di progetto

È possibile usare il nome o il percorso del progetto nel file di progetto senza dover creare una proprietà. MSBuild proprietà riservate che fanno riferimento al nome del file di progetto e ad altre proprietà correlate al progetto. Per altre informazioni sulle proprietà riservate, vedere [Proprietà di MSBuild riservate e note](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="use-the-project-properties"></a>Usare le proprietà del progetto

 MSBuild alcune proprietà riservate che è possibile usare nei file di progetto senza definirle ogni volta. La proprietà riservata `MSBuildProjectName`, ad esempio, fornisce un riferimento al nome file di progetto. La proprietà riservata `MSBuildProjectDirectory` specifica un riferimento al percorso del file di progetto.

#### <a name="to-use-the-project-properties"></a>Per usare le proprietà di progetto

- Fare riferimento alla proprietà nel file di progetto con la notazione $(), come per qualsiasi altra proprietà. Esempio:

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  Uno dei vantaggi dell'uso di una proprietà riservata è che eventuali modifiche apportate al nome file di progetto vengono incorporate automaticamente. La volta successiva in cui si compila il progetto, il file di output assumerà il nuovo nome senza nessuna altra azione da parte dell'utente.

  Per altre informazioni sull'uso di caratteri speciali nei riferimenti a file o progetti, [MSBuild caratteri speciali.](../msbuild/msbuild-special-characters.md)

> [!NOTE]
> Le proprietà riservate non possono essere ridefinite nel file di progetto.

## <a name="example-1"></a>Esempio 1

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

## <a name="example-2"></a>Esempio 2

 Il file di progetto di esempio seguente usa la proprietà `MSBuildProjectDirectory` riservata per creare il percorso completo a un file del percorso del file di progetto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

Nell'esempio viene [utilizzata la sintassi](property-functions.md) della funzione Property per chiamare il metodo .NET Framework statico <xref:System.IO.Path.Combine*?displayProperty=fullName> .

## <a name="see-also"></a>Vedi anche

- [MSBuild](../msbuild/msbuild.md)
- [Proprietà riservate e note MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
