---
title: GlobalOn e GlobalOff | Microsoft Docs
description: Esaminare le opzioni GlobalOn e GlobalOff in VSPerfCmd.exe. Queste opzioni sospendono e riprendono la profilatura per processi e thread in una sessione di profilatura della riga di comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 960a7d4f1977dfd79ba4d80505b733eba876e38721615f364986ac0bd22b23a8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121355256"
---
# <a name="globalon-and-globaloff"></a>GlobalOn e GlobalOff
Le *VSPerfCmd.exe* **opzioni GlobalOff** e **GlobalOn** sospendino e riprendono la profilatura per tutti i processi e i thread in una sessione di profilatura della riga di comando.

 È possibile specificare **GlobalOn** e **GlobalOff** come le uniche opzioni in una riga di comando *diVSPerfCmd.exeoppure* includerle nelle righe di comando che contengono anche le opzioni **Start**, **Launch** o **Attach.**

 **GlobalOn** e **GlobalOff** possono anche essere combinate con le opzioni **ProcessOn**, **ProcessOff**, **ThreadOn** e **ThreadOff**.

 Le opzioni **GlobalOn** e **GlobalOff** interagiscono con le opzioni **ProcessOn** e **ProcessOff** che controllano la raccolta dei dati per un processo specificato e con le opzioni **ThreadOn** e **ThreadOff** che controllano la raccolta dei dati per un thread specificato.

 Le opzioni **GlobalOff** e **GlobalOn** influiscono anche sul conteggio globale Start/Stop gestito dalle funzioni API del profiler.

- **GlobalOff** imposta immediatamente il conteggio globale Start/Stop su 0 e sospendere la profilatura.

- **GlobalOn** imposta immediatamente il conteggio globale Start/Stop su 1 e riprende la profilatura.

  Per altre informazioni, vedere [API per strumenti di profilatura](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /{GlobalOff|GlobalOn}

VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]

VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]
```

#### <a name="parameters"></a>Parametri
 nessuno

## <a name="valid-options"></a>Opzioni valide
 **GlobalOn** e **GlobalOff** possono essere specificate su righe di comando che contengono anche le opzioni seguenti.

 **Avvio:** `Method` Inizializza la sessione del profiler della riga di comando e imposta il metodo di profilatura specificato.

 **Avviare:** `AppName` Avvia l'applicazione specificata e inizia la profilatura con il metodo di campionamento.

 **Collega:** `PID` Avvia la profilatura del processo specificato.

 {**ProcessOff&#124;** **ProcessOn**} **:**`PID` Arresta o avvia la profilatura per il processo specificato.

 {**ThreadOff**&#124;**ThreadOn**} **:**`TID` Arresta o avvia la profilatura per il processo specificato (solo metodo di strumentazione).

## <a name="example"></a>Esempio
 In questo esempio le opzioni **GlobalOff** e **GlobalOn** vengono usate per evitare di raccogliere dati di profilatura per l'avvio e la chiusura delle applicazioni.

```cmd
; Initialize the profiler with profiling stopped.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff
; Start an instrumented application and wait for it to warm up.
; Start profiling.
VSPerfCmd.exe /GlobalOn
; Exercise the application functionality that you want to profile.
; Stop profiling.
VSPerfCmd.exe /GlobalOff
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Vedi anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
