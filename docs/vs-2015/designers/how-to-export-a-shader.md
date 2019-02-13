---
title: 'Procedura: Esportare uno Shader | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3858d10d685e104617a6de7b5c11c87cfee1872d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802793"
---
# <a name="how-to-export-a-shader"></a>Procedura: Esportare uno shader
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo documento illustra come usare la finestra di progettazione shader per esportare uno shader DGSL (Directed Graph Shader Language) da usare nell'app.  
  
 Questo documento illustra questa attività:  
  
-   Esportazione di uno shader  
  
## <a name="exporting-a-shader"></a>Esportazione di uno shader  
 Dopo aver creato uno shader tramite la finestra di progettazione shader, prima di poterlo usare nell'app è necessario esportarlo in un formato supportato dall'API di grafica in uso. È possibile esportare uno shader in modi diversi, in base alle proprie esigenze.  
  
#### <a name="to-export-a-shader"></a>Per esportare uno shader  
  
1.  In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aprire un file **Visual Shader Graph (.dgsl)**.  
  
     Se non ha un file **Visual Shader Graph (.dgsl)** da aprire, crearne uno come descritto in [Procedura: Creare uno shader con colore di base](../designers/how-to-create-a-basic-color-shader.md).  
  
2.  Nella barra degli strumenti **Progettazione shader** scegliere **Avanzate**, **Esporta**, **Esporta come**. Viene visualizzata la finestra di dialogo **Esporta shader**.  
  
3.  Nell'elenco a discesa **Salva come** scegliere il formato in cui si vuole esportare il file.  
  
     Di seguito sono illustrati i formati che è possibile scegliere:  
  
     **Pixel shader HLSL (\*.hlsl)**  
     Esporta lo shader come codice sorgente High Level Shader Language (HLSL). Questa opzione consente di modificare lo shader in un secondo momento, anche dopo essere stato distribuito in un'app. Offre quindi l'opportunità di eseguire il debug e correggere il codice in base ai problemi riscontrati dagli utenti finali, ma al tempo stesso rende anche più facile per un utente modificare lo shader in modi indesiderati, ad esempio per ottenere un vantaggio sleale in un gioco competitivo. È inoltre possibile aumentare il tempo di caricamento dello shader.  
  
     **Pixel shader compilato (\*.cso)**  
     Esporta lo shader come bytecode HLSL. Questa opzione consente di modificare lo shader in un secondo momento, anche dopo essere stato distribuito in un'app. Offre quindi l'opportunità di eseguire il debug e correggere il codice in base ai problemi riscontrati dagli utenti finali ma, poiché lo shader è precompilato, non comporta un sovraccarico di runtime aggiuntivo quando lo shader viene caricato dall'app. Utenti sufficientemente esperti possono comunque modificare lo shader in modi indesiderati, ma la compilazione dello shader rende questa operazione molto più difficile.  
  
     **Intestazione C++ (\*.h)**  
     Esporta lo shader come intestazione di tipo C che definisce una matrice di byte contenente il bytecode HLSL. Questa opzione allunga i tempi necessari per eseguire il debug e correggere il codice in base ai problemi riscontrati dagli utenti finali, perché per testare la correzione è necessario ricompilare l'app. Questa opzione rende particolarmente difficile, seppure non impossibile, modificare lo shader dopo essere stato distribuito in un'app. Eventuali utenti che intendano modificare lo shader in modi indesiderati riscontreranno quindi grandi difficoltà.  
  
4.  Nella casella combinata **Nome file** specificare un nome per lo shader esportato e scegliere il pulsante **Salva**.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare uno shader con colore di base](../designers/how-to-create-a-basic-color-shader.md)   
 [Finestra di progettazione shader](../designers/shader-designer.md)
