---
title: 'CA1900: I campi dei tipi di valore devono essere portabili'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 84861aa1d17f041061d1666d6f78c9d273b948b4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037772"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: I campi dei tipi di valore devono essere portabili

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Category|Microsoft.Portability|
|Modifica importante|Rilievo - se il campo può essere visualizzato all'esterno dell'assembly.<br /><br /> Non sostanziale - Se il campo non è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Questa regola verifica che le strutture che vengono dichiarate con layout esplicito vengano allineate correttamente quando il marshalling nel codice non gestito nei sistemi operativi a 64 bit. IA-64 non consente gli accessi alla memoria non allineata e il processo verrà arrestato se questa violazione non viene risolto.

## <a name="rule-description"></a>Descrizione della regola
 Strutture con layout esplicito che contiene campi non allineati causano arresti anomali nei sistemi operativi a 64 bit.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Tutti i campi che sono inferiori a 8 byte devono disporre di offset che siano un multiplo della dimensione e i campi che sono a 8 byte o superiori devono avere gli offset sono un multiplo di 8. Un'altra soluzione consiste nell'usare `LayoutKind.Sequential` invece di `LayoutKind.Explicit`se ragionevole.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Questo avviso deve essere eliminato solo se si verifica in errore.