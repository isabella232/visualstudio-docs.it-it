---
title: Informazioni sui valori dei dati su conflitti di risorse | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10c06805db7ef817421f7c9f85e316af8d4b5b35
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526933"
---
# <a name="understanding-resource-contention-data-values"></a>Informazioni sui valori dei dati su conflitti di risorse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [valori dei dati sui conflitti di risorse Understanding](https://docs.microsoft.com/visualstudio/profiling/understanding-resource-contention-data-values).  
  
La profilatura dei conflitti di risorse raccoglie informazioni dettagliate sullo stack di chiamate ogni volta che thread concorrenti in un'applicazione sono obbligati ad attendere l'accesso a una risorsa condivisa.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 I report sui conflitti di risorse visualizzano il numero totale di conflitti e il tempo totale trascorso in attesa di una risorsa per i moduli, le funzioni, le righe del codice sorgente e le istruzioni in cui si è verificata l'attesa.  
  
-   I valori inclusivi mostrano il numero totale di conflitti che hanno costretto una funzione ad attendere a causa di conflitti di risorse e il tempo totale di attesa per la funzione.  I conflitti causati dalle funzioni figlio chiamate dalla funzione sono inclusi nei valori inclusivi.  
  
-   I valori esclusivi mostrano solo il numero di conflitti che hanno costretto una funzione ad attendere e che sono stati causati dal codice nel corpo della funzione. I conflitti causati da funzioni figlio non sono inclusi. Il tempo esclusivo per la funzione include inoltre solo i tempi di attesa causati dalle istruzioni nel corpo della funzione.  
  
 Le visualizzazioni dei report sui conflitti di risorse includono anche grafici della sequenza temporale che mostrano i singoli eventi di conflitto nel tempo e gli stack di chiamate che hanno creato l'evento specifico. Per altre informazioni, vedere uno degli argomenti seguenti:  
  
-   [Visualizzazione Dettagli thread](../profiling/thread-details-view-contention-data.md)  
  
-   [Visualizzazione Dettagli risorsa](../profiling/resource-details-view-contention-data.md)  
  
 Per altre informazioni sulla seconda modalità di profilatura della concorrenza, vedere [Visualizzatore di concorrenza](../profiling/concurrency-visualizer.md).



