---
title: API di grafica e le statistiche di memoria | Microsoft Docs
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
ms.openlocfilehash: e0c1ed6e2fdd461b0fdf502c01089aeafd9a87cb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925630"
---
# <a name="graphics-api-and-memory-statistics"></a>API di grafica e le statistiche di memoria
<!-- VERSIONLESS --> Visual Studio 2017 e versioni successiva supporta gli strumenti di grafica API statistiche e le statistiche di memoria.  Questi due strumenti consentono di visualizzare diverse parti di informazioni su utilizzo dell'API Direct3D, così come il consumo di memoria GPU di varie risorse.

## <a name="graphics-api-statistics"></a>Statistiche API grafica
Le statistiche di API di grafica in Visual Studio Graphics Diagnostics consente di visualizzare tutte le chiamate Direct3D che sono state apportate e il conteggio di ogni chiamata.  Per visualizzare la finestra, selezionare la **Visualizza > statistiche API** voce di menu.

![Statistiche API](media/gfx_diag_api_statistics.png)

Questo strumento può essere utile individuare chiamate DirectX che non è possibile comprendere si stanno apportando le chiamate o che si stanno apportando troppo spesso.

È possibile fare doppio clic nella finestra per copiare tutti i dati in formato CSV, che può essere incollato in un elemento come Excel per un'ulteriore analisi.

## <a name="memory-statistics"></a>Statistiche memoria
Questo strumento visualizzerà la quantità di memoria allocata dal driver di grafica per le risorse create in un frame.  Per visualizzare questa finestra, selezionare la **Visualizza > statistiche memoria** voce di menu.

![Statistiche memoria](media/gfx_diag_memory_statistics.png)

Il **allocazione GPU** colonna consente di visualizzare la quantità di memoria utilizzata dall'evento visualizzato nei **evento** colonna.  È anche possibile selezionare l'icona di espressioni di controllo ![icona watch](media/gfx_watch.png) per visualizzare i [cronologia risorse](graphics-event-list.md#resource-history) per l'evento selezionato.

Come con lo strumento di statistiche API, è possibile fare doppio clic nella finestra per copiare tutti i dati in formato CSV, che può essere incollato in un elemento come Excel per un'ulteriore analisi.

## <a name="see-also"></a>Vedere anche  
[Diagnostica della grafica (debug della grafica DirectX)](visual-studio-graphics-diagnostics.md)   
[Cronologia risorse](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->