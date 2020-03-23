---
title: 'Procedura: esportare una trama che contiene mipmap'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71d570e6dc7544911ebe2bb279aafb3a07620cbc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589409"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Procedura: Esportare una trama che contiene mipmap

La pipeline di contenuti immagine può generare mipmap da un'immagine di origine come parte della fase di compilazione del progetto. Per ottenere alcuni effetti, a volte è necessario specificare manualmente il contenuto dell'immagine di ogni livello MIP. Quando non è necessario specificare manualmente il contenuto dell'immagine di ogni livello MIP, la generazione di mipmap in fase di compilazione garantisce che il contenuto mipmap non diventi mai obsoleto. Elimina inoltre i costi di prestazioni per la generazione di mipmap in fase di esecuzione.

Questo articolo riguarda:

- Configurazione dell'immagine di origine che deve essere elaborata dalla pipeline di contenuti immagine.

- Configurazione di pipeline di contenuti immagine per generare mipmap.

## <a name="export-mipmaps"></a>Esportare mipmap

La creazione di mipmap offre un livello di dettaglio automatico sullo spazio della schermata per aree con trame in giochi 3D o in app. Migliora le prestazioni di rendering di un gioco o di un'app pre-elaborando versioni a campionamento ridotto di una trama, in modo che l'intera trama non debba essere elaborata ogni volta che viene campionata.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Per esportare una trama che contiene mipmap

1. Iniziare con una trama di base. Caricare un file d'immagine esistente oppure crearne uno nuovo, come illustrato in [Procedura: Creare una trama di base](../designers/how-to-create-a-basic-texture.md). Per supportare le mipmap, specificare una trama la cui larghezza e altezza corrispondano a un valore esponenziale con base due, ad esempio, 64 x 64, 256 x 256 o 512 x 512.

2. Configurare il file di trama appena creato in modo che venga elaborato dalla pipeline di contenuti immagine. In **Esplora soluzioni** aprire il menu di scelta rapida per il file di trama creato e quindi scegliere **Proprietà**. Nella pagina**Informazioni generali** **proprietà** > di configurazione impostare la proprietà **Tipo di elemento** su Pipeline contenuto **immagine**. Assicurarsi che la proprietà **Contenuto** sia impostata su **Sì** e che l'opzione **Exclude From Build** (Escludi da build) sia impostata su **No**. Selezionare **Applica**.

   Viene visualizzata la pagina delle proprietà di configurazione **Image Content Pipeline** (Pipeline di contenuti immagine).

3. Configurare la pipeline di contenuti immagine per generare mipmap. Nella**pagina** Generale**pipeline** > contenuto immagine delle proprietà > di **configurazione**impostare la proprietà **Genera Mips** su **Sì (/generatemips)**.

4. Selezionare **OK**.

Quando si compila il progetto, la pipeline di contenuti immagine converte l'immagine di origine dal formato di lavoro al formato di output specificato, includendo i livelli MIP. Il risultato viene copiato nella directory di output del progetto.
