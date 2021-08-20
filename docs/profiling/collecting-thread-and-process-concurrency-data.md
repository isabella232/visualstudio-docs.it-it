---
title: Raccogliere dati di concorrenza & thread e processi
description: Usare il Strumenti di profilatura di profilatura della concorrenza per raccogliere dati su ogni evento di sincronizzazione che fa in modo che una funzione attenda l'accesso alle risorse.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cdcefa6559aea6ed59bb2097e2a2285eabc4b07a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142325"
---
# <a name="collect-thread-and-process-concurrency-data"></a>Raccogliere dati di concorrenza di thread e processi

Il metodo di profilatura della concorrenza degli strumenti di profilatura di Visual Studio consente di raccogliere dati sui conflitti di risorse, ovvero informazioni relative a tutti gli eventi di sincronizzazione a causa dei quali una funzione nell'applicazione sottoposta a profilatura deve attendere per accedere a una risorsa.

È possibile specificare il metodo di profilatura della concorrenza tramite una delle procedure seguenti:

- Nella prima pagina della procedura guidata di profilatura fare clic su **Concorrenza**.
- Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni fare clic su **Concorrenza**.
- Nell'elenco **Metodo** della barra degli strumenti di **Esplora prestazioni** fare clic su **Concorrenza**.

## <a name="common-tasks"></a>Attività comuni

È possibile specificare altre opzioni nella finestra di dialogo _Pagine delle proprietà_**Sessioni prestazioni** della sessione di prestazioni. Per aprire questa finestra di dialogo:

- In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni e quindi scegliere **Proprietà.**

Le attività nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo _Pagine delle proprietà_ della **sessione di prestazioni** quando si esegue la profilatura con il metodo di concorrenza.

|Attività|Contenuto correlato|
|----------|---------------------|
|Nella pagina **Generale** specificare i dettagli di denominazione per il file di dati di profilatura (con estensione vsp) generato.|- [Procedura: Impostare le opzioni relative al nome del file di dati sulle prestazioni](../profiling/how-to-set-performance-data-file-name-options.md)|
|Se il codice contiene più progetti Exe, nella pagina **Avvia** specificare l'applicazione da avviare.|- [Procedura: Specificare il file binario da avviare](../profiling/how-to-specify-the-binary-to-start.md)|
|Nella pagina **Interazione tra livelli** aggiungere i dati delle chiamate ADO.NET per l'esecuzione della profilatura.|- [Raccogliere dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|
|Nella pagina **Contatori Windows** specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilatura come contrassegni.|- [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Nella pagina **Avanzate** specificare la versione del .NET Framework di esecuzione da profilare se i moduli dell'applicazione usano più versioni. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.|- [Procedura: Specificare il runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
