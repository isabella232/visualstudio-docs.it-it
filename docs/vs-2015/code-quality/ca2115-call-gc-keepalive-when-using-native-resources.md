---
title: 'CA2115: chiamare GC. KeepAlive quando si utilizzano risorse native | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e0aa10cc453919a2a79ee6d3d46db95c19d8756e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658690"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Chiamare GC.KeepAlive durante l'utilizzo di risorse native
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo dichiarato in un tipo con un finalizzatore fa riferimento a un <xref:System.IntPtr?displayProperty=fullName> o <xref:System.UIntPtr?displayProperty=fullName> campo, ma non chiama <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Garbage Collection finalizza un oggetto se non sono presenti altri riferimenti al codice gestito. I riferimenti non gestiti agli oggetti non impediscono la Garbage Collection. Questa regola rileva gli errori che possono verificarsi qualora una risorsa non gestita venga completata mentre è ancora usata da codice non gestito.

 Questa regola presuppone che i campi <xref:System.IntPtr> e <xref:System.UIntPtr> memorizzino i puntatori alle risorse non gestite. Poiché lo scopo di un finalizzatore è liberare le risorse non gestite, la regola presuppone che il finalizzatore libererà la risorsa non gestita a cui puntano i campi del puntatore. Questa regola presuppone inoltre che il metodo faccia riferimento al campo puntatore per passare la risorsa non gestita al codice non gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere una chiamata a <xref:System.GC.KeepAlive%2A> al metodo, passando l'istanza corrente (`this` in C# e C++) come argomento. Posizionare la chiamata dopo l'ultima riga di codice in cui l'oggetto deve essere protetto da Garbage Collection. Immediatamente dopo la chiamata a <xref:System.GC.KeepAlive%2A>, l'oggetto viene di nuovo considerato pronto per Garbage Collection presumendo che non vi siano riferimenti gestiti.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Questa regola fa alcune ipotesi che possono causare falsi positivi. È possibile eliminare in modo sicuro un avviso da questa regola se:

- Il finalizzatore non libera il contenuto del campo <xref:System.IntPtr> o <xref:System.UIntPtr> a cui fa riferimento il metodo.

- Il metodo non passa il campo <xref:System.IntPtr> o <xref:System.UIntPtr> a codice non gestito.

  Esaminare attentamente altri messaggi prima di escluderli. Questa regola rileva gli errori difficili da riprodurre ed eseguire il debug.

## <a name="example"></a>Esempio
 Nell'esempio seguente `BadMethod` non include una chiamata a `GC.KeepAlive` e pertanto viola la regola. `GoodMethod` contiene il codice corretto.

> [!NOTE]
> Questo esempio è pseudo-codice anche se il codice viene compilato ed eseguito, l'avviso non viene generato perché una risorsa non gestita non viene creata o liberata.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Criterio Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
