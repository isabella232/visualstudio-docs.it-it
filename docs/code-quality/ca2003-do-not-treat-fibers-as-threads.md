---
title: 'CA2003: Non considerare i fiber come i thread'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f5e4e7eb28207cb37824b23acbbac02b6df380d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233140"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Non considerare i fiber come i thread

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Category|Microsoft.Reliability|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un thread gestito viene considerato come un thread Win32.

## <a name="rule-description"></a>Descrizione della regola

Non presupporre che un thread gestito sia un thread Win32; si tratta di una fibra. Il Common Language Runtime (CLR) esegue thread gestiti come fibre nel contesto di thread reali di proprietà di SQL. Questi thread possono essere condivisi tra AppDomain e persino i database nel processo di SQL Server. L'uso dell'archiviazione locale del thread gestito funziona, ma non è possibile usare l'archiviazione locale di thread non gestiti o si presuppone che il codice venga eseguito nuovamente sul thread del sistema operativo corrente. Non modificare le impostazioni, ad esempio le impostazioni locali del thread. Non chiamare CreateCriticalSection o CreateMutex tramite P/Invoke perché richiedono che anche il thread che immette un blocco debba uscire dal blocco. Poiché il thread che entra in un blocco non esce da un blocco quando si usano i fiber, le sezioni critiche e i mutex Win32 sono inutili in SQL. È possibile utilizzare in modo sicuro la maggior parte dello stato <xref:System.Threading.Thread> di un oggetto gestito, tra cui l'archiviazione locale di thread gestiti e le impostazioni cultura dell'interfaccia utente corrente del thread. Tuttavia, per motivi di programmazione, non sarà possibile modificare le impostazioni cultura correnti di un thread quando si usa SQL. Questa limitazione verrà applicata tramite una nuova autorizzazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Esaminare l'utilizzo dei thread e modificare di conseguenza il codice.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non eliminare questa regola.