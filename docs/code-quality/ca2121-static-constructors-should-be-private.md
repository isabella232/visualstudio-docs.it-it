---
title: 'CA2121: I costruttori statici devono essere privati'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 124d65f1147bbc9aa0d38b2bca8f742bf1b60a9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954263"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: I costruttori statici devono essere privati

|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo ha un costruttore statico non è privato.

## <a name="rule-description"></a>Descrizione della regola

Un costruttore statico, noto anche come un costruttore di classe, viene utilizzato per inizializzare un tipo. Il costruttore statico viene chiamato prima che venga creata la prima istanza del tipo o venga fatto riferimento a qualsiasi membro statico. L'utente non ha alcun controllo su quando viene chiamato il costruttore statico. Se un costruttore statico non è privato, può essere chiamato da codice esterno al sistema. A seconda delle operazioni eseguite nel costruttore, questa situazione può causare comportamenti imprevisti.

Questa regola viene applicata dai compilatori c# e Visual Basic.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Le violazioni sono in genere causate da una delle azioni seguenti:

- È definito un costruttore statico per il tipo e non hai apportato privata.

- Il compilatore del linguaggio di programmazione aggiunto un costruttore statico predefinito al tipo e non hai apportato privata.

Per risolvere il tipo prima della violazione, rendere privato il costruttore statico. Per risolvere il tipo di secondo, aggiungere un costruttore statico privato per il tipo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non visualizzare tali violazioni. Se la progettazione software richiede una chiamata esplicita a un costruttore statico, è probabile che la struttura contiene difetti grave e deve essere esaminata.