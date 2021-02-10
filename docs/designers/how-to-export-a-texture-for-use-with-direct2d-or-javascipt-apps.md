---
title: Esportare una trama per le app Direct2D e JavaScript
description: La pipeline di contenuti immagine genera trame compatibili con il rendering interno Direct2D da usare nelle app Direct2D e nelle app UWP create con JavaScript.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 84fadd786e7a1bf978ec4df919b691031c316a4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930954"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascript-apps"></a>Procedura: esportare una trama da usare con app Direct2D o JavaScript

La pipeline di contenuti immagine può generare trame compatibili con le convenzioni di rendering interne di Direct2D. Le trame di questo genere sono adatte alle app che usano Direct2D e alle app UWP create mediante JavaScript.

Questo documento illustra queste attività:

- Configurazione dell'immagine di origine che deve essere elaborata dalla pipeline di contenuti immagine.

- Configurazione della pipeline di contenuti immagine per generare una trama che è possibile usare in un'app JavaScript o Direct2D.

  - Generare un file con *estensione DDS* compresso a blocchi.

  - Generare il valore alfa premoltiplicato.

  - Disabilitare la generazione di mipmap.

## <a name="rendering-conventions-in-direct2d"></a>Convenzioni di rendering in Direct2D

Le trame usate nel contesto di Direct2D devono essere conformi alle convenzioni di rendering interne di Direct2D seguenti:

- Direct2D implementa la trasparenza e la traslucidità usando il valore alfa premoltiplicato. Le trame usate con Direct2D devono contenere i valori alfa premoltiplicati, anche se la trama non usa la trasparenza o la traslucidità. Per altre informazioni sull'alfa premoltiplicato, vedere [procedura: esportare una trama con alfa premoltiplicato](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).

- La trama deve essere fornita in formato *DDS* , usando uno di questi formati di compressione a blocchi:

  - Compressione BC1_UNORM

  - Compressione BC2_UNORM

  - Compressione BC3_UNORM

- Le mipmap non sono supportate.

### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Per creare una trama compatibile con le convenzioni di rendering Direct2D

1. Iniziare con una trama di base. Caricare un'immagine esistente o crearne una nuova, come descritto in [procedura: creare una trama di base](../designers/how-to-create-a-basic-texture.md). Per supportare la compressione a blocchi in formato *DDS* , specificare una trama con larghezza e altezza multipli di quattro, ad esempio, 100x100, 128x128 o 256x192. Poiché il mapping MIP non è supportato, la trama non deve essere quadrata e le dimensioni non devono essere una potenza di due.

2. Configurare il file di trama in modo che venga elaborato dalla pipeline di contenuti immagine. In **Esplora soluzioni** aprire il menu di scelta rapida per il file di trama appena creato e quindi scegliere **Proprietà**. Nella pagina **proprietà di configurazione**  >  **generale** impostare la proprietà **tipo di elemento** su **pipeline contenuto immagine**. Assicurarsi che la proprietà **Contenuto** sia impostata su **Sì** e che l'opzione **Exclude From Build** (Escludi da compilazione) sia impostata su **No**, quindi scegliere il pulsante **Applica**. Viene visualizzata la pagina delle proprietà di configurazione **Image Content Pipeline** (Pipeline di contenuti immagine).

3. Impostare il formato di output su uno dei formati compressi a blocchi. Nella   >  pagina generale della **pipeline di contenuti immagine** delle proprietà  >   di configurazione impostare la proprietà **Comprimi** su **BC3_UNORM Compression (/Compress: BC3_UNORM)**. È possibile scegliere uno degli altri formati BC1, BC2 o BC3, in base alle specifiche esigenze. Direct2D attualmente non supporta le trame BC4, BC5, BC6 o BC7. Per altre informazioni sui diversi formati BC, vedere [compressione dei blocchi (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-block-compression).

   > [!NOTE]
   > Il formato di compressione specificato determina il formato del file generato dalla pipeline di contenuti immagine. Questo si differenzia dalla proprietà **Formato** dell'immagine di origine nell'editor di immagini, che determina il formato del file di immagine di origine così com'è archiviato su disco, ovvero il *formato di lavoro*. In genere, non è consigliabile usare un formato di lavoro compresso.

4. Configurare la pipeline di contenuti immagine in modo da generare output che usa il valore alfa premoltiplicato. Nella pagina generale della pipeline di contenuti immagine delle **proprietà di configurazione**  >    >   impostare la proprietà **Converti in formato alfa pre-moltiplicato** su **Sì (/generatepremultipliedalpha)**.

5. Configurare la pipeline di contenuti immagine in modo che non generi mipmap. Nella   >  pagina generale della **pipeline di contenuti immagine** delle proprietà di configurazione  >   impostare la proprietà **Genera MIP** su **No**.

6. Fare clic su **OK** .

   Quando si compila il progetto, la pipeline di contenuti immagine converte l'immagine di origine dal formato di lavoro al formato di output specificato, generando anche valori alfa premoltiplicato. Il risultato viene copiato nella directory di output del progetto.
