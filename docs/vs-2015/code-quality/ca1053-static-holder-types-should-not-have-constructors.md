---
title: 'CA1053: I tipi statici non devono avere costruttori | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 83000143674e7cc3bc412c0ca8a579660160514c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444563"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: I tipi che contengono membri statici non devono avere costruttori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o annidato dichiara solo membri statici e presenta un costruttore predefinito pubblico o protetto.

## <a name="rule-description"></a>Descrizione della regola
 Il costruttore non è necessario perché la chiamata a membri statici non richiede un'istanza del tipo. Inoltre, perché il tipo non dispone di membri non statici, creare un'istanza non fornisce l'accesso a uno dei membri del tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il costruttore predefinito o renderla privata.

> [!NOTE]
> Se il tipo non definisce alcun costruttore, alcuni compilatori di creano automaticamente un costruttore predefinito pubblico. Se questo è il caso con il tipo, aggiungere un costruttore privato predefinito per eliminare la violazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. La presenza del costruttore suggerisce che il tipo non è un tipo statico.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola. Si noti che nel codice sorgente non sia presente alcun costruttore predefinito. Quando questo codice viene compilato in un assembly, il compilatore C# inserirà un costruttore predefinito, che verrà violano questa regola. Per risolvere il problema, dichiarare un costruttore privato.

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]
