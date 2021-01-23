---
title: Console | Microsoft Docs
description: Usare l'opzione console di VSPerfCmd.exe per avviare l'applicazione specificata in una nuova finestra del prompt dei comandi. È necessario usarlo con l'opzione Launch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 93c39bfb503bec9858e33b7acf04e0f0433264b9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720904"
---
# <a name="console"></a>Console
L'opzione **Console** di VSPerfCmd.exe consente di avviare l'applicazione specificata in una nuova finestra del prompt dei comandi. **Console** può essere usata solo con l'opzione **Launch** di VSPerfCmd. Se l'applicazione non è un'applicazione della riga di comando, **Console** non ha alcun effetto.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parametri
 nessuno

## <a name="required-options"></a>Opzioni obbligatorie
 L'opzione **Console** può essere specificata solo in una riga di comando che contiene anche l'opzione **Launch**.

 **Avvia:** `AppName` Avvia il profiler e l'applicazione specificata da `AppName` .

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
