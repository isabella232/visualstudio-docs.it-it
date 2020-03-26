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
ms.openlocfilehash: 43126f4bba8afc50fc5c1e4cf6a3b9a67c6f340c
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233055"
---
# <a name="analyze-memory-usage"></a>Analizzare l'utilizzo della memoria

Per individuare perdite di memoria e un utilizzo inefficiente della memoria, è possibile utilizzare strumenti quali lo strumento di diagnostica Utilizzo memoria integrato nel debugger o strumenti nel Profiler prestazioni, ad esempio lo strumento di allocazione degli oggetti .NET e lo strumento di utilizzo della memoria post-mortem.

Lo strumento Utilizzo memoria consente di eseguire uno o più *snapshot* dell'heap di memoria gestito e nativo. È possibile raccogliere snapshot di app .NET, ASP.NET, native o in modalità mista (.NET e native). Lo strumento **Utilizzo memoria** può essere eseguito in un progetto di Visual Studio aperto, in un'app di Microsoft Store installata o collegato a un'app o un processo in esecuzione. È possibile eseguire lo strumento in computer locali o remoti oppure in un simulatore o in un emulatore. È possibile eseguire lo strumento **Utilizzo memoria** con o senza debug. Per ulteriori informazioni, vedere Eseguire strumenti di [profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Nel debugger è possibile attivare e disattivare la profilatura della memoria e visualizzare un'interruzione per oggetto dell'utilizzo della memoria. È possibile visualizzare i risultati dell'utilizzo della memoria quando l'esecuzione viene sospesa, ad esempio in corrispondenza di un punto di interruzione.

Lo strumento **.NET Object Allocation** consente di identificare i modelli di allocazione e le anomalie nel codice .NET. Questo strumento viene eseguito solo come strumento post-mortem.

Per istruzioni dettagliate che descrivono come utilizzare gli strumenti di analisi della memoria, vedere [l'esercitazione Analizzare l'utilizzo](../profiling/memory-usage.md) della memoria e [lo strumento Allocazione oggetti .NET](../profiling/dotnet-alloc-tool.md).

È possibile usare gli strumenti di profilatura senza il debugger con Windows 7 e versioni successive. Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**.

## <a name="blogs-and-videos"></a>Blog e video

[Analizzare CPU e memoria durante il debug](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog su Visual C++: Profilatura della memoria in Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Vedere anche

- [Profilatura in Visual Studio](../profiling/index.yml)
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)
- [Analizzare l'utilizzo della memoria senza il debugger](../profiling/memory-usage-without-debugging2.md)
