---
title: Mark | Microsoft Docs
description: Informazioni sul modo in cui l'opzione VSPerfCmd.exe Mark inserisce le informazioni specificate nel file di dati di profilatura.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4554a994fe790d5e0ec46762e830576181b312dd
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722139"
---
# <a name="mark"></a>Contrassegno
In *VSPerfCmd.exe l'opzione* **Mark** consente di inserire le informazioni specificate nel file di dati di profilatura. L'opzione Mark può essere elencata in un report di VSPerfReport separato o nella visualizzazione Contrassegni dell'interfaccia utente del profiler. È possibile usare **Mark** per specificare i punti di inizio e fine nel report e visualizzare i filtri.

 L'opzione **Mark** deve essere l'unica opzione specificata nella riga di comando.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>Parametri
 `MarkID` Intero definito dall'utente elencato come ID contrassegno nelle visualizzazioni e nei report del profiler. `MarkID` non deve essere univoco.

 `MarkName` (Facoltativo) Stringa definita dall'utente elencata come Nome contrassegno nelle visualizzazioni e nei report del profiler. Se non si specifica `MarkName`, il campo Nome contrassegno dell'elenco dei contrassegni sarà vuoto. Racchiudere le stringhe che contengono spazi o barre ("/") tra virgolette.

## <a name="example"></a>Esempio
 Questo esempio inserisce un contrassegno con ID 123 e il nome di contrassegno "TestMark".

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
