---
title: 'CA2003: Non considerare i fiber come i thread | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6563537df74d9e392bad8c4f6ce28c85b8441546
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590286"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Non considerare i fiber come i thread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2003: non considerare i fiber come i thread](https://docs.microsoft.com/visualstudio/code-quality/ca2003-do-not-treat-fibers-as-threads).

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Category|Microsoft.Reliability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un thread gestito viene considerato come un thread Win32.

## <a name="rule-description"></a>Descrizione della regola
 Non presupporre che un thread gestito è un thread Win32. È un fiber. Common language runtime (CLR) verrà eseguita thread gestiti come i fiber nel contesto del thread reali che appartengono a SQL. Questi thread possono essere condivisi tra domini applicazione e perfino i database nel processo di SQL Server. Gestita funzionerà archiviazione locale, ma non è possibile usare l'archiviazione locale di thread non gestito o si supponga che il codice verrà eseguito nuovamente sul thread del sistema operativo corrente. Non modificare le impostazioni, ad esempio le impostazioni locali del thread. Non chiamare CreateCriticalSection o CreateMutex tramite P/Invoke perché richiedono che il thread che accede a un blocco deve inoltre uscirne. Perché quando si utilizzano i fiber questo non è il caso, i mutex e sezioni critiche Win32 sarà inutili in SQL. È possibile usare la maggior parte dello stato in modo sicuro in un oggetto System. thread gestito. Ciò include l'archivio locale dei thread gestiti e le impostazioni cultura dell'interfaccia utente correnti del thread. Tuttavia, per motivi legati al modello di programmazione, non sarà in grado di modificare le impostazioni cultura correnti di un thread quando si usa SQL; questo verrà applicato a una nuova autorizzazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Esaminare l'utilizzo di thread e modificare di conseguenza il codice.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non si deve eliminare questa regola.



