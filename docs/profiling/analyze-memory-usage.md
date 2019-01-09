---
title: Analizzare l'utilizzo della memoria
ms.custom: seodec18
ms.date: 01/02/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1dcd3467f474d5c2b3e24ed1d1e490a73e7498bb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867186"
---
# <a name="analyze-memory-usage"></a>Analizzare l'utilizzo della memoria
Usare lo strumento di diagnostica **Utilizzo memoria** integrato nel debugger per rilevare perdite di memoria e usi inefficienti della memoria. Lo strumento Utilizzo memoria consente di eseguire uno o più *snapshot* dell'heap di memoria gestito e nativo. È possibile raccogliere snapshot di app .NET, ASP.NET, native o in modalità mista (.NET e native).  
  
-   È possibile analizzare un singolo snapshot per ottenere informazioni sull'impatto relativo dei tipi di oggetto sull'uso della memoria e per trovare nell'app il codice che usa la memoria in modo non efficiente.  
  
-   È anche possibile confrontare (diff) due snapshot di un'app per trovare le aree del codice che provocano l'incremento dell'uso della memoria nel tempo.  

Per istruzioni dettagliate, vedere l'esercitazione sull'[analisi dell'uso della memoria](../profiling/memory-usage.md).  Attualmente, per misurare l'utilizzo della memoria per un'app .NET Core, è necessario utilizzare lo strumento con il debugger collegato. Per altre app gestite e native, è possibile usare lo strumento con o senza il debugger collegato.

È possibile usare gli strumenti di profilatura senza il debugger con Windows 7 e versioni successive. Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**.
  
## <a name="blogs-and-videos"></a>Blog e video  

| | |
|---------|---------|
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) sull'uso degli strumenti di diagnostica che illustra come analizzare l'uso della memoria e della CPU in Visual Studio 2017. |

 [Analizzare CPU e memoria in fase di debug](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/)  
  
 [Visual C++ Blog: Memory Profiling in Visual C++ 2015](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/) (Blog di Visual C++: Profilatura della memoria in Visual C++ 2015)  

## <a name="see-also"></a>Vedere anche
 [Profilatura in Visual Studio](../profiling/index.md)  
 [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)