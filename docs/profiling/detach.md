---
title: Detach | Microsoft Docs
description: Usare l'opzione Scollega VSPerfCmd.exe per disconnettere il profiler dal processo specificato o da tutti i processi se non ne viene specificato nessuno.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5738548f5a06804ab6405606b02dbcb1cfcb76f2a8784ac61b4dd9f9f873e7b6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333197"
---
# <a name="detach"></a>Detach
L'opzione **Detach** di VSPerfCmd.exe disconnette il profiler dai processi specificati o da tutti i processi se non ne vengono specificati. La profilatura deve essere inizializzata usando il metodo di campionamento.

 La profilatura avviata con l'opzione **Launch** o **Attach** può essere disconnessa con **Detach**. Il profiler può essere ricollegato usando i comandi **Attach** successivi.

 **Detach** non consente di chiudere il file di dati di profilatura. Usare l'opzione **Shutdown** per terminare la profilatura e chiudere il file di dati.

> [!NOTE]
> Se l'opzione **Start** è stata specificata con l'opzione **Crosssession**, eventuali chiamate a **VSPerfCmd /Attach** o a **VSPerfCmd /Detach** devono specificare anche **Crosssession**.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]
```

#### <a name="parameters"></a>Parametri
 `PIDs|ProcessNames``PID`: identificatore di sistema numerico di uno o più processi.

 `ProcessNames` - Nome del processo. Se si eseguono più istanze del processo denominato, i risultati sono imprevedibili.

 Se si specificano più processi, separarli con virgole.

 Se non viene specificato alcun processo, il profiler viene disconnesso da tutti i processi profilati.

## <a name="valid-options"></a>Opzioni valide
 Le seguenti opzioni di **VSPerfCmd** possono essere combinate con l'opzione **Attach** in una singola riga di comando.

 **Crosssession** Consente la profilatura delle applicazioni in sessioni diverse da quella di accesso. Obbligatoria se l'opzione **Start** è stata specificata con l'opzione **Crosssession**.

## <a name="example"></a>Esempio
 In questo esempio il comando **Detach** sospende la profilatura e il comando **Shutdown** chiude il file di dati del profiler.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
;REM Excercise the application
VSPerfCmd.exe /Detach
VSPerfCmd.exe /Shutdown
```

## <a name="see-also"></a>Vedi anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
