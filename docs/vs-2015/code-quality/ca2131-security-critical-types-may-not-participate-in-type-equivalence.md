---
title: "CA2131: I tipi SecurityCritical possono non partecipare all'equivalenza del tipo | Microsoft Docs"
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
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ce845cf463e74ba0b41cb3f10a9253a2662fab55
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248638"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: I tipi SecurityCritical possono non partecipare all'equivalenza del tipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo partecipa all'equivalenza del tipo e il tipo stesso o un membro o un campo del tipo, è contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> attributo.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola viene attivata su qualsiasi tipo critico o a tipi che contengono metodi o campi critici che partecipano all'equivalenza del tipo. Quando CLR rileva tale tipo, non è possibile caricarlo con un <xref:System.TypeLoadException> in fase di esecuzione. In genere, questa regola funziona solo quando gli utenti implementano l'equivalenza del tipo manualmente piuttosto che basarsi su tlbimp e i compilatori per fare l'equivalenza del tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere l'attributo SecurityCritical.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Gli esempi seguenti illustrano un'interfaccia, un metodo e un campo che causa la regola da attivare.

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2131.criticaltypesmustnotparticipateintypeequivalence/cs/ca2131 - criticaltypesmustnotparticipateintypeequivalence.cs#1)]

## <a name="see-also"></a>Vedere anche
 [Codice SecurityTransparent, livello 2](http://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)



