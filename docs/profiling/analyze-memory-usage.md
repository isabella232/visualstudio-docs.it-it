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
ms.openlocfilehash: 5ddb082bf2451759be239d5c16404e82bcd84733
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578154"
---
# <a name="analyze-memory-usage"></a>Analizzare l'utilizzo della memoria

per individuare le perdite di memoria e l'utilizzo inefficiente della memoria, è possibile utilizzare strumenti come lo strumento di diagnostica utilizzo memoria integrato nel debugger o gli strumenti nel profiler delle prestazioni, ad esempio lo strumento di allocazione oggetti .NET e lo strumento di utilizzo della memoria post-mortem. Lo strumento Utilizzo memoria consente di eseguire uno o più *snapshot* dell'heap di memoria gestito e nativo. È possibile raccogliere snapshot di app .NET, ASP.NET, native o in modalità mista (.NET e native). 

Lo strumento **utilizzo memoria** può essere eseguito in un progetto di Visual Studio aperto, in un'app Microsoft Store installata oppure collegato a un'app o a un processo in esecuzione. È possibile eseguire lo strumento in computer locali o remoti oppure in un simulatore o in un emulatore. Per altre informazioni, vedere [Eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

È possibile eseguire lo strumento **utilizzo memoria** con o senza debug. Nel debugger è possibile attivare e disattivare la profilatura della memoria e vedere la suddivisione in base all'oggetto dell'utilizzo della memoria. È possibile visualizzare i risultati dell'utilizzo della memoria quando l'esecuzione viene sospesa, ad esempio in corrispondenza di un punto di interruzione.

Lo strumento di **allocazione oggetti .NET** viene eseguito solo come strumento post-mortem.

Per istruzioni dettagliate che descrivono come usare gli strumenti di analisi della memoria, vedere l'esercitazione [analizzare l'utilizzo della memoria](../profiling/memory-usage.md) e lo strumento di [allocazione oggetti .NET](../profiling/dotnet-alloc-tool.md).

È possibile usare gli strumenti di profilatura senza il debugger con Windows 7 e versioni successive. Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**.

## <a name="blogs-and-videos"></a>Blog e video

[Analizzare CPU e memoria in fase di debug](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog su Visual C++: Profilatura della memoria in Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Vedere anche

- [Profilatura in Visual Studio](../profiling/index.yml)
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)
- [Analizzare l'utilizzo della memoria senza il debugger](../profiling/memory-usage-without-debugging2.md)
