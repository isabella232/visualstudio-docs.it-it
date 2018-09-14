---
title: 'CA2140: Il codice Transparent non deve far riferimento a elementi SecurityCritical'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98f7793890bc938f6f1e89f653985b91a99393a9
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548277"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Il codice Transparent non deve far riferimento a elementi SecurityCritical

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un metodo trasparente:

- gestisce un tipo di eccezione di sicurezza critico per la protezione

- ha un parametro contrassegnato come un tipo SecurityCritical

- ha un parametro generico con vincoli SecurityCritical

- dispone di una variabile locale di un tipo SecurityCritical

- fa riferimento a un tipo contrassegnato come sicurezza critico

- chiama un metodo contrassegnato come sicurezza critico

- fa riferimento a un campo contrassegnato come sicurezza critico

- Restituisce un tipo contrassegnato come sicurezza critico

## <a name="rule-description"></a>Descrizione della regola

Un elemento di codice contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> attributo sia critico per la sicurezza. Un metodo trasparente non può usare un elemento critico per la sicurezza. Se un tipo trasparente tenta di usare un tipo SecurityCritical una <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , o <xref:System.FieldAccessException> viene generato.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, eseguire una delle operazioni seguenti:

- Contrassegnare l'elemento di codice che usa il codice SecurityCritical con il <xref:System.Security.SecurityCriticalAttribute> attributo

     \- oppure -

- Rimuovere il <xref:System.Security.SecurityCriticalAttribute> attributo dagli elementi di codice che sono contrassegnati come SecurityCritical e contrassegnarli invece con il <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityTransparentAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio

Negli esempi seguenti, un metodo trasparente tenta di fare riferimento a una raccolta generica di sicurezza critiche, un campo di sicurezza critiche e un metodo SecurityCritical.

[!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityCriticalAttribute>
- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityTreatAsSafeAttribute>
- <xref:System.Security?displayProperty=fullName>