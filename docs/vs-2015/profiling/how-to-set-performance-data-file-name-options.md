---
title: 'Procedura: Impostare le opzioni relative ai nomi file dei dati sulle prestazioni | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19a29c143ecc2ce413e6f6480b2c49e52277af3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526396"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Procedura: Impostare le opzioni relative ai nomi file dei dati sulle prestazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: impostare opzioni di prestazioni dei dati File nome](https://docs.microsoft.com/visualstudio/profiling/how-to-set-performance-data-file-name-options).  
  
Per impostazione predefinita, un file dei dati di profilatura (con estensione vsp) viene salvato con la sintassi seguente:  
  
 *Percorso\File-VSP\AAMMGG(N)* **.vsp**  
  
 È possibile modificare i parametri di denominazione nella pagina Generale della finestra di dialogo delle proprietà per la sessione di prestazioni.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
|||  
|-|-|  
|*Percorso*|Directory che contiene il rapporto. Il percorso predefinito è la cartella della soluzione o il percorso predefinito per i progetti e le soluzioni dell'utente.|  
|*File-VSP*|Nome del file di dati di profilatura. Il nome predefinito è il nome della soluzione o del file eseguibile che viene profilato.|  
|*AAMMGG*|Indicatore di data che indica l'anno, il mese e il giorno in cui sono stati raccolti i dati di profilatura.|  
|*(N)*|Se esiste più di un file di dati di profilatura, al nome del file tra parentesi viene aggiunto un numero incrementato.|  
  
### <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Per modificare la sintassi di denominazione dei file di dati di profilatura di una sessione di prestazioni  
  
1.  In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi fare clic su **Proprietà**.  
  
2.  Fare clic su **Generale**.  
  
3.  In **Rapporto** modificare le impostazioni seguenti:  
  
    |||  
    |-|-|  
    |**Percorso rapporto**|Specificare una directory per archiviare i file di dati di profilatura.|  
    |**Nome rapporto**|Specificare un nome di base per i file.|  
    |**Aggiungere automaticamente nuovi rapporti alla sessione**|Selezionare la casella di controllo per aggiungere automaticamente il file di dati alla sessione di prestazioni.|  
    |**Accodare un numero incrementale ai rapporti generati**|Selezionare la casella di controllo per aggiungere un numero incrementale al nome del file quando esiste più di un file con lo stesso nome. Deselezionare la casella di controllo per sovrascrivere un file esistente.|  
    |**Utilizzare un timestamp per il numero**|Selezionare la casella di controllo per aggiungere un datestamp al nome del file.|



