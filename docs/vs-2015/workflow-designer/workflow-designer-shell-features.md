---
title: Funzionalità della shell di Progettazione flussi di lavoro | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c59dc8232713d4126b2c37693a1e241735eb163
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606593"
---
# <a name="workflow-designer-shell-features"></a>Caratteristiche della shell di Progettazione flussi di lavoro
[!INCLUDE[wfd1](../includes/wfd1-md.md)] è costituito da tre aree principali dell'interfaccia utente: l'area di progettazione, la barra di navigazione sopra e la shell sotto di essa. La barra di navigazione, posizionata nella parte superiore dello schermo, viene usata per visualizzare l'elenco di predecessori dell'attività radice corrente. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Procedura: utilizzare l'esplorazione di navigazione](../workflow-designer/how-to-use-breadcrumb-navigation.md). L'area della finestra di progettazione, posizionata al centro dello schermo, viene usata per creare flussi di lavoro. La shell, posizionata nella parte inferiore dello schermo, contiene alcuni pulsanti per la gestione della visualizzazione corrente.

## <a name="shell-features"></a>Caratteristiche della shell
 La shell presenta dei pulsanti sul lato destro della barra che è possibile usare per eseguire lo zoom avanti o indietro del flusso di lavoro, adattare il contenuto del flusso di lavoro alla dimensione dello schermo e mostrare o nascondere la carta panoramica. È possibile eseguire lo zoom avanti o indietro di un flusso di lavoro usando i tasti di scelta rapida CTRL++ e CTRL+ -.

## <a name="overview-map"></a>Carta panoramica
 Nella carta panoramica viene visualizzata una versione ridotta dell'intera attività alla radice della barra di navigazione corrente, inclusi tutti i relativi figli e figli espansi. Un riquadro di visualizzazione, ovvero un rettangolo con un bordo arancione, evidenzia la parte dell'attività attualmente visualizzata nell'editor. Trascinando il rettangolo attorno alla carta panoramica è possibile scorrere la finestra di progettazione del flusso di lavoro e modificare la visualizzazione dell'editor.

> [!NOTE]
> L'interfaccia utente di [!INCLUDE[wfd2](../includes/wfd2-md.md)] è virtualizzata. Gli ActivityDesigner sono sottoposti a rendering solo se necessario. Se una parte del flusso di lavoro non è stata mai disegnata nell'area della finestra di progettazione, viene visualizzata come bianca sulla carta panoramica. Il flusso di lavoro viene disegnato scorrendo su tutta la carta panoramica.

## <a name="copying-or-saving-workflows-as-images"></a>Copia o salvataggio dei flussi di lavoro come immagini
 I flussi di lavoro possono essere copiati in formato bitmap o salvati in formato bitmap o vettoriale. La copia o il salvataggio di un'immagine consente di esportare in un altro programma una visualizzazione dell'intera attività alla radice della barra di navigazione corrente, inclusi tutti i relativi figli e figli espansi.

 Per copiare come immagine, fare clic con il pulsante destro del mouse in un punto qualsiasi della finestra di progettazione e selezionare **copia come immagine**. Per salvare come immagine, fare clic con il pulsante destro del mouse in un punto qualsiasi della finestra di progettazione e selezionare **Salva come immagine**. È possibile salvare i flussi di lavoro in formato JPG, PNG, GIF o XPS. Il formato è selezionato nella finestra di dialogo **Salva con nome** nella casella di riepilogo a discesa **tipo:** nella parte inferiore della finestra.

## <a name="fonts-and-colors"></a>Tipi di carattere e colori
 I tipi di carattere usati in [!INCLUDE[wfd2](../includes/wfd2-md.md)] all'interno di [!INCLUDE[vs2010](../includes/vs2010-md.md)] dipendono dal tipo di carattere dell'ambiente. I colori visualizzati in [!INCLUDE[wfd2](../includes/wfd2-md.md)] cambiano se si usa una combinazione di colori di contrasto elevato per il tema del sistema operativo. Per rendere effettive le modifiche in [!INCLUDE[vs2010](../includes/vs2010-md.md)], è necessario riavviare [!INCLUDE[wfd2](../includes/wfd2-md.md)] dopo aver modificato le impostazioni del tipo di carattere e del colore.