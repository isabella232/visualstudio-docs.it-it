---
title: 'DA0026: Tempo di elaborazione CPU kernel eccessivo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fef0a3c42be1057bd1217ec676ae43b220d80345
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54768971"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Tempo di elaborazione CPU kernel eccessivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rule Id|TODO|  
| Categoria | Utilizzo degli strumenti di profilatura |  
| Metodo di profilatura | Campionamento |  
| Messaggio | È stata misurata relativamente elevata quantità di tempo di CPU in modalità kernel. Per determinare la causa, abilitare il campionamento SysCall.  
| Tipo di regola | Informazioni |  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## <a name="cause"></a>Causa  
 Il tempo CPU proporzionale eseguito in modalità kernel ha superato la quantità di tempo trascorso in modalità utente. Per determinare la causa degli elevati tempi di esecuzione in modalità kernel, eseguire di nuovo la profilatura e abilitare il campionamento del numero di chiamate di sistema (syscalls).  
  
## <a name="rule-description"></a>Descrizione della regola  
 La percentuale relativamente elevata del tempo impiegato dall'applicazione in modalità kernel può giustificare l'esecuzione di ulteriori analisi. Un'applicazione in modalità utente passa alla modalità kernel per eseguire operazioni di I/O, per attendere primitive di sincronizzazione di thread o processi o per eseguire chiamate di sistema. È possibile analizzare i tipi di chiamate di sistema effettuati dall'applicazione e le funzioni responsabili di tali chiamate selezionando l'opzione per raccogliere stack di chiamate campione in base alle chiamate di sistema.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per analizzare i tipi di chiamate di sistema effettuati dall'applicazione, eseguire nuovamente il profilo e selezionare l'opzione per raccogliere campioni in base alle chiamate al sistema. Se si eseguono gli strumenti di profilatura nell'IDE, vedere [Procedura: Scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md) per altre informazioni. Se si eseguono gli strumenti di profilatura dalla riga di comando, vedere la sezione **Sampling Interval Options** (Opzioni di intervallo di campionamento) dell'argomento [VSPerfCmd](../profiling/vsperfcmd.md) nel riferimento agli strumenti di profilatura della riga di comando.
