---
title: Proprietà di MSBuild | Microsoft Docs
description: Informazioni su MSBuild proprietà nome-valore possono passare valori alle attività, valutare le condizioni e archiviare i valori.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 2d1dec974c9271c12ab0780233a31361c4e7d359
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077179"
---
# <a name="msbuild-properties"></a>proprietà di MSBuild

Le proprietà sono coppie nome-valore che possono essere usate per configurare le compilazioni. Le proprietà sono utili per passare i valori alle attività, valutare le condizioni e archiviare i valori a cui si farà riferimento nel file di progetto.

## <a name="define-and-reference-properties-in-a-project-file"></a>Definire e fare riferimento alle proprietà in un file di progetto

 Per dichiarare le proprietà, è necessario creare un elemento con lo stesso nome della proprietà, come figlio di un elemento [PropertyGroup](../msbuild/propertygroup-element-msbuild.md). l codice XML seguente, ad esempio, crea una proprietà denominata `BuildDir` con un valore `Build`.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Nel file di progetto, per fare riferimento alle proprietà, si usa la sintassi $(\<PropertyName>). Ad esempio, per fare riferimento alla proprietà nell'esempio precedente, si usa $(BuildDir).

 I valori delle proprietà possono essere modificati ridefinendo la proprietà. È possibile assegnare un nuovo valore alla proprietà `BuildDir` usando questo codice XML:

```xml
<PropertyGroup>
    <BuildDir>Alternate</BuildDir>
</PropertyGroup>
```

 Le proprietà vengono valutate nell'ordine in cui sono visualizzate nel file di progetto. Il nuovo valore per `BuildDir` deve essere dichiarato dopo che è stato assegnato il valore precedente.

## <a name="reserved-properties"></a>Proprietà riservate

 In MSBuild alcuni nomi di proprietà sono riservati per archiviare le informazioni relative al file di progetto e ai file binari di MSBuild. Per fare riferimento a queste proprietà, si usa la notazione $, come per qualsiasi altra proprietà. Ad esempio, $(MSBuildProjectFile) restituisce il nome file completo del file di progetto, inclusa l'estensione di file.

 Per altre informazioni, vedere [Procedura: Fare](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) riferimento al nome o al percorso del file di progetto e MSBuild [proprietà riservate e note.](../msbuild/msbuild-reserved-and-well-known-properties.md)

## <a name="environment-properties"></a>Proprietà dell'ambiente

 È possibile fare riferimento alle variabili di ambiente nei file di progetto esattamente come si fa riferimento alle proprietà riservate. Ad esempio, per usare la variabile di ambiente `PATH` nel file di progetto, usare $(Path). Se il progetto contiene una definizione di una proprietà con lo stesso nome di una proprietà di ambiente, la proprietà nel progetto esegue l'override del valore della variabile di ambiente.

 A ogni progetto MSBuild è associato un blocco di ambiente isolato: nel relativo blocco personalizzato sono visualizzate solo le letture e le scritture.  Tramite MSBuild vengono lette le variabili di ambiente solo durante l'inizializzazione della raccolta di proprietà, prima che il file di progetto venga valutato o compilato. Successivamente, le proprietà dell'ambiente sono statiche, cioè ciascuno strumento generato inizia con gli stessi nomi e valori.

 Per ottenere il valore corrente delle variabili di ambiente [](../msbuild/property-functions.md) dall'interno di uno strumento generato, usare le funzioni di proprietà System.Environment.GetEnvironmentVariable. Il metodo consigliato, tuttavia, consiste nell'utilizzare il parametro dell'attività <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>. Le proprietà dell'ambiente impostate in questa matrice di stringhe possono essere passate allo strumento generato senza influire sulle variabili di ambiente del sistema.

> [!TIP]
> Non tutte le variabili di ambiente vengono lette per diventare proprietà iniziali. Tutte le variabili di ambiente il cui nome non è un nome di proprietà MSBuild valido, ad esempio "386", vengono ignorate.

 Per altre informazioni, vedere [Procedura: Usare variabili di ambiente in una compilazione.](../msbuild/how-to-use-environment-variables-in-a-build.md)

## <a name="registry-properties"></a>Proprietà del Registro di sistema

 È possibile leggere i valori del Registro di sistema usando la sintassi seguente, dove è l'hive del Registro di sistema `Hive` **(ad esempio, HKEY_LOCAL_MACHINE**), è il nome della chiave, è il nome della sottochiave e è il valore della `MyKey` `MySubKey` `Value` sottochiave.

```xml
$(registry:Hive\MyKey\MySubKey@Value)
```

 Per ottenere il valore della sottochiave predefinito, omettere `Value`.

```xml
$(registry:Hive\MyKey\MySubKey)
```

 Questo valore del Registro di sistema può essere usato per inizializzare una proprietà di compilazione. Ad esempio, per creare una proprietà di compilazione che rappresenta la home page del Web browser di Visual Studio, usare questo codice:

