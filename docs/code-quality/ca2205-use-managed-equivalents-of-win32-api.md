---
title: "CA2205: Usare equivalenti gestiti dell'API Win32"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6481bbcca68c7471e4f25c7629e3b55fa407d175
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231711"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Usare equivalenti gestiti dell'API Win32

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Viene definito un metodo di platform invoke e in .NET esiste un metodo con la funzionalità equivalente.

## <a name="rule-description"></a>Descrizione della regola

Un metodo di Platform Invoke viene usato per chiamare una funzione dll non gestita e viene definito usando l' <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attributo o la `Declare` parola chiave in Visual Basic. Un metodo di platform invoke definito in modo non corretto può causare eccezioni di runtime a causa di problemi quali una funzione senza nome, un mapping errato di tipi di dati di parametri e valori restituiti e specifiche di campo non corrette, ad esempio la convenzione di chiamata e il carattere set. Se disponibile, è più semplice e meno soggetta a errori chiamare il metodo gestito equivalente rispetto alla definizione e alla chiamata diretta del metodo non gestito. La chiamata a un metodo di platform invoke può anche causare problemi di sicurezza aggiuntivi che devono essere risolti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, sostituire la chiamata alla funzione non gestita con una chiamata al relativo equivalente gestito.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Eliminare un avviso da questa regola se il metodo di sostituzione suggerito non fornisce la funzionalità necessaria.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata una definizione di metodo platform invoke che viola la regola. Vengono inoltre visualizzate le chiamate al metodo platform invoke e al metodo gestito equivalente.

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA1404: Chiamare GetLastError immediatamente dopo P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060 Sposta P/Invoke nella classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400 I punti di ingresso P/Invoke devono esistere](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401: I P/Invoke non devono essere visibili](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)