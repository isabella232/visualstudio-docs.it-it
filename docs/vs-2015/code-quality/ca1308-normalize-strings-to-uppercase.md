---
title: 'CA1308: normalizzare le stringhe in lettere maiuscole | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c068fcda7d03ae91435c040d2110d632668d832a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538736"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizzare le stringhe in lettere maiuscole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
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
 Modificare le operazioni che convertono le stringhe in lettere minuscole in modo che le stringhe vengano convertite in maiuscolo. Puoi ad esempio modificare `String.ToLower(CultureInfo.InvariantCulture)` in `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile evitare di visualizzare un messaggio di avviso quando non si decide di prendere decisioni di sicurezza in base al risultato, ad esempio quando viene visualizzato nell'interfaccia utente.

## <a name="see-also"></a>Vedere anche
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)
