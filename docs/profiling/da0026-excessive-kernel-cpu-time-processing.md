---
title: DA0026 - Tempo di elaborazione CPU kernel eccessivo | Microsoft Docs
description: Il tempo CPU proporzionale eseguito in modalità kernel ha superato la quantità di tempo trascorso in modalità utente.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2c0c15ef033b6e27dd047992e3c50cdbb25cf53a14e1bf6092f527ee2a298da1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396721"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Tempo di elaborazione CPU kernel eccessivo

|Elemento|valore|
|-|-|
|ID regola|TODO|
|Category|Uso degli strumenti di profilatura|
|Metodo di profilatura|campionamento|
|Message|È stato rilevato un elevato livello di tempo CPU in modalità kernel. Per determinare la causa, abilitare il campionamento SysCall.|
|Tipo regola|Informazioni|

 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.

## <a name="cause"></a>Causa
 Il tempo CPU proporzionale eseguito in modalità kernel ha superato la quantità di tempo trascorso in modalità utente. Per determinare la causa degli elevati tempi di esecuzione in modalità kernel, eseguire di nuovo la profilatura e abilitare il campionamento del numero di chiamate di sistema (syscalls).

## <a name="rule-description"></a>Descrizione della regola
 La percentuale relativamente elevata del tempo impiegato dall'applicazione in modalità kernel può giustificare l'esecuzione di ulteriori analisi. Un'applicazione in modalità utente passa alla modalità kernel per eseguire operazioni di I/O, per attendere primitive di sincronizzazione di thread o processi o per eseguire chiamate di sistema. È possibile analizzare i tipi di chiamate di sistema effettuati dall'applicazione e le funzioni responsabili di tali chiamate selezionando l'opzione per raccogliere stack di chiamate campione in base alle chiamate di sistema.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per analizzare i tipi di chiamate di sistema effettuati dall'applicazione, eseguire nuovamente il profilo e selezionare l'opzione per raccogliere campioni in base alle chiamate al sistema. Se si eseguono gli strumenti di profilatura nell'IDE, vedere [Procedura: Scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md) per altre informazioni. Se gli strumenti di profilatura vengono eseguiti dalla riga di comando, vedere la sezione **Opzioni dell'intervallo di campionamento** dell'articolo relativo a [VSPerfCmd](../profiling/vsperfcmd.md) nei riferimenti agli strumenti della riga di comando degli strumenti di profilatura.
