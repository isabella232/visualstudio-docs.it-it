---
title: Avvisi di affidabilità | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 250eb10581858534ec6325a1bfb61d84bddac05a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603967"
---
# <a name="reliability-warnings"></a>avvisi di affidabilità
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli avvisi di affidabilità supportano la libreria e l'affidabilità delle applicazioni, ad esempio l'utilizzo corretto della memoria e del thread.

## <a name="in-this-section"></a>Contenuto della sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA2000: Eliminare gli oggetti prima che siano esterni all'ambito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Poiché è possibile che si verifichi un evento eccezionale che impedisca l'esecuzione del finalizzatore di un oggetto, è opportuno eliminare in modo esplicito l'oggetto prima che tutti i riferimenti a tale oggetto siano esterni all'ambito.|
|[CA2001: Evitare le chiamate a metodi problematici](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Un membro chiama un metodo potenzialmente pericoloso o problematico.|
|[CA2002: Non bloccare oggetti con identità debole](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Un oggetto presenta un'identità debole quando è possibile accedere ad esso direttamente attraverso i confini dei domini applicazione. Un thread che tenta di acquisire un blocco su un oggetto con identità debole può essere bloccato da un secondo thread in un altro dominio applicazione con un blocco sullo stesso oggetto.|
|[CA2003: Non considerare i fiber come i thread](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Un thread gestito viene considerato come un thread Win32.|
|[CA2004: Rimuovere le chiamate a GC.KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Se si esegue la conversione in utilizzo di SafeHandle, rimuovere tutte le chiamate a GC. KeepAlive (oggetto). In questo caso, le classi non devono chiamare GC. KeepAlive, presumendo che non dispongano di un finalizzatore, ma si affidino a SafeHandle per finalizzare l'handle del sistema operativo.|
|[CA2006: Usare SafeHandle per incapsulare le risorse native](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|L'utilizzo di IntPtr nel codice gestito potrebbe indicare un potenziale problema di sicurezza e affidabilità. Tutte le occorrenze di IntPtr devono essere esaminate per stabilire se al loro posto è necessario utilizzare SafeHandle o una tecnologia simile.|
