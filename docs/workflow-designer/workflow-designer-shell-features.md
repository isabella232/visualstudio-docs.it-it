---
title: Funzionalità della shell di Progettazione flussi di lavoro
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4519be8ec5c5d4ba8a611df1880ae770a83cf981
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919469"
---
# <a name="workflow-designer-shell-features"></a>Funzionalità della shell di Progettazione flussi di lavoro

Finestra di progettazione del flusso di lavoro è costituito da tre principali aree dell'interfaccia utente: l'area di progettazione, la barra di navigazione superiore e la shell di sotto di essa. La barra di navigazione, posizionata nella parte superiore dello schermo, viene usata per visualizzare l'elenco di predecessori dell'attività radice corrente. Per altre informazioni, vedere [Procedura: Usare la struttura di spostamento](../workflow-designer/how-to-use-breadcrumb-navigation.md). L'area della finestra di progettazione, posizionata al centro dello schermo, viene usata per creare flussi di lavoro. La shell, posizionata nella parte inferiore dello schermo, contiene alcuni pulsanti per la gestione della visualizzazione corrente.

## <a name="shell-features"></a>Caratteristiche della shell
 La shell presenta dei pulsanti sul lato destro della barra che è possibile usare per eseguire lo zoom avanti o indietro del flusso di lavoro, adattare il contenuto del flusso di lavoro alla dimensione dello schermo e mostrare o nascondere la carta panoramica. È possibile eseguire lo zoom avanti o indietro di un flusso di lavoro usando i tasti di scelta rapida CTRL++ e CTRL+ -.

## <a name="overview-map"></a>Carta panoramica
 Nella carta panoramica viene visualizzata una versione ridotta dell'intera attività alla radice della barra di navigazione corrente, inclusi tutti i relativi figli e figli espansi. Un riquadro di visualizzazione, ovvero un rettangolo con un bordo arancione, evidenzia la parte dell'attività attualmente visualizzata nell'editor. Trascinando il rettangolo attorno alla carta panoramica è possibile scorrere la finestra di progettazione del flusso di lavoro e modificare la visualizzazione dell'editor.

> [!NOTE]
> L'interfaccia utente di progettazione del flusso di lavoro viene virtualizzato. Gli ActivityDesigner sono sottoposti a rendering solo se necessario. Se una parte del flusso di lavoro non è stata mai disegnata nell'area della finestra di progettazione, viene visualizzata come bianca sulla carta panoramica. Il flusso di lavoro viene disegnato scorrendo su tutta la carta panoramica.

## <a name="copying-or-saving-workflows-as-images"></a>Copia o salvataggio dei flussi di lavoro come immagini
 I flussi di lavoro possono essere copiati in formato bitmap o salvati in formato bitmap o vettoriale. La copia o il salvataggio di un'immagine consente di esportare in un altro programma una visualizzazione dell'intera attività alla radice della barra di navigazione corrente, inclusi tutti i relativi figli e figli espansi.

 Per copiare come immagine, fare doppio clic su un punto qualsiasi nella finestra di progettazione e selezionare **copia come immagine**. Per salvare come immagine, fare doppio clic su un punto qualsiasi nella finestra di progettazione e selezionare **Salva come immagine**. È possibile salvare i flussi di lavoro in formato JPG, PNG, GIF o XPS. Il formato è selezionato nella **Salva con nome** nella finestra di dialogo il **Salva come tipo:** casella nella parte inferiore della finestra a discesa.

## <a name="fonts-and-colors"></a>Tipi di carattere e colori

I tipi di carattere utilizzati nella finestra di progettazione del flusso di lavoro all'interno di Visual Studio sono controllate dal tipo di carattere ambiente. Se si usa una combinazione di colori a contrasto elevato per il tema del sistema operativo, modificare i colori visualizzati nella finestra di progettazione del flusso di lavoro. È necessario riavviare Visual Studio dopo aver apportato una modifica alle impostazioni del tipo di carattere o colore affinché le modifiche abbiano effetto nella finestra di progettazione del flusso di lavoro.