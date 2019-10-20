---
title: Set di regole di globalizzazione per codice gestito | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1630769b5150d9cef7b00e575ac9c555f5bc5be1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667613"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Set di regole delle Regole di globalizzazione per codice gestito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile utilizzare il set di regole di globalizzazione Microsoft per concentrarsi sui problemi che potrebbero impedire che i dati nell'applicazione vengano visualizzati correttamente in lingue, impostazioni locali e impostazioni cultura diverse. È necessario includere questo set di regole se l'applicazione è localizzata, globalizzata o entrambe.

|Regola|Descrizione|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Specificare MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Evitare tasti di scelta rapida duplicati|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Non impostare come hardcoded le stringhe delle impostazioni locali|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Non passare valori letterali come parametri localizzati|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Specificare CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Specificare IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Specificare le impostazioni locali per i tipi di dati|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Specificare StringComparison|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizzare le stringhe in lettere maiuscole|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Usare StringComparison ordinale|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Specificare il marshalling per gli argomenti di stringa P/Invoke|
