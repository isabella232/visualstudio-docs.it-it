---
title: Direttiva assembly T4
description: Si apprenderà che Visual Studio modello di testo della fase di progettazione la direttiva assembly carica un assembly in modo che il codice del modello possa usare i relativi tipi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 02eee819bec26614e8ddf4860c258973174689ff1b6480726b1474ac6f463533
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428679"
---
# <a name="t4-assembly-directive"></a>Direttiva assembly T4

In un Visual Studio di testo della fase di progettazione, la direttiva carica un assembly in modo che il codice del modello `assembly` possa usare i relativi tipi. L'effetto è simile all'aggiunta di un riferimento all'assembly in un Visual Studio progetto.

 Per una panoramica generale della scrittura di modelli di testo, vedere [Scrittura di un modello di testo T4.](../modeling/writing-a-t4-text-template.md)

> [!NOTE]
> La direttiva `assembly` in un modello di testo (pre-elaborato) della fase di esecuzione non è necessaria. Aggiungere invece gli assembly necessari ai **riferimenti** del progetto Visual Studio progetto.

## <a name="using-the-assembly-directive"></a>Utilizzo della direttiva Assembly
 La sintassi della direttiva è la seguente:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Il nome dell'assembly deve essere uno dei seguenti:

- Il nome sicuro dell'assembly nella GAC, quale `System.Xml.dll`. È inoltre possibile utilizzare la forma estesa, quale `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Per altre informazioni, vedere <xref:System.Reflection.AssemblyName>.

- Il percorso assoluto dell'assembly

  È possibile usare la `$(variableName)` sintassi per fare riferimento Visual Studio variabili, ad esempio `$(SolutionDir)` , e per fare riferimento a variabili di `%VariableName%` ambiente. Esempio:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 La direttiva dell'assembly non ha alcun effetto in un modello di testo pre-elaborato. Includere invece i riferimenti necessari nella **sezione Riferimenti** del Visual Studio progetto. Per altre informazioni, vedere [Generazione di testo di run-time con modelli di testo T4.](../modeling/run-time-text-generation-with-t4-text-templates.md)

## <a name="standard-assemblies"></a>Assembly standard
 Gli assembly seguenti vengono caricati automaticamente, in modo che non sia necessario scrivere per essi direttive dell'assembly:

- `Microsoft.VisualStudio.TextTemplating.1*.dll`

- `System.dll`

- `WindowsBase.dll`

  Se si utilizza una direttiva personalizzata, il processore di direttiva potrebbe caricare assembly aggiuntivi. Ad esempio, se si scrivono modelli per un linguaggio specifico di dominio (DSL), non è necessario scrivere direttive dell'assembly per gli assembly seguenti:

- `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`

- `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`

- `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`

- Assembly contenente il modello DSL.

## <a name="using-project-properties-in-both-msbuild-and-visual-studio"></a><a name="msbuild"></a>Uso delle proprietà del progetto in MSBuild e Visual Studio
 Visual Studio macro come $(SolutionDir) non funzionano in MSBuild. Se si desidera trasformare i modelli nel computer di compilazione, è necessario utilizzare le proprietà del progetto.

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

 È ora possibile utilizzare la proprietà del progetto nei modelli di testo, che si convertono correttamente in Visual Studio e in MSBuild:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
```

## <a name="see-also"></a>Vedi anche

- [Direttiva include T4](../modeling/t4-include-directive.md)
