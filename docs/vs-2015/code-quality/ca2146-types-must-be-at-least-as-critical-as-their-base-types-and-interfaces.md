---
title: 'CA2146: i tipi devono essere critici almeno quanto i tipi di base e le interfacce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ab621ade120a257508eddbf9527f674b5fda8748
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610182"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: I tipi devono essere Critical almeno come le interfacce e i tipi base relativi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo trasparente viene derivato da un tipo contrassegnato con <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityCriticalAttribute> oppure un tipo contrassegnato con l'attributo <xref:System.Security.SecuritySafeCriticalAttribute> viene derivato da un tipo contrassegnato con l'attributo <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola viene attivata quando un tipo derivato dispone di un attributo di trasparenza di sicurezza che non è critico come il tipo di base o l'interfaccia implementata. Solo i tipi critici possono derivare da tipi di base critici o implementare interfacce critiche e solo tipi critici o critici per la sicurezza possono derivare da tipi di base critici per la sicurezza o implementare interfacce critiche per la sicurezza. Le violazioni di questa regola nella trasparenza di livello 2 generano un <xref:System.TypeLoadException> per il tipo derivato.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere questa violazione, contrassegnare il tipo derivato o di implementazione con un attributo di trasparenza che è almeno critico come il tipo o l'interfaccia di base.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]
