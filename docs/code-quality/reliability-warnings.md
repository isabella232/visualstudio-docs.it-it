---
title: avvisi di affidabilità
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 009422eaf9ac81af6e8f9d48732655b2528c85a0
ms.sourcegitcommit: 92a04c57ac0a49f304fa2ea5043436f30068c3cd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65976154"
---
# <a name="reliability-warnings"></a>Avvisi di affidabilità

Gli avvisi di affidabilità supportano affidabilità di libreria e applicazione, ad esempio, utilizzo della memoria e thread corretto. Le regole di affidabilità includono:

|Regola|Descrizione|
|----------|-----------------|
|[CA2000: Eliminare gli oggetti prima di perdere l'ambito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Poiché è possibile che si verifichi un evento eccezionale che impedisca l'esecuzione del finalizzatore di un oggetto, è opportuno eliminare in modo esplicito l'oggetto prima che tutti i riferimenti a tale oggetto siano esterni all'ambito.|
|[CA2001: Evitare chiamate a metodi problematici](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Un membro chiama un metodo potenzialmente pericoloso o problematico.|
|[CA2002: Non bloccare oggetti con identità debole](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Un oggetto presenta un'identità debole quando è possibile accedere ad esso direttamente attraverso i confini dei domini applicazione. Un thread che tenta di acquisire un blocco su un oggetto con identità debole può essere bloccato da un secondo thread in un altro dominio applicazione con un blocco sullo stesso oggetto.|
|[CA2003: Non considerare i fiber come i thread](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Un thread gestito viene considerato come un thread Win32.|
|[CA2004: Rimuovere le chiamate a GC. KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Se esegue la conversione all'utilizzo di SafeHandle, rimuovere tutte le chiamate a GC. KeepAlive (object). In questo caso, le classi non necessario per chiamare GC. KeepAlive, supponendo che non è un finalizzatore ma utilizzino SafeHandle per finalizzare il sistema operativo gestisce per loro.|
|[CA2006: Usare SafeHandle per incapsulare le risorse native](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|L'utilizzo di IntPtr nel codice gestito potrebbe indicare un potenziale problema di sicurezza e affidabilità. Tutte le occorrenze di IntPtr devono essere esaminate per stabilire se al loro posto è necessario utilizzare SafeHandle o una tecnologia simile.|
|[CA2007: Non attende direttamente un'attività](../code-quality/ca2007-do-not-directly-await-task.md)|Un metodo asincrono [attende](/dotnet/csharp/language-reference/keywords/await) un <xref:System.Threading.Tasks.Task> direttamente.|