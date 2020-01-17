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
ms.openlocfilehash: e936222a95681796f5c5ca423d122995e1ea5f79
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113264"
---
# <a name="reliability-warnings"></a>Avvisi di affidabilità

Gli avvisi di affidabilità supportano la libreria e l'affidabilità delle applicazioni, ad esempio l'utilizzo corretto della memoria e del thread. Di seguito sono riportate le regole di affidabilità:

|Regola|Descrizione|
|----------|-----------------|
|[CA2000: Eliminare gli oggetti prima di perdere l'ambito](../code-quality/ca2000.md)|Poiché è possibile che si verifichi un evento eccezionale che impedisca l'esecuzione del finalizzatore di un oggetto, è opportuno eliminare in modo esplicito l'oggetto prima che tutti i riferimenti a tale oggetto siano esterni all'ambito.|
|[CA2001: Evitare le chiamate a metodi problematici](../code-quality/ca2001.md)|Un membro chiama un metodo potenzialmente pericoloso o problematico.|
|[CA2002: Non bloccare oggetti con identità debole](../code-quality/ca2002.md)|Un oggetto presenta un'identità debole quando è possibile accedere ad esso direttamente attraverso i confini dei domini applicazione. Un thread che tenta di acquisire un blocco su un oggetto con identità debole può essere bloccato da un secondo thread in un altro dominio applicazione con un blocco sullo stesso oggetto.|
|[CA2003: Non considerare i fiber come i thread](../code-quality/ca2003.md)|Un thread gestito viene considerato come un thread Win32.|
|[CA2004: Rimuovere le chiamate a GC.KeepAlive](../code-quality/ca2004.md)|Se si esegue la conversione in utilizzo di SafeHandle, rimuovere tutte le chiamate a GC. KeepAlive (oggetto). In questo caso, le classi non devono chiamare GC. KeepAlive, presumendo che non dispongano di un finalizzatore, ma si affidino a SafeHandle per finalizzare l'handle del sistema operativo.|
|[CA2006: Usare SafeHandle per incapsulare le risorse native](../code-quality/ca2006.md)|L'utilizzo di IntPtr nel codice gestito potrebbe indicare un potenziale problema di sicurezza e affidabilità. Tutte le occorrenze di IntPtr devono essere esaminate per stabilire se al loro posto è necessario utilizzare SafeHandle o una tecnologia simile.|
|[Ca2007: non eseguire direttamente l'attesa di un'attività](../code-quality/ca2007.md)|Un metodo asincrono [attende](/dotnet/csharp/language-reference/keywords/await) direttamente un <xref:System.Threading.Tasks.Task>.|
