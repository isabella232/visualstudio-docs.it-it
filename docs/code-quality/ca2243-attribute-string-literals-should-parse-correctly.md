---
title: 'CA2243: I valori letterali stringa di attributo devono essere analizzati correttamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2627e94dbdd0504b164fee3ecd95dc99b3094db7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237823"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: I valori letterali stringa di attributo devono essere analizzati correttamente

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Il parametro valore letterale stringa di un attributo non viene analizzato correttamente per un URL, un GUID o una versione.

## <a name="rule-description"></a>Descrizione della regola
Poiché gli attributi sono derivati da <xref:System.Attribute?displayProperty=fullName>e gli attributi vengono utilizzati in fase di compilazione, solo i valori costanti possono essere passati ai relativi costruttori. I parametri di attributo che devono rappresentare URL, GUID e versioni non possono essere tipizzati <xref:System.Guid?displayProperty=fullName>come <xref:System.Uri?displayProperty=fullName>, <xref:System.Version?displayProperty=fullName>e, perché questi tipi non possono essere rappresentati come costanti. Ma devono essere rappresentati da stringhe.

Poiché il parametro è tipizzato come stringa, è possibile che un parametro formattato in modo non corretto possa essere passato in fase di compilazione.

Questa regola utilizza un approccio euristico di denominazione per individuare i parametri che rappresentano un URI (Uniform Resource Identifier), un identificatore univoco globale (GUID) o una versione e verifica che il valore passato sia corretto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Modificare la stringa del parametro in un URL, un GUID o una versione correttamente formattato.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola se il parametro non rappresenta un URL, un GUID o una versione.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato il codice per AssemblyFileVersionAttribute che viola questa regola.

[!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

La regola viene attivata con i parametri seguenti:

- I parametri che contengono ' version ' e non possono essere analizzati in System. Version.

- I parametri che contengono ' GUID ' e non possono essere analizzati in System. Guid.

- I parametri che contengono ' URI ',' urn ' o ' URL ' e non possono essere analizzati in System. Uri.

## <a name="see-also"></a>Vedere anche

- [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)