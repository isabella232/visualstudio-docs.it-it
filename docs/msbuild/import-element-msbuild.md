---
title: Elemento Import (MSBuild) | Microsoft Docs
description: Informazioni su come MSBuild usa l'elemento Import per importare il contenuto di un file di progetto in un altro file di progetto.
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
ms.workload:
- multiple
ms.openlocfilehash: c3a0d22019a0c7722b135392c53c7f9bfbcaab69
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914107"
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

 nessuno

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto MSBuild. |
| [ImportGroup](../msbuild/importgroup-element.md) | Contiene una raccolta di elementi `Import` raggruppati in una condizione facoltativa. |

## <a name="remarks"></a>Commenti

 Tramite l'elemento `Import` , è possibile riutilizzare codice comune a più file di progetto. Ciò semplifica la gestione del codice, poiché tutti gli aggiornamenti apportati al codice condiviso vengono propagati a tutti i progetti che lo importano.

 Per convenzione, i file di progetto condivisi importati vengono salvati come file con *estensione targets* , ma sono file di progetto MSBuild standard. MSBuild non impedisce l'importazione di un progetto con una diversa estensione del nome di file, ma è consigliabile usare l'estensione *. targets* per coerenza.

 I percorsi relativi nei progetti importati vengono interpretati in relazione alla directory del progetto di importazione (con alcune eccezioni descritte più avanti in questo paragrafo). Pertanto, se uno stesso file di progetto viene importato in vari file di progetto che si trovano in posizioni diverse, i percorsi relativi nel file di progetto importato vengano interpretati in modo diverso per ogni progetto importato. Sono presenti due eccezioni. Un'eccezione è che negli `Import` elementi, il percorso viene sempre interpretato in relazione al progetto che contiene l' `Import` elemento. Un'altra eccezione è che `UsingTask` interpreta sempre il percorso relativo dell' `AssemblyFile` attributo rispetto al file che contiene l' `UsingTask` elemento.

 A tutte le proprietà riservate di MSBuild correlate al file di progetto, ad esempio `MSBuildProjectDirectory` e `MSBuildProjectFile` , a cui viene fatto riferimento in un progetto importato vengono assegnati valori basati sul file di progetto che esegue l'importazione.

 Se il progetto importato non ha un attributo `DefaultTargets` , i progetti importati vengono esaminati nell'ordine in cui sono importati e viene usato il valore del primo attributo `DefaultTargets` individuato. Se, ad esempio, Projecta importa ProjectB e ProjectC (in questo ordine) e ProjectB Imports proiettati, MSBuild cerca innanzitutto `DefaultTargets` specificato in ProjectA, quindi ProjectB, quindi proiettato e infine ProjectC.

 Lo schema di un progetto importato è identico a quello di un progetto standard. Sebbene MSBuild possa essere in grado di compilare un progetto importato, è improbabile che un progetto importato non contenga informazioni sulle proprietà da impostare o sull'ordine in cui eseguire le destinazioni. Il progetto importato dipende dal progetto in cui viene importato per fornire tali informazioni.

## <a name="wildcards"></a>Caratteri jolly

 In .NET Framework 4, MSBuild consente l'uso di caratteri jolly nell'attributo Project. Quando sono presenti caratteri jolly, tutte le corrispondenze trovate vengono ordinate (per riproducibilità) e quindi vengono importate nell'ordine specificato come se l'ordine fosse stato impostato in modo esplicito.

 Ciò è utile se si desidera offrire un punto di estensibilità in modo che un altro utente possa importare un file senza che sia necessario aggiungere esplicitamente il nome del file al file di importazione. A questo scopo, *Microsoft. Common. targets* contiene la riga seguente all'inizio del file.

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

- [Riferimento allo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
- [Procedura: usare la stessa destinazione in più file di progetto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
