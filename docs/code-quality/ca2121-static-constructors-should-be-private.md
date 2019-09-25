---
title: 'CA2121: I costruttori statici devono essere privati'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b52f4412b1b048c41033f74200828f70361c1ea3
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232498"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: I costruttori statici devono essere privati

|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Category|Microsoft.Security|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Un tipo dispone di un costruttore statico che non è privato.

## <a name="rule-description"></a>Descrizione della regola

Un costruttore statico, noto anche come costruttore di classe, viene usato per inizializzare un tipo. Il costruttore statico viene chiamato prima che venga creata la prima istanza del tipo o venga fatto riferimento a qualsiasi membro statico. L'utente non ha alcun controllo sul momento in cui viene chiamato il costruttore statico. Se un costruttore statico non è privato, può essere chiamato da codice esterno al sistema. A seconda delle operazioni eseguite nel costruttore, questa situazione può causare comportamenti imprevisti.

Questa regola viene applicata dai compilatori C# e Visual Basic.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Le violazioni sono in genere dovute a una delle azioni seguenti:

- È stato definito un costruttore statico per il tipo e non è stato reso privato.

- Il compilatore del linguaggio di programmazione ha aggiunto un costruttore statico predefinito al tipo e non è stato reso privato.

Per correggere il primo tipo di violazione, rendere privato il costruttore statico. Per correggere il secondo tipo, aggiungere un costruttore statico privato al tipo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere queste violazioni. Se la progettazione del software richiede una chiamata esplicita a un costruttore statico, è probabile che la progettazione contenga gravi errori e che sia necessario esaminarla.