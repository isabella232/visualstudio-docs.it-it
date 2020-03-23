---
title: Esportare una trama per applicazioni Direct2D e JavaScript
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d163aafa8b00ce1d59b1fc7b597ab5ca535a1ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "72635503"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascript-apps"></a>Procedura: Esportare una trama da usare con le app Direct2D o JavaScriptHow to: Export a texture for use with Direct2D or JavaScript apps

La pipeline di contenuti immagine può generare trame compatibili con le convenzioni di rendering interne di Direct2D. Le trame di questo genere sono adatte alle app che usano Direct2D e alle app UWP create mediante JavaScript.

Questo documento illustra queste attività:

- Configurazione dell'immagine di origine che deve essere elaborata dalla pipeline di contenuti immagine.

- Configurazione della pipeline di contenuti immagine per generare una trama che è possibile usare in un'app JavaScript o Direct2D.

  - Generare un file *.dds* compresso a blocchi.

  - Generare il valore alfa premoltiplicato.

  - Disabilitare la generazione di mipmap.

## <a name="rendering-conventions-in-direct2d"></a>Convenzioni di rendering in Direct2D

Le trame usate nel contesto di Direct2D devono essere conformi alle convenzioni di rendering interne di Direct2D seguenti:

- Direct2D implementa la trasparenza e la traslucidità usando il valore alfa premoltiplicato. Le trame usate con Direct2D devono contenere i valori alfa premoltiplicati, anche se la trama non usa la trasparenza o la traslucidità. Per ulteriori informazioni sull'alfa premoltiplicato, consultate [Procedura: Esportare una trama con Alfa premoltiplicato](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).

- La texture deve essere fornita in formato *.dds,* utilizzando uno di questi formati di compressione a blocchi:

  - Compressione BC1_UNORM

  - Compressione BC2_UNORM

  - Compressione BC3_UNORM

- Le mipmap non sono supportate.

### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Per creare una trama compatibile con le convenzioni di rendering Direct2D

1. Iniziare con una trama di base. Caricare un'immagine esistente o crearne una nuova come descritto in [Procedura: Creare una trama di base.](../designers/how-to-create-a-basic-texture.md) Per supportare la compressione a blocchi in formato *.dds,* specificare una trama con larghezza e altezza di dimensioni multiple di quattro, ad esempio 100x100, 128x128 o 256x192. Poiché il mapping MIP non è supportato, la trama non deve essere quadrata e le dimensioni non devono essere una potenza di due.

2. Configurare il file di trama in modo che venga elaborato dalla pipeline di contenuti immagine. In **Esplora soluzioni** aprire il menu di scelta rapida per il file di trama appena creato e quindi scegliere **Proprietà**. Nella pagina**Informazioni generali** **proprietà** > di configurazione impostare la proprietà **Tipo di elemento** su Pipeline contenuto **immagine**. Assicurarsi che la proprietà **Contenuto** sia impostata su **Sì** e che l'opzione **Exclude From Build** (Escludi da compilazione) sia impostata su **No**, quindi scegliere il pulsante **Applica**. Viene visualizzata la pagina delle proprietà di configurazione **Image Content Pipeline** (Pipeline di contenuti immagine).

3. Impostare il formato di output su uno dei formati compressi a blocchi. Nella**pagina** **Informazioni di** > configurazione generale**pipeline** > contenuto immagine impostare la proprietà **Compress** su **compressione BC3_UNORM (/compress:BC3_UNORM)**. È possibile scegliere uno degli altri formati BC1, BC2 o BC3, in base alle specifiche esigenze. Direct2D attualmente non supporta le trame BC4, BC5, BC6 o BC7. Per ulteriori informazioni sui diversi formati BC, vedere [Compressione a blocchi (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-block-compression).

   > [!NOTE]
   > Il formato di compressione specificato determina il formato del file generato dalla pipeline di contenuti immagine. Questo si differenzia dalla proprietà **Formato** dell'immagine di origine nell'editor di immagini, che determina il formato del file di immagine di origine così com'è archiviato su disco, ovvero il *formato di lavoro*. In genere, non è consigliabile usare un formato di lavoro compresso.

4. Configurare la pipeline di contenuti immagine in modo da generare output che usa il valore alfa premoltiplicato. Nella**pagina** **Informazioni** > di configurazione generale**pipeline** > contenuto immagine impostare la proprietà **Converti in formato alfa premoltiplicato** su **Sì (/generatepremultipliedalpha)**.

5. Configurare la pipeline di contenuti immagine in modo che non generi mipmap. Nella**pagina** Generale**pipeline** > contenuto immagine delle proprietà > di **configurazione**impostare la proprietà **Genera Mips** su **No**.

6. Fare clic su **OK** .

   Quando si compila il progetto, la pipeline di contenuti immagine converte l'immagine di origine dal formato di lavoro al formato di output specificato, generando anche valori alfa premoltiplicato. Il risultato viene copiato nella directory di output del progetto.
