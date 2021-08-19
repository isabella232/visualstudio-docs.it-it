---
title: API grafica e statistiche di memoria | Microsoft Docs
description: Esaminare gli strumenti Statistiche API grafica e Statistiche memoria, che mostrano informazioni sull'utilizzo dell'API Direct3D e sull'utilizzo della memoria GPU di varie risorse.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7cdd9def44588dacb6995dee966e8f23266aff51
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121037"
---
# <a name="graphics-api-and-memory-statistics"></a>API grafica e statistiche di memoria
<!-- VERSIONLESS -->
Visual Studio 2017 e versione successiva supportano gli strumenti Statistiche API grafica e Statistiche memoria.  Questi due strumenti consentono di visualizzare vari bit di informazioni sull'utilizzo dell'API Direct3D e sull'utilizzo della memoria GPU di varie risorse.

## <a name="graphics-api-statistics"></a>Statistiche dell'API Grafica
Le statistiche dell'API grafica Visual Studio Diagnostica della grafica consentono di visualizzare tutte le chiamate Direct3D effettuate e il conteggio di ogni chiamata.  Per visualizzare la finestra, selezionare la voce di menu View > API Statistics (Visualizza **statistiche API).**

![Statistiche API](media/gfx_diag_api_statistics.png)

Questo strumento può essere utile per individuare le chiamate DirectX che non si stanno effettuando o le chiamate effettuate troppo spesso.

È possibile fare clic con il pulsante destro del mouse nella finestra per copiare tutti i dati in formato CSV, che può essere incollato in un Excel per un'ulteriore analisi.

## <a name="memory-statistics"></a>Statistiche memoria
Questo strumento visualizza la quantità di memoria allocata dal driver di grafica per le risorse create in un frame.  Per visualizzare questa finestra, selezionare la **voce di menu > statistiche memoria** .

![Statistiche memoria](media/gfx_diag_memory_statistics.png)

Nella **colonna Allocazione GPU** viene visualizzata la quantità di memoria usata dall'evento visualizzato nella **colonna** Evento .  È anche possibile selezionare l'icona dell'orologio icona ![ ](media/gfx_watch.png) dell'orologio per visualizzare la cronologia delle [risorse](graphics-event-list.md#resource-history) per l'evento selezionato.

Come con lo strumento Statistiche API, è possibile fare clic con il pulsante destro del mouse nella finestra per copiare tutti i dati in formato CSV, che può essere incollato in un file simile Excel per un'ulteriore analisi.

## <a name="see-also"></a>Vedi anche
- [Diagnostica della grafica (Debug grafica DirectX)](visual-studio-graphics-diagnostics.md)
- [Cronologia risorse](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->