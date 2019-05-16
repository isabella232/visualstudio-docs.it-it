---
title: "CA2115: Chiamare GC. KeepAlive durante l'utilizzo di risorse native | Microsoft Docs"
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c035c05480279012fba1101c3a60b020d34b1890
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687337"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Chiamare GC.KeepAlive durante l'uso di risorse native
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo dichiarato in un tipo con un finalizzatore fa riferimento a un <xref:System.IntPtr?displayProperty=fullName> oppure <xref:System.UIntPtr?displayProperty=fullName> campo, ma non chiama <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Operazione di Garbage collection completa un oggetto se non sono presenti più riferimenti a esso nel codice gestito. I riferimenti agli oggetti non gestiti non impediscono operazioni di garbage collection. Questa regola rileva gli errori che possono verificarsi qualora una risorsa non gestita venga completata mentre è ancora usata da codice non gestito.

 Questa regola presuppone che <xref:System.IntPtr> e <xref:System.UIntPtr> campi archiviano i puntatori alle risorse non gestite. Poiché lo scopo di un finalizzatore è liberare le risorse non gestite, la regola presuppone che il finalizzatore consente di liberare la risorsa non gestita a cui punta i campi di puntatore. Questa regola presuppone inoltre che il metodo fa riferimento il campo del puntatore per passare la risorsa non gestita nel codice non gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere una chiamata a <xref:System.GC.KeepAlive%2A> al metodo, passando l'istanza corrente (`this` in c# e C++) come argomento. Posizionare la chiamata dopo l'ultima riga di codice in cui l'oggetto deve essere protetto da operazioni di garbage collection. Immediatamente dopo la chiamata a <xref:System.GC.KeepAlive%2A>, l'oggetto viene considerato pronto per l'operazione di garbage collection anche in questo caso presupponendo che non sono presenti riferimenti gestiti ad esso.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Questa regola consente di alcuni presupposti che possono provocare falsi positivi. È possibile eliminare un avviso da questa regola in modo sicuro se:

- Il finalizzatore non liberare il contenuto del <xref:System.IntPtr> o <xref:System.UIntPtr> campo fa riferimento il metodo.

- Il metodo non ha superato il <xref:System.IntPtr> o <xref:System.UIntPtr> campo al codice non gestito.

  Esaminare attentamente gli altri messaggi prima di escluderli. Questa regola rileva gli errori che sono difficili da riprodurre ed eseguire il debug.

## <a name="example"></a>Esempio
 Nell'esempio riportato di seguito `BadMethod` non include una chiamata a `GC.KeepAlive` e pertanto viola la regola. `GoodMethod` contiene il codice corretto.

> [!NOTE]
> In questo esempio è pseudo-codice anche se il codice viene compilato ed eseguito, l'avviso non viene generato perché una risorsa non gestita non viene creata o liberata.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Criterio Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
