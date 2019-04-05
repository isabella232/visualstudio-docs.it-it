---
title: 'CA2141: i metodi Transparent non devono soddisfare i LinkDemand | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a7c54b472e91aa2be1d8e5bb1a9c32c26c0cb299
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968147"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141:I metodi Transparent non devono soddisfare i LinkDemand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo trasparente per la sicurezza chiama un metodo in un assembly che non sia contrassegnato con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attributo (APTCA) o un metodo trasparente per la sicurezza soddisfa un <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` per un tipo o un metodo.

## <a name="rule-description"></a>Descrizione della regola
 Che soddisfa un LinkDemand è un'operazione sensibile di sicurezza che può causare l'elevazione dei privilegi non intenzionale dei privilegi. Codice SecurityTransparent non deve soddisfare i LinkDemand, perché non è soggetta agli stessi requisiti di controllo di sicurezza del codice SecurityCritical. I metodi Transparent negli assembly di livello 1 set di regole di sicurezza causa tutti i LinkDemand soddisfano da convertire in richieste complete in fase di esecuzione, che può causare problemi di prestazioni. Nell'assembly di livello 2 set di regole di sicurezza, i metodi transparent avrà esito negativo per la compilazione del compilatore just-in-time (JIT) se provano a soddisfa un LinkDemand.

 Negli assembly che utilizzano la sicurezza di livello 2, i tentativi da parte di un metodo trasparente per sicurezza soddisfa un LinkDemand o chiamare un metodo in un assembly APTCA non genera un <xref:System.MethodAccessException>; negli assembly di livello 1 LinkDemand diventano richieste complete.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, contrassegnare il metodo di accesso con il <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> attributo o rimuovere i LinkDemand dal metodo di accesso.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 In questo esempio, un metodo trasparente tenta di chiamare un metodo che presenta un LinkDemand. Questa regola viene generato su questo codice.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]
