---
title: Raccolta di dati di concorrenza di thread e processi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c3310a87a4b25e560ea5303553e3eb75c0da001
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831532"
---
# <a name="collect-thread-and-process-concurrency-data"></a>Raccogliere dati di concorrenza di thread e processi

Il metodo di profilatura della concorrenza degli strumenti di profilatura di Visual Studio consente di raccogliere dati sui conflitti di risorse, ovvero informazioni relative a tutti gli eventi di sincronizzazione a causa dei quali una funzione nell'applicazione sottoposta a profilatura deve attendere per accedere a una risorsa.

È possibile specificare il metodo di profilatura della concorrenza tramite una delle procedure seguenti:

- Nella prima pagina della procedura guidata di profilatura fare clic su **Concorrenza**.
- Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni fare clic su **Concorrenza**.
- Nell'elenco **Metodo** della barra degli strumenti di **Esplora prestazioni** fare clic su **Concorrenza**.

## <a name="common-tasks"></a>Attività comuni

È possibile specificare altre opzioni nella finestra di dialogo _Pagine delle proprietà_**Sessioni prestazioni** della sessione di prestazioni. Per aprire questa finestra di dialogo:

- In **Esplora prestazioni**fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni e quindi scegliere **Proprietà**.

Le attività nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo _Pagine delle proprietà_ della **sessione di prestazioni** quando si esegue la profilatura con il metodo di concorrenza.

|Attività|Contenuto correlato|
|----------|---------------------|
|Nella pagina **Generale** specificare i dettagli di denominazione per il file di dati di profilatura (con estensione vsp) generato.|- [Procedura: Impostare le opzioni relative ai nomi file dei dati sulle prestazioni](../profiling/how-to-set-performance-data-file-name-options.md)|
|Se il codice contiene più progetti Exe, nella pagina **Avvia** specificare l'applicazione da avviare.|- [Procedura: Specificare il file binario da avviare](../profiling/how-to-specify-the-binary-to-start.md)|
|Nella pagina **Interazione tra livelli** aggiungere i dati delle chiamate ADO.NET per l'esecuzione della profilatura.|- [Raccogliere dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|
|Nella pagina **Contatori Windows** specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilatura come contrassegni.|- [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Nella pagina **Avanzate** specificare la versione del runtime di .NET Framework da sottoporre a profilatura se i moduli dell'applicazione usano più versioni di questo. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.|- [Procedura: Specificare il runtime di .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|