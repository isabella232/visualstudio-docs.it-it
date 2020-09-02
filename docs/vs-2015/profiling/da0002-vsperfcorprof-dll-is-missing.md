---
title: 'DA0002: VSPerfCorProf.dll mancante | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5723506415a0ddbf816b896e23e93eaa706bf7e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158723"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll mancante
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID regola | DA0002 |  
| Categoria | Utilizzo Strumenti di profilatura |  
| Metodi di profilatura | Profilatura tramite gli strumenti da riga di comando VSPerfCmd e VSPerfASPNETCmd |  
| Messaggio | Sembra che il file sia stato raccolto senza impostare correttamente le variabili di ambiente con VSPerfCLREnv. cmd. I simboli per i file binari gestiti potrebbero non essere risolti.|  
| Tipo di regola | Informazioni |  
  
## <a name="cause"></a>Causa  
 Il profiler non è in grado di trovare VSPerfCorProf.dll durante l'esecuzione della profilatura. Questo avviso si verifica quando vengono usati gli strumenti da riga di comando per la raccolta di dati del profiler senza usare lo strumento VSPerfCLREnv.cmd per inizializzare le variabili di ambiente necessarie. L'avviso può essere generato anche se un altro profiler è in esecuzione all'avvio degli strumenti di profilatura.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Prima di eseguire la profilatura è necessario impostare variabili di ambiente specifiche per consentire al profiler di risolvere i simboli nei file binari di .NET Framework. Questo avviso indica che lo strumento VSPerfCLREnv.cmd non è stato eseguito prima della raccolta dei dati di profilatura. È possibile che i simboli per i file binari gestiti non vengano risolti. Per ulteriori informazioni sull'utilizzo del Strumenti di profilatura dalla riga di comando, vedere [profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Quando si profilano applicazioni gestite usando gli strumenti da riga di comando negli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], eseguire lo strumento da riga di comando [VSPerfCLREnv](../profiling/vsperfclrenv.md) prima di iniziare la raccolta dei dati.
