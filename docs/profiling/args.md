---
title: Args | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b6d01a95b7e0872d6bb36c6d9f3917bc6a05b3b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "74779818"
---
# <a name="args"></a>Args
L'opzione **Args** di VSPerfCmd.exe specifica un elenco di argomenti passati all'applicazione di destinazione del sottocomando **Launch**.

 **Args** può essere usata solo quando è specificato anche **Launch** nella riga di comando. **Args** è facoltativa quando è specificato **Launch**.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Parametri
 `Arguments` Elenco di argomenti per l'applicazione di destinazione del comando **Launch** .

## <a name="required-options"></a>Opzioni obbligatorie
 **Avvia:** `AppName` Avvia l'applicazione specificata e inizia la profilatura con il metodo di campionamento.

## <a name="example"></a>Esempio
 L'esempio seguente usa l'opzione **Args** per passare gli argomenti a TestApp.exe.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Servizi di profilatura](../profiling/command-line-profiling-of-services.md)
