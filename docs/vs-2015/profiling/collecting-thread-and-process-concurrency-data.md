---
title: Raccolta di dati di concorrenza di thread e processi | Microsoft Docs
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
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd63966dba73d57d12d68552e57828b9d17ee84e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590706"
---
# <a name="collecting-thread-and-process-concurrency-data"></a>Raccolta di dati di concorrenza di thread e processi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Collecting Thread and Process Concurrency Data](https://docs.microsoft.com/visualstudio/profiling/collecting-thread-and-process-concurrency-data).  
  
Il metodo di profilatura della concorrenza degli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente di raccogliere dati sui conflitti di risorse, ovvero informazioni relative a tutti gli eventi di sincronizzazione a causa dei quali una funzione nell'applicazione sottoposta a profilatura deve attendere per accedere a una risorsa.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 È possibile specificare il metodo di profilatura della concorrenza tramite una delle procedure seguenti:  
  
-   Nella prima pagina della procedura guidata di profilatura fare clic su **Concorrenza**.  
  
-   Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni fare clic su **Concorrenza**.  
  
-   Nell'elenco **Metodo** della barra degli strumenti di **Esplora prestazioni** fare clic su **Concorrenza**.  
  
## <a name="common-tasks"></a>Attività comuni  
 È possibile specificare altre opzioni nella finestra di dialogo _Pagine delle proprietà_**Sessioni prestazioni** della sessione di prestazioni. Per aprire questa finestra di dialogo:  
  
-   In **Esplora prestazioni**fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni e quindi scegliere **Proprietà**.  
  
 Le attività nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo _Pagine delle proprietà_ della **sessione di prestazioni** quando si esegue la profilatura con il metodo di concorrenza.  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|Nella pagina **Generale** specificare i dettagli di denominazione per il file di dati di profilatura (con estensione vsp) generato.|-   [How to: Set Performance Data File Name Options](../profiling/how-to-set-performance-data-file-name-options.md) (Procedura: Impostare le opzioni relative ai nomi file dei dati di profilatura)|  
|Se il codice contiene più progetti Exe, nella pagina **Avvia** specificare l'applicazione da avviare.|-   [How to: Specify the Binary to Start](../profiling/how-to-specify-the-binary-to-start.md) (Procedura: Specificare il file binario da avviare)|  
|Nella pagina **Interazione tra livelli** aggiungere i dati delle chiamate ADO.NET per l'esecuzione della profilatura.|-   [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|  
|Nella pagina **Contatori Windows** specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilatura come contrassegni.|-   [How to: Collect Windows Counter Data](../profiling/how-to-collect-windows-counter-data.md) (Procedura: Raccogliere i dati dei contatori Windows)|  
|Nella pagina **Avanzate** specificare la versione del runtime di .NET Framework da sottoporre a profilatura se i moduli dell'applicazione usano più versioni di questo. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.|-   [How to: Specify the .NET Framework Runtime](../profiling/how-to-specify-the-dotnet-framework-runtime.md) (Procedura: Specificare il runtime di .NET Framework)|



