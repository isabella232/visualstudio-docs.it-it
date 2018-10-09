---
title: ': CA2126 per le richieste di collegamento richieste di ereditarietà | Microsoft Docs'
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
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3f482350517858fffc74600c3743a22192aa6a49
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589779"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Per le richieste di collegamento dei tipi sono necessarie richieste di ereditarietà
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2126: le richieste di collegamento necessarie richieste di ereditarietà](https://docs.microsoft.com/visualstudio/code-quality/ca2126-type-link-demands-require-inheritance-demands).

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo non sealed pubblico è protetto con una richiesta di collegamento, dispone di un metodo sottoponibile a override e il tipo né il metodo è protetto con una richiesta di ereditarietà.

## <a name="rule-description"></a>Descrizione della regola
 Una richiesta di collegamento in un metodo o nel relativo tipo dichiarante richiede che il chiamante immediato del metodo di avere l'autorizzazione specificata. Una richiesta di ereditarietà in un metodo richiede un metodo di override per avere l'autorizzazione specificata. Una richiesta di ereditarietà in un tipo richiede una classe di derivazione per avere l'autorizzazione specificata.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, proteggere il tipo o il metodo con una richiesta di ereditarietà per la stessa autorizzazione della richiesta di collegamento.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cpp/FxCop.Security.TypesWithLinkDemands.cpp#1)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cs/FxCop.Security.TypesWithLinkDemands.cs#1)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/vb/FxCop.Security.TypesWithLinkDemands.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2108: Controllare la sicurezza dichiarativa sui tipi di valori](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122: Non esporre in modo indiretto metodi con richieste di collegamento](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123: Le richieste di collegamento negli override devono essere identiche a quelle nei metodi di base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Vedere anche
 [Linee guida per la generazione di codice sicuro](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [richieste di ereditarietà](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [collegarle](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [richieste](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)


