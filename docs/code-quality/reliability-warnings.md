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
ms.openlocfilehash: d45deadc48445e043535e84b36718a14f5b391f6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182807"
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
|[CA2007: Non attendere direttamente un'attività](../code-quality/ca2007.md)|Un metodo asincrono [attende](/dotnet/csharp/language-reference/keywords/await) direttamente un oggetto <xref:System.Threading.Tasks.Task> .|
|[CA2009: Non chiamare ToImmutableCollection su un valore ImmutableCollection](../code-quality/ca2009.md)|`ToImmutable`il metodo è stato chiamato inutilmente su una raccolta non modificabile dallo <xref:System.Collections.Immutable> spazio dei nomi.|
|[CA2011: Non assegnare la proprietà all'interno del relativo setter](../code-quality/ca2011.md) | Una proprietà è stata assegnata per errore a un valore all'interno della relativa [funzione di accesso set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
|[Ca2015: non definire finalizzatori per i tipi derivati da MemoryManager &lt; T&gt;](../code-quality/ca2015.md) | L'aggiunta di un finalizzatore a un tipo derivato da <xref:System.Buffers.MemoryManager%601> può consentire la liberazione della memoria mentre è ancora in uso da un oggetto <xref:System.Span%601> . |
