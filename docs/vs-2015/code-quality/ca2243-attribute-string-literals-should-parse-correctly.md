---
title: 'CA2243: Valori letterali stringa di attributo devono essere analizzate correttamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 770c805489e358252151dc8e777941a267f76363
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965461"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: I valori letterali stringa di attributo devono essere analizzati correttamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 Questa regola viene utilizzata un'euristica dei nomi per trovare i parametri che rappresentano un uniform resource identifier (URI), un identificatore univoco globale (GUID, Globally Unique Identifier) o una versione e verifica che il valore passato sia corretto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare la stringa di parametri a un URL, GUID o versione in formato corretto.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il parametro non rappresenta un URL, GUID o versione.

## <a name="example"></a>Esempio
 L'esempio seguente illustra codice per il AssemblyFileVersionAttribute che violano questa regola.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 La regola viene attivata dagli elementi seguenti:

-   Parametri che contengono 'version' e non possono essere analizzati per Version.

-   Parametri che contengono "guid" e non possono essere analizzati da System. GUID.

-   Parametri che contengono 'uri', 'urn' o 'url' e non possono essere analizzati in System. Uri.

## <a name="see-also"></a>Vedere anche
 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
