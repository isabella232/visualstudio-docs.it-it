---
title: 'CA2101: Specificare il marshalling per gli argomenti di stringa P-Invoke'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 778668f799f325aee98334e243a0501a185a9ceb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915649"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un platform invoke membro consente chiamanti parzialmente attendibili, ha un parametro di stringa e non esegue in modo esplicito il marshalling della stringa.

## <a name="rule-description"></a>Descrizione della regola
 Quando si converte da Unicode ad ANSI, è possibile che non tutti i caratteri Unicode possono essere rappresentati in una tabella codici ANSI specifica. *Mapping più appropriato* tenta di risolvere questo problema sostituendo un carattere per carattere che non può essere rappresentato. L'uso di questa funzionalità può causare una potenziale vulnerabilità di sicurezza perché non è possibile controllare il carattere che viene scelto. Ad esempio codice dannoso intenzionalmente è stato possibile creare una stringa Unicode che contiene i caratteri che non si trovano in una tabella codici specifico, che vengono convertiti in caratteri speciali del file system, ad esempio '.. ' o '/'. Si noti anche che i controlli di sicurezza per i caratteri speciali spesso si verificano prima che la stringa viene convertita in formato ANSI.

 Mapping più appropriato è quello predefinito per la conversione non gestito, WChar a MB liberi per. A meno che non si disabiliti esplicitamente il mapping più appropriato, il codice potrebbe contenere una vulnerabilità della protezione a causa di questo problema.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, in modo esplicito il marshalling dei tipi dati stringa.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che viola questa regola e quindi viene illustrato come correggere la violazione.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]