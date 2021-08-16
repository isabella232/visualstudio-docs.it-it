---
title: Iniziare e terminare la raccolta dei dati sulle prestazioni | Microsoft Docs
description: Informazioni su come aggiungere il file binario di destinazione che si vuole profilare alla sessione di prestazioni prima di avviare la profilatura.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f0a712e33e6961193f9145efe69b229638c090c4e75427c8fe92809cc0e3fd58
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396435"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Procedura: Iniziare e terminare la raccolta dati sulle prestazioni
Prima di avviare la profilatura, è necessario aggiungere alla sessione di prestazioni il file binario di destinazione che si vuole profilare. Per aggiungere una destinazione, fare clic con il pulsante destro del mouse su **Destinazioni** in **Esplora prestazioni** e quindi fare clic su **Aggiungi binario di destinazione**. Nella finestra di dialogo **Aggiungi binario di destinazione** selezionare il nome del file e quindi fare clic su **Apri**. Verrà aggiunto un nuovo file binario.

### <a name="to-start-profiling"></a>Per avviare la profilatura

1. Fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni nella finestra **Esplora prestazioni** e scegliere una delle opzioni seguenti:

    - **Avvio con analisi**: avvia l'applicazione e comincia immediatamente la profilatura.

    - **Avvio con analisi sospeso**: avvia l'applicazione ma non comincia la profilatura. È possibile avviare la profilatura selezionando **Riprendi raccolta** nella finestra **Controllo raccolta dati**. Per altre informazioni, vedere [Procedura: Sospendere e riprendere la raccolta dei dati sulle prestazioni](../profiling/how-to-pause-and-resume-performance-data-collection.md).

### <a name="to-end-profiling"></a>Per terminare la profilatura

- Il metodo consigliato per terminare una sessione di profilatura consiste nella chiusura dell'applicazione. Per terminare immediatamente la profilatura, nella barra degli strumenti di **Esplora prestazioni** fare clic su **Interrompi**.

## <a name="see-also"></a>Vedi anche
- [Controllare la raccolta dati](../profiling/controlling-data-collection.md)
- [Procedura: Sospendere e riprendere la raccolta dati prestazioni](../profiling/how-to-pause-and-resume-performance-data-collection.md)
