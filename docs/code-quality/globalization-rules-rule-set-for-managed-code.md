---
title: Set di regole delle Regole di globalizzazione per codice gestito
ms.date: 11/04/2016
description: Informazioni sul set di regole di globalizzazione in Visual Studio, che è incentrato sui problemi correlati a lingue, impostazioni locali e impostazioni cultura. Vedere le descrizioni delle regole.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: fdf816b978aac5d22b1750eeabe3737f1eb64085
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867932"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Set di regole delle Regole di globalizzazione per codice gestito

Usare il set di regole di globalizzazione Microsoft per concentrarsi sui problemi che potrebbero impedire che i dati nell'applicazione vengano visualizzati correttamente in lingue, impostazioni locali e impostazioni cultura diverse. È necessario includere questo set di regole se l'applicazione è localizzata, globalizzata o entrambe.

|Regola|Descrizione|
|----------|-----------------|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Non passare valori letterali come parametri localizzati|
|[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304)|Specificare CultureInfo|
|[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305)|Specificare IFormatProvider|
|[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307)|Specificare StringComparison per maggiore chiarezza|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Normalizzare le stringhe in lettere maiuscole|
|[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309)|Usare StringComparison ordinale|
|[CA1310](/dotnet/fundamentals/code-analysis/quality-rules/ca1310)|Specificare StringComparison per correttezza|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Specificare il marshalling per gli argomenti di stringa P/Invoke|
