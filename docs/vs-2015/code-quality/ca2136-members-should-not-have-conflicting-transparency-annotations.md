---
title: 'CA2136: i membri non devono avere annotazioni di trasparenza in conflitto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3a17a0db7dd4ad1c57d23104a313a78cd1289ed
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547693"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: I membri non devono avere annotazioni di trasparenza in conflitto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Questa regola viene attivata quando un membro di un tipo è contrassegnato con un <xref:System.Security> attributo di sicurezza con una trasparenza diversa rispetto all'attributo di sicurezza di un contenitore del membro.

## <a name="rule-description"></a>Descrizione della regola
 Gli attributi di trasparenza vengono applicati da elementi di codice con un ambito più ampio a elementi con ambito più ridotto. Gli attributi di trasparenza di elementi di codice che presentano un ambito più ampio hanno la precedenza su quelli contenuti nel primo elemento. Una classe contrassegnata con l'attributo, ad esempio, <xref:System.Security.SecurityCriticalAttribute> non può contenere un metodo contrassegnato con l' <xref:System.Security.SecuritySafeCriticalAttribute> attributo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere questa violazione, rimuovere l'attributo di sicurezza dall'elemento di codice con ambito inferiore oppure modificare l'attributo in modo che corrisponda all'elemento di codice contenitore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare gli avvisi da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente un metodo è contrassegnato con l' <xref:System.Security.SecuritySafeCriticalAttribute> attributo ed è un membro di una classe contrassegnata con l' <xref:System.Security.SecurityCriticalAttribute> attributo. È necessario rimuovere l'attributo security safe.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
