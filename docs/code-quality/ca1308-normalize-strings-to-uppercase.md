---
title: 'CA1308: Normalizzare le stringhe in lettere maiuscole'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06fe8d4fbd4def14bfb8a24f4f211a121c809930
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922245"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizzare le stringhe in lettere maiuscole

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Category|Microsoft. globalizzazione|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
Un'operazione normalizza una stringa in minuscolo.

## <a name="rule-description"></a>Descrizione della regola
Le stringhe devono essere normalizzate in maiuscolo. Un piccolo gruppo di caratteri, quando vengono convertiti in caratteri minuscoli, non può creare un round trip. Per creare un round trip significa convertire i caratteri da un'impostazione locale a un'altra locale che rappresenta i dati di tipo carattere in modo diverso e quindi recuperare accuratamente i caratteri originali dai caratteri convertiti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Modificare le operazioni che convertono le stringhe in lettere minuscole in modo che le stringhe vengano convertite in maiuscolo. Ad esempio, modificare `String.ToLower(CultureInfo.InvariantCulture)` in `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile evitare di visualizzare un messaggio di avviso quando non si decide di prendere decisioni di sicurezza in base al risultato, ad esempio quando viene visualizzato nell'interfaccia utente.

## <a name="see-also"></a>Vedere anche
[Avvisi di globalizzazione](../code-quality/globalization-warnings.md)