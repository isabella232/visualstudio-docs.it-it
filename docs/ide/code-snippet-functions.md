---
title: Funzioni dei frammenti di codice
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7cf31fed530447af986d96418d06cf46f02b14b1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907813"
---
# <a name="code-snippet-functions"></a>Funzioni dei frammenti di codice

Con i frammenti di codice C# è possibile usare tre funzioni. Le funzioni sono specificate nell'elemento [Function](../ide/code-snippets-schema-reference.md#function-element) del frammento di codice. Per informazioni sulla creazione di frammenti di codice, vedere [Frammenti di codice](../ide/code-snippets.md).

## <a name="functions"></a>Funzioni

Nella tabella seguente vengono descritte le funzioni disponibili per l'uso con l'elemento `Function` nei frammenti di codice.

|Funzione|Description|Linguaggio|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Genera un'istruzione switch e un set di istruzioni case per i membri dell'enumerazione specificata dal parametro `EnumerationLiteral`. Il parametro `EnumerationLiteral` deve essere un riferimento a un valore letterale di enumerazione o un tipo di enumerazione.|C#|
|`ClassName()`|Restituisce il nome della classe che contiene il frammento inserito.|C#|
|`SimpleTypeName(` `TypeName` `)`|Riduce il parametro *TypeName* alla forma più semplice nel contesto in cui il frammento è stato richiamato.|C#|

## <a name="example"></a>Esempio

L'esempio seguente illustra come usare la funzione `GenerateSwitchCases`. Quando questo frammento viene inserito e un'enumerazione viene immessa nel valore letterale `$switch_on$`, il valore letterale `$cases$` genera un'istruzione `case` per ogni valore presente nell'enumerazione.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>switch</Title>
            <Shortcut>switch</Shortcut>
            <Description>Code snippet for switch statement</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>expression</ID>
                    <ToolTip>Expression to switch on</ToolTip>
                    <Default>switch_on</Default>
                </Literal>
                <Literal Editable="false">
                    <ID>cases</ID>
                    <Function>GenerateSwitchCases($expression$)</Function>
                    <Default>default:</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    switch ($expression$)
                    {
                        $cases$
                    }
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="example"></a>Esempio

L'esempio seguente illustra come usare la funzione `ClassName`. Quando questo frammento viene inserito, il valore letterale `$classname$` viene sostituito con il nome della classe contenitore nella posizione corrispondente nel file di codice.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Common constructor pattern</Title>
            <Shortcut>ctor</Shortcut>
            <Description>Code Snippet for a constructor</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>type</ID>
                    <Default>int</Default>
                </Literal>
                <Literal>
                    <ID>name</ID>
                    <Default>field</Default>
                </Literal>
                <Literal default="true" Editable="false">
                    <ID>classname</ID>
                    <ToolTip>Class name</ToolTip>
                    <Function>ClassName()</Function>
                    <Default>ClassNamePlaceholder</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp" Format="CData">
                <![CDATA[
                    public $classname$ ($type$ $name$)
                    {
                        this._$name$ = $name$;
                    }
                    private $type$ _$name$;
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="example"></a>Esempio

In questo esempio viene illustrato come usare la funzione `SimpleTypeName`. Quando questo frammento viene inserito in un file di codice, il valore letterale `$SystemConsole$` verrà sostituito con la forma più semplice del tipo <xref:System.Console> nel contesto in cui il frammento è stato richiamato.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Console_WriteLine</Title>
            <Shortcut>cw</Shortcut>
            <Description>Code snippet for Console.WriteLine</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal Editable="false">
                    <ID>SystemConsole</ID>
                    <Function>SimpleTypeName(global::System.Console)</Function>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    $SystemConsole$.WriteLine();
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Vedere anche

- [Elemento Function](../ide/code-snippets-schema-reference.md#function-element)
- [Informazioni di riferimento sullo schema dei frammenti di codice](../ide/code-snippets-schema-reference.md)
