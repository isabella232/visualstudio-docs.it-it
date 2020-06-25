---
title: Condizioni di MSBuild | Microsoft Docs
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
ms.openlocfilehash: fea7763bf1cbce5fac36ce2cd5e54c40e1da989a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289235"
---
# <a name="msbuild-conditions"></a>Condizioni di MSBuild

MSBuild supporta un set specifico di condizioni che possono essere applicate ovunque `Condition` sia consentito un attributo. La tabella seguente illustra tali condizioni.

|Condizione|Description|
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

## <a name="see-also"></a>Vedi anche

- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Costrutti condizionali](../msbuild/msbuild-conditional-constructs.md)
- [Procedura dettagliata: Creazione di un nuovo file di progetto MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
