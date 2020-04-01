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
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d51aa0a5ef995abbe150160e378aa8885cc9706
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472677"
---
# <a name="msbuild-conditions"></a>Condizioni di MSBuild

MSBuild supporta un set specifico di condizioni `Condition` che possono essere applicate ovunque sia consentito un attributo. La tabella seguente illustra tali condizioni.

|Condizione|Descrizione|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Restituisce `true` se `stringA` è uguale a `stringB`.<br /><br /> Ad esempio:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti.|
|'`stringA`' != '`stringB`'|Restituisce `true` se `stringA` non è uguale a `stringB`.<br /><br /> Ad esempio:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti.|
|\<, >, \<=, >=|Restituisce i valori numerici degli operandi. Restituisce `true` se la valutazione relazionale è true. Gli operandi devono restituire un numero decimale o esadecimale. I numeri esadecimali devono iniziare con "0x". **Nota:** in XML i caratteri `<` e `>` devono essere preceduti da un carattere di escape. Il simbolo `<` viene rappresentato come `&lt;`. Il simbolo `>` viene rappresentato come `&gt;`.|
|Exists('`stringA`')|Restituisce `true` se esiste un file o una cartella con il nome `stringA`.<br /><br /> Ad esempio:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti.|
|HasTrailingSlash('`stringA`')|Restituisce `true` se la stringa specificata contiene un carattere di barra (/) o di barra rovesciata (\\) finale.<br /><br /> Ad esempio:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti.|
|!|Restituisce `true` se l'operando restituisce `false`.|
|e|Restituisce `true` se entrambi gli operandi restituiscono `true`.|
|Oppure|Restituisce `true` se almeno uno degli operandi restituisce `true`.|
|()|Meccanismo di raggruppamento che restituisce `true` se le espressioni contenute all'interno restituiscono `true`.|
|$if$ ( %expression% ), $else$, $endif$|Controlla se l'oggetto `%expression%` specificato corrisponde al valore stringa del parametro di modello personalizzato passato. Se la condizione `$if$` restituisce `true`, le istruzioni vengono eseguite. In caso contrario, viene controllata la condizione `$else$`. Se la condizione `$else$` è `true`, le istruzioni vengono eseguite. In caso contrario, la condizione `$endif$` termina la valutazione dell'espressione.<br /><br /> Per esempi di utilizzo, vedere Logica dei parametri del [modello di progetto/elemento](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic)di Visual Studio.|

È possibile utilizzare i metodi stringa nelle condizioni, <xref:System.String.TrimEnd> come illustrato nell'esempio seguente, in cui la funzione viene utilizzata per confrontare solo la parte rilevante della stringa, per distinguere tra i framework di destinazione di .NET Framework e .NET Core.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd('0123456789.'))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)
- [Costrutti condizionali](../msbuild/msbuild-conditional-constructs.md)
- [Procedura dettagliata: creazione di un file di progetto MSBuild da zeroWalkthrough: Creating an MSBuild project file from scratch](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
