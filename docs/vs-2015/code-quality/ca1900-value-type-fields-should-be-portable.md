---
title: 'CA1900: i campi del tipo di valore devono essere portabili | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ece4788a277bfc4d16568d4014f9eae2ed4de33
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545275"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: I campi dei tipi di valore devono essere portabili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente su Visual Studio, vedere [CA1900: i campi dei tipi di valore devono essere](/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable)portabili.

|Elemento|valore|
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Category|Microsoft. portabilità|
|Modifica importante|Interruzioni: se il campo può essere visualizzato all'esterno dell'assembly.<br /><br /> Senza interruzioni: se il campo non è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Questa regola consente di verificare che le strutture dichiarate con layout esplicito vengano allineate correttamente quando viene eseguito il marshalling a codice non gestito in sistemi operativi a 64 bit. IA-64 non consente accessi di memoria non allineati e il processo si arresterà in modo anomalo se questa violazione non è corretta.

## <a name="rule-description"></a>Descrizione della regola
 Le strutture con layout esplicito che contiene campi non allineati provocano arresti anomali nei sistemi operativi a 64 bit.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per tutti i campi di dimensioni inferiori a 8 byte devono essere presenti offset che sono un multiplo delle dimensioni e i campi di 8 byte o più piccoli devono contenere offset che sono un multiplo di 8. Un'altra soluzione consiste nell'usare al `LayoutKind.Sequential` posto di `LayoutKind.Explicit` , se ragionevole.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Questo avviso deve essere eliminato solo se si verifica un errore.
