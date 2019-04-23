---
title: Variante del formato di destinazione di rendering a 16bpp | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94775b717a3095d54d3fa52e3d2a5325dc3d21c5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075792"
---
# <a name="16-bpp-render-target-format-variant"></a>eseguire il rendering di destinazione variante del formato di 16 bpp
Imposta il formato di pixel su DXGI_FORMAT_B5G6R5_UNORM per tutte le destinazioni di rendering e i buffer nascosti.

## <a name="interpretation"></a>Interpretazione
 Una destinazione di rendering o un buffer nascosto Usa in genere un formato di 32 bpp (32 bit per pixel), ad esempio B8G8R8A8_UNORM. formati di 32 bpp possono utilizzare una grande quantità di larghezza di banda di memoria. Poiché il formato B5G6R5_UNORM è un formato di 16-bit per pixel che è metà delle dimensioni dei formati di 32 bpp, usarlo possibile alleggerire il carico sulla larghezza di banda di memoria, ma al costo di fedeltà dei colori ridotta.

 Se questa variante mostra un miglioramento notevole delle prestazioni, ciò potrebbe indicare un consumo eccessivo della larghezza di banda della memoria. È possibile ottenere miglioramenti significativi delle prestazioni, soprattutto quando il fotogramma profilato era una quantità significativa di caricamento o fusione alfa.

Formato di destinazione di rendering 16-bit per pixel può ridurre fuori banda di memoria con l'utilizzo quando l'applicazione presenta le seguenti condizioni:
- Non richiede la riproduzione dei colori ad alta fedeltà.
- Non richiede un canale alfa.
- Ofent privo di sfumature (che sono soggette agli elementi di rappresentazione per bande fedeltà dei colori ridotta).

Altre strategie per ridurre la larghezza di banda di memoria includono:
- Ridurre la quantità di caricamento o fusione alfa.
- Ridurre le dimensioni del buffer frame.
- Ridurre le dimensioni delle risorse di trama.
- Ridurre la compressione delle risorse di trama.

Di norma, è necessario valutare i compromessi relativi alla qualità di immagine associati a ognuna di queste ottimizzazioni.

Le applicazioni che fanno parte di una catena di scambio hanno un formato di buffer nascosto (DXGI_FORMAT_B5G6R5_UNORM) che non supporta i 16 bit per pixel. Queste catene di scambio vengono create usando `D3D11CreateDeviceAndSwapChain` o `IDXGIFactory::CreateSwapChain`. Per aggirare questa limitazione, procedere come segue:
1. Creare una destinazione di rendering formato B5G6R5_UNORM usando `CreateTexture2D` ed eseguire il rendering che hanno come destinazione.
2. Copiare la destinazione di rendering nel buffer nascosto della catena di scambio disegnando una quad a schermo intero con la destinazione di rendering come trama di origine.
3. Chiamare Present sulla catena di scambio.

   Se questa strategia consente di salvare più larghezza di banda usata dalla copia di destinazione di rendering per il buffer nascosto della catena di scambio, le prestazioni di rendering sono stata migliorata.

   Le architetture GPU che usano tecniche di rendering possono visualizzare i vantaggi significativi delle prestazioni utilizzando un formato di buffer di frame di 16 bit per pixel. Questo miglioramento è perché una parte maggiore del buffer di frame può adattarsi alla cache del buffer di ogni riquadro frame locale. Le architetture di rendering basate su riquadri vengono spesso usate nelle GPU di telefoni cellulari e tablet; è raro trovarle in altri tipi di dispositivi.

## <a name="remarks"></a>Note
 Il formato della destinazione di rendering viene reimpostato su DXGI_FORMAT_B5G6R5_UNORM a ogni chiamata al metodo `ID3D11Device::CreateTexture2D` che crea una destinazione di rendering. In particolare, il formato viene sovrascritto quando l'oggetto D3D11_TEXTURE2D_DESC passato a pDesc descrive una destinazione di rendering, ovvero:

- Il membro BindFlags presenta il flag D3D11_BIND_REDNER_TARGET impostato.

- Il membro BindFlags presenta il flag D3D11_BIND_DEPTH_STENCIL deselezionato.

- Il membro Usage è impostato su D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Limiti e restrizioni
 Poiché il formato B5G6R5 non ha un canale alfa, il contenuto alfa non viene mantenuto da questa variante. Se il rendering dell'app richiede un canale alfa nella destinazione di rendering, non è possibile passare semplicemente al formato B5G6R5.

## <a name="example"></a>Esempio
 Il **bpp 16 formato di destinazione di rendering** variante può essere riprodotta per destinazioni di rendering create tramite `CreateTexture2D` usando codice simile al seguente:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
