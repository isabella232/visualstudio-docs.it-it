---
title: Launch | Microsoft Docs
description: Informazioni su come l'opzione Launch avvia il profiler usando il metodo di campionamento e avvia anche l'applicazione specificata.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 57c7cbe1ee119489171417515e557b46ee2755ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107420"
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

 **Avvio:** `Method` Inizializza la sessione del profiler della riga di comando e imposta il metodo di profilatura specificato.

 **GlobalOn** e **GlobalOff** Riprende (**GlobalOn**) o sospende (**GlobalOff**) la profilatura, ma non termina la sessione di profilatura.

 **ProcessOn:** `PID` e **ProcessOff**: riprende `PID` (**ProcessOn**) o sospende (**ProcessOff**) la profilatura per il processo specificato.

 **TargetCLR** Specifica la versione di Common Language Runtime (CLR) di .NET Framework da sottoporre a profilatura quando in una sessione di profilatura è caricata più di una versione. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.

## <a name="exclusive-options"></a>Opzioni esclusive
 È possibile usare le opzioni seguenti solo con l'opzione **Launch**.

 **Console** Avvia l'applicazione della riga di comando specificata in una nuova finestra.

 **Args:** `ArgList` Specifica l'elenco di argomenti da passare all'applicazione.

 **LineOff** Disabilita la raccolta dei dati di profilatura a livello di riga.

## <a name="sampling-options"></a>Opzioni di campionamento
 È possibile specificare una delle opzioni seguenti per l'intervallo di campionamento nella riga di comando di **Launch**. L'intervallo di campionamento predefinito è 10.000.000 di cicli di clock del processore.

 **Timer**[**:** `Cycles` ]**PF**[**:** `Events` ]**Sys**[**:** `Events` ]**Counter**[**:**, ] GC [: allocation&#124;lifetime ] Specifica il numero e il tipo di intervallo `Name` `Reload` di `FriendlyName` campionamento. 

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

## <a name="see-also"></a>Vedi anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
