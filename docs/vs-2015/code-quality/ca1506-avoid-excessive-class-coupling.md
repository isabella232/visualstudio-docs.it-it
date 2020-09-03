---
title: 'CA1506: evitare un accoppiamento di classe eccessiva | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 07f19cb9d4aa2ed118898a1816092479cbd16565
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545704"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Evitare un numero eccessivo di accoppiamenti tra classi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Category|Microsoft. gestibilità|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo o un metodo è abbinato a molti altri tipi.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo.

 I tipi e i metodi con un elevato grado di accoppiamento della classe possono essere difficili da gestire. È consigliabile disporre di tipi e metodi che presentano un accoppiamento basso e una coesione elevata.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere la violazione, provare a riprogettare il tipo o il metodo per ridurre il numero di tipi a cui è associato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Escludere questo avviso quando il tipo o il metodo è ancora considerato gestibile nonostante il numero elevato di dipendenze da altri tipi.

## <a name="see-also"></a>Vedere anche
 [Avvisi di gestibilità](../code-quality/maintainability-warnings.md) [per la misurazione della complessità e della gestibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
