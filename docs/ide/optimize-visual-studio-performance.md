---
title: Migliorare le prestazioni se Visual Studio è lento
titleSuffix: ''
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.performancecenter
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f5fe9324360a01700024e14e6c70755d61aa3e60
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065775"
---
# <a name="optimize-visual-studio-performance"></a>Ottimizzare le prestazioni di Visual Studio

Questo articolo offre alcuni suggerimenti da applicare in caso di rallentamento delle prestazioni di Visual Studio. È anche possibile dare un'occhiata a [Suggerimenti sulle prestazioni di Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md) per altri consigli su come migliorare le prestazioni.

## <a name="upgrade-to-visual-studio-2017-version-156-or-later"></a>Eseguire l'aggiornamento a Visual Studio 2017 15.6 o versione successiva

Se è attualmente in uso Visual Studio 2015, scaricare gratuitamente [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per verificare subito il miglioramento nelle prestazioni. Le soluzioni si caricano due-tre volte più velocemente in Visual Studio 2017, con miglioramenti nelle prestazioni anche in altre aree. Visual Studio 2017 è compatibile side-by-side con Visual Studio 2015, in modo da non perdere nulla nel periodo di prova.

Se è attualmente in uso Visual Studio 2017, assicurarsi di disporre almeno della versione 15.6. In base ai dati raccolti, le soluzioni si caricano due-tre volte più velocemente nella versione 15.6. Il download è disponibile [qui](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

## <a name="extensions-and-tool-windows"></a>Estensioni e finestre degli strumenti

Alcune estensioni installate potrebbero rallentare Visual Studio. Per informazioni sulla gestione delle estensioni per migliorare le prestazioni, vedere [Change extension settings to improve performance](../ide/optimize-visual-studio-startup-time.md#extensions) (Modificare le impostazioni delle estensioni per migliorare le prestazioni).

In modo analogo, alcune finestre degli strumenti potrebbero rallentare Visual Studio. Per informazioni sulla gestione delle finestre degli strumenti, vedere [Change tool window settings to improve performance](../ide/optimize-visual-studio-startup-time.md#tool-windows) (Modificare le impostazioni delle finestre degli strumenti per migliorare le prestazioni).

## <a name="hardware"></a>Hardware

Se si sta valutando l'aggiornamento dell'hardware, un'unità SSD è più efficace in termini di prestazioni rispetto a una CPU più veloce o una RAM aggiuntiva.

Se si aggiunge un'unità SSD, per ottenere prestazioni ottimali installare Windows sull'unità anziché un disco rigido (HDD). Il percorso dell'unità delle soluzioni Visual Studio non è così importante.

Non eseguire la soluzione da un'unità USB. Copiarla nell'unità disco rigido o SSD.

## <a name="help-us-improve"></a>Consigli per miglioramenti

Il feedback degli utenti ci permette di migliorare i nostri prodotti. Usare la funzione **Segnala un problema** per "registrare" un'analisi e inviarla a Microsoft. Selezionare l'icona del feedback accanto ad **Avvio veloce** o scegliere **Guida** > **Commenti e suggerimenti** > **Segnala un problema** dalla barra dei menu. Per altre informazioni, vedere [Come segnalare un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="see-also"></a>Vedere anche

- [Suggerimenti sulle prestazioni](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog su Visual Studio - Load solutions faster with Visual Studio 2017 version 15.6](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/) (Caricamento più rapido delle soluzioni con Visual Studio 2017 Versione 15.6)