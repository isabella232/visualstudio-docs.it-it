---
title: Novità degli strumenti di profilatura in Visual Studio 2017 | Microsoft Docs
description: Informazioni su strumenti di diagnostica che includono nuove visualizzazioni che consentono di identificare i problemi nell'app che devono essere risolti.
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: ae501119b74300dea4397ccaaadbf13da99bbf6e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637052"
---
# <a name="whats-new-in-profiling-tools-in-includevs_dev15"></a>Novità negli strumenti di profilatura di [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Gli strumenti di diagnostica includono nuove visualizzazioni che consentono di identificare i problemi da risolvere nell'app. Gli strumenti di diagnostica ora includono il supporto per le app ASP.NET.

Per altre informazioni, vedere le [Note sulla versione per [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](/visualstudio/releasenotes/vs2017-relnotes).

È stata aggiunta agli strumenti una scheda **Riepilogo**, che consente di concentrarsi sulle aree principali per l'analisi delle prestazioni. Questa scheda mostra il numero di eventi si sono verificati, consente di creare snapshot dell'heap e consente di abilitare rapidamente la raccolta dei dati di utilizzo della CPU. Questa visualizzazione mostra eventuali eventi di [Application Insights](/azure/azure-monitor/app/visual-studio) o di [Analisi interfaccia utente](/visualstudio/releasenotes/vs2017-relnotes). Inoltre, per Visual Studio Enterprise, questa visualizzazione mostra anche gli eventi di IntelliTrace.

![Scheda Riepilogo strumenti di diagnostica](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

Lo strumento Utilizzo CPU dispone di [nuove visualizzazioni](../profiling/Beginners-Guide-to-Performance-Profiling.md) che aiutano a identificare le funzioni che possono causare problemi di prestazioni. La nuova visualizzazione **Chiamante/chiamato** consente di analizzare i costi delle chiamate di funzione effettuate da e verso una funzione selezionata.

![Visualizzazione chiamante chiamato degli strumenti di diagnostica](../profiling/media/diag-tools-caller-callee-2.png "DiagToolsCallerCallee")

## <a name="see-also"></a>Vedi anche

- [Eseguire la profilatura in Visual Studio](../profiling/index.yml)
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)