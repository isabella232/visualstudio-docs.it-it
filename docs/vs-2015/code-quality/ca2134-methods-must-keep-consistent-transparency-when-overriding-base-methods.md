---
title: "CA2134: I metodi devono conservare trasparenza consistente durante l'override dei metodi di base | Microsoft Docs"
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
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: df04e5462e2b03c402ce792b390b476b05873036
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589598"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: I metodi devono conservare trasparenza consistente durante l'override dei metodi base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2134: i metodi devono conservare trasparenza consistente durante l'override dei metodi base](https://docs.microsoft.com/visualstudio/code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods).

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Questa regola viene attivata quando un metodo contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> esegue l'override di un metodo trasparente o contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute>. La regola viene attivata anche quando un metodo trasparente o contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute> esegue l'override di un metodo contrassegnato con un <xref:System.Security.SecurityCriticalAttribute>.

 La regola è applicata in caso di esecuzione dell'override di un metodo virtuale o di implementazione di un'interfaccia.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola viene attivata sui tentativi di modificare l'accessibilità di sicurezza di un metodo ulteriormente la catena di ereditarietà. Ad esempio, se un metodo virtuale in una classe di base è trasparente o critico, quindi la classe derivata deve sostituirlo con un metodo trasparente o critico. Viceversa, se virtuale è critico per la sicurezza, la classe derivata deve eseguirne l'override con un metodo SecurityCritical. Le stesse regole valgono per l'implementazione di metodi di interfaccia.

 Regole di trasparenza vengono applicate quando il codice JIT compilato anziché in fase di esecuzione, in modo che il calcolo della trasparenza non dispone di informazioni di tipo dinamico. Di conseguenza, il risultato del calcolo della trasparenza deve essere in grado di essere determinata esclusivamente dai tipi statici compilato tramite JIT, indipendentemente dal tipo dinamico.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare la trasparenza del metodo che viene viene sottoposto a override un metodo virtuale o che implementa un'interfaccia in modo da corrispondere la trasparenza del commutatore o il metodo di interfaccia.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare gli avvisi da questa regola. Le violazioni di questa regola comporterà un runtime <xref:System.TypeLoadException> per gli assembly che usano la trasparenza di livello 2.

## <a name="examples"></a>Esempi

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Vedere anche
 [Codice SecurityTransparent, livello 2](http://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)



