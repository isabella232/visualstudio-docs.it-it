---
title: 'CA1506: Evitare un numero eccessivo di accoppiamenti tra classi'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1721fd52c00c5b312c88f19d48b668b12d28f050
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234486"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Evitare un numero eccessivo di accoppiamenti tra classi

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Category|Microsoft.Maintainability|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Un tipo o un metodo è abbinato a molti altri tipi.

## <a name="rule-description"></a>Descrizione della regola

Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo.

I tipi e i metodi con un elevato grado di accoppiamento della classe possono essere difficili da gestire. È consigliabile disporre di tipi e metodi che presentano un accoppiamento basso e una coesione elevata.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere la violazione, provare a riprogettare il tipo o il metodo per ridurre il numero di tipi a cui è associato.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Escludere questo avviso quando il tipo o il metodo è considerato gestibile nonostante il numero elevato di dipendenze da altri tipi.

## <a name="see-also"></a>Vedere anche

- [Avvisi di manutenibilità](../code-quality/maintainability-warnings.md)
- [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/code-metrics-values.md)