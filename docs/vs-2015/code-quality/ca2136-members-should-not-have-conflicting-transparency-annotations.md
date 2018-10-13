---
title: 'CA2136: I membri non devono avere annotazioni di trasparenza in conflitto | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a45e949733acc923c4d4dc2ab5ee102ee8367ff6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280137"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: I membri non devono avere annotazioni di trasparenza in conflitto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Questa regola viene attivata quando un membro del tipo è contrassegnato con un <xref:System.Security> attributo di sicurezza che dispone di una trasparenza diversa rispetto all'attributo di sicurezza di un contenitore del membro.

## <a name="rule-description"></a>Descrizione della regola
 Gli attributi di trasparenza vengono applicati da elementi di codice con un ambito più ampio a elementi con ambito più ridotto. Gli attributi di trasparenza di elementi di codice che presentano un ambito più ampio hanno la precedenza su quelli contenuti nel primo elemento. Ad esempio, una classe contrassegnata con il <xref:System.Security.SecurityCriticalAttribute> attributo non può contenere un metodo contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute> attributo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere questa violazione, rimuovere l'attributo di sicurezza dall'elemento di codice che ha un ambito più basso o modificare il relativo attributo per corrispondere all'elemento di codice che lo contiene.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare gli avvisi da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente, un metodo è contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute> attributo ed è un membro di una classe contrassegnata con il <xref:System.Security.SecurityCriticalAttribute> attributo. L'attributo di protezione sicura deve essere rimosso.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]



