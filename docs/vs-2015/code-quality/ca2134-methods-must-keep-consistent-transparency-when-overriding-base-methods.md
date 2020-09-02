---
title: "CA2134: i metodi devono garantire una trasparenza coerente quando si esegue l'override di metodi di base | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fe9a84280b0124eed6bb0cfffae9c1ec2942bddf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547719"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: I metodi devono mantenere trasparenza consistente durante l'override dei metodi base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Questa regola viene attivata quando un metodo contrassegnato con l'oggetto <xref:System.Security.SecurityCriticalAttribute> esegue l'override di un metodo trasparente o contrassegnato con <xref:System.Security.SecuritySafeCriticalAttribute> . La regola viene attivata anche quando un metodo trasparente o contrassegnato con l'oggetto <xref:System.Security.SecuritySafeCriticalAttribute> esegue l'override di un metodo contrassegnato con un oggetto <xref:System.Security.SecurityCriticalAttribute> .

 La regola è applicata in caso di esecuzione dell'override di un metodo virtuale o di implementazione di un'interfaccia.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola viene attivata quando si tenta di modificare l'accessibilità di sicurezza di un metodo verso l'alto nella catena di ereditarietà. Se, ad esempio, un metodo virtuale in una classe base è trasparente o critico per la sicurezza, la classe derivata deve eseguirne l'override con un metodo trasparente o critico per la sicurezza. Viceversa, se il virtuale è critico per la sicurezza, la classe derivata deve eseguirne l'override con un metodo critico per la sicurezza. La stessa regola si applica all'implementazione dei metodi di interfaccia.

 Le regole di trasparenza vengono applicate quando il codice viene compilato tramite JIT anziché in fase di esecuzione, in modo che il calcolo della trasparenza non disponga di informazioni sui tipi dinamici. Pertanto, il risultato del calcolo della trasparenza deve poter essere determinato esclusivamente dai tipi statici che vengono compilati tramite JIT, indipendentemente dal tipo dinamico.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare la trasparenza del metodo che esegue l'override di un metodo virtuale o implementando un'interfaccia in modo che corrisponda alla trasparenza del metodo virtuale o dell'interfaccia.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare gli avvisi da questa regola. Le violazioni di questa regola comporteranno un runtime <xref:System.TypeLoadException> per gli assembly che usano la trasparenza di livello 2.

## <a name="examples"></a>Esempi

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Vedere anche
 [Codice SecurityTransparent, livello 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
