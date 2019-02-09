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
ms.openlocfilehash: 8faaf3c6557065188c795d75ea9bbe4e78998709
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55969841"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Non considerare i fiber come i thread

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Category|Microsoft.Reliability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un thread gestito viene considerato come un thread Win32.

## <a name="rule-description"></a>Descrizione della regola

Non presupporre che un thread gestito è un thread Win32. è un fiber. Common language runtime (CLR) i thread gestiti viene eseguito come fiber nel contesto del thread reali che appartengono a SQL. Questi thread possono essere condivisi tra domini applicazione e perfino i database nel processo di SQL Server. Usando managed works archiviazione locale di thread, ma non è possibile usare l'archiviazione locale di thread non gestito o si supponga che il codice verrà eseguito nuovamente sul thread del sistema operativo corrente. Non modificare le impostazioni, ad esempio le impostazioni locali del thread. Non chiamare CreateCriticalSection o CreateMutex tramite P/Invoke perché richiedono che il thread che accede a un blocco deve inoltre uscirne. Poiché il thread che accede a un blocco non consente di uscire un blocco quando si usano fiber, mutex e sezioni critiche Win32 sono inutili in SQL. È possibile usare la maggior parte dello stato in modo sicuro in un oggetto gestito <xref:System.Threading.Thread> oggetto, tra cui archivio locale dei thread gestiti e le impostazioni cultura dell'interfaccia utente correnti del thread. Per motivi legati al modello di programmazione, tuttavia, sarà possibile modificare le impostazioni cultura correnti di un thread quando si usa SQL. Questa limitazione verrà imposta una nuova autorizzazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Esaminare l'utilizzo di thread e modificare di conseguenza il codice.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non eliminare questa regola.