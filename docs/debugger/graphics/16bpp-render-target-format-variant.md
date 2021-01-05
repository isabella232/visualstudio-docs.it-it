---
title: Variante del formato di destinazione di rendering 16bpp | Microsoft Docs
description: Applicare la variante del formato di destinazione di rendering a 16 bit per pixel (BPP) impostando il formato pixel su DXGI_FORMAT_B5G6R5_UNORM per tutte le destinazioni di rendering e i buffer back.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa73637244469d781ac77acba362886b5656f8d8
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728044"
---
# <a name="16-bpp-render-target-format-variant"></a>Variante del formato di destinazione di rendering a 16 BPP
Imposta il formato di pixel su DXGI_FORMAT_B5G6R5_UNORM per tutte le destinazioni di rendering e i buffer nascosti.

## <a name="interpretation"></a>Interpretazione
 Una destinazione di rendering o un buffer nascosto USA in genere un formato di 32 BPP (32 bit per pixel), ad esempio B8G8R8A8_UNORM. i formati 32-BPP possono utilizzare una grande quantità di larghezza di banda di memoria. Poiché il formato di B5G6R5_UNORM è un formato a 16 BPP che rappresenta la metà delle dimensioni dei formati 32-BPP, l'uso di tale formato può ridurre la pressione della larghezza di banda di memoria, ma a scapito della fedeltà dei colori ridotta.

 Se questa variante mostra un miglioramento notevole delle prestazioni, ciò potrebbe indicare un consumo eccessivo della larghezza di banda della memoria. È possibile ottenere un miglioramento significativo delle prestazioni, soprattutto quando il frame profilato ha una quantità significativa di Overcast o alfa-Blend.

Un formato di destinazione di rendering a 16 BPP può ridurre la banda di memoria con utilizzo quando l'applicazione presenta le condizioni seguenti:
- Non richiede la riproduzione di colori ad alta fedeltà.
- Non richiede un canale alfa.
- Non dispone spesso di sfumature smussate, che sono soggette a bande di elementi con una fedeltà dei colori ridotta.

Altre strategie per ridurre la larghezza di banda di memoria includono:
- Ridurre la quantità di overblend o la fusione alfa.
- Ridurre le dimensioni del buffer del frame.
- Ridurre le dimensioni delle risorse di trama.
- Ridurre le compressioni delle risorse di trama.

Di norma, è necessario valutare i compromessi relativi alla qualità di immagine associati a ognuna di queste ottimizzazioni.

Le applicazioni che fanno parte di una catena di scambio hanno un formato di buffer nascosto (DXGI_FORMAT_B5G6R5_UNORM) che non supporta 16 BPP. Queste catene di scambio vengono create usando `D3D11CreateDeviceAndSwapChain` o `IDXGIFactory::CreateSwapChain` . Per ovviare a questa limitazione, attenersi alla procedura seguente:
1. Creare una destinazione di rendering del formato B5G6R5_UNORM usando `CreateTexture2D` ed eseguendo il rendering su tale destinazione.
2. Copiare la destinazione di rendering nel buffer a catena di scambio disegnando un quad a schermo intero con la destinazione di rendering come trama di origine.
3. Chiamata presente nella catena di scambio.

   Se questa strategia salva una maggiore larghezza di banda rispetto a quella utilizzata copiando la destinazione di rendering nel buffer nascosto della catena di scambio, le prestazioni di rendering risultano migliorate.

   Le architetture GPU che usano tecniche di rendering affiancate possono avere vantaggi significativi in merito alle prestazioni usando un formato di buffer di frame a 16 BPP. Questo miglioramento è dovuto al fatto che una parte più ampia del buffer dei frame può adattarsi alla cache del buffer dei frame locale di ogni riquadro. Le architetture di rendering basate su riquadri vengono spesso usate nelle GPU di telefoni cellulari e tablet; è raro trovarle in altri tipi di dispositivi.

## <a name="remarks"></a>Commenti
 Il formato della destinazione di rendering viene reimpostato su DXGI_FORMAT_B5G6R5_UNORM a ogni chiamata al metodo `ID3D11Device::CreateTexture2D` che crea una destinazione di rendering. In particolare, il formato viene sovrascritto quando l'oggetto D3D11_TEXTURE2D_DESC passato a pDesc descrive una destinazione di rendering, ovvero:

- Il membro BindFlags presenta il flag D3D11_BIND_REDNER_TARGET impostato.

- Il membro BindFlags presenta il flag D3D11_BIND_DEPTH_STENCIL deselezionato.

- Il membro Usage è impostato su D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Restrizioni e limitazioni
 Poiché il formato B5G6R5 non ha un canale alfa, il contenuto alfa non viene mantenuto da questa variante. Se il rendering dell'app richiede un canale alfa nella destinazione di rendering, non è possibile passare semplicemente al formato B5G6R5.

## <a name="example"></a>Esempio
 La variante del **formato di destinazione di rendering a 16 BPP** può essere riprodotta per le destinazioni di rendering create tramite usando `CreateTexture2D` codice simile al seguente:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
