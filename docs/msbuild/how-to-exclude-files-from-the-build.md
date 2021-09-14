---
title: 'Procedura: Escludere file dalla compilazione | Microsoft Docs'
description: Informazioni su come escludere in modo esplicito o includere in modo condizionale i file dalle compilazioni nei MSBuild di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 7d75523b50cddf5270480747345fbcf021ea655e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625728"
---
# <a name="how-to-exclude-files-from-the-build"></a>Procedura: Escludere file dalla compilazione

In un file di progetto è possibile usare caratteri jolly per includere tutti i file in una sola directory o in un set annidato di directory come input per una compilazione. Potrebbe tuttavia essere presente un file nella directory o una directory in un set annidato di directory che non si vuole includere come input per una compilazione. È possibile escludere in modo esplicito tale file o directory dall'elenco di input. In un progetto potrebbe anche essere presente un file che si vuole includere solo in determinate condizioni. È possibile dichiarare in modo esplicito le condizioni in cui un file viene incluso in una compilazione.

## <a name="exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Escludere un file o una directory dagli input per una compilazione

 Gli elenchi di elementi sono i file di input per una compilazione. Gli elementi che si vuole includere vengono dichiarati separatamente o come gruppo usando l'attributo `Include`. Ad esempio:

```xml
<CSFile Include="Form1.cs"/>
<CSFile Include ="File1.cs;File2.cs"/>
<CSFile Include="*.cs"/>
<JPGFile Include="Images\**\*.jpg"/>
```

 Se sono stati usati caratteri jolly per includere tutti i file in una directory o in un set annidato di directory come input per una compilazione, potrebbe essere presente uno o più file nella directory oppure una directory nel set annidato di directory che non si vuole includere. Per escludere un elemento dall'elenco di elementi, usare l'attributo `Exclude`.

#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Per includere tutti i *file con estensione cs* o *vb* ad eccezione di *Form2*

- Usare uno degli attributi `Include` e `Exclude` seguenti:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs"/>
    ```

    oppure

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb"/>
    ```

#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Per includere tutti i *file con estensione cs* o *vb* ad eccezione *di Form2* e *Form3*

- Usare uno degli attributi `Include` e `Exclude` seguenti:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>
    ```

    oppure

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>
    ```

#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Per includere tutti *.jpg* file nelle sottodirectory della directory *Images* ad eccezione di quelli nella directory *Version2*

- Usare gli attributi `Include` e `Exclude` seguenti:

    ```xml
    <JPGFile
        Include="Images\**\*.jpg"
        Exclude = "Images\**\Version2\*.jpg"/>
    ```

    > [!NOTE]
    > È necessario specificare il percorso per entrambi gli attributi. Se si usa un percorso assoluto per specificare i percorsi file nell'attributo `Include`, è necessario usare un percorso assoluto anche nell'attributo `Exclude`. Se si usa un percorso relativo nell'attributo `Include`, è necessario usare un percorso relativo anche nell'attributo `Exclude`.

## <a name="use-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Usare le condizioni per escludere un file o una directory dagli input per una compilazione

 Se sono presenti elementi che si vuole includere, ad esempio, in una build di debug, ma non in una build di versione, è possibile usare l'attributo `Condition` per specificare le condizioni in cui includere l'elemento.

#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Per includere il file *Formula.vb* solo nelle build di versione

- Usare un attributo `Condition` simile al seguente:

    ```xml
    <Compile
        Include="Formula.vb"
        Condition=" '$(Configuration)' == 'Release' " />
    ```

## <a name="example"></a>Esempio

 L'esempio di codice seguente compila un progetto con tutti i file con estensione *cs* nella directory ad eccezione *di Form2.cs*.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" Exclude="Form2.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Elementi](../msbuild/msbuild-items.md)
- [MSBuild](../msbuild/msbuild.md)
- [Procedura: Selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md)
