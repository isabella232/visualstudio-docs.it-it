---
title: Analizzare l'utilizzo della memoria
description: Informazioni sugli strumenti che è possibile usare per individuare le perdite di memoria e l'utilizzo inefficiente della memoria, strumenti come lo strumento utilizzo memoria e lo strumento di allocazione oggetti .NET.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2af4bc47d711275716eea528a4d9bd816408322f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901132"
---
# <a name="analyze-memory-usage"></a>Analizzare l'utilizzo della memoria

Per individuare le perdite di memoria e l'utilizzo inefficiente della memoria, è possibile utilizzare strumenti come lo strumento di diagnostica utilizzo memoria integrato nel debugger o gli strumenti nel profiler delle prestazioni, ad esempio lo strumento di allocazione oggetti .NET e lo strumento di utilizzo della memoria post-mortem.

Lo strumento Utilizzo memoria consente di eseguire uno o più *snapshot* dell'heap di memoria gestito e nativo. È possibile raccogliere snapshot delle app .NET, ASP.NET, C++ o miste (.NET e native). Lo strumento **utilizzo memoria** può essere eseguito in un progetto di Visual Studio aperto, in un'app Microsoft Store installata oppure collegato a un'app o a un processo in esecuzione. È possibile eseguire lo strumento **utilizzo memoria** con o senza debug. Per altre informazioni, vedere [eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Nel debugger è possibile attivare e disattivare la profilatura della memoria e vedere la suddivisione in base all'oggetto dell'utilizzo della memoria. È possibile visualizzare i risultati dell'utilizzo della memoria quando l'esecuzione viene sospesa, ad esempio in corrispondenza di un punto di interruzione.

Gli sviluppatori .NET possono scegliere tra lo strumento di allocazione oggetti .NET o lo strumento [utilizzo memoria](../profiling/memory-usage.md) .

- Lo [strumento di allocazione oggetti .NET](../profiling/dotnet-alloc-tool.md) consente di identificare i modelli di allocazione e le anomalie nel codice .NET e consente di identificare i problemi più comuni con Garbage Collection. Questo strumento viene eseguito solo come strumento post-mortem. È possibile eseguire questo strumento in computer locali o remoti.
- Lo [strumento utilizzo memoria](../profiling/memory-usage-without-debugging2.md) è utile per identificare le perdite di memoria, che in genere non sono comuni nelle app .NET. Se è necessario utilizzare le funzionalità del debugger durante il controllo della memoria, ad esempio l'esecuzione di un'istruzione alla volta nel codice, è consigliabile usare lo strumento [utilizzo memoria integrato del debugger](../profiling/memory-usage.md) .

Gli sviluppatori C++ possono utilizzare lo strumento di utilizzo della memoria integrato nel debugger o non del debugger.

- [Analizzare l'utilizzo della memoria con il debugger](../profiling/memory-usage.md)
- [Analizzare l'utilizzo della memoria senza il debugger](../profiling/memory-usage-without-debugging2.md)

È possibile usare gli strumenti di profilatura senza il debugger con Windows 7 e versioni successive. Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**.

## <a name="blogs-and-videos"></a>Blog e video

[Analizza CPU e memoria durante il debug](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog su Visual C++: Profilatura della memoria in Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Vedi anche

- [Profilatura in Visual Studio](../profiling/index.yml)
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)
