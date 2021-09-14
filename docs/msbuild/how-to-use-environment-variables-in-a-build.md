---
title: 'Procedura: Usare le variabili di ambiente in una compilazione | Microsoft Docs'
description: Informazioni su come accedere alle variabili di ambiente MSBuild file di progetto e usare le variabili di ambiente per impostare le opzioni di compilazione senza modificare il file di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 1a56d81586fa855552eb5d400c43ddd03e39098b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625680"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Procedura: Usare le variabili di ambiente in una compilazione

Quando si compilano i progetti, spesso è necessario impostare le opzioni di compilazione usando informazioni non incluse nel file di progetto o nei file che costituiscono il progetto. Queste informazioni sono in genere archiviate nelle variabili di ambiente.

## <a name="reference-environment-variables"></a>Fare riferimento alle variabili di ambiente

 Tutte le variabili di ambiente sono disponibili per il file Microsoft Build Engine (MSBuild) come proprietà.

> [!NOTE]
> Se il file di progetto contiene una definizione esplicita di una proprietà con lo stesso nome di una variabile di ambiente, la proprietà nel file di progetto esegue l'override del valore della variabile di ambiente.

#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Per usare una variabile di ambiente in un progetto MSBuild

- Fare riferimento alla variabile di ambiente esattamente come a una variabile dichiarata nel file di progetto. Il codice seguente, ad esempio, fa riferimento alla variabile di ambiente BIN_PATH:

   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`

  È possibile usare un attributo `Condition` per fornire un valore predefinito per una proprietà se la variabile di ambiente non è stata impostata.

#### <a name="to-provide-a-default-value-for-a-property"></a>Per fornire un valore predefinito per una proprietà

- Usare un attributo `Condition` in una proprietà per impostare il valore solo se la proprietà non ha un valore. Il codice seguente, ad esempio, imposta la proprietà `ToolsPath` su *c:\tools* solo se la variabile di ambiente `ToolsPath` non è impostata:

     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`

    > [!NOTE]
    > Per i nomi delle proprietà non viene rilevata la distinzione tra maiuscole e minuscole, quindi sia `$(ToolsPath)` che `$(TOOLSPATH)` fanno riferimento alla stessa proprietà o variabile di ambiente.

## <a name="example"></a>Esempio

 Il file di progetto seguente usa variabili di ambiente per specificare il percorso delle directory.

```xml
<Project DefaultTargets="FakeBuild">
    <PropertyGroup>
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">
            C:\Tools
        </ToolsPath>
    </PropertyGroup>
    <Target Name="FakeBuild">
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Vedi anche

- [MSBuild](../msbuild/msbuild.md)
- [proprietà di MSBuild](../msbuild/msbuild-properties.md)
- [Procedura: Compilare gli stessi file di origine con opzioni diverse](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
