---
title: 'CA1053: I tipi che contengono membri statici non devono avere costruttori'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7f99804abeac1c9f536c94c542f6e031bf16ec6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: I tipi che contengono membri statici non devono avere costruttori
|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o annidato dichiara solo membri statici e presenta un costruttore predefinito pubblico o protetto.

## <a name="rule-description"></a>Descrizione della regola
 Il costruttore non è necessario perché la chiamata a membri statici non richiede un'istanza del tipo. Inoltre, perché il tipo non dispone di membri non statici, creazione di un'istanza non fornisce accesso a uno dei membri del tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il costruttore predefinito o renderlo privato.

> [!NOTE]
>  Se il tipo non definisce alcun costruttore, alcuni compilatori di creano automaticamente un costruttore predefinito pubblico. In questo caso con il tipo, aggiungere un costruttore privato predefinito per eliminare la violazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. La presenza del costruttore suggerisce che il tipo non è un tipo statico.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola questa regola. Si noti che nel codice sorgente è presente alcun costruttore predefinito. Quando questo codice viene compilato in un assembly, il compilatore c# viene inserito un costruttore predefinito, che verrà violano questa regola. Per risolvere il problema, dichiarare un costruttore privato.

 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]