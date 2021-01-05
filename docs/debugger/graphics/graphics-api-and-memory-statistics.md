---
title: API grafica e statistiche di memoria | Microsoft Docs
description: Esaminare gli strumenti Statistiche API grafica e statistiche memoria, che mostrano le informazioni sull'utilizzo dell'API Direct3D e sull'utilizzo della memoria GPU di varie risorse.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e0ad2bc48e1e15e1b061cdb600ce65773523e70
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727890"
---
# <a name="graphics-api-and-memory-statistics"></a>API grafica e statistiche di memoria
<!-- VERSIONLESS -->
Visual Studio 2017 e versioni successive supportano gli strumenti Statistiche API grafica e statistiche memoria.  Questi due strumenti consentono di visualizzare diversi bit di informazioni sull'utilizzo dell'API Direct3D, oltre al consumo della memoria GPU di varie risorse.

## <a name="graphics-api-statistics"></a>Statistiche dell'API grafica
Le statistiche dell'API grafica in Visual Studio Diagnostica della grafica consentono di visualizzare tutte le chiamate Direct3D effettuate e il conteggio di ogni chiamata.  Per visualizzare la finestra, selezionare la voce di menu **view > API Statistics** .

![Statistiche API](media/gfx_diag_api_statistics.png)

Questo strumento può essere utile per individuare le chiamate a DirectX che potrebbero non essere realizzate o chiamate effettuate troppo spesso.

È possibile fare clic con il pulsante destro del mouse nella finestra per copiare tutti i dati come CSV, che possono essere incollati in un file come Excel per un'ulteriore analisi.

## <a name="memory-statistics"></a>Statistiche memoria
Questo strumento visualizzerà la quantità di memoria allocata dal driver di grafica per le risorse create in un frame.  Per visualizzare questa finestra, selezionare la voce di menu **visualizza > statistiche memoria** .

![Statistiche memoria](media/gfx_diag_memory_statistics.png)

Nella colonna **allocazione GPU** viene visualizzata la quantità di memoria utilizzata dall'evento visualizzato nella colonna **evento** .  È anche possibile selezionare l'icona espressioni ![ di controllo ](media/gfx_watch.png) per visualizzare la [cronologia delle risorse](graphics-event-list.md#resource-history) per l'evento selezionato.

Come per lo strumento Statistiche API, è possibile fare clic con il pulsante destro del mouse nella finestra per copiare tutti i dati come CSV, che possono essere incollati in un elemento come Excel per un'ulteriore analisi.

## <a name="see-also"></a>Vedi anche
- [Diagnostica della grafica (Debug grafica DirectX)](visual-studio-graphics-diagnostics.md)
- [Cronologia risorse](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->