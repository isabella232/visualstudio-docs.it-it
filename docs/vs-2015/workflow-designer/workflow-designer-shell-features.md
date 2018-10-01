---
title: Funzionalità della Shell della finestra di progettazione del flusso di lavoro | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: e0ac119908003efdbdbda4c01bce18de4a5f0faa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526958"
---
# <a name="workflow-designer-shell-features"></a>Funzionalità della shell di Progettazione flussi di lavoro
[!INCLUDE[wfd1](../includes/wfd1-md.md)] è formato da tre principali aree dell'interfaccia utente, ovvero l'area della finestra di progettazione, la barra di navigazione al di sopra di essa e la shell al di sotto di essa. La barra di navigazione, posizionata nella parte superiore dello schermo, viene usata per visualizzare l'elenco di predecessori dell'attività radice corrente. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Procedura: usare dello spostamento Breadcrumb](../workflow-designer/how-to-use-breadcrumb-navigation.md). L'area della finestra di progettazione, posizionata al centro dello schermo, viene usata per creare flussi di lavoro. La shell, posizionata nella parte inferiore dello schermo, contiene alcuni pulsanti per la gestione della visualizzazione corrente.  
  
## <a name="shell-features"></a>Caratteristiche della shell  
 La shell presenta dei pulsanti sul lato destro della barra che è possibile usare per eseguire lo zoom avanti o indietro del flusso di lavoro, adattare il contenuto del flusso di lavoro alla dimensione dello schermo e mostrare o nascondere la carta panoramica. È possibile eseguire lo zoom avanti o indietro di un flusso di lavoro usando i tasti di scelta rapida CTRL++ e CTRL+ -.  
  
## <a name="overview-map"></a>Carta panoramica  
 Nella carta panoramica viene visualizzata una versione ridotta dell'intera attività alla radice della barra di navigazione corrente, inclusi tutti i relativi figli e figli espansi. Un riquadro di visualizzazione, ovvero un rettangolo con un bordo arancione, evidenzia la parte dell'attività attualmente visualizzata nell'editor. Trascinando il rettangolo attorno alla carta panoramica è possibile scorrere la finestra di progettazione del flusso di lavoro e modificare la visualizzazione dell'editor.  
  
> [!NOTE]
>  L'interfaccia utente di [!INCLUDE[wfd2](../includes/wfd2-md.md)] è virtualizzata. Gli ActivityDesigner sono sottoposti a rendering solo se necessario. Se una parte del flusso di lavoro non è stata mai disegnata nell'area della finestra di progettazione, viene visualizzata come bianca sulla carta panoramica. Il flusso di lavoro viene disegnato scorrendo su tutta la carta panoramica.  
  
## <a name="copying-or-saving-workflows-as-images"></a>Copia o salvataggio dei flussi di lavoro come immagini  
 I flussi di lavoro possono essere copiati in formato bitmap o salvati in formato bitmap o vettoriale. La copia o il salvataggio di un'immagine consente di esportare in un altro programma una visualizzazione dell'intera attività alla radice della barra di navigazione corrente, inclusi tutti i relativi figli e figli espansi.  
  
 Per copiare come immagine, fare doppio clic su un punto qualsiasi nella finestra di progettazione e selezionare **copia come immagine**. Per salvare come immagine, fare doppio clic su un punto qualsiasi nella finestra di progettazione e selezionare **Salva come immagine**. È possibile salvare i flussi di lavoro in formato JPG, PNG, GIF o XPS. Il formato è selezionato nella **Salva con nome** nella finestra di dialogo il **Salva come tipo:** casella nella parte inferiore della finestra a discesa.  
  
## <a name="fonts-and-colors"></a>Tipi di carattere e colori  
 I tipi di carattere usati in [!INCLUDE[wfd2](../includes/wfd2-md.md)] all'interno di [!INCLUDE[vs2010](../includes/vs2010-md.md)] dipendono dal tipo di carattere dell'ambiente. I colori visualizzati in [!INCLUDE[wfd2](../includes/wfd2-md.md)] cambiano se si usa una combinazione di colori di contrasto elevato per il tema del sistema operativo. Per rendere effettive le modifiche in [!INCLUDE[vs2010](../includes/vs2010-md.md)], è necessario riavviare [!INCLUDE[wfd2](../includes/wfd2-md.md)] dopo aver modificato le impostazioni del tipo di carattere e del colore.