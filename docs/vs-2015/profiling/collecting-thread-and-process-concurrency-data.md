---
title: Raccolta di dati di concorrenza di thread e processi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf8a9de5f2a7e520a745fab81197016d6e1bd15d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568195"
---
# <a name="collecting-thread-and-process-concurrency-data"></a>Raccolta di dati di concorrenza di thread e processi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il metodo di profilatura della concorrenza degli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente di raccogliere dati sui conflitti di risorse, ovvero informazioni relative a tutti gli eventi di sincronizzazione a causa dei quali una funzione nell'applicazione sottoposta a profilatura deve attendere per accedere a una risorsa.  
  
 **Requisiti**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  È possibile specificare il metodo di profilatura della concorrenza tramite una delle procedure seguenti:  
  
- Nella prima pagina della procedura guidata di profilatura fare clic su **Concorrenza**.  
  
- Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni fare clic su **Concorrenza**.  
  
- Nell'elenco **Metodo** della barra degli strumenti di **Esplora prestazioni** fare clic su **Concorrenza**.  
  
## <a name="common-tasks"></a>Attività comuni  
 È possibile specificare altre opzioni nella finestra di dialogo _Pagine delle proprietà_**Sessioni prestazioni** della sessione di prestazioni. Per aprire questa finestra di dialogo:  
  
- In **Esplora prestazioni**fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni, quindi scegliere **Proprietà**.  
  
  Le attività nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo _Pagine delle proprietà_ della **sessione di prestazioni** quando si esegue la profilatura con il metodo di concorrenza.  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|Nella pagina **Generale** specificare i dettagli di denominazione per il file di dati di profilatura (con estensione vsp) generato.|-   [Procedura: impostare le opzioni relative ai nomi file dei dati sulle prestazioni](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Se il codice contiene più progetti Exe, nella pagina **Avvia** specificare l'applicazione da avviare.|-   [Procedura: specificare il file binario da avviare](../profiling/how-to-specify-the-binary-to-start.md)|  
|Nella pagina **Interazione tra livelli** aggiungere i dati delle chiamate ADO.NET per l'esecuzione della profilatura.|-   [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|  
|Nella pagina **Contatori Windows** specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilatura come contrassegni.|-   [Procedura: raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Nella pagina **Avanzate** specificare la versione del .NET Framework Runtime da profilare se i moduli dell'applicazione usano più versioni. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.|-   [Procedura: specificare il runtime di .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
