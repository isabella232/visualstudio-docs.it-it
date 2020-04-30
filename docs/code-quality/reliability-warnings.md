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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4b888dbbe7a26e5ff333ec39aa0fdfcec90b429
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586208"
---
# <a name="reliability-warnings"></a>Avvisi di affidabilità

Gli avvisi di affidabilità supportano la libreria e l'affidabilità delle applicazioni, ad esempio l'utilizzo corretto della memoria e del thread. Di seguito sono riportate le regole di affidabilità:

|Regola|Descrizione|
|----------|-----------------|
|[CA2000: Eliminare gli oggetti prima che siano esterni all'ambito](../code-quality/ca2000.md)|Poiché è possibile che si verifichi un evento eccezionale che impedisca l'esecuzione del finalizzatore di un oggetto, è opportuno eliminare in modo esplicito l'oggetto prima che tutti i riferimenti a tale oggetto siano esterni all'ambito.|
|[CA2001: Evitare le chiamate a metodi problematici](../code-quality/ca2001.md)|Un membro chiama un metodo potenzialmente pericoloso o problematico.|
|[CA2002: Non bloccare oggetti con identità debole](../code-quality/ca2002.md)|Un oggetto presenta un'identità debole quando è possibile accedere ad esso direttamente attraverso i confini dei domini applicazione. Un thread che tenta di acquisire un blocco su un oggetto con identità debole può essere bloccato da un secondo thread in un altro dominio applicazione con un blocco sullo stesso oggetto.|
|[CA2003: Non considerare i fiber come i thread](../code-quality/ca2003.md)|Un thread gestito viene considerato come un thread Win32.|
|[CA2004: Rimuovere le chiamate a GC.KeepAlive](../code-quality/ca2004.md)|Se si esegue la conversione in utilizzo di SafeHandle, rimuovere tutte le chiamate a GC. KeepAlive (oggetto). In questo caso, le classi non devono chiamare GC. KeepAlive, presumendo che non dispongano di un finalizzatore, ma si affidino a SafeHandle per finalizzare l'handle del sistema operativo.|
|[CA2006: Usare SafeHandle per incapsulare le risorse native](../code-quality/ca2006.md)|L'utilizzo di IntPtr nel codice gestito potrebbe indicare un potenziale problema di sicurezza e affidabilità. Tutte le occorrenze di IntPtr devono essere esaminate per stabilire se al loro posto è necessario utilizzare SafeHandle o una tecnologia simile.|
|[CA2007: Non attendere direttamente un'attività](../code-quality/ca2007.md)|Un metodo asincrono [attende](/dotnet/csharp/language-reference/keywords/await) direttamente un <xref:System.Threading.Tasks.Task> oggetto.|
|[CA2009: Non chiamare ToImmutableCollection su un valore ImmutableCollection](../code-quality/ca2009.md)|`ToImmutable`il metodo è stato chiamato inutilmente su una raccolta non <xref:System.Collections.Immutable> modificabile dallo spazio dei nomi.|
