---
title: 'CA2003: non considerare i fiber come thread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 943b52f9703e60f14756bde97ce6f27c0c6f5296
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672508"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Non considerare i fiber come i thread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Category|Microsoft. affidabilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un thread gestito viene considerato come un thread Win32.

## <a name="rule-description"></a>Descrizione della regola
 Non presupporre che un thread gestito sia un thread Win32. Si tratta di una fibra. Il Common Language Runtime (CLR) eseguirà thread gestiti come fiber nel contesto di thread reali di proprietà di SQL. Questi thread possono essere condivisi tra AppDomain e persino i database nel processo di SQL Server. L'uso dell'archiviazione locale del thread gestito funziona, ma non è possibile usare l'archiviazione locale di thread non gestiti o si presuppone che il codice venga eseguito nuovamente sul thread del sistema operativo corrente. Non modificare le impostazioni, ad esempio le impostazioni locali del thread. Non chiamare CreateCriticalSection o CreateMutex tramite P/Invoke perché richiedono che anche il thread che immette un blocco debba uscire dal blocco. Poiché questo non avviene quando si usano i fiber, le sezioni e i mutex critici di Win32 saranno inutili in SQL. È possibile utilizzare in modo sicuro la maggior parte dello stato in un oggetto System. thread gestito. Sono incluse l'archiviazione locale dei thread gestiti e le impostazioni cultura correnti dell'interfaccia utente del thread. Tuttavia, per motivi di programmazione, non sarà possibile modificare le impostazioni cultura correnti di un thread quando si usa SQL; Questa operazione verrà applicata tramite una nuova autorizzazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Esaminare l'utilizzo dei thread e modificare di conseguenza il codice.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare questa regola.
