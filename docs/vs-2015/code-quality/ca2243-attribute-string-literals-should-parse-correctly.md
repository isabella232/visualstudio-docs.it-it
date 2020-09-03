---
title: 'CA2243: i valori letterali stringa di attributo devono essere analizzati correttamente | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 09e932651576f9b6d595657ad024b8f2697ad016
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535746"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: I valori letterali stringa di attributo devono essere analizzati correttamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Il parametro valore letterale stringa di un attributo non viene analizzato correttamente per un URL, un GUID o una versione.

## <a name="rule-description"></a>Descrizione della regola
 Poiché gli attributi sono derivati da <xref:System.Attribute?displayProperty=fullName> e gli attributi vengono utilizzati in fase di compilazione, solo i valori costanti possono essere passati ai relativi costruttori. I parametri di attributo che devono rappresentare URL, GUID e versioni non possono essere tipizzati come <xref:System.Uri?displayProperty=fullName> , <xref:System.Guid?displayProperty=fullName> e <xref:System.Version?displayProperty=fullName> , perché questi tipi non possono essere rappresentati come costanti. Ma devono essere rappresentati da stringhe.

 Poiché il parametro è tipizzato come stringa, è possibile che un parametro formattato in modo non corretto possa essere passato in fase di compilazione.

 Questa regola utilizza un approccio euristico di denominazione per individuare i parametri che rappresentano un URI (Uniform Resource Identifier), un identificatore univoco globale (GUID) o una versione e verifica che il valore passato sia corretto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare la stringa del parametro in un URL, un GUID o una versione correttamente formattato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il parametro non rappresenta un URL, un GUID o una versione.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato il codice per AssemblyFileVersionAttribute che viola questa regola.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 La regola viene attivata da quanto segue:

- I parametri che contengono ' version ' e non possono essere analizzati in System. Version.

- I parametri che contengono ' GUID ' e non possono essere analizzati in System. Guid.

- I parametri che contengono ' URI ',' urn ' o ' URL ' e non possono essere analizzati in System. Uri.

## <a name="see-also"></a>Vedere anche
 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
