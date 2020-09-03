---
title: 'CA1053: i tipi di segnaposto statici non devono avere costruttori | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 29cc322dd59dc0de66af8f92a46524d15b0022c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539581"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: I tipi che contengono membri statici non devono avere costruttori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o annidato dichiara solo membri statici e presenta un costruttore predefinito pubblico o protetto.

## <a name="rule-description"></a>Descrizione della regola
 Il costruttore non è necessario perché la chiamata a membri statici non richiede un'istanza del tipo. Inoltre, poiché il tipo non dispone di membri non statici, la creazione di un'istanza non fornisce l'accesso ai membri del tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il costruttore predefinito o renderlo privato.

> [!NOTE]
> Alcuni compilatori creano automaticamente un costruttore predefinito pubblico se il tipo non definisce costruttori. Se questo è il caso del tipo, aggiungere un costruttore predefinito privato per eliminare la violazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. La presenza del costruttore suggerisce che il tipo non è un tipo statico.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola questa regola. Si noti che nel codice sorgente non è presente alcun costruttore predefinito. Quando questo codice viene compilato in un assembly, il compilatore C# inserisce un costruttore predefinito che viola questa regola. Per risolvere il problema, dichiarare un costruttore privato.

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]
