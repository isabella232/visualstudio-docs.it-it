---
title: Launch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9834c10c58fb343de0707fa0b805586a6cdebcb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778609"
---
# <a name="launch"></a>Launch
L'opzione **Launch** avvia il profiler usando il metodo di campionamento e avvia anche l'applicazione specificata.

 Per usare l'opzione **Launch**, è necessario specificare il metodo **Sample** nell'opzione **Start**.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Launch:AppName [Options]
```

#### <a name="parameters"></a>Parametri
 `AppName` Nome dell'applicazione da avviare. Sono supportati percorsi completi e parziali dalla directory corrente.

## <a name="valid-options"></a>Opzioni valide
 Le seguenti opzioni di VSPerfCmd possono essere combinate con l'opzione **Launch** in una singola riga di comando.

 **Inizio:** `Method` Inizializza la sessione del profiler da riga di comando e imposta il metodo di profilatura specificato.

 **GlobalOn** e **GlobalOff** Riprende (**GlobalOn**) o sospende (**GlobalOff**) la profilatura, ma non termina la sessione di profilatura.

 **ProcessOn:** `PID` e **ProcessOff**: `PID` riprende (**ProcessOn**) o sospende (**ProcessOff**) la profilatura per il processo specificato.

 **TargetCLR** Specifica la versione di Common Language Runtime (CLR) di .NET Framework da sottoporre a profilatura quando in una sessione di profilatura è caricata più di una versione. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.

## <a name="exclusive-options"></a>Opzioni esclusive
 È possibile usare le opzioni seguenti solo con l'opzione **Launch**.

 **Console** Avvia l'applicazione della riga di comando specificata in una nuova finestra.

 **Argomenti:** `ArgList` Specifica l'elenco di argomenti da passare all'applicazione.

 **LineOff** Disabilita la raccolta dei dati di profilatura a livello di riga.

## <a name="sampling-options"></a>Opzioni di campionamento
 È possibile specificare una delle opzioni seguenti per l'intervallo di campionamento nella riga di comando di **Launch**. L'intervallo di campionamento predefinito è 10.000.000 di cicli di clock del processore.

 **Timer**[**:** `Cycles` ]**PF**[**:** `Events` ]**sys**[**:** `Events` ]**Counter**[**:** `Name` , `Reload` , `FriendlyName` ]**GC**[:**allocation**&#124;**Lifetime**] specifica il numero e il tipo di intervallo di campionamento.

- **Timer**: esegue il campionamento di ogni `Cycles` dei cicli di clock del processore non interrotti. Se non si specifica `Cycles`, vengono usati 10.000.000 di cicli.

- **PF**: esegue il campionamento di ogni `Events` errori di pagina. Se non si specifica `Events`, vengono usati 10 errori di pagina.

- **Sys**: esegue il campionamento ogni `Events` chiamate al sistema operativo. Se non si specifica `Events`, vengono usate 10 chiamate del sistema.

- **Counter**: esegue il campionamento ogni `Reload` dei contatori delle prestazioni della CPU specificato da `Name`. Facoltativamente, `FriendlyName` può specificare una stringa da usare come intestazione di colonna nei rapporti del profiler.

- **GC**: raccoglie dati di memoria .NET. Per impostazione predefinita, (**allocation**), i dati vengono raccolti in corrispondenza di ogni evento di allocazione di memoria. Quando si specifica il parametro **lifetime**, i dati vengono raccolti anche in corrispondenza di ogni evento di Garbage Collection.

## <a name="example"></a>Esempio
 Questo esempio illustra l'uso di **Launch** per avviare un'applicazione.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
