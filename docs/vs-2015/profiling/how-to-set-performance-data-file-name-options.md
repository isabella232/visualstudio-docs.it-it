---
title: 'Procedura: Impostare le opzioni relative ai nomi file dei dati sulle prestazioni | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71ac053a24b3f765a58fc050ceec84115e1a4e3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548395"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Procedura: Impostare le opzioni relative ai nomi file dei dati sulle prestazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per impostazione predefinita, un file dei dati di profilatura (con estensione vsp) viene salvato con la sintassi seguente:  
  
 *Percorso\File-VSP\AAMMGG(N)* **.vsp**  
  
 È possibile modificare i parametri di denominazione nella pagina Generale della finestra di dialogo delle proprietà per la sessione di prestazioni.  
  
 **Requisiti**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
|Elemento Syntax|Descrizione|  
|-|-|  
|*Percorso*|Directory che contiene il rapporto. Il percorso predefinito è la cartella della soluzione o il percorso predefinito per i progetti e le soluzioni dell'utente.|  
|*File-VSP*|Nome del file di dati di profilatura. Il nome predefinito è il nome della soluzione o del file eseguibile che viene profilato.|  
|*AAMMGG*|Indicatore di data che indica l'anno, il mese e il giorno in cui sono stati raccolti i dati di profilatura.|  
|*N*|Se esiste più di un file di dati di profilatura, al nome del file tra parentesi viene aggiunto un numero incrementato.|  
  
### <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Per modificare la sintassi di denominazione dei file di dati di profilatura di una sessione di prestazioni  
  
1. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi fare clic su **Proprietà**.  
  
2. Fare clic su **Generale**.  
  
3. In **Rapporto** modificare le impostazioni seguenti:  
  
    |Name|Descrizione|  
    |-|-|  
    |**Percorso report**|Specificare una directory per archiviare i file di dati di profilatura.|  
    |**Nome del report**|Specificare un nome di base per i file.|  
    |**Aggiungere automaticamente nuovi rapporti alla sessione**|Selezionare la casella di controllo per aggiungere automaticamente il file di dati alla sessione di prestazioni.|  
    |**Accodare un numero incrementale ai rapporti generati**|Selezionare la casella di controllo per aggiungere un numero incrementale al nome del file quando esiste più di un file con lo stesso nome. Deselezionare la casella di controllo per sovrascrivere un file esistente.|  
    |**Utilizzare un timestamp per il numero**|Selezionare la casella di controllo per aggiungere un datestamp al nome del file.|
