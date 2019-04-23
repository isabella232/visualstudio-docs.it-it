---
title: 'CA2140: Il codice Transparent non deve fare riferimento a elementi SecurityCritical | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1990e781b5793b05166c6ff5b6e9c14141ffdd69
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60058603"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Il codice Transparent non deve far riferimento a elementi SecurityCritical
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Negli esempi seguenti, un metodo trasparente tenta di fare riferimento a una raccolta generica di sicurezza critiche, un campo di sicurezza critiche e un metodo SecurityCritical.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>
