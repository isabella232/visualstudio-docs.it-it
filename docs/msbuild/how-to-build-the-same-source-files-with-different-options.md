---
title: Compilare gli stessi file di origine con opzioni diverse
description: Informazioni su come creare configurazioni MSBuild build diverse per compilare gli stessi file di origine con opzioni diverse.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: cd2a701d8e5be3084466617e966f0475807e74db4645ffe6c1754a0cf0bafdaf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427860"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Procedura: Compilare gli stessi file di origine con opzioni diverse

Quando si compilano progetti, spesso si compilano gli stessi componenti con opzioni di compilazione diverse. È possibile, ad esempio, creare una build di debug con informazioni sui simboli o una build di versione senza informazioni sui simboli, ma con le ottimizzazioni abilitate In caso contrario, è possibile compilare un progetto da eseguire in una piattaforma specifica, ad esempio x86 o x64. In tutti questi casi, la maggior parte delle opzioni di compilazione è la stessa. Vengono modificate solo alcune opzioni per controllare la configurazione della build. Con MSBuild, si usano proprietà e condizioni per creare le diverse configurazioni di compilazione.

## <a name="use-properties-to-control-build-settings"></a>Usare le proprietà per controllare le impostazioni di compilazione

L'elemento `Property` definisce una variabile a cui si fa riferimento più volte in un file di progetto, ad esempio per indicare la posizione di una directory temporanea o per impostare i valori delle proprietà usate in più configurazioni, ad esempio in una build di debug e in una build di rilascio. Per altre informazioni sulle proprietà, vedere [Proprietà di MSBuild](../msbuild/msbuild-properties.md).

È possibile usare le proprietà per modificare la configurazione della build senza dover modificare il file di progetto. L'attributo `Condition` dell'elemento `Property` e dell'elemento `PropertyGroup` consente di modificare il valore delle proprietà. Per altre informazioni sulle condizioni MSBuild, vedere [Condizioni](../msbuild/msbuild-conditions.md).

### <a name="to-set-a-group-of-properties-that-depends-on-another-property"></a>Per impostare un gruppo di proprietà che dipende da un'altra proprietà

- Usare un attributo `Condition` in un elemento `PropertyGroup` simile al seguente:

  ```xml
  <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
      <DebugType>full</DebugType>
      <Optimize>no</Optimize>
  </PropertyGroup>
  ```

### <a name="to-define-a-property-that-depends-on-another-property"></a>Per definire una proprietà che dipende da un'altra proprietà

- Usare un attributo `Condition` in un elemento `Property` simile al seguente:

  ```xml
  <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>
  ```

## <a name="specify-properties-on-the-command-line"></a>Specificare le proprietà nella riga di comando

Dopo avere scritto il file di progetto in modo che accetti più configurazioni, è necessario poter modificare tali configurazioni ogni volta che si compila il progetto. MSBuild questa funzionalità consentendo di impostare le proprietà nella riga di comando usando l'opzione **-property** **o -p.**

### <a name="to-set-a-project-property-at-the-command-line"></a>Per impostare una proprietà del progetto nella riga di comando

- Usare **l'opzione -property** con la proprietà e il valore della proprietà . Ad esempio:

  ```cmd
  msbuild file.proj -property:Flavor=Debug
  ```

  o

  ```cmd
  Msbuild file.proj -p:Flavor=Debug
  ```

### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Per specificare più di una proprietà del progetto nella riga di comando

- Usare l'opzione **-property** o **-p** più volte con i valori della proprietà e della proprietà oppure usare un'opzione **-property** o **-p** e separare più proprietà con punti e virgola (;). Ad esempio:

  ```cmd
  msbuild file.proj -p:Flavor=Debug;Platform=x86
  ```

  o

  ```cmd
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86
  ```

  Le variabili di ambiente vengono considerate anche come proprietà e vengono incorporate automaticamente da MSBuild. Per altre informazioni sull'uso delle variabili di ambiente, [vedere Procedura: Usare variabili di ambiente in una compilazione.](../msbuild/how-to-use-environment-variables-in-a-build.md)

  Il valore della proprietà specificato nella riga di comando ha la precedenza sui valori impostati per la stessa proprietà nel file di progetto e tale valore nel file di progetto ha la precedenza sul valore in una variabile di ambiente.

  È possibile modificare questo comportamento usando l'attributo `TreatAsLocalProperty` in un tag di progetto. Per i nomi di proprietà elencati con tale attributo, il valore della proprietà specificato nella riga di comando non ha la precedenza sul valore nel file di progetto. È possibile trovare un esempio più avanti in questo argomento.

## <a name="example-1"></a>Esempio 1

L'esempio di codice seguente del progetto "Hello World" contiene due nuovi gruppi di proprietà che possono essere usati per creare una build di debug e una build di rilascio.

Per compilare la versione di debug di questo progetto, digitare:

```cmd
msbuild consolehwcs1.proj -p:flavor=debug
```

Per compilare la versione finale di questo progetto, digitare:

```cmd
msbuild consolehwcs1.proj -p:flavor=retail
```

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Sets the default flavor if an environment variable called
    Flavor is not set or specified on the command line -->
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
    </PropertyGroup>

    <!-- Define the DEBUG settings -->
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
        <DebugType>full</DebugType>
        <Optimize>no</Optimize>
    </PropertyGroup>

    <!-- Define the RETAIL settings -->
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">
        <DebugType>pdbonly</DebugType>
        <Optimize>yes</Optimize>
    </PropertyGroup>

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files
        of type CSFile -->
        <CSC  Sources = "@(CSFile)"
            DebugType="$(DebugType)"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe" >

            <!-- Set the OutputAssembly attribute of the CSC
            task to the name of the executable file that is
            created -->
            <Output TaskParameter="OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example-2"></a>Esempio 2

L'esempio seguente mostra come usare l'attributo `TreatAsLocalProperty`. La proprietà `Color` ha un valore di `Blue` nel file di progetto e `Green` nella riga di comando. Con `TreatAsLocalProperty="Color"` nel tag di progetto, la proprietà della riga di comando (`Green`) non esegue l'override della proprietà definita nel file di progetto (`Blue`).

Per compilare il progetto, immettere il comando seguente:

```cmd
msbuild colortest.proj -t:go -property:Color=Green
```

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0" TreatAsLocalProperty="Color">

    <PropertyGroup>
        <Color>Blue</Color>
    </PropertyGroup>

    <Target Name="go">
        <Message Text="Color: $(Color)" />
    </Target>
</Project>

<!--
  Output with TreatAsLocalProperty="Color" in project tag:
     Color: Blue

  Output without TreatAsLocalProperty="Color" in project tag:
     Color: Green
-->
```

## <a name="see-also"></a>Vedi anche

- [MSBuild](../msbuild/msbuild.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Project elemento (MSBuild)](../msbuild/project-element-msbuild.md)
