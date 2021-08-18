---
title: Analizzare l'utilizzo della memoria
description: Informazioni sugli strumenti che è possibile usare per individuare perdite di memoria e utilizzo inefficiente della memoria, strumenti come lo strumento Utilizzo memoria e lo strumento Allocazione oggetti .NET.
ms.custom: SEO-VS-2020
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ec323cea6d2a5e5ed41b226a3994b5084a70968c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131989"
---
# <a name="analyze-memory-usage"></a>Analizzare l'utilizzo della memoria

Per individuare perdite di memoria e utilizzo inefficiente della memoria, è possibile usare strumenti come lo strumento di diagnostica Utilizzo memoria integrato nel debugger o gli strumenti nel Profiler prestazioni, ad esempio lo strumento di allocazione di oggetti .NET e lo strumento Utilizzo memoria post-mortem.

Lo strumento Utilizzo memoria consente di eseguire uno o più *snapshot* dell'heap di memoria gestito e nativo. È possibile raccogliere snapshot di app .NET, ASP.NET, C++ o in modalità mista (.NET e native). Lo **strumento Utilizzo memoria** può essere eseguito in un progetto Visual Studio aperto, in un'app Microsoft Store installata o collegata a un'app o a un processo in esecuzione. È possibile eseguire lo strumento **Utilizzo memoria** con o senza debug. Per altre informazioni, vedere [Eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Nel debugger è possibile attivare e disattivare la profilatura della memoria e visualizzare una suddivisione per oggetto dell'utilizzo della memoria. È possibile visualizzare i risultati dell'utilizzo della memoria quando l'esecuzione viene sospesa, ad esempio in corrispondenza di un punto di interruzione.

Gli sviluppatori .NET possono scegliere tra lo strumento di allocazione di oggetti .NET o lo [strumento Utilizzo memoria.](../profiling/memory-usage.md)

- Lo [strumento di allocazione](../profiling/dotnet-alloc-tool.md) di oggetti .NET consente di identificare i modelli di allocazione e le anomalie nel codice .NET e consente di identificare i problemi comuni relativi a Garbage Collection. Questo strumento viene eseguito solo come strumento post-mortem. È possibile eseguire questo strumento in computer locali o remoti.
- Lo [strumento Utilizzo memoria](../profiling/memory-usage-without-debugging2.md) è utile per identificare le perdite di memoria, che in genere non sono comuni nelle app .NET. Se è necessario usare le funzionalità del debugger durante il controllo della memoria, ad esempio l'esecuzione di codice un'istruzione alla volta, è consigliabile usare lo strumento di utilizzo della memoria integrato [nel debugger.](../profiling/memory-usage.md)

Gli sviluppatori C++ possono usare lo strumento Utilizzo memoria integrato nel debugger o non del debugger.

- [Analizzare l'utilizzo della memoria con il debugger](../profiling/memory-usage.md)
- [Analizzare l'utilizzo della memoria senza il debugger](../profiling/memory-usage-without-debugging2.md)

È possibile usare gli strumenti di profilatura senza il debugger con Windows 7 e versioni successive. Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**.

## <a name="blogs-and-videos"></a>Blog e video

[Analizzare CPU e memoria durante il debug](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog su Visual C++: Profilatura della memoria in Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Vedi anche

- [Profilatura in Visual Studio](../profiling/index.yml)
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)
