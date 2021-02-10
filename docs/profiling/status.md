---
title: Status | Microsoft Docs
description: Informazioni sul modo in cui l'opzione stato VSPerfCmd.exe Visualizza informazioni sullo stato del profiler e sui processi attualmente in corso di profilatura.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 894afcbf8827fe0b5d5662a4c20e302f8224263f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960039"
---
# <a name="status"></a>Stato
L'opzione *Status di* **VSPerfCmd.exe** visualizza informazioni sullo stato del profiler e di eventuali processi in corso di profilatura.

 L'opzione **Status** deve essere l'unica opzione specificata nella riga di comando. Prima di poter visualizzare qualsiasi stato è necessario inizializzare il profiler con l'opzione *Start di* **VSPerfCmd.exe**.

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
