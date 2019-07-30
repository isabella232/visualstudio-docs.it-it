---
title: 'CA1053: I tipi che contengono membri statici non devono avere costruttori'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fec59e1d683c7867eb1cad9ae4e796a0815200d4
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2019
ms.locfileid: "68604780"
---
# <a name="ca1053-static-holder-types-should-not-have-default-constructors"></a>CA1053: I tipi di segnaposto statici non devono avere costruttori predefiniti

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

> [!NOTE]
> La regola CA1053 è combinata [in CA1052: I tipi di segnaposto statici](ca1052-static-holder-types-should-be-sealed.md) devono essere sealed negli [analizzatori FxCop](fxcop-analyzers.yml).

## <a name="cause"></a>Causa

Un tipo pubblico o annidato pubblico dichiara solo i membri statici e dispone di un costruttore predefinito.

## <a name="rule-description"></a>Descrizione della regola

Il costruttore predefinito non è necessario perché la chiamata a membri statici non richiede un'istanza del tipo. Inoltre, poiché il tipo non dispone di membri non statici, la creazione di un'istanza non fornisce l'accesso ai membri del tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere il costruttore predefinito.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola. La presenza del costruttore predefinito suggerisce che il tipo non è un tipo statico.