---
title: Args | Microsoft Docs
description: Usare l'opzione ARGS di VSPerfCmd.exe passare un elenco di argomenti all'applicazione di destinazione del sottocomando Launch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b91d00896b72f95b3340e8741867b58d4c2494b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142416"
---
# <a name="args"></a>Args
L'opzione **Args** di VSPerfCmd.exe specifica un elenco di argomenti passati all'applicazione di destinazione del sottocomando **Launch**.

 **Args** può essere usata solo quando è specificato anche **Launch** nella riga di comando. **Args** è facoltativa quando è specificato **Launch**.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Parametri
 `Arguments`Elenco di argomenti per l'applicazione di destinazione del **comando Launch.**

## <a name="required-options"></a>Opzioni obbligatorie
 **Launch (Avvia):** `AppName` Avvia l'applicazione specificata e inizia la profilatura con il metodo di campionamento.

## <a name="example"></a>Esempio
 L'esempio seguente usa l'opzione **Args** per passare gli argomenti a TestApp.exe.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Vedi anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilatura ASP.NET applicazioni Web](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Servizi di profilatura](../profiling/command-line-profiling-of-services.md)
