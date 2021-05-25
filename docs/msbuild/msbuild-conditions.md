---
title: Condizioni di MSBuild | Microsoft Docs
description: Informazioni su come MSBuild supporta un set specifico di condizioni che possono essere applicate ovunque sia consentito un attributo Condition.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
- Exists, MSBuild condition function
- HasTrailingSlash, MSBuild condition function
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76bafaf5192c59e0f23078e396ae553b3023e060
ms.sourcegitcommit: d3577395cf016f2836eb5a3c1d496cca6d449baa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2021
ms.locfileid: "110413325"
---
# <a name="msbuild-conditions"></a>Condizioni di MSBuild

MSBuild supporta un set specifico di condizioni che possono essere applicate ovunque sia `Condition` consentito un attributo. La tabella seguente illustra tali condizioni.

|Condizione|Descrizione|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Restituisce `true` se `stringA` è uguale a `stringB`.<br /><br /> Ad esempio:<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti. Questo controllo non fa distinzione tra maiuscole e minuscole.|
|'`stringA`' != '`stringB`'|Restituisce `true` se `stringA` non è uguale a `stringB`.<br /><br /> Ad esempio:<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti. Questo controllo non fa distinzione tra maiuscole e minuscole.|
|\<, >, \<=, >=|Restituisce i valori numerici degli operandi. Restituisce `true` se la valutazione relazionale è true. Gli operandi devono restituire un numero decimale o esadecimale o una versione punteggiata in quattro parti. I numeri esadecimali devono iniziare con "0x". **Nota:** in XML i caratteri `<` e `>` devono essere preceduti da un carattere di escape. Il simbolo `<` viene rappresentato come `&lt;`. Il simbolo `>` viene rappresentato come `&gt;`.|
|Exists('`stringA`')|Restituisce `true` se esiste un file o una cartella con il nome `stringA`.<br /><br /> Ad esempio:<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti.|
|HasTrailingSlash('`stringA`')|Restituisce `true` se la stringa specificata contiene un carattere di barra (/) o di barra rovesciata (\\) finale.<br /><br /> Ad esempio:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti.|
|!|Restituisce `true` se l'operando restituisce `false`.|
|`And`|Restituisce `true` se entrambi gli operandi restituiscono `true`.|
|`Or`|Restituisce `true` se almeno uno degli operandi restituisce `true`.|
|()|Meccanismo di raggruppamento che restituisce `true` se le espressioni contenute all'interno restituiscono `true`.|
|$if$ ( %expression% ), $else$, $endif$|Controlla se l'oggetto `%expression%` specificato corrisponde al valore stringa del parametro di modello personalizzato passato. Se la condizione `$if$` restituisce `true`, le istruzioni vengono eseguite. In caso contrario, viene controllata la condizione `$else$`. Se la condizione `$else$` è `true`, le istruzioni vengono eseguite. In caso contrario, la condizione `$endif$` termina la valutazione dell'espressione.<br /><br /> Per esempi di utilizzo, vedere Visual Studio logica dei parametri del modello [di progetto/elemento.](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic)|

È possibile usare metodi stringa nelle condizioni, come illustrato nell'esempio seguente, in cui la funzione [TrimEnd()](/dotnet/api/system.string.trimend) viene usata per confrontare solo la parte pertinente della stringa, per distinguere tra framework di destinazione .NET Framework e .NET Core.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

Nei file di progetto MSBuild non esiste un vero tipo booleano. I dati booleani sono rappresentati in proprietà che potrebbero essere vuote o impostate su qualsiasi valore. Pertanto, `'$(Prop)' == 'true'` indica "se Prop è ," ma indica "se Prop è o non è impostato o impostato su un altro `true` `'$(Prop)' != 'false'` `true` elemento".

La logica booleana viene valutata solo nel contesto delle condizioni, quindi le impostazioni delle proprietà, ad esempio sono rappresentate come stringa (dopo l'espansione della variabile), non valutate `<Prop2>'$(Prop1)' == 'true'</Prop>` come valori booleani.  

MSBuild implementa alcune regole di elaborazione speciali per semplificare l'uso delle proprietà stringa usate come valori booleani. I valori letterali booleani vengono accettati e `Condition="true"` `Condition="false"` funzionano come previsto. MSBuild include anche regole speciali per supportare l'operatore di negazione booleano. Pertanto, se è "true", si espande in e viene `$(Prop)` `!$(Prop)` `!true` confrontato con `false` , come ci si aspetterebbe.

## <a name="comparing-versions"></a>Confronto tra versioni

Gli operatori relazionali , , e supportano le versioni analizzate da , in modo da poter confrontare tra loro versioni con quattro `<` `>` parti `<=` `>=` <xref:System.Version?displayProperty=fullName> numeriche. Ad `'1.2.3.4' < '1.10.0.0'` esempio, è `true` .

> [!CAUTION]
> `System.Version` I confronti possono produrre risultati sorprendenti quando una o entrambe le versioni non specificano tutte e quattro le parti. Ad esempio, la versione 1.1 è precedente alla versione 1.1.0.

MSBuild fornisce [funzioni di proprietà per confrontare le](property-functions.md#MSBuild-version-comparison-functions) versioni con un set diverso di regole compatibili con il controllo delle versioni semantico (semver).

## <a name="see-also"></a>Vedi anche

- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Costrutti condizionali](../msbuild/msbuild-conditional-constructs.md)
- [Procedura dettagliata: Creazione di un nuovo file di progetto MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
