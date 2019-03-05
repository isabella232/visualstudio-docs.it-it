---
title: Console | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74a5cecbdf3bba942c888a5cde3d49236047f4ee
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607876"
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

 **Launch:** `AppName` Avvia il profiler e l'applicazione specificata da `AppName`.

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)