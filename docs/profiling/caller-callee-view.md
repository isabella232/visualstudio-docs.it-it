---
description: La visualizzazione Chiamante/chiamato consente di visualizzare informazioni di profilatura per una funzione selezionata e le relative funzioni padre e figlio.
title: Visualizzazione Chiamante/chiamato | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 375c0f366fb32fcbe8187c2c4b5d1d3d632f7260
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223706"
---
# <a name="callercallee-view"></a>visualizzazione Chiamante/Chiamato
La visualizzazione Chiamante/chiamato consente di visualizzare informazioni di profilatura per una funzione selezionata e le relative funzioni padre e figlio. La visualizzazione Chiamante/chiamato contiene tre griglie:

 Nella griglia centrale **Funzione corrente** visualizza le informazioni di profilatura per la funzione selezionata. I valori includono tutte le chiamate alla funzione che sono state raccolte nell'esecuzione della profilatura.

 La griglia superiore contiene **Funzioni che hanno chiamato la funzione corrente**, che visualizza il numero di valori della funzione selezionata (corrente) generati da chiamate da parte della funzione chiamante (padre).

 Nella griglia inferiore **Funzioni che sono state chiamate dalla funzione corrente** visualizza informazioni di profilatura per le funzioni chiamate (figlio) della funzione selezionata quando la funzione figlio è stata chiamata dalla funzione corrente.

 Le colonne disponibili nella visualizzazione Chiamante/chiamato dipendono dal metodo di profilatura (campionamento o strumentazione) usato per raccogliere i dati e dal fatto che i dati della memoria .NET siano stati raccolti o meno durante l'esecuzione della profilatura.

 È possibile selezionare un'altra funzione come funzione corrente nella parte centrale della visualizzazione report facendo doppio clic su una delle funzioni elencate nelle altre due parti della visualizzazione. La visualizzazione report viene automaticamente aggiornata in base alle modifiche.

 Per ordinare i dati è possibile fare clic sui nomi delle colonne. È possibile aggiungere altre colonne alla visualizzazione Chiamante/chiamato. Per altre informazioni, vedere [procedura: personalizzare le colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md).

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Chiamante/chiamato: dati di campionamento](../profiling/caller-callee-view-sampling-data.md)
- [Visualizzazione chiamante/chiamato: dati di strumentazione](../profiling/caller-callee-view-instrumentation-data.md)
- [Visualizzazione chiamante/chiamato: dati di strumentazione di memoria .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Visualizzazione chiamante/chiamato: dati di campionamento di memoria .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Visualizzazione Chiamante/chiamato: dati sui conflitti](../profiling/caller-callee-view-contention-data.md)
