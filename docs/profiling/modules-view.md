---
title: Visualizzazione Moduli | Microsoft Docs
description: Informazioni su come la visualizzazione Moduli elenca i moduli dei dati di profilatura. Ogni modulo è il nodo radice di una struttura gerarchica.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.modules
helpviewer_keywords:
- Modules view
- profiling tools reports, Modules view
- profiling tools, Modules view
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e03c12722f6a35dae70b5cbe789524adf78b18a7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107336"
---
# <a name="modules-view"></a>Visualizzazione Moduli
La visualizzazione Moduli elenca i moduli dei dati di profilatura. Ogni modulo è il nodo radice di una struttura gerarchica. Le funzioni profilate del modulo sono elencate sotto il nodo del modulo. Se i dati di profilatura vengono raccolti tramite il metodo di campionamento, le informazioni sulle righe sono elencate sotto il nodo della funzione e i dati del puntatore alle istruzioni sotto il nodo delle righe.

 Espandere o comprimere il nome del modulo per visualizzare o chiudere la visualizzazione dei dati relativi alle prestazioni del modulo.

 Per aggiungere o rimuovere colonne, fare clic con il pulsante destro del mouse nella finestra del report e quindi scegliere **Aggiungi/Rimuovi colonne**. Per ordinare i dati è possibile fare clic sul nome di una colonna. Per altre informazioni, vedere [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md).

 Le colonne disponibili nella visualizzazione Moduli dipendono dal metodo di profilatura (campionamento o strumentazione) usato per raccogliere i dati e dal fatto che i dati della memoria .NET siano stati raccolti o meno durante l'esecuzione della profilatura.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Moduli](../profiling/modules-view-sampling-data.md)
- [Visualizzazione Moduli](../profiling/modules-view-instrumentation-data.md)
- [Visualizzazione Moduli - Strumentazione](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Visualizzazione Moduli - Campionamento](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Visualizzazione Moduli](../profiling/modules-view-contention-data.md)
