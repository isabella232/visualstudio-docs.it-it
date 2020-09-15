---
title: Analizzare l'utilizzo della memoria
ms.custom: seodec18
ms.date: 03/30/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f77fa9087673ff8e9a429caa27318a60f21d4a60
ms.sourcegitcommit: 14637be49401f56341c93043eab560a4ff6b57f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075444"
---
# <a name="analyze-memory-usage"></a>Analizzare l'utilizzo della memoria

Per individuare le perdite di memoria e l'utilizzo inefficiente della memoria, è possibile utilizzare strumenti come lo strumento di diagnostica utilizzo memoria integrato nel debugger o gli strumenti nel profiler delle prestazioni, ad esempio lo strumento di allocazione oggetti .NET e lo strumento di utilizzo della memoria post-mortem.

Lo strumento Utilizzo memoria consente di eseguire uno o più *snapshot* dell'heap di memoria gestito e nativo. È possibile raccogliere snapshot di app .NET, ASP.NET, native o in modalità mista (.NET e native). Lo strumento **utilizzo memoria** può essere eseguito in un progetto di Visual Studio aperto, in un'app Microsoft Store installata oppure collegato a un'app o a un processo in esecuzione. È possibile eseguire lo strumento **utilizzo memoria** con o senza debug. Per altre informazioni, vedere [eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Nel debugger è possibile attivare e disattivare la profilatura della memoria e vedere la suddivisione in base all'oggetto dell'utilizzo della memoria. È possibile visualizzare i risultati dell'utilizzo della memoria quando l'esecuzione viene sospesa, ad esempio in corrispondenza di un punto di interruzione.

Lo strumento di **allocazione oggetti .NET** consente di identificare i modelli di allocazione e le anomalie nel codice .NET. Questo strumento viene eseguito solo come strumento post-mortem. È possibile eseguire questo strumento in computer locali o remoti.

Per istruzioni dettagliate che descrivono come usare gli strumenti di analisi della memoria, vedere l'esercitazione [analizzare l'utilizzo della memoria](../profiling/memory-usage.md) e lo strumento di [allocazione oggetti .NET](../profiling/dotnet-alloc-tool.md).

È possibile usare gli strumenti di profilatura senza il debugger con Windows 7 e versioni successive. Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**.

## <a name="blogs-and-videos"></a>Blog e video

[Analizza CPU e memoria durante il debug](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog su Visual C++: Profilatura della memoria in Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Vedere anche

- [Analizzare l'utilizzo della memoria senza il debugger](../profiling/memory-usage-without-debugging2.md)
- [Profilatura in Visual Studio](../profiling/index.yml)
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)
