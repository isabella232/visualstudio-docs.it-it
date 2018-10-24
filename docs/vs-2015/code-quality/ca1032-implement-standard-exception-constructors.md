---
title: 'CA1032: Implementare costruttori di eccezioni standard | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: efef441e84c4f1d51c633e3fdcb2da8d1ba3e963
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868612"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementare costruttori di eccezioni standard
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Estende un tipo <xref:System.Exception?displayProperty=fullName> e non dichiara tutti i costruttori necessari.

## <a name="rule-description"></a>Descrizione della regola
 Tipi di eccezione devono implementare i costruttori seguenti:

- NewException() pubblico

- NewException(string) pubblico

- pubblica NewException (string, eccezione)

- NewException protetti o privati (SerializationInfo, StreamingContext)

  Se non viene fornito l'insieme completo di costruttori può risultare difficile gestire correttamente le eccezioni. Ad esempio, il costruttore con la firma `NewException(string, Exception)` viene usato per creare le eccezioni sono causate da altri tipi di eccezioni. Senza questo costruttore non è possibile creare e generare un'istanza di eccezione personalizzata contenente un'eccezione (annidata) interna, che è necessario eseguire l'operazione per il codice gestito in tale situazione. I primi tre costruttori di eccezioni sono pubblici per convenzione. Il quarto costruttore è protetto nelle classi unsealed e private in classi sealed. Per altre informazioni, vedere [CA2229: implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere i costruttori mancanti per l'eccezione e assicurarsi che abbiano l'accessibilità corretto.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando la violazione è causata dall'utilizzo di un livello di accesso diversi per i costruttori pubblici.

## <a name="example"></a>Esempio
 Nell'esempio seguente contiene un tipo di eccezione che violano questa regola e un tipo di eccezione che viene implementato in modo corretto.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]



