---
title: ProcessOn e ProcessOff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab218f8dabb2b4360c1be17d809399a752f7cc2c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972411"
---
# <a name="processon-and-processoff"></a>ProcessOn e ProcessOff
I sottocomandi **ProcessOff** e **ProcessOn** di VSPerfCmd.exe sospendono e riprendono la profilatura per il processo specificato in una sessione di profilatura da riga di comando. **ProcessOff** arresta la profilatura del processo e **ProcessOn** avvia la profilatura del processo.

 Nella maggior parte dei casi si specifica **ProcessOn** o **ProcessOff** come unica opzione in una riga di comando di VSPerfCmd.exe, ma questi sottocomandi possono anche essere combinati con i sottocomandi **GlobalOn**, **GlobalOff**, **ThreadOn** e **ThreadOff**.

 I sottocomandi **ProcessOn** e **ProcessOff** interagiscono con i sottocomandi **GlobalOn** e **GlobalOff** che controllano la raccolta dei dati per tutti i processi in una sessione di profilatura da riga di comando e i sottocomandi **ThreadOn** e **ThreadOff** che controllano la raccolta dei dati per un processo specificato.

 I sottocomandi **ProcessOff** e **ProcessOn** influenzano anche il conteggio Start/Stop per il processo, gestito dalle funzioni API del profiler.

- **ProcessOff** imposta immediatamente il conteggio Start/Stop per il processo su 0 e sospende quindi la profilatura.

- **ProcessOn** imposta immediatamente il conteggio Start/Stop per il processo su 1 e riprende quindi la profilatura.

  Per altre informazioni, vedere [API per strumenti di profilatura](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]

```

#### <a name="parameters"></a>Parametri
 `PID` Identificatore integer del processo da avviare o arrestare. Gli ID di processo sono elencati nella scheda **Processi** di Gestione attività Windows.

## <a name="required-subcommands"></a>Sottocomandi obbligatori
 nessuno

## <a name="valid-subcommands"></a>Sottocomandi validi
 **ProcessOn** e **ProcessOff** possono essere specificati su righe di comando che contengono anche i sottocomandi seguenti.

 **Start:** `Method` Inizializza la sessione di profilatura da riga di comando e imposta il metodo di profilatura specificato.

 **Launch:** `AppName` Avvia l'applicazione specificata e inizia la profilatura con il metodo di campionamento.

 **Attach:** `PID` Avvia la profilatura del processo specificato.

 **GlobalOff**&#124;**GlobalOn** Arresta o avvia la profilatura per tutti i processi in una sessione di profilatura da riga di comando.

 {**ThreadOff**&#124;**ThreadOn**}**:**`TID` Arresta o avvia la profilatura per il thread specificato (solo metodo di strumentazione).

## <a name="example"></a>Esempio
 In questo esempio, il sottocomando **ProcessOff** viene usato per raccogliere dati di profilatura per l'avvio dell'applicazione.

```cmd
; Initialize the profiler.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp
; Start the instrumented application.
; Stop profiling the process after startup.
VSPerfCmd.exe /ProcessOff:12345
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)