---
title: "CA2205: Utilizzare equivalenti gestiti dell'API Win32"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d0b43d328dc122a60d2c397cc59e39426e4c4f4c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860741"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Utilizzare equivalenti gestiti dell'API Win32

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un platform invoke viene definito metodo e un metodo con la funzionalità equivalente è presente nella libreria di classi .NET Framework.

## <a name="rule-description"></a>Descrizione della regola

Un platform invoke (metodo) viene usato per chiamare una funzione DLL non gestita e viene definita utilizzando il <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attributo, o `Declare` parola chiave in Visual Basic. Metodo di richiamo una piattaforma definita in modo errato può causare eccezioni di runtime a causa di problemi, ad esempio una funzione di nome non corretto, mapping dei tipi di dati di valore di parametro e restituire e specifiche di campo corretto, ad esempio la convenzione di chiamata e il carattere errato set. Se disponibile, è errore più semplice e meno soggetto a chiamare il metodo gestito equivalente a to definire e chiamare direttamente il metodo non gestito. La chiamata a una piattaforma di richiamo metodo possono causare problemi di sicurezza aggiuntive che devono essere risolte.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, sostituire la chiamata alla funzione non gestita con una chiamata nel relativo equivalente gestito.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Eliminare un avviso da questa regola se il metodo di sostituzione suggerita non fornisce le funzionalità necessarie.

## <a name="example"></a>Esempio

L'esempio seguente mostra un platform invoke definizione del metodo che viola la regola. Inoltre, le chiamate alla piattaforma invoke (metodo) e il metodo equivalente gestito vengono visualizzati.

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA1404: Chiamare GetLastError immediatamente dopo P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060: Spostare i P/Invoke nella classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400: I punti di ingresso P/Invoke devono esistere](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401: P/Invoke non devono essere visibili](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)