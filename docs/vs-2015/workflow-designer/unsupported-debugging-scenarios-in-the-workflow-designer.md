---
title: Non è supportato nella finestra di progettazione del flusso di lavoro scenari di debug | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 651777d3488460394b79488d3d0fc67ff286bbfb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47541154"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Scenari di debug non supportati in Progettazione flussi di lavoro
In Progettazione flussi di lavoro in [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] sono state aggiunte numerose e nuove funzionalità, ma sono ancora presenti alcuni scenari di debug non supportati. In questo documento vengono indicati gli scenari di debug non supportati in Progettazione flussi di lavoro.  
  
-   Impossibile continuare l'esecuzione dopo che il codice è stato modificato.  
  
-   Impossibile continuare l'esecuzione da un punto arbitrario nel flusso di lavoro (Imposta istruzione successiva).  
  
-   Impossibile continuare l'esecuzione fino a quando non si raggiunge il cursore (Esegui fino al cursore).  
  
-   Impossibile usare Progettazione flussi di lavoro per eseguire debug di flussi di lavoro creati in codice senza l'uso della finestra di progettazione.  
  
-   Impossibile eseguire il debug di flussi di lavoro creati in versioni precedenti di [!INCLUDE[wf](../includes/wf-md.md)] nella finestra di progettazione di [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].  
  
-   Impossibile definire i punti di interruzione nei collegamenti tra attività o nodi <xref:System.Activities.Statements.Flowchart>.  
  
-   Gli Appunti non sono disponibili durante l'esecuzione del debug.  
  
-   I punti di interruzione non vengono mantenuti quando le attività vengono copiate o incollate.  
  
-   Impossibile impostare i punti di interruzione del flusso di lavoro nella finestra dello stack di chiamate.  
  
-   Durante la creazione di punti di interruzione nella finestra di progettazione, il **Line** e **carattere** impostazioni nel **nuovo punto di interruzione** finestra di dialogo non vengono usati.  
  
-   La finestra Punto di interruzione o il menu di scelta rapida non supporta le colonne o le opzioni seguenti per il debug del flusso di lavoro:  
  
    -   Condizione  
  
    -   Passaggi  
  
    -   Quando raggiunto  
  
    -   Funzione  
  
    -   Dati  
  
    -   Processo  
  
    -   Vai a disassembly