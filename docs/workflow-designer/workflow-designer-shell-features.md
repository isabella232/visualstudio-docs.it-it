---
title: Funzionalità della shell di Progettazione flussi di lavoro
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4644d9bfa336b85b9ad124751db4f3fb0417475c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973708"
---
# <a name="workflow-designer-shell-features"></a>Funzionalità della shell di Progettazione flussi di lavoro

Progettazione del flusso di lavoro di Windows è composto da tre principali aree dell'interfaccia utente: area di progettazione, la barra di navigazione superiore e la shell sotto di essa. La barra di navigazione, posizionata nella parte superiore dello schermo, viene usata per visualizzare l'elenco di predecessori dell'attività radice corrente. Per ulteriori informazioni, vedere [procedura: utilizzare la struttura di spostamento](../workflow-designer/how-to-use-breadcrumb-navigation.md). L'area della finestra di progettazione, posizionata al centro dello schermo, viene usata per creare flussi di lavoro. La shell, posizionata nella parte inferiore dello schermo, contiene alcuni pulsanti per la gestione della visualizzazione corrente.

## <a name="shell-features"></a>Caratteristiche della shell
 La shell presenta dei pulsanti sul lato destro della barra che è possibile usare per eseguire lo zoom avanti o indietro del flusso di lavoro, adattare il contenuto del flusso di lavoro alla dimensione dello schermo e mostrare o nascondere la carta panoramica. È possibile eseguire lo zoom avanti o indietro di un flusso di lavoro usando i tasti di scelta rapida CTRL++ e CTRL+ -.

## <a name="overview-map"></a>Carta panoramica
 Nella carta panoramica viene visualizzata una versione ridotta dell'intera attività alla radice della barra di navigazione corrente, inclusi tutti i relativi figli e figli espansi. Un riquadro di visualizzazione, ovvero un rettangolo con un bordo arancione, evidenzia la parte dell'attività attualmente visualizzata nell'editor. Trascinando il rettangolo attorno alla carta panoramica è possibile scorrere la finestra di progettazione del flusso di lavoro e modificare la visualizzazione dell'editor.

> [!NOTE]
> L'interfaccia utente di progettazione flussi di lavoro è virtualizzato. Gli ActivityDesigner sono sottoposti a rendering solo se necessario. Se una parte del flusso di lavoro non è stata mai disegnata nell'area della finestra di progettazione, viene visualizzata come bianca sulla carta panoramica. Il flusso di lavoro viene disegnato scorrendo su tutta la carta panoramica.

## <a name="copying-or-saving-workflows-as-images"></a>Copia o salvataggio dei flussi di lavoro come immagini
 I flussi di lavoro possono essere copiati in formato bitmap o salvati in formato bitmap o vettoriale. La copia o il salvataggio di un'immagine consente di esportare in un altro programma una visualizzazione dell'intera attività alla radice della barra di navigazione corrente, inclusi tutti i relativi figli e figli espansi.

 Per copiare come immagine, fare clic nella finestra di progettazione e selezionare **copia come immagine**. Per salvare come immagine, fare clic nella finestra di progettazione e selezionare **Salva come immagine**. È possibile salvare i flussi di lavoro in formato JPG, PNG, GIF o XPS. Il formato viene selezionato nel **Salva con nome** nella finestra di dialogo di **Salva come:** nella parte inferiore della finestra casella a discesa.

## <a name="fonts-and-colors"></a>Tipi di carattere e colori

I tipi di carattere utilizzati nella finestra di progettazione del flusso di lavoro all'interno di Visual Studio 2010 vengono controllate dal tipo di carattere ambiente. I colori visualizzati nella finestra di progettazione del flusso di lavoro modificare se si utilizza una combinazione di colori a contrasto elevato per il tema del sistema operativo. Dopo aver apportato una modifica alle impostazioni del tipo di carattere o colore affinché le modifiche abbiano effetto nella finestra di progettazione del flusso di lavoro, è necessario riavviare Visual Studio 2010.