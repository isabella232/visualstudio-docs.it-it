---
title: Elemento Import (MSBuild) | Microsoft Docs
description: Informazioni su MSBuild'elemento Import per importare il contenuto di un file di progetto in un altro file di progetto.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: c3fa19baefe0269d5b1818c65dd205635329771c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143326"
---
# <a name="import-element-msbuild"></a>Elemento Import (MSBuild)

Importa il contenuto di un file di progetto in un altro file di progetto.

\<Project>
\<Import>

## <a name="syntax"></a>Sintassi

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Project`|Attributo obbligatorio.<br /><br /> Percorso del file di progetto da importare. Il percorso può includere caratteri jolly. I file corrispondenti vengono importati in base all'ordine. Usando questa funzionalità, è possibile aggiungere codice a un progetto aggiungendo il file di codice a una directory.|
|`Condition`|Attributo facoltativo.<br /><br /> Una condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|
|`Sdk`| Attributo facoltativo.<br /><br /> Fa riferimento a un SDK di progetto.|

### <a name="child-elements"></a>Elementi figlio

 Nessuno

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un MSBuild di progetto. |
| [ImportGroup](../msbuild/importgroup-element.md) | Contiene una raccolta di elementi `Import` raggruppati in una condizione facoltativa. |

## <a name="remarks"></a>Commenti

 Tramite l'elemento `Import` , è possibile riutilizzare codice comune a più file di progetto. Ciò semplifica la gestione del codice, poiché tutti gli aggiornamenti apportati al codice condiviso vengono propagati a tutti i progetti che lo importano.

 Per convenzione, i file di progetto importati condivisi vengono salvati come file con estensione *targets,* ma sono file MSBuild file di progetto. MSBuild non impedisce l'importazione di un progetto con un'estensione di file diversa, ma è consigliabile usare l'estensione *targets* per coerenza.

 I percorsi relativi nei progetti importati vengono interpretati in relazione alla directory del progetto di importazione(con alcune eccezioni descritte più avanti in questo paragrafo). Pertanto, se uno stesso file di progetto viene importato in vari file di progetto che si trovano in posizioni diverse, i percorsi relativi nel file di progetto importato vengano interpretati in modo diverso per ogni progetto importato. Esistono due eccezioni. Un'eccezione è che `Import` negli elementi il percorso viene sempre interpretato rispetto al progetto che contiene l'elemento. `Import` Un'altra eccezione è `UsingTask` che interpreta sempre il percorso relativo per l'attributo relativo al file che contiene `AssemblyFile` `UsingTask` l'elemento .

 A MSBuild proprietà riservate correlate al file di progetto, ad esempio e , a cui viene fatto riferimento in un progetto importato, vengono assegnati valori in base al `MSBuildProjectDirectory` file di progetto di `MSBuildProjectFile` importazione.

 Se il progetto importato non ha un attributo `DefaultTargets` , i progetti importati vengono esaminati nell'ordine in cui sono importati e viene usato il valore del primo attributo `DefaultTargets` individuato. Se, ad esempio, ProjectA importa ProjectB e ProjectC (in questo ordine) e ProjectB importa ProjectD, MSBuild cerca prima specificato in `DefaultTargets` ProjectA, ProjectB, ProjectD e infine ProjectC.

 Lo schema di un progetto importato è identico a quello di un progetto standard. Sebbene MSBuild possibile compilare un progetto importato, è improbabile perché un progetto importato in genere non contiene informazioni sulle proprietà da impostare o sull'ordine in cui eseguire le destinazioni. Il progetto importato dipende dal progetto in cui viene importato per fornire tali informazioni.

## <a name="wildcards"></a>Caratteri jolly

 In .NET Framework 4, MSBuild consente l'uso di caratteri jolly nell'attributo Project. Quando sono presenti caratteri jolly, tutte le corrispondenze trovate vengono ordinate (per riproducibilità) e quindi vengono importate nell'ordine specificato come se l'ordine fosse stato impostato in modo esplicito.

 Ciò è utile se si desidera offrire un punto di estensibilità in modo che un altro utente possa importare un file senza che sia necessario aggiungere esplicitamente il nome del file al file di importazione. A questo scopo, *Microsoft.Common.Targets* contiene la riga seguente all'inizio del file.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>Esempio

 L'esempio seguente illustra un progetto con diversi elementi e proprietà che importa un file di progetto generale.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <resourcefile>Strings.resx</resourcefile>

        <compiledresources>
            $(O)\$(MSBuildProjectName).Strings.resources
        </compiledresources>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" />

        <Reference Include="System" />
        <Reference Include="System.Data" />
    </ItemGroup>

    <Import Project="$(CommonLocation)\General.targets" />
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Project riferimento allo schema di file](../msbuild/msbuild-project-file-schema-reference.md)
- [Procedura: Usare la stessa destinazione in più file di progetto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
