---
title: Set di regole minime gestite per codice gestito
ms.date: 11/04/2016
description: Informazioni sul set di regole regole minime gestite in Visual Studio, in particolare sicurezza, affidabilità e altri problemi critici. Vedere le descrizioni delle regole.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 35cc4d2abc0c99afd3d9add98178aea54e5f2367
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631901"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Set di regole minime gestite per codice gestito

Le regole minime gestite sono incentrate sui problemi più critici nel codice, inclusi potenziali problemi di sicurezza, arresti anomali dell'applicazione e altri errori di logica e progettazione importanti. Includere questo set di regole in qualsiasi set di regole personalizzato creato per i progetti.

|Regola|Descrizione|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|I tipi proprietari di campi Disposable devono essere Disposable|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Rimuovere i finalizzatori vuoti|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|I campi eliminabili devono essere eliminati|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Operatore di overload uguale a in caso di override `ValueType.Equals`|
