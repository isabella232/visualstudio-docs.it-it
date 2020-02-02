---
title: Analizzare l'utilizzo della memoria
ms.custom: seodec18
ms.date: 01/02/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98382cdcde1e8413d7b6592b52aaee09e6c4274c
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76923328"
---
# <a name="analyze-memory-usage"></a>Analizzare l'utilizzo della memoria
Usare lo strumento di diagnostica **Utilizzo memoria** integrato nel debugger per rilevare perdite di memoria e usi inefficienti della memoria. Lo strumento Utilizzo memoria consente di eseguire uno o più *snapshot* dell'heap di memoria gestito e nativo. È possibile raccogliere snapshot di app .NET, ASP.NET, native o in modalità mista (.NET e native).

- È possibile analizzare un singolo snapshot per ottenere informazioni sull'impatto relativo dei tipi di oggetto sull'uso della memoria e per trovare nell'app il codice che usa la memoria in modo non efficiente.

- È anche possibile confrontare (diff) due snapshot di un'app per individuare le aree del codice che provocano l'incremento dell'uso della memoria nel tempo.

Per istruzioni dettagliate, vedere l'esercitazione sull'[analisi dell'uso della memoria](../profiling/memory-usage.md).  Attualmente, per misurare l'utilizzo della memoria per un'app .NET Core, è necessario utilizzare lo strumento con il debugger collegato. Per altre app gestite e native, è possibile usare lo strumento con o senza il debugger collegato.

È possibile usare gli strumenti di profilatura senza il debugger con Windows 7 e versioni successive. Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**.

## <a name="blogs-and-videos"></a>Blog e video

[Analizzare CPU e memoria in fase di debug](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog su Visual C++: Profilatura della memoria in Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Vedere anche

- [Profilatura in Visual Studio](../profiling/index.yml)
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)
- [Analizzare l'utilizzo della memoria senza il debugger](../profiling/memory-usage-without-debugging2.md)
