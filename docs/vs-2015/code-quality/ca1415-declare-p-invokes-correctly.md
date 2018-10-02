---
title: 'CA1415: Dichiarare P-Invoke correttamente | Microsoft Docs'
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
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c80a68d19e03f7e4b04dae728dd2e9cc120eb370
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589144"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Dichiarare correttamente i P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1415: dichiarare a P-Invoke correttamente](https://docs.microsoft.com/visualstudio/code-quality/ca1415-declare-p-invokes-correctly).

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Category|Microsoft.Interoperability|
|Modifica importante|Non sostanziale - Se i P/Invoke che dichiara il parametro non è visibile all'esterno dell'assembly. Rilievo - se i P/Invoke che dichiara il parametro può essere visualizzato all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Metodo di un platform invoke viene dichiarato in modo non corretto.

## <a name="rule-description"></a>Descrizione della regola
 Una piattaforma di richiamare codice non gestito accede a metodo e viene definito tramite il `Declare` parola chiave in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o il <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Attualmente, questa regola consente di cercare le dichiarazioni di metodo che usano funzioni Win32 con un puntatore a un parametro di struttura OVERLAPPED di platform invoke e il cui parametro gestito corrispondente non è un puntatore a un <xref:System.Threading.NativeOverlapped?displayProperty=fullName> struttura.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, dichiarare correttamente il platform invoke (metodo).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra i metodi che violano la regola e soddisfano la regola di platform invoke.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>Vedere anche
 [Interoperabilità con codice non gestito](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



