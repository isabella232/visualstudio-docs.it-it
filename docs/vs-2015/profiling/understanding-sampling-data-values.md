---
title: Informazioni sui valori dei dati di campionamento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91a4a50ecc745c0b56167d6a5dbb1932af7ed2bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54752652"
---
# <a name="understanding-sampling-data-values"></a>Informazioni sui valori dei dati di campionamento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il metodo di profilatura di *campionamento* degli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interrompe il processore del computer a intervalli prestabiliti e raccoglie lo stack di chiamate della funzione. Lo *stack di chiamate* è una struttura dinamica che archivia informazioni sulle funzioni in esecuzione nel processore.  
  
 **Requisiti**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  L'analisi del profiler determina se il processore esegue codice nel processo di destinazione. Se il processore non esegue codice nel processo di destinazione, il campione viene ignorato.  
  
  Se il processore esegue il codice di destinazione, il profiler incrementa i conteggi dei campioni per ogni funzione nello stack di chiamate. Nel momento in cui viene acquisito il campione, una sola funzione nello stack di chiamate esegue codice. Le altre funzioni nello stack sono elementi padre nella gerarchia delle chiamate di funzioni che sono in attesa dei valori restituiti dalle relative funzioni figlio.  
  
  Per l'evento di campionamento, il profiler incrementa il conteggio dei campioni *esclusivi* della funzione che sta attualmente eseguendo le proprie istruzioni. Dato che un campione esclusivo fa anche parte del totale (*inclusivo*) dei campioni della funzione, viene incrementato anche il conteggio dei campioni inclusivi della funzione attiva.  
  
  Il profiler incrementa il numero di campioni inclusivi di tutte le altre funzioni nello stack di chiamate.  
  
## <a name="inclusive-samples"></a>Campioni inclusivi  
 Numero totale di campioni raccolti durante l'esecuzione della funzione di destinazione.  
  
 Sono inclusi campioni raccolti durante l'esecuzione diretta del codice della funzione e campioni raccolti durante l'esecuzione delle funzioni figlio chiamate dalla funzione di destinazione.  
  
## <a name="exclusive-samples"></a>Campioni esclusivi  
 Numero di campioni raccolti durante l'esecuzione diretta delle istruzioni della funzione di destinazione.  
  
 Nei campioni esclusivi non sono compresi i campioni raccolti durante l'esecuzione delle funzioni chiamate dalla funzione di destinazione.  
  
## <a name="inclusive-percent"></a>% inclusivi  
 Percentuale del numero totale di campioni inclusivi nell'esecuzione della profilatura che sono campioni inclusivi della funzione o dell'intervallo di dati.  
  
## <a name="exclusive-percent"></a>% esclusivi  
 Percentuale del numero totale di campioni esclusivi nell'esecuzione della profilatura che sono campioni esclusivi della funzione o dell'intervallo di dati.  
  
## <a name="see-also"></a>Vedere anche  
 [How to: Choose Collection Methods](../profiling/how-to-choose-collection-methods.md)  (Procedura: Scegliere un metodo di raccolta)  
 [Analisi dei dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md)
