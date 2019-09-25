---
title: 'CA1900: I campi dei tipi di valore devono essere portabili'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bef51c547d4a1614137e0691343bef635aed50d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233283"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: I campi dei tipi di valore devono essere portabili

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Category|Microsoft. portabilità|
|Modifica|Interruzioni: se il campo può essere visualizzato all'esterno dell'assembly.<br /><br /> Senza interruzioni: se il campo non è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
Questa regola consente di verificare che le strutture dichiarate con layout esplicito vengano allineate correttamente quando viene eseguito il marshalling a codice non gestito in sistemi operativi a 64 bit. IA-64 non consente accessi di memoria non allineati e il processo si arresterà in modo anomalo se questa violazione non è corretta.

## <a name="rule-description"></a>Descrizione della regola
Le strutture con layout esplicito che contiene campi non allineati provocano arresti anomali nei sistemi operativi a 64 bit.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per tutti i campi di dimensioni inferiori a 8 byte devono essere presenti offset che sono un multiplo delle dimensioni e i campi di 8 byte o più piccoli devono contenere offset che sono un multiplo di 8. Un'altra soluzione consiste nell' `LayoutKind.Sequential` usare al `LayoutKind.Explicit`posto di, se ragionevole.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Questo avviso deve essere eliminato solo se si verifica un errore.