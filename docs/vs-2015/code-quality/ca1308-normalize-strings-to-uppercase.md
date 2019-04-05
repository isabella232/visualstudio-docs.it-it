---
title: 'CA1308: Normalizzare le stringhe in lettere maiuscole | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8385839ce7029ef0676225fd443582ba750b618b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968427"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizzare le stringhe in lettere maiuscole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un'operazione normalizza una stringa in caratteri minuscoli.

## <a name="rule-description"></a>Descrizione della regola
 Le stringhe devono essere normalizzate in maiuscolo. Un piccolo gruppo di caratteri, quando questi vengono convertiti in caratteri minuscoli, non è possibile completare un round trip. Per completare un round trip mezzi per convertire i caratteri delle impostazioni locali in un'altra delle impostazioni locali che rappresenta i dati di tipo carattere in modo diverso, quindi in modo accurato recupero i caratteri originali dai caratteri convertiti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare le operazioni di conversione di stringhe in caratteri minuscoli in modo che le stringhe vengono convertite in caratteri maiuscoli invece. Ad esempio, modificare `String.ToLower(CultureInfo.InvariantCulture)` in `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un messaggio di avviso quando non si apportano decisione relativa alla sicurezza in base al risultato (ad esempio, quando si visualizza nell'interfaccia utente).

## <a name="see-also"></a>Vedere anche
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)
