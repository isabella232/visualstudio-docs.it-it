---
title: 'Procedura: Esportare uno shader'
description: Informazioni su come usare la finestra di progettazione shader per esportare uno shader del linguaggio di Graph shader diretto per poterlo usare nell'app.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da09feffc4d2f804660f02dbda6055bf59099500
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134302"
---
# <a name="how-to-export-a-shader"></a>Procedura: Esportare uno shader

Questo articolo illustra come usare la **finestra di progettazione shader** per esportare uno shader DGSL (Directed Graph Shader Language) da usare nell'app.

## <a name="export-a-shader"></a>Esportare uno shader

Dopo aver creato uno shader tramite la finestra di progettazione shader, prima di poterlo usare nell'app è necessario esportarlo in un formato supportato dall'API di grafica in uso. È possibile esportare uno shader in modi diversi, in base alle proprie esigenze.

1. In Visual Studio aprire un file **Visual Shader Graph (.dgsl)** .

     Se non si ha un file **Visual Shader Graph (.dgsl)** da aprire, crearne uno come descritto in [Procedura: Creare uno shader con colore di base](../designers/how-to-create-a-basic-color-shader.md).

2. Nella barra degli strumenti **Progettazione shader** scegliere **Avanzate** > **Esporta** > **Esporta come** . Viene visualizzata la finestra di dialogo **Esporta shader** .

3. Nell'elenco a discesa **Salva come** scegliere il formato in cui si vuole esportare il file.

     Di seguito sono illustrati i formati che è possibile scegliere:

     **Pixel Shader HLSL (\*.hlsl)** Esporta lo shader come codice sorgente High Level Shader Language (HLSL). Questa opzione consente di modificare lo shader in un secondo momento, anche dopo essere stato distribuito in un'app. Offre quindi l'opportunità di eseguire il debug e correggere il codice in base ai problemi riscontrati dagli utenti finali, ma al tempo stesso rende anche più facile per un utente modificare lo shader in modi indesiderati, ad esempio per ottenere un vantaggio sleale in un gioco competitivo. È inoltre possibile aumentare il tempo di caricamento dello shader.

     **Pixel Shader compilato (\*.cso)** Esporta lo shader come bytecode HLSL. Questa opzione consente di modificare lo shader in un secondo momento, anche dopo essere stato distribuito in un'app. Offre quindi l'opportunità di eseguire il debug e correggere il codice in base ai problemi riscontrati dagli utenti finali ma, poiché lo shader è precompilato, non comporta un sovraccarico di runtime aggiuntivo quando lo shader viene caricato dall'app. Utenti sufficientemente esperti possono comunque modificare lo shader in modi indesiderati, ma la compilazione dello shader rende questa operazione molto più difficile.

     **Intestazione C++ (\*.h)** Esporta lo shader come intestazione di tipo C che definisce una matrice di byte contenente il bytecode HLSL. Questa opzione allunga i tempi necessari per eseguire il debug e correggere il codice in base ai problemi riscontrati dagli utenti finali, perché per testare la correzione è necessario ricompilare l'app. Questa opzione rende particolarmente difficile, seppure non impossibile, modificare lo shader dopo essere stato distribuito in un'app. Eventuali utenti che intendano modificare lo shader in modi indesiderati riscontreranno quindi grandi difficoltà.

4. Nella casella combinata **Nome file** specificare un nome per lo shader esportato e scegliere il pulsante **Salva** .

## <a name="see-also"></a>Vedere anche

- [Procedura: creare uno shader con colore di base](../designers/how-to-create-a-basic-color-shader.md)
- [Finestra di progettazione shader](../designers/shader-designer.md)
