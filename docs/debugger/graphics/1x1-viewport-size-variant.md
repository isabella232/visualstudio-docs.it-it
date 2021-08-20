---
title: Variante delle dimensioni del viewport 1x1 | Microsoft Docs
description: Applicare la variante delle dimensioni del viewport 1x1 per ridurre le dimensioni del viewport in tutte le destinazioni di rendering a 1x1 pixel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: bf619c6f9499916971620e3d428cf3545fd4cea1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121100"
---
# <a name="1x1-viewport-size-variant"></a>Variante delle dimensioni del viewport 1x1
Riduce a 1x1 pixel le dimensioni del riquadro di visualizzazione in tutte le destinazioni di rendering.

## <a name="interpretation"></a>Interpretazione
 Un riquadro di visualizzazione più piccolo riduce il numero di pixel da ombreggiatura. Tuttavia, un viewport più piccolo non riduce il numero di vertici da elaborare. L'impostazione delle dimensioni del riquadro di visualizzazione su 1x1 pixel consente di eliminare l'ombreggiatura dei pixel dall'app.

 Se questa variante mostra un miglioramento delle prestazioni elevato, potrebbe indicare che l'app usa troppe fill rate. Inoltre, la risoluzione potrebbe essere troppo elevata per la piattaforma di destinazione o l'app potrebbe dedicare molto tempo all'ombreggiatura dei pixel che vengono successivamente sovrascritti, noti anche come *overdraw.* Un buffer di frame più piccolo o la riduzione della quantità di sovrapposizione miglioreranno le prestazioni dell'app.

## <a name="remarks"></a>Commenti
 Le dimensioni del riquadro di visualizzazione vengono reimpostate su 1x1 pixel dopo ogni chiamata a `ID3D11DeviceContext::OMSetRenderTargets` o `ID3D11DeviceContext::RSSetViewports`.

## <a name="example"></a>Esempio
 Questa variante può essere riprodotta con il codice seguente:

```cpp
D3D11_VIEWPORT viewport;
viewport.TopLeftX = 0;
viewport.TopLeftY = 0;
viewport.Width = 1;
viewport.Height = 1;
d3d_context->RSSetViewports(1, &viewport);
```
