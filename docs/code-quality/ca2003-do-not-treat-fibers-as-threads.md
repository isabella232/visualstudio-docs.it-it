---
title: 'CA2003: Non considerare i fiber come i thread | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 16e3873c54b4b0c060f6703102d0429136ed710a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
 Si presuppone che un thread gestito è un thread Win32. È un fiber. Common language runtime (CLR) eseguirà i thread gestiti come fiber nel contesto del thread reali che appartengono a SQL. Questi thread possono essere condivisi tra AppDomains e database nel processo di SQL Server. Utilizzando gestito funzionerà archiviazione locale di thread, ma è possibile non utilizzare l'archiviazione locale di thread non gestito o si presuppone che il codice verrà eseguito nuovamente sul thread del sistema operativo corrente. Non modificare le impostazioni, ad esempio le impostazioni locali del thread. Non chiamare CreateCriticalSection o CreateMutex tramite P/Invoke perché richiedono che il thread che accede a un blocco deve anche uscirne. Poiché non sarà il caso quando si utilizzano i fiber, i mutex e le sezioni critiche Win32 dovrà essere inutili, in SQL. Potrebbe essere possibile utilizzare la maggior parte dello stato su un oggetto System. thread gestito. Ciò include l'archiviazione locale di thread gestiti e le impostazioni cultura dell'interfaccia utente correnti del thread. Tuttavia, per motivi legati al modello di programmazione, non sarà in grado di modificare le impostazioni cultura correnti di un thread quando si utilizza SQL. verrà applicata una nuova autorizzazione.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Esaminare l'utilizzo di thread e modificare di conseguenza il codice.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non è necessario eliminare questa regola.