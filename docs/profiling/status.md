---
title: Status | Microsoft Docs
description: Informazioni su come lVSPerfCmd.exe'opzione Stato visualizza informazioni sullo stato del profiler e su tutti i processi attualmente profilati.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9d72f8062f607da08775d369dc7a154a8016e45c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141311"
---
# <a name="status"></a>Stato
 **LVSPerfCmd.exe'opzione Stato** visualizza informazioni sullo stato del profiler e su tutti i processi attualmente profilati.

 L'opzione **Status** deve essere l'unica opzione specificata nella riga di comando. Il profiler deve essere  inizializzato con **lVSPerfCmd.exe'opzione Start** prima di poter visualizzare qualsiasi stato.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Status
```

#### <a name="parameters"></a>Parametri
 nessuno

## <a name="remarks"></a>Osservazioni
 L'opzione **Status** consente di visualizzare le informazioni sullo stato seguenti per il profiler.

 **Nome file di output** Percorso e nome del file di dati del profiler corrente.

 **Modalità di raccolta** SAMPLE o TRACE

 **Numero massimo di processi** Numero massimo di processi di cui è possibile eseguire la profilatura contemporaneamente e numero di processi attivi.

 **Numero massimo di thread** Numero massimo di thread di cui è possibile eseguire la profilatura contemporaneamente.

 **Numero di buffer** Numero di buffer di memoria dedicati alla scrittura dei dati di profilatura.

 **Dimensione dei buffer** Dimensione di un buffer di memoria in byte.

 L'opzione **Status** visualizza le informazioni sullo stato seguenti per ogni processo in corso di profilatura.

 **Processo** Nome del processo di cui è stata eseguita la profilatura.

 **ID processo** Identificatore di sistema del processo.

 **Num. thread** Numero di thread in esecuzione.

 **Conteggio Start/Stop** Conteggio del profiler interno principale per controllare la raccolta dei dati per questo processo. Il conteggio deve essere uguale a uno per raccogliere i dati. Il conteggio Start/Stop può essere modificato dalle API del profiler e dalle opzioni di VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** e **ThreadOff**.

 **Conteggio Suspend/Resume** Conteggio del profiler interno principale per controllare la raccolta dei dati per questo processo. Il conteggio deve essere minore o uguale a zero per raccogliere i dati. Il conteggio **Suspend/Resume** può essere modificato solo dalle API del profiler.

 **Utenti con diritti di accesso al monitor** Elenca i nomi degli utenti che hanno accesso al profiler. È possibile concedere l'accesso ad altri utenti tramite l'opzione **Admin** di VSPerfCmd.exe.

## <a name="see-also"></a>Vedi anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
