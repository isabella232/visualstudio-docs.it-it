---
title: Caratteristiche della shell di Progettazione flussi di lavoro
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a6b192eae3340c6a3d84bb3ccbcce7cbf8d65b3
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816384"
---
# <a name="workflow-designer-shell-features"></a>Caratteristiche della shell di Progettazione flussi di lavoro

Progettazione flussi di lavoro è costituito da tre aree principali dell'interfaccia utente: l'area di progettazione, la barra di navigazione sopra e la shell sotto di essa. La barra di navigazione, posizionata nella parte superiore dello schermo, viene usata per visualizzare l'elenco di predecessori dell'attività radice corrente. Per altre informazioni, vedere [procedura: usare l'esplorazione di navigazione](../workflow-designer/how-to-use-breadcrumb-navigation.md). L'area della finestra di progettazione, posizionata al centro dello schermo, viene usata per creare flussi di lavoro. La shell, posizionata nella parte inferiore dello schermo, contiene alcuni pulsanti per la gestione della visualizzazione corrente.

## <a name="shell-features"></a>Caratteristiche della shell
 La shell presenta dei pulsanti sul lato destro della barra che è possibile usare per eseguire lo zoom avanti o indietro del flusso di lavoro, adattare il contenuto del flusso di lavoro alla dimensione dello schermo e mostrare o nascondere la carta panoramica. È possibile eseguire lo zoom avanti o indietro di un flusso di lavoro usando i tasti di scelta rapida CTRL++ e CTRL+ -.

## <a name="overview-map"></a>Carta panoramica
 Nella carta panoramica viene visualizzata una versione ridotta dell'intera attività alla radice della barra di navigazione corrente, inclusi tutti i relativi figli e figli espansi. Un riquadro di visualizzazione, ovvero un rettangolo con un bordo arancione, evidenzia la parte dell'attività attualmente visualizzata nell'editor. Trascinando il rettangolo attorno alla carta panoramica è possibile scorrere la finestra di progettazione del flusso di lavoro e modificare la visualizzazione dell'editor.

> [!NOTE]
> L'interfaccia utente Progettazione flussi di lavoro è virtualizzata. Gli ActivityDesigner sono sottoposti a rendering solo se necessario. Se una parte del flusso di lavoro non è stata mai disegnata nell'area della finestra di progettazione, viene visualizzata come bianca sulla carta panoramica. Il flusso di lavoro viene disegnato scorrendo su tutta la carta panoramica.

## <a name="copying-or-saving-workflows-as-images"></a>Copia o salvataggio dei flussi di lavoro come immagini
 I flussi di lavoro possono essere copiati in formato bitmap o salvati in formato bitmap o vettoriale. La copia o il salvataggio di un'immagine consente di esportare in un altro programma una visualizzazione dell'intera attività alla radice della barra di navigazione corrente, inclusi tutti i relativi figli e figli espansi.

 Per copiare come immagine, fare clic con il pulsante destro del mouse in un punto qualsiasi della finestra di progettazione e selezionare **copia come immagine**. Per salvare come immagine, fare clic con il pulsante destro del mouse in un punto qualsiasi della finestra di progettazione e selezionare **Salva come immagine**. È possibile salvare i flussi di lavoro in formato JPG, PNG, GIF o XPS. Il formato è selezionato nella finestra di dialogo **Salva con nome** nella casella di riepilogo a discesa **tipo:** nella parte inferiore della finestra.

## <a name="fonts-and-colors"></a>Tipi di carattere e colori

I tipi di carattere usati in Progettazione flussi di lavoro all'interno di Visual Studio sono controllati dal tipo di carattere ambiente. I colori visualizzati in Progettazione flussi di lavoro cambiano se si usa una combinazione di colori a contrasto elevato per il tema del sistema operativo. È necessario riavviare Visual Studio dopo avere apportato una modifica alle impostazioni del tipo di carattere o del colore prima che le modifiche abbiano effetto in Progettazione flussi di lavoro.