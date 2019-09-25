---
title: 'CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f49c9dfdac1d8d8aec8ec32df7374b5ae0a28e92
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233018"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Category|Microsoft. globalizzazione|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un membro platform invoke consente chiamanti parzialmente attendibili, presenta un parametro di stringa e non esegue il marshalling esplicito della stringa.

## <a name="rule-description"></a>Descrizione della regola
Quando si esegue la conversione da Unicode a ANSI, è possibile che non tutti i caratteri Unicode possano essere rappresentati in una specifica tabella codici ANSI. Il *mapping più appropriato* tenta di risolvere questo problema sostituendo un carattere per il carattere che non può essere rappresentato. L'uso di questa funzionalità può causare una potenziale vulnerabilità di sicurezza perché non è possibile controllare il carattere scelto. Ad esempio, il codice dannoso potrebbe creare intenzionalmente una stringa Unicode che contiene caratteri non presenti in una determinata tabella codici, che vengono convertiti in file system caratteri speciali, ad esempio '. .' o '/'. Si noti inoltre che i controlli di sicurezza per i caratteri speciali si verificano spesso prima che la stringa venga convertita in ANSI.

Il mapping più appropriato è quello predefinito per la conversione non gestita, da WChar a MByte. A meno che non si disabilita in modo esplicito il mapping più appropriato, il codice potrebbe contenere una vulnerabilità di sicurezza sfruttabile a causa di questo problema.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, effettuare il marshalling esplicito dei tipi di dati stringa.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un metodo che viola questa regola, quindi viene illustrato come correggere la violazione.

[!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]