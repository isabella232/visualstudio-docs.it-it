---
title: Variante delle dimensioni del Viewport 1x1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 168b358bf58dcb2c91814f5460b203873255e275
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433246"
---
# <a name="1x1-viewport-size-variant"></a>Variante delle dimensioni del viewport 1x1
Riduce a 1x1 pixel le dimensioni del riquadro di visualizzazione in tutte le destinazioni di rendering.  
  
## <a name="interpretation"></a>Interpretazione  
 Un viewport più piccolo consente di ridurre il numero di pixel da shade. Tuttavia, un viewport più piccolo non riduce il numero di vertici che devono essere processo. L'impostazione delle dimensioni del riquadro di visualizzazione su 1x1 pixel consente di eliminare l'ombreggiatura dei pixel dall'app.  
  
 Se questa variante Mostra un miglioramento notevole delle prestazioni, può indicare che l'app utilizza una quantità eccessiva velocità di riempimento. Inoltre, la risoluzione potrebbe essere troppo elevata per la piattaforma di destinazione o l'app avrebbe potuto impiegare molto tempo l'ombreggiatura di pixel che viene sovrascritti in un secondo momento, noto anche come *estenda*. Un buffer di frame più piccoli o riducendo la quantità di carica presente migliorerà le prestazioni dell'app.  
  
## <a name="remarks"></a>Note  
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
