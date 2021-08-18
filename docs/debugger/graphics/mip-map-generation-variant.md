---
title: Variante di generazione mappa mip | Microsoft Docs
description: Se la generazione di mappe MIP mostra miglioramenti significativi delle prestazioni, significa che si usano trame senza abilitare le mappe MIP e senza ottenere il massimo dalla cache delle trame.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7cae61a6ee7d72adf51165f12a2651d9c98a35cd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154187"
---
# <a name="mip-map-generation-variant"></a>Variante di generazione di mappe MIP
Abilita le mappe MIP nelle trame che non corrispondono a destinazioni di rendering.

## <a name="interpretation"></a>Interpretazione
Le mappe MIP vengono principalmente usate per eliminare gli artefatti di aliasing nelle trame minimizzate tramite il precalcolo di versioni della trama di dimensioni inferiori. Sebbene queste trame aggiuntive utilizzino una maggiore quantità di memoria GPU, circa il 33% più della trama originale, sono anche più efficienti perché l'area della superficie che può essere memorizzata nella cache della trama GPU è maggiore e garantisce un utilizzo più elevato del relativo contenuto.

Per le scene 3D, è consigliabile usare le mappe MIP quando è disponibile memoria per archiviare tramite aggiuntive, in modo da aumentare sia le prestazioni di rendering che la qualità dell'immagine.

Se questa variante mostra un aumento delle prestazioni significativo, indica che si stanno usando trame senza abilitare le mappe MIP e pertanto senza sfruttare al massimo la cache delle trame.

## <a name="remarks"></a>Commenti
La generazione di mappe MIP viene forzata a ogni chiamata a `ID3D11Device::CreateTexture2D` che crea una trama di origine. In particolare, la generazione di mappe mip viene forzata quando l'oggetto D3D11_TEXTURE2D_DESC passato descrive una risorsa shader immutante, `pDesc` ad esempio:

- Il membro BindFlags presenta solo il flag D3D11_BIND_SHADER_RESOURCE impostato.

- Il membro Usage è impostato su D3D11_USAGE_DEFAULT o su D3D11_USAGE_IMMUTABLE.

- Il membro CPUAccessFlags è impostato su 0 (nessun accesso alla CPU).

- Il membro Count del membro SampleDesc è impostato su 1 (nessun anti-aliasing multicampione).

- Il membro MipLevels è impostato su 1 (nessuna mappa MIP esistente).

  Quando i dati iniziali sono forniti dall'applicazione, il formato della trama deve supportare la generazione automatica di mappe MIP, come determinato da D3D11_FORMAT_SUPPORT_MIP_AUTOGEN, a meno che il formato non sia BC1, BC2 o BC3. In caso contrario, la trama non viene modificata e non vengono generate mappe MIP quando vengono forniti i dati iniziali.

  Le mappe MIP sono state generate automaticamente per una trama, le chiamate a `ID3D11Device::CreateShaderResourceView` vengono modificate durante la riproduzione affinché usino la catena MIP durante il campionamento della trama.

## <a name="example"></a>Esempio
La variante **Generazione di mappe MIP** può essere riprodotta usando codice simile al seguente:

```cpp
D3D11_TEXTURE2D_DESC texture_description;

// ...

texture_description.MipLevels = 0; // generate a full mipchain

std::vector<D3D11_SUBRESOURCE_DATA> initial_data(num_mips);

for (auto&& mip_level : initial_data)
{
    // fill mip_level with the application-supplied initial data
}

d3d_device->CreateTexture2D(&texture_description, initial_data.data(), &texture)
```

Per creare una trama con una catena MIP completa, impostare `D3D11_TEXTURE2D_DESC::MipLevels` su 0. Il numero di livelli mip in una catena mip completa è floor(log2(n) + 1), dove n è la dimensione più grande della trama.

Ricordare che quando vengono forniti i dati iniziali a `CreateTexture2D`, è necessario fornire un oggetto D3D11_SUBRESOURCE_DATA per ogni livello MIP.

> [!NOTE]
> Se si vuole fornire contenuto di livello MIP personalizzato anziché generarlo automaticamente, è necessario creare le proprie trame tramite un editor di immagini che supporta trame con mappe MIP, caricare il file e passare i livelli MIP a `CreateTexture2D`.

## <a name="see-also"></a>Vedi anche
[Variante delle dimensioni della trama a metà trimestre](half-quarter-texture-dimensions-variant.md)
