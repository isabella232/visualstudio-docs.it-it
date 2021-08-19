---
title: Variante di formato di destinazione di rendering 16bpp | Microsoft Docs
description: Applicare la variante di formato di destinazione di rendering a 16 bit per pixel (bpp) impostando il formato pixel su DXGI_FORMAT_B5G6R5_UNORM per tutte le destinazioni di rendering e i buffer back.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a1713dba828af71b1a6a23cc7de0f46fd28bab70
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154317"
---
# <a name="16-bpp-render-target-format-variant"></a>Variante di formato di destinazione di rendering a 16 bpp
Imposta il formato di pixel su DXGI_FORMAT_B5G6R5_UNORM per tutte le destinazioni di rendering e i buffer nascosti.

## <a name="interpretation"></a>Interpretazione
 Una destinazione di rendering o un buffer nascosto usa in genere un formato a 32 bpp (32 bit per pixel), ad esempio B8G8R8A8_UNORM. I formati a 32 bpp possono utilizzare una grande quantità di larghezza di banda di memoria. Poiché il formato B5G6R5_UNORM è un formato a 16 bpp che è la metà delle dimensioni dei formati a 32 bpp, l'uso di questo formato può ridurre la pressione sulla larghezza di banda della memoria, ma a costo di ridurre la fedeltà dei colori.

 Se questa variante mostra un miglioramento notevole delle prestazioni, ciò potrebbe indicare un consumo eccessivo della larghezza di banda della memoria. È possibile ottenere un miglioramento significativo delle prestazioni, soprattutto quando il frame profilato ha una quantità significativa di overdraw o alpha-blending.

Un formato di destinazione di rendering a 16 bpp può ridurre la banda di memoria con l'utilizzo quando l'applicazione presenta le condizioni seguenti:
- Non richiede la riproduzione dei colori ad alta fedeltà.
- Non richiede un canale alfa.
- Spesso non ha sfumature uniformi (che sono soggette a bande di artefatti in fedeltà ai colori ridotta).

Altre strategie per ridurre la larghezza di banda della memoria includono:
- Ridurre la quantità di overdraw o alpha blending.
- Ridurre le dimensioni del buffer dei frame.
- Ridurre le dimensioni delle risorse di trama.
- Ridurre le compressioni delle risorse di trama.

Di norma, è necessario valutare i compromessi relativi alla qualità di immagine associati a ognuna di queste ottimizzazioni.

Le applicazioni che fanno parte di una catena di scambio hanno un formato di buffer nascosto (DXGI_FORMAT_B5G6R5_UNORM) che non supporta 16 bpp. Queste catene di scambio vengono create tramite `D3D11CreateDeviceAndSwapChain` o `IDXGIFactory::CreateSwapChain` . Per risolvere questa limitazione, seguire questa procedura:
1. Creare una destinazione B5G6R5_UNORM di rendering in formato personalizzato usando `CreateTexture2D` ed eseguirne il rendering in tale destinazione.
2. Copiare la destinazione di rendering nel backbuffer della catena di scambio disegnando un quad a schermo intero con la destinazione di rendering come trama di origine.
3. Chiamare Present nella catena di scambio.

   Se questa strategia consente di risparmiare più larghezza di banda di quella utilizzata copiando la destinazione di rendering nel backbuffer della catena di scambio, le prestazioni di rendering sono migliorate.

   Le architetture GPU che usano tecniche di rendering affiancato possono vedere vantaggi significativi in termini di prestazioni usando un formato di buffer di frame a 16 bpp. Questo miglioramento è dovuto al fatto che una parte più grande del buffer dei frame può essere inserita nella cache del buffer frame locale di ogni riquadro. Le architetture di rendering basate su riquadri vengono spesso usate nelle GPU di telefoni cellulari e tablet; è raro trovarle in altri tipi di dispositivi.

## <a name="remarks"></a>Commenti
 Il formato della destinazione di rendering viene reimpostato su DXGI_FORMAT_B5G6R5_UNORM a ogni chiamata al metodo `ID3D11Device::CreateTexture2D` che crea una destinazione di rendering. In particolare, il formato viene sovrascritto quando l'oggetto D3D11_TEXTURE2D_DESC passato a pDesc descrive una destinazione di rendering, ovvero:

- Il membro BindFlags presenta il flag D3D11_BIND_REDNER_TARGET impostato.

- Il membro BindFlags presenta il flag D3D11_BIND_DEPTH_STENCIL deselezionato.

- Il membro Usage è impostato su D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Restrizioni e limitazioni
 Poiché il formato B5G6R5 non ha un canale alfa, il contenuto alfa non viene mantenuto da questa variante. Se il rendering dell'app richiede un canale alfa nella destinazione di rendering, non è possibile passare semplicemente al formato B5G6R5.

## <a name="example"></a>Esempio
 La **variante 16 bpp Render Target Format** può essere riprodotta per le destinazioni di rendering create usando codice simile al `CreateTexture2D` seguente:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
