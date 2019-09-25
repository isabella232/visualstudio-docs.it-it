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
ms.openlocfilehash: 44bdb8c12b48a983b88e6a035fc1522856b306be
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235578"
---
# <a name="ca1053-static-holder-types-should-not-have-default-constructors"></a>CA1053: I tipi di segnaposto statici non devono avere costruttori predefiniti

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Category|Microsoft.Design|
|Modifica|Interruzione|

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