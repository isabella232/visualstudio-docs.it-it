---
title: DA0014- Frequenze estremamente elevate di paging della memoria attiva su disco | Microsoft Docs
description: I dati relativi alle prestazioni di sistema raccolti nell'esecuzione della profilatura indicano che si è verificata una frequenza estremamente elevata di paging di memoria attiva da e su disco durante la profilatura.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAMemoryBound
- vs.performance.DA0014
- vs.performance.14
- vs.performance.rules.DA0014
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ea42e94eab6c5da65e5e1d59e93f71680dea1500
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131755"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014: Frequenze molto elevate di paging di memoria attiva su disco

|Elemento|valore|
|-|-|
|ID regola|DA0014|
|Category|Memoria e paging|
|Metodo di profilatura|Tutti|
|Message|È stata rilevata una frequenza molto elevata di paging di memoria attiva su disco. L'applicazione potrebbe essere associata alla memoria.|
|Tipo regola|Avviso|

 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 25 campioni per attivare questa regola.

## <a name="cause"></a>Causa
 I dati relativi alle prestazioni di sistema raccolti nell'esecuzione della profilatura indicano che si è verificata una frequenza estremamente elevata di paging di memoria attiva da e su disco durante la profilatura. In genere le frequenze di paging a questo livello hanno un impatto sulle prestazioni e sulla capacità di risposta dell'applicazione. È consigliabile ridurre le allocazioni di memoria rivedendo gli algoritmi. Potrebbe inoltre essere necessario esaminare i requisiti di memoria dell'applicazione. Eseguire di nuovo la profilatura su un computer con una maggiore quantità di memoria.

## <a name="rule-description"></a>Descrizione della regola
 Un'attività di paging su disco eccessiva può essere causata da memoria fisica insufficiente. Se le operazioni di paging usano in modo dominante il disco fisico su cui risiede il file di paging, possono rallentare le altre operazioni del disco orientate all'applicazione sullo stesso disco.

 Le pagine vengono spesso lette dal disco o scritte nel disco mediante operazioni di paging in blocco. Ad esempio, il numero di output di pagine al secondo è spesso maggiore del numero di scritture di pagine al secondo. Ciò avviene perché il numero di pagine generate al secondo include anche le pagine di dati modificate dalla cache dei file di sistema. Tuttavia, non è sempre facile determinare quale processo è direttamente responsabile del paging o perché.

> [!NOTE]
> Questa regola viene attivata quando i livelli di paging della memoria attiva raggiungono una frequenza molto elevata. Quando il livello di paging è significativo, ma non estremo, viene invece attivata la regola informativa [DA0017: Frequenze elevate di paging di memoria attiva su disco](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione](../profiling/marks-view.md) Contrassegni. Individuare la colonna **Memoria\Pagine/sec**. Determinare se sono presenti fasi specifiche di esecuzione del programma in cui l'attività I/O di paging è più elevata rispetto ad altre fasi.

 Se si raccolgono dati del profilo per un'applicazione ASP.NET in un scenario del test di carico, provare a eseguire nuovamente il test di carico su un computer configurato con memoria fisica (o RAM) aggiuntiva.

 È consigliabile ridurre le allocazioni di memoria rivedendo gli algoritmi ed evitando API che usano molta memoria, ad esempio String.Concat e String.Substring.
