---
title: 'CA2101: specificare il marshalling per gli argomenti di stringa P-Invoke | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 57b7214058baf63ffa5e3ee2c9a982bf411b60e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652188"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Category|Microsoft. globalizzazione|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un membro platform invoke consente chiamanti parzialmente attendibili, presenta un parametro di stringa e non esegue il marshalling esplicito della stringa.

## <a name="rule-description"></a>Descrizione della regola
 Quando si esegue la conversione da Unicode a ANSI, è possibile che non tutti i caratteri Unicode possano essere rappresentati in una specifica tabella codici ANSI. Il *mapping più appropriato* tenta di risolvere questo problema sostituendo un carattere per il carattere che non può essere rappresentato. L'uso di questa funzionalità può causare una potenziale vulnerabilità di sicurezza perché non è possibile controllare il carattere scelto. Ad esempio, il codice dannoso potrebbe creare intenzionalmente una stringa Unicode che contiene caratteri non presenti in una determinata tabella codici, che vengono convertiti in file system caratteri speciali, ad esempio '. .' o '/'. Si noti inoltre che i controlli di sicurezza per i caratteri speciali si verificano spesso prima che la stringa venga convertita in ANSI.

 Il mapping più appropriato è quello predefinito per la conversione non gestita, da WChar a MByte. A meno che non si disabilita in modo esplicito il mapping più appropriato, il codice potrebbe contenere una vulnerabilità di sicurezza sfruttabile a causa di questo problema.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, effettuare il marshalling esplicito dei tipi di dati stringa.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che viola questa regola, quindi viene illustrato come correggere la violazione.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PinvokeAnsiUnicode/cs/FxCop.Security.PinvokeAnsiUnicode.cs#1)]
