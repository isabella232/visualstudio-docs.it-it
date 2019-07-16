---
title: Esempi di diagnostica della grafica | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14b4ac689109e29baa4ee06c668b208d0d5227b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159709"
---
# <a name="graphics-diagnostics-examples"></a>Esempi di diagnostica grafica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questi esempi mostrano come eseguire il debug dei problemi di rendering nelle app basate su DirectX usando la diagnostica della grafica di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="capturing-graphics-information"></a>Acquisizione di informazioni grafiche  
 Prima di poter usare la diagnostica della grafica per individuare problemi di rendering dell'app, è necessario acquisire informazioni grafiche dall'applicazione durante l'esecuzione. È possibile acquisire informazioni grafiche da un'app eseguita in un computer locale o da un'app eseguita in un computer o dispositivo remoto. Queste procedure dettagliate dimostrano come è possibile acquisire informazioni grafiche da un'app manualmente o a livello di codice:  
  
- [Procedura dettagliata: Acquisizione di informazioni grafiche](../debugger/walkthrough-capturing-graphics-information.md)  
  
- [Procedura dettagliata: Acquisizione di informazioni grafiche a livello di codice](../debugger/walkthrough-capturing-graphics-information-programmatically.md)  
  
## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>Usare la diagnostica della grafica con un dispositivo basato su ARM  
 È possibile usare la diagnostica della grafica per eseguire il debug della propria app Direct3D in un dispositivo basato su ARM tramite debug remoto. Per altre informazioni, vedere [Procedura: Usare la diagnostica della grafica con un dispositivo ARM](../debugger/how-to-use-graphics-diagnostics-with-an-arm-device.md).  
  
## <a name="playing-back-graphics-information"></a>Riproduzione di informazioni grafiche  
 Dopo aver acquisito le informazioni grafiche da un'app in esecuzione, è possibile riprodurre gli eventi acquisiti per diagnosticare problemi di rendering. Per riprodurre, è possibile usare il computer di sviluppo oppure un computer remoto o un dispositivo connesso. Per altre informazioni, vedere [Procedura: Modificare il computer di riproduzione della diagnostica della grafica](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="debugging-missing-objects"></a>Debug degli oggetti mancanti  
 Un oggetto mancante (o più oggetti mancanti) è uno dei problemi di rendering più comuni rilevati dagli sviluppatori di grafica. Questo tipo di problema può essere difficile da individuare perché diversi tipi di errori potrebbero causare la scomparsa apparente di un oggetto. Le cause comuni per gli oggetti mancanti sono uno stato del dispositivo non configurato correttamente, problemi nella trasformazione geometrica dell'oggetto o una configurazione errata della pipeline grafica.  
  
 Questi scenari illustrano come usare la diagnostica della grafica per determinare perché manca un oggetto e per trovare il codice responsabile.  
  
- [Procedura dettagliata: Oggetti mancanti a causa dello stato del dispositivo](../debugger/walkthrough-missing-objects-due-to-device-state.md)  
  
- [Procedura dettagliata: Oggetti mancanti a causa dello sfondo Vertex](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)  
  
- [Procedura dettagliata: Oggetti mancanti a causa di una pipeline configurata in modo non corretto](../debugger/walkthrough-missing-objects-due-to-misconfigured-pipeline.md)  
  
## <a name="debugging-rendering-errors"></a>Debug degli errori di rendering  
 Un oggetto (o più oggetti) che non ha l'aspetto corretto è un altro problema comune agli sviluppatori di grafica. Questo tipo di problema può essere difficile da individuare perché le cause di un aspetto non corretto possono variare da errori molto banali, ad esempio l'associazione di una trama errata, a errori meno ovvi, come un bug nel codice dello shader o un'interazione inattesa tra shader. Alcuni problemi possono essere causati da una combinazione di errori.  
  
 Di seguito è riportato uno scenario che dimostra come usare la diagnostica grafica per individuare un problema di rendering non troppo complesso causato da un bug secondario dello shader:  
  
- [Procedura dettagliata: Debug degli errori di rendering dovuti allo sfondo](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)  
  
## <a name="debugging-compute-shaders"></a>Debug di compute shader  
 È possibile usare la diagnostica della grafica per il debug dei kernel del compute shader DirectCompute che generano risultati errati. Con DirectCompute, è possibile usare la potenza di calcolo della GPU per eseguire calcoli su un numero elevato di elementi dati in parallelo. Per alcuni tipi di problemi, l'uso della GPU può fornire prestazioni molto superiori a quelle offerte da un codice, per quanto ben ottimizzato, per CPU. I debugger tradizionali non possono tuttavia rilevare codice eseguito su GPU. Il debug di questo tipo di codice spesso richiede strumenti specializzati specifici del fornitore, che potrebbero non integrarsi bene con Visual Studio. Per rendere il debug di compute shader più coerente su un intervallo di GPU, la diagnostica della grafica acquisisce eventi di invio di DirectCompute, in aggiunta agli eventi di rendering Direct3D, così che sia possibile usare strumenti comuni per il debug dei problemi nel codice del compute shader.  
  
 Per uno scenario che dimostra come eseguire il debug di un problema di simulazione causato da un bug nel compute shader, vedere [procedura dettagliata: Usare diagnostica della grafica per eseguire il Debug di un Compute Shader](../debugger/walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md).
