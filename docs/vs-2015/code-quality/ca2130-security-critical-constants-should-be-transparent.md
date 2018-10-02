---
title: 'CA2130: Le costanti SecurityCritical devono essere transparent | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a74d6fe3c0507914fa4bd9723a53579db230c467
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589595"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: Le costanti SecurityCritical devono essere Transparent
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2130: le costanti SecurityCritical devono essere transparent](https://docs.microsoft.com/visualstudio/code-quality/ca2130-security-critical-constants-should-be-transparent).

|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un campo costante o un membro di enumerazione è contrassegnato con il <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Descrizione della regola
 L'imposizione della trasparenza non viene applicata ai valori costanti perché i compilatori rendono inline valori costanti in modo che non sia richiesta alcuna ricerca in fase di esecuzione. I campi costanti devono essere trasparenti per la sicurezza in modo che i revisori del codice non suppongano che il codice trasparente non possa accedere alla costante.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere l'attributo SecurityCritical dal campo o valore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Negli esempi seguenti, il valore enum `EnumWithCriticalValues.CriticalEnumValue` e la costante `CriticalConstant` generava questo avviso. Per risolvere i problemi, rimuovere il [`SecurityCritical`] attributo per renderli trasparente.

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2130.constantsshouldbetransparent/cs/ca2130 - constantsshouldbetransparent.cs#1)]