```xml
<PropertyGroup>
  <VisualStudioWebBrowserHomePage>
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\WebBrowser@HomePage)
  </VisualStudioWebBrowserHomePage>
<PropertyGroup>
```

## <a name="global-properties"></a>Proprietà globali

 MSBuild consente di impostare le proprietà nella riga di comando usando l'opzione **-property** (o **-p).** Questi valori delle proprietà globali eseguono l'override dei valori delle proprietà impostati nel file di progetto. incluse le proprietà di ambiente, ma non le proprietà riservate, che non possono essere modificate.

 L'esempio seguente imposta la proprietà `Configuration` globale su `DEBUG`.

```cmd
msbuild.exe MyProj.proj -p:Configuration=DEBUG
```

 Le proprietà globali possono anche essere impostate o modificate per i progetti figlio in una compilazione a più progetti usando l'attributo `Properties` dell'attività di MSBuild. Le proprietà globali vengono anche inoltrate ai progetti figlio, a meno che l'attributo `RemoveProperties` dell'attività MSBuild non venga usato per specificare l'elenco di proprietà da non inoltrare. Per altre informazioni, vedere MSBuild [attività](../msbuild/msbuild-task.md).

 Se si specifica una proprietà utilizzando l'attributo `TreatAsLocalProperty` in un tag di progetto, con il valore di quella proprietà globale non verrà sovrascritto il valore della proprietà impostata nel file di progetto. Per altre informazioni, vedere [Project (MSBuild)](../msbuild/project-element-msbuild.md) e [Procedura: Compilare](../msbuild/how-to-build-the-same-source-files-with-different-options.md)gli stessi file di origine con opzioni diverse.

## <a name="property-functions"></a>Funzioni delle proprietà

 A partire da .NET Framework versione 4 è possibile utilizzare funzioni delle proprietà per valutare gli script MSBuild. È possibile leggere l'ora di sistema, confrontare stringhe, trovare la corrispondenza per espressioni regolari ed eseguire numerose altre azioni nello script di compilazione senza usare le attività di MSBuild.

 È possibile usare metodi di stringa (istanza) per operare su qualsiasi valore della proprietà ed è possibile chiamare i metodi statici di diverse classi di sistema. È ad esempio possibile impostare una proprietà di compilazione sulla data odierna come segue.

```xml
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>
```

 Per altre informazioni e un elenco di funzioni di proprietà, vedere [Funzioni di proprietà](../msbuild/property-functions.md).

## <a name="create-properties-during-execution"></a>Creare proprietà durante l'esecuzione

 Alle proprietà non comprese in elementi `Target` vengono assegnati valori durante la fase di valutazione di una compilazione. Durante la fase di esecuzione successiva, le proprietà possono essere create o modificate come segue:

- Una proprietà può essere creata da qualsiasi attività. Per creare una proprietà, l'elemento [Task](../msbuild/task-element-msbuild.md) deve avere un elemento [Output](../msbuild/output-element-msbuild.md) figlio con un attributo `PropertyName`.

- Una proprietà può essere creata dall'attività [CreateProperty](../msbuild/createproperty-task.md). Questo utilizzo è deprecato.

- A partire da .NET Framework 3.5, gli elementi `Target` possono contenere elementi `PropertyGroup` che possono contenere dichiarazioni di proprietà.

## <a name="store-xml-in-properties"></a>Archiviare codice XML nelle proprietà

 Le proprietà possono contenere codice XML arbitrario, che consente di passare i valori alle attività o di visualizzare le informazioni di registrazione. L'esempio seguente illustra la proprietà `ConfigTemplate`, che ha un valore contenente codice XML e riferimenti ad altre proprietà. MSBuild sostituisce i riferimenti alle proprietà usando i rispettivi valori di proprietà. I valori delle proprietà vengono assegnati nell'ordine in cui sono visualizzati. In questo esempio quindi `$(MySupportedVersion)`, `$(MyRequiredVersion)` e `$(MySafeMode)` devono essere già stati definiti.

```xml
<PropertyGroup>
    <ConfigTemplate>
        <Configuration>
            <Startup>
                <SupportedRuntime
                    ImageVersion="$(MySupportedVersion)"
                    Version="$(MySupportedVersion)"/>
                <RequiredRuntime
                    ImageVersion="$(MyRequiredVersion)"
                    Version="$(MyRequiredVersion)"
                    SafeMode="$(MySafeMode)"/>
            </Startup>
        </Configuration>
    </ConfigTemplate>
</PropertyGroup>
```

## <a name="see-also"></a>Vedi anche

- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Procedura: Usare variabili di ambiente in una compilazione](../msbuild/how-to-use-environment-variables-in-a-build.md)
- [Procedura: Fare riferimento al nome o al percorso del file di progetto](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)
- [Procedura: Compilare gli stessi file di origine con opzioni diverse](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
- [Proprietà riservate e note MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
- [Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)
