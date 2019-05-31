---
title: GlobalOn e GlobalOff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ee29b677096e46d965e8191cf26a829587471dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969628"
---
# <a name="globalon-and-globaloff"></a>GlobalOn e GlobalOff
Le opzioni *GlobalOff* e **GlobalOn** di **VSPerfCmd.exe** consentono di sospendere e riprendere la profilatura per tutti i processi e i thread in una sessione di profilatura da riga di comando.

 È possibile specificare **GlobalOn** e **GlobalOff** come le uniche opzioni in una riga di comando di *VSPerfCmd.exe* oppure includerle in righe di comando che contengono anche le opzioni **Start**, **Launch** o **Attach**.

 **GlobalOn** e **GlobalOff** possono anche essere combinate con le opzioni **ProcessOn**, **ProcessOff**, **ThreadOn** e  **ThreadOff**.

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

 **Start:** `Method` Inizializza la sessione del profiler da riga di comando e imposta il metodo di profilatura specificato.

 **Launch:** `AppName` Avvia l'applicazione specificata e inizia la profilatura con il metodo di campionamento.

 **Attach:** `PID` Avvia la profilatura del processo specificato.

 {**ProcessOff**&#124;**ProcessOn**} **:** `PID` Arresta o avvia la profilatura per il processo specificato.

 {**ThreadOff**&#124;**ThreadOn**} **:** `TID` Arresta o avvia il profiling per il processo specificato (solo metodo di strumentazione).

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

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)