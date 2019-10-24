---
title: Direttiva assembly T4
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f605748d4bda13567713b646f0232d684ec46fe1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748181"
---
# <a name="t4-assembly-directive"></a>Direttiva assembly T4

In un modello di testo della fase di progettazione di Visual Studio, la direttiva `assembly` carica un assembly in modo che il codice del modello possa usare i relativi tipi. L'effetto è simile all'aggiunta di un riferimento a un assembly in un progetto di Visual Studio.

 Per una panoramica generale sulla scrittura di modelli di testo, vedere [scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> La direttiva `assembly` in un modello di testo (pre-elaborato) della fase di esecuzione non è necessaria. Aggiungere invece gli assembly necessari ai **riferimenti** del progetto di Visual Studio.

## <a name="using-the-assembly-directive"></a>Utilizzo della direttiva Assembly
 La sintassi della direttiva è la seguente:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Il nome dell'assembly deve essere uno dei seguenti:

- Il nome sicuro dell'assembly nella GAC, quale `System.Xml.dll`. È inoltre possibile utilizzare la forma estesa, quale `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Per ulteriori informazioni, vedere <xref:System.Reflection.AssemblyName>.

- Il percorso assoluto dell'assembly

  È possibile usare la sintassi `$(variableName)` per fare riferimento a variabili di Visual Studio, ad esempio `$(SolutionDir)` e `%VariableName%` per fare riferimento alle variabili di ambiente. Esempio:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 La direttiva dell'assembly non ha alcun effetto in un modello di testo pre-elaborato. In alternativa, includere i riferimenti necessari nella sezione **riferimenti** del progetto di Visual Studio. Per altre informazioni, vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

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

## <a name="msbuild"></a>Uso delle proprietà del progetto in MSBuild e Visual Studio
 Le macro di Visual Studio, ad esempio $ (SolutionDir), non funzionano in MSBuild. Se si desidera trasformare i modelli nel computer di compilazione, è necessario utilizzare le proprietà del progetto.

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

## <a name="see-also"></a>Vedere anche

- [Direttiva include T4](../modeling/t4-include-directive.md)