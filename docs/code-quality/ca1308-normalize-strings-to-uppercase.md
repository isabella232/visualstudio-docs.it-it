---
title: 'CA1308: Normalizzare le stringhe in lettere maiuscole'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5cda66d2a43ee3fde8e3e7b2d22a64a09655da3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31897143"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizzare le stringhe in lettere maiuscole
|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un'operazione normalizza stringa in caratteri minuscoli.

## <a name="rule-description"></a>Descrizione della regola
 Le stringhe devono essere normalizzate in maiuscolo. Un piccolo gruppo di caratteri, quando vengono convertiti in caratteri minuscoli, non è possibile completare un round trip. Per completare un round trip mezzi per convertire i caratteri da una delle impostazioni locali a un altro che rappresenta i dati di tipo carattere in modo diverso, quindi in modo accurato recuperano i caratteri originali dai caratteri convertiti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare le operazioni che convertono le stringhe in caratteri minuscoli in modo che le stringhe vengono convertite in caratteri maiuscoli invece. Ad esempio, modificare `String.ToLower(CultureInfo.InvariantCulture)` a `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un messaggio di avviso quando si fanno decisione relativa alla sicurezza in base al risultato (ad esempio, quando si visualizza nell'interfaccia utente).

## <a name="see-also"></a>Vedere anche
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)