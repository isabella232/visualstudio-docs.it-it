---
title: 'CA2140: il codice Transparent non deve fare riferimento a elementi critici per la sicurezza | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c3e624e4210e59406fd1d5955cd37c2e83ed79a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602872"
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
 Metodo trasparente:

- gestisce un tipo di eccezione di sicurezza critico per la sicurezza

- dispone di un parametro contrassegnato come tipo critico di sicurezza

- dispone di un parametro generico con vincoli critical per la sicurezza

- dispone di una variabile locale di un tipo critico per la sicurezza

- fa riferimento a un tipo contrassegnato come critico per la sicurezza

- chiama un metodo contrassegnato come critico per la sicurezza

- fa riferimento a un campo contrassegnato come critico per la sicurezza

- Restituisce un tipo contrassegnato come critico per la sicurezza

## <a name="rule-description"></a>Descrizione della regola
 Un elemento di codice contrassegnato con l'attributo <xref:System.Security.SecurityCriticalAttribute> è critico per la sicurezza. Un metodo trasparente non può usare un elemento critico per la sicurezza. Se un tipo trasparente tenta di usare un tipo critico per la sicurezza, viene generato un <xref:System.TypeAccessException>, <xref:System.MethodAccessException> o <xref:System.FieldAccessException>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, effettuare una delle operazioni seguenti:

- Contrassegnare l'elemento di codice che usa il codice critico per la sicurezza con l'attributo <xref:System.Security.SecurityCriticalAttribute>

     \- oppure -

- Rimuovere l'attributo <xref:System.Security.SecurityCriticalAttribute> dagli elementi di codice contrassegnati come critici per la sicurezza e contrassegnarli invece con l'attributo <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityTransparentAttribute>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Negli esempi seguenti un metodo trasparente tenta di fare riferimento a una raccolta generica di sicurezza critica, un campo critico per la sicurezza e un metodo critico per la sicurezza.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>
