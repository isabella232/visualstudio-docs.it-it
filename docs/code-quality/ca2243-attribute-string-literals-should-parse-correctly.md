---
title: 'CA2243: Valori letterali stringa di attributo devono essere analizzate correttamente'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6c7aa4638a1a0a863bf53c85a5e182f57a366d8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939992"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Valori letterali stringa di attributo devono essere analizzate correttamente

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Parametro dell'attributo del valore letterale stringa non analizza correttamente per un URL, GUID o versione.

## <a name="rule-description"></a>Descrizione della regola
 Poiché gli attributi sono derivati da <xref:System.Attribute?displayProperty=fullName>e gli attributi vengono utilizzati in fase di compilazione, solo i valori costanti possono essere passati ai relativi costruttori. Parametri dell'attributo che devono rappresentare gli URL, GUID e le versioni non possono essere tipizzati come <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, e <xref:System.Version?displayProperty=fullName>, perché questi tipi non possono essere rappresentati come costanti. Invece, devono essere rappresentati da stringhe.

 Poiché il parametro è tipizzato come una stringa, è possibile che un parametro di formato non corretto può essere passato in fase di compilazione.

 Questa regola viene utilizzata un'euristica dei nomi per trovare i parametri che rappresentano un identificatore di risorsa uniforme (URI), un identificatore univoco globale (GUID, Globally Unique Identifier) o una versione e verifica che il valore passato sia corretto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare la stringa di parametri a un URL, GUID o versione in formato corretto.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se il parametro non rappresenta un URL, GUID o versione.

## <a name="example"></a>Esempio
 L'esempio seguente illustra codice per il AssemblyFileVersionAttribute che violano questa regola.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

 La regola viene attivata dai parametri seguenti:

- Parametri che contengono 'version' e non possono essere analizzati per Version.

- Parametri che contengono "guid" e non possono essere analizzati da System. GUID.

- Parametri che contengono 'uri', 'urn' o 'url' e non possono essere analizzati in System. Uri.

## <a name="see-also"></a>Vedere anche

- [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)