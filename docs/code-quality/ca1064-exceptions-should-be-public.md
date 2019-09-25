---
title: 'CA1064: Le eccezioni devono essere pubbliche'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ffc12d8d047be1bb13fcac133a61b047152ce3d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235323"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Le eccezioni devono essere pubbliche

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Category|Microsoft.Design|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un'eccezione non pubblica deriva direttamente da <xref:System.Exception>, <xref:System.SystemException>o <xref:System.ApplicationException>.

## <a name="rule-description"></a>Descrizione della regola
Un'eccezione interna è visibile solo all'interno del proprio ambito interno. Se l'eccezione si verifica al di fuori dell'ambito interno, può essere rilevata solo tramite l'eccezione di base. Se l'eccezione interna è ereditata da <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>, il codice esterno non avrà informazioni sufficienti per sapere cosa fare con l'eccezione.

Tuttavia, se il codice presenta un'eccezione pubblica che in un secondo momento viene usato come base per un'eccezione interna, è ragionevole presupporre che il codice più avanti possa eseguire un'operazione intelligente con l'eccezione di base. L'eccezione pubblica avrà più informazioni rispetto a quelle fornite da <xref:System.Exception>, <xref:System.SystemException>o <xref:System.ApplicationException>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Rendere pubblica l'eccezione o derivare l'eccezione interna da un'eccezione pubblica che non <xref:System.Exception>è, <xref:System.SystemException>o. <xref:System.ApplicationException>

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Eliminare un messaggio da questa regola se si è certi di tutti i casi in cui l'eccezione privata verrà rilevata all'interno del proprio ambito interno.

## <a name="example"></a>Esempio
Questa regola viene attivata sul primo metodo di esempio, FirstCustomException perché la classe Exception deriva direttamente dall'eccezione ed è interna. La regola non viene attivata sulla classe SecondCustomException perché anche se la classe deriva direttamente dall'eccezione, la classe è dichiarata pubblica. La terza classe non genera inoltre la regola perché non deriva direttamente da <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>o <xref:System.ApplicationException?displayProperty=fullName>.

[!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
