---
title: 'Procedura: Esportare una trama con valori alfa premoltiplicati | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a68f6c58ad7e497dfc0e91e92f2cf40e4bd8d992
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897537"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Procedura: esportare una trama con alfa premoltiplicati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La pipeline di contenuti immagine può generare trame con valori alfa premoltiplicati da un'immagine di origine. Queste trame possono essere più semplici da usare e più solide delle trame che non contengono valori alfa premoltiplicati.  
  
 Questo documento illustra le attività seguenti:  
  
-   Configurazione dell'immagine di origine che deve essere elaborata dalla pipeline di contenuti immagine.  
  
-   Configurazione della pipeline di contenuti immagine per generare valori alfa premoltiplicati.  
  
## <a name="premultiplied-alpha"></a>Valori alfa premoltiplicati  
 Valori alfa premoltiplicati offrono diversi vantaggi rispetto convenzionali non premoltiplicati, perché rappresenta meglio l'interazione reale della luce con materiali fisici separando il contributo di colore del texel (il colore che viene aggiunto per il scena) dalla traslucidità (la quantità di colore sottostante consentita). Alcuni dei vantaggi dell'uso di valori alfa premoltiplicati sono:  
  
-   La fusione con valori alfa premoltiplicati è un'operazione associativa. Il risultato della fusione di più trame traslucide è simile, indipendentemente dall'ordine in cui vengono fuse le trame.  
  
-   Grazie alla natura associativa della fusione con valori alfa premoltiplicati, il rendering a più passaggi degli oggetti traslucidi risulta semplificato.  
  
-   Tramite l'uso di valori alfa premoltiplicati, la fusione correttiva pura (impostando alfa su zero) e la fusione interpolata linearmente possono essere realizzate contemporaneamente. Ad esempio, in un sistema di particelle, una particella fuoco fusa può diventare una particella fumo semitrasparente che viene sfumata utilizzando l'interpolazione lineare. Senza valori alfa premoltiplicati, sarebbe necessario disegnare le particelle Fuoco separatamente dalle particelle Fumo e modificare lo stato di rendering tra le chiamate di disegno.  
  
-   Le trame che usano valori alfa premoltiplicati vengono compresse con qualità più elevata rispetto a quelli che non e non presentano bordi aureola, o "effetti", che può verificarsi quando si fondono trame che non usano valori alfa premoltiplicati.  
  
#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Per creare una trama che usa valori alfa premoltiplicati  
  
1. Iniziare con una trama di base. Caricare un file d'immagine esistente oppure crearne uno nuovo, come illustrato in [Procedura: Creare una trama di base](../designers/how-to-create-a-basic-texture.md).  
  
2. Configurare il file di trama in modo che venga elaborato dalla Pipeline di contenuti immagine. In **Esplora soluzioni**, aprire il menu di scelta rapida del file della trama e scegliere **Proprietà**. Nella pagina **Proprietà di configurazione**, **Generale**, impostare la proprietà **Tipo di elemento** su **Image Content Pipeline** (Pipeline di contenuti immagine). Assicurarsi che la proprietà **Contenuto** sia impostata su **Sì** e che l'opzione **Exclude From Build** (Escludi da compilazione) sia impostata su **No**, quindi scegliere il pulsante **Applica**. Viene visualizzata la pagina delle proprietà di configurazione **Image Content Pipeline** (Pipeline di contenuti immagine).  
  
3. Configurare la pipeline di contenuti immagine per generare valori alfa premoltiplicati. Nella pagina **Proprietà di configurazione**, **Image Content Pipeline** (Pipeline di contenuti immagine), **Generale**, impostare la proprietà **Convert to pre-multiplied alpha format** (Converti in formato alfa premoltiplicato) su **Sì (/generatepremultipliedalpha)**.  
  
4. Fare clic sul pulsante **OK** .  
  
   Quando si compila il progetto, la Pipeline di contenuti immagine converte l'immagine di origine dal formato di lavoro al formato di output specificato, inclusa la conversione dell'immagine in formato alfa premoltiplicato, e il risultato viene copiato l'output del progetto Directory.



