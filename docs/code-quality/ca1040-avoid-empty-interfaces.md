---
title: "CA1040: Evitare l'uso di interfacce vuote"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ffdea7cadbf7bfc2803573a78fdd9bbc74b1d287
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936866"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Evitare l'uso di interfacce vuote

|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 L'interfaccia non dichiarato alcun membro o implementare due o più interfacce.

## <a name="rule-description"></a>Descrizione della regola
 Le interfacce definiscono membri che forniscono un comportamento o un contratto di utilizzo. La funzionalità descritta dall'interfaccia può essere adottata da qualsiasi tipo, indipendentemente dal punto in cui il tipo è visualizzato nella gerarchia di ereditarietà. Un tipo implementa un'interfaccia fornendo implementazioni per i membri dell'interfaccia. Un'interfaccia vuota non definisce alcun membro. Pertanto, non definisce un contratto che può essere implementato.

 Se la progettazione include vuota sono deve implementare le interfacce che è stato digitato, probabilmente si sta usando un'interfaccia come marcatore o come un modo per identificare un gruppo di tipi. Se questa identificazione si verifica in fase di esecuzione, il modo corretto per eseguire questa operazione è usare un attributo personalizzato. Usare la presenza o assenza dell'attributo o le proprietà dell'attributo, per identificare i tipi di destinazione. Se l'identificazione deve verificarsi in fase di compilazione, quindi è possibile utilizzare un'interfaccia vuota.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere l'interfaccia o aggiungervi membri. Se l'interfaccia vuota viene utilizzato per etichettare un set di tipi, sostituire l'interfaccia con un attributo personalizzato.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola quando l'interfaccia viene utilizzata per identificare un set di tipi in fase di compilazione.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un'interfaccia vuota.

 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]