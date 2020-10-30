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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62031255daca971345b2dd3dbc7c37eb7f4003c9
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046379"
---
# <a name="msbuild-conditions"></a>Condizioni di MSBuild

MSBuild supporta un set specifico di condizioni che possono essere applicate ovunque `Condition` sia consentito un attributo. La tabella seguente illustra tali condizioni.

|Condizione|Descrizione|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Restituisce `true` se `stringA` è uguale a `stringB`.<br /><br /> Ad esempio:<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti. Questo controllo non fa distinzione tra maiuscole e minuscole.|
|'`stringA`' != '`stringB`'|Restituisce `true` se `stringA` non è uguale a `stringB`.<br /><br /> Ad esempio:<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti. Questo controllo non fa distinzione tra maiuscole e minuscole.|
|\<, >, \<=, >=|Restituisce i valori numerici degli operandi. Restituisce `true` se la valutazione relazionale è true. Gli operandi devono restituire un numero decimale o esadecimale. I numeri esadecimali devono iniziare con "0x". **Nota:** in XML i caratteri `<` e `>` devono essere preceduti da un carattere di escape. Il simbolo `<` viene rappresentato come `&lt;`. Il simbolo `>` viene rappresentato come `&gt;`.|
|Exists('`stringA`')|Restituisce `true` se esiste un file o una cartella con il nome `stringA`.<br /><br /> Ad esempio:<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti.|
|HasTrailingSlash('`stringA`')|Restituisce `true` se la stringa specificata contiene un carattere di barra (/) o di barra rovesciata (\\) finale.<br /><br /> Ad esempio:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti.|
|!|Restituisce `true` se l'operando restituisce `false`.|
|`And`|Restituisce `true` se entrambi gli operandi restituiscono `true`.|
|`Or`|Restituisce `true` se almeno uno degli operandi restituisce `true`.|
|()|Meccanismo di raggruppamento che restituisce `true` se le espressioni contenute all'interno restituiscono `true`.|
|$if$ ( %expression% ), $else$, $endif$|Controlla se l'oggetto `%expression%` specificato corrisponde al valore stringa del parametro di modello personalizzato passato. Se la condizione `$if$` restituisce `true`, le istruzioni vengono eseguite. In caso contrario, viene controllata la condizione `$else$`. Se la condizione `$else$` è `true`, le istruzioni vengono eseguite. In caso contrario, la condizione `$endif$` termina la valutazione dell'espressione.<br /><br /> Per esempi di utilizzo, vedere [logica dei parametri del modello di progetto/elemento di Visual Studio](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

È possibile usare i metodi di stringa in condizioni, come illustrato nell'esempio seguente, in cui la funzione [trirammenda ()](/dotnet/api/system.string.trimend) viene usata per confrontare solo la parte pertinente della stringa, per distinguere tra .NET Framework e i Framework di destinazione .NET Core.

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

Nei file di progetto MSBuild non esiste alcun tipo booleano vero. I dati booleani sono rappresentati in proprietà che possono essere vuote o impostate su qualsiasi valore. Pertanto, `'$(Prop)' == 'true'` significa "If prop is `true` ,", ma `'$(Prop)' != 'false'` significa "If prop è `true` o unannullato o impostato su qualcos'altro".

La logica booleana viene valutata solo nel contesto delle condizioni, quindi le impostazioni delle proprietà come `<Prop2>'$(Prop1)' == 'true'</Prop>` sono rappresentate come stringa (dopo l'espansione della variabile), non valutate come valori booleani.  

MSBuild implementa alcune regole di elaborazione speciali per semplificare l'utilizzo delle proprietà di stringa utilizzate come valori booleani. I valori letterali booleani sono accettati, quindi `Condition="true"` e `Condition="false"` funzionano come previsto. MSBuild include inoltre regole speciali per supportare l'operatore di negazione booleano. Quindi, se `$(Prop)` è' true ', si `!$(Prop)` espande a `!true` e questo confronto è uguale a `false` , come previsto.

## <a name="see-also"></a>Vedi anche

- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Costrutti condizionali](../msbuild/msbuild-conditional-constructs.md)
- [Procedura dettagliata: Creazione di un nuovo file di progetto MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
