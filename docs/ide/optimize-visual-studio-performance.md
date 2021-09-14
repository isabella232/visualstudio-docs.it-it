---
title: Migliorare le prestazioni se Visual Studio è lento
titleSuffix: ''
description: Informazioni su come migliorare Visual Studio prestazioni se si verifica un'esecuzione lenta.
ms.custom: SEO-VS-2020
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: d8842764d81aa40c13865975e2d5dd28ae55eefa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636052"
---
# <a name="optimize-visual-studio-performance"></a>Ottimizzare le prestazioni di Visual Studio

Questo articolo offre alcuni suggerimenti da applicare in caso di rallentamento delle prestazioni di Visual Studio. È anche possibile dare un'occhiata a [Suggerimenti sulle prestazioni di Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md) per altri consigli su come migliorare le prestazioni.

## <a name="upgrade-visual-studio"></a>Effettuare l'aggiornamento di Visual Studio

Se è attualmente in uso Visual Studio 2015, scaricare gratuitamente [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) o [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) per verificare subito il miglioramento nelle prestazioni. Le soluzioni si caricano due-tre volte più velocemente che in Visual Studio 2015, con miglioramenti nelle prestazioni anche in altre aree. Visual Studio 2017 e Visual Studio 2019 sono compatibili side-by-side con Visual Studio 2015, in modo da non perdere nulla nel periodo di prova.

::: moniker range="vs-2017"

Se è già in uso Visual Studio 2017, assicurarsi di avere almeno la versione 15.6. In base ai dati raccolti, le soluzioni si caricano due-tre volte più velocemente nella versione 15.6. Scaricarla [qui](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download).

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Estensioni e finestre degli strumenti

Alcune estensioni installate potrebbero rallentare Visual Studio. Per informazioni sulla gestione delle estensioni per migliorare le prestazioni, vedere [Change extension settings to improve performance](../ide/optimize-visual-studio-startup-time.md#extensions) (Modificare le impostazioni delle estensioni per migliorare le prestazioni).

In modo analogo, alcune finestre degli strumenti potrebbero rallentare Visual Studio. Per informazioni sulla gestione delle finestre degli strumenti, vedere [Change tool window settings to improve performance](../ide/optimize-visual-studio-startup-time.md#tool-windows) (Modificare le impostazioni delle finestre degli strumenti per migliorare le prestazioni).

## <a name="hardware"></a>Hardware

Se si sta valutando l'aggiornamento dell'hardware, un'unità SSD è più efficace in termini di prestazioni rispetto a una CPU più veloce o una RAM aggiuntiva.

Se si aggiunge un'unità SSD, per ottenere prestazioni ottimali installare Windows sull'unità anziché un disco rigido (HDD). Il percorso dell'unità delle soluzioni Visual Studio non è così importante.

Non eseguire la soluzione da un'unità USB. Copiarla nell'unità disco rigido o SSD.

## <a name="help-us-improve"></a>Consigli per miglioramenti

Il feedback degli utenti ci permette di migliorare i nostri prodotti. Usare la funzione **Segnala un problema** per "registrare" un'analisi e inviarla a Microsoft. Selezionare l'icona del feedback accanto ad **Avvio veloce** o scegliere **Guida** > **Commenti e suggerimenti** > **Segnala un problema** dalla barra dei menu. Per altre informazioni, vedere [Come segnalare un problema con Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Vedi anche

- [Suggerimenti e consigli sulle prestazioni](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog su Visual Studio - Load solutions faster with Visual Studio 2017 version 15.6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/) (Caricamento più rapido delle soluzioni con Visual Studio 2017 Versione 15.6)
