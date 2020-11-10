---
title: Set di regole minime gestite per codice gestito
ms.date: 11/04/2016
description: Informazioni sul set di regole minime gestite in Visual Studio, che è incentrato sulla sicurezza, l'affidabilità e altri problemi critici. Vedere le descrizioni delle regole.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5a0e5c59621f948cbb7465a6726fa8c3003480d4
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435391"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Set di regole minime gestite per codice gestito

Le regole minime gestite sono incentrate sui problemi più critici del codice, inclusi i potenziali problemi di sicurezza, gli arresti anomali dell'applicazione e altri importanti errori di logica e progettazione. Includere questo set di regole in tutti i set di regole personalizzati creati per i progetti.

|Regola|Descrizione|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|I tipi proprietari di campi Disposable devono essere Disposable|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Rimuovere i finalizzatori vuoti|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|I campi eliminabili devono essere eliminati|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Overload Operator equivale a override `ValueType.Equals`|
