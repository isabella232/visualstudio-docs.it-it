---
title: Variante dimensioni viewport 1x1 | Microsoft Docs
description: Applicare la variante della dimensione del viewport 1x1 per ridurre le dimensioni del viewport in tutte le destinazioni di rendering in 1x1 pixel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1041f3a8016500a6e1f217849654d9710a508d8
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726488"
---
# <a name="1x1-viewport-size-variant"></a>Variante delle dimensioni del viewport 1x1
Riduce a 1x1 pixel le dimensioni del riquadro di visualizzazione in tutte le destinazioni di rendering.

## <a name="interpretation"></a>Interpretazione
 Un viewport più piccolo riduce il numero di pixel che è necessario ombreggiare. Tuttavia, un viewport più piccolo non riduce il numero di vertici che è necessario elaborare. L'impostazione delle dimensioni del riquadro di visualizzazione su 1x1 pixel consente di eliminare l'ombreggiatura dei pixel dall'app.

 Se questa variante Mostra un notevole miglioramento delle prestazioni, potrebbe indicare che l'app consuma una quantità eccessiva di riempimento. Inoltre, la risoluzione potrebbe essere troppo elevata per la piattaforma di destinazione o l'app potrebbe dedicare un tempo di ombreggiatura notevole dei pixel che vengono sovrascritti *in un* secondo momento, anche noto come sovrascrittura. Un buffer di frame più piccolo o la riduzione della quantità di sovradisegni migliorerà le prestazioni dell'app.

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
