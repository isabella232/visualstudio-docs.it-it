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
ms.openlocfilehash: cb39bb5f59373f52d77c7cc5d13d12544d4c0314
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252581"
---
# <a name="reliability-warnings"></a>Avvisi di affidabilità

Gli avvisi di affidabilità supportano la libreria e l'affidabilità delle applicazioni, ad esempio l'utilizzo corretto della memoria e del thread. Di seguito sono riportate le regole di affidabilità:

|Regola|Descrizione|
|----------|-----------------|
|[CA2000: Elimina gli oggetti prima di perdere l'ambito @ no__t-0|Poiché è possibile che si verifichi un evento eccezionale che impedisca l'esecuzione del finalizzatore di un oggetto, è opportuno eliminare in modo esplicito l'oggetto prima che tutti i riferimenti a tale oggetto siano esterni all'ambito.|
|[CA2001: Evitare la chiamata a metodi problematici @ no__t-0|Un membro chiama un metodo potenzialmente pericoloso o problematico.|
|[CA2002: Non bloccare gli oggetti con identità vulnerabile @ no__t-0|Un oggetto presenta un'identità debole quando è possibile accedere ad esso direttamente attraverso i confini dei domini applicazione. Un thread che tenta di acquisire un blocco su un oggetto con identità debole può essere bloccato da un secondo thread in un altro dominio applicazione con un blocco sullo stesso oggetto.|
|[CA2003: Non considerare i fiber come thread @ no__t-0|Un thread gestito viene considerato come un thread Win32.|
|[CA2004: Rimuovere le chiamate a GC. KeepAlive @ no__t-0|Se si esegue la conversione in utilizzo di SafeHandle, rimuovere tutte le chiamate a GC. KeepAlive (oggetto). In questo caso, le classi non devono chiamare GC. KeepAlive, presumendo che non dispongano di un finalizzatore, ma si affidino a SafeHandle per finalizzare l'handle del sistema operativo.|
|[CA2006: Utilizzare SafeHandle per incapsulare le risorse native @ no__t-0|L'utilizzo di IntPtr nel codice gestito potrebbe indicare un potenziale problema di sicurezza e affidabilità. Tutte le occorrenze di IntPtr devono essere esaminate per stabilire se al loro posto è necessario utilizzare SafeHandle o una tecnologia simile.|
|[CA2007: Non attendere direttamente un'attività @ no__t-0|Un metodo asincrono [attende](/dotnet/csharp/language-reference/keywords/await) direttamente un <xref:System.Threading.Tasks.Task>.|
