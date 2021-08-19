---
title: Stato della grafica | Microsoft Docs
description: Risolvere i problemi di rendering tramite la visualizzazione dello stato della grafica per ogni chiamata di disegno. Le parti dello stato modificate rispetto alla chiamata precedente sono evidenziate.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.statewindow
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a33f50be257c3e484d99ca6851d125f414edb424
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138900"
---
# <a name="graphics-state"></a>Stato grafica
La finestra Stato in Diagnostica grafica di Visual Studio consente di comprendere lo stato di grafica attivo al momento dell'evento corrente, ad esempio una chiamata di disegno.

## <a name="understanding-the-state-window"></a>Informazioni sulla finestra Stato
 La finestra Stato raccoglie gli stati che influiscono sul rendering e li visualizza in modo gerarchico, in un'unica posizione. In base alla versione di Direct3D usata dall'app, le informazioni presentate nella finestra di stato potrebbero essere diverse.

### <a name="state-views"></a>Visualizzazioni stato
 Si può visualizzare la tabella di stato in vari modi:

|Visualizzazione|Descrizione|
|----------|-----------------|
|Visualizzazione stato di input API|Questa visualizzazione presenta lo stato con un layout simile a quello degli oggetti Direct3D che compongono lo stato.|
|Visualizzazione stato di input logico|Presenta lo stato in una visualizzazione logica che non rispecchia il layout degli oggetti Direct3D che compongono lo stato.|
|Visualizzazione stato bloccato|Anziché in una gerarchia, la visualizzazione stato bloccato presenta gli elementi di stato bloccati in un elenco semplice con nomi completi. Questa visualizzazione consente di vedere molti elementi da aggregazioni di stati diverse in un numero limitato di righe.|

##### <a name="to-change-the-state-view"></a>Per modificare la visualizzazione stato

- Nell'angolo superiore sinistro della finestra Stato, sotto la barra del titolo, scegliere il pulsante che corrisponde allo stile di visualizzazione da usare.

  - **Mostra la visualizzazione stato di input API**

  - **Mostra la visualizzazione stato logico**

  - **Mostra la visualizzazione stato bloccato**

> [!IMPORTANT]
> È necessario bloccare lo stato nelle visualizzazioni **Stato di input API** o **Stato logico** perché sia mostrato nella **Visualizzazione stato bloccato**.

### <a name="state-table-format"></a>Formato della tabella di stato
 La finestra Stato contiene diverse colonne di informazioni.

|Colonna|Descrizione|
|------------|-----------------|
|Nome|Nome dell'elemento di stato. Se questo elemento rappresenta un'aggregazione di stati, può essere espanso per visualizzarlo.<br /><br /> In **Visualizzazione stato di input API** e **Visualizzazione stato logico**, i nomi sono rientrati per mostrare la relazione gerarchica tra gli stati.<br /><br /> In **Visualizzazione stato bloccato** vengono visualizzati i nomi completi in un elenco semplice.|
|Valore|Valore dell'elemento di stato.|
|Tipo|Tipo dell'elemento di stato.|

### <a name="changed-state"></a>Stato modificato
 Lo stato di grafica in genere viene modificato in modo incrementale tra chiamate di disegno successive e molti tipi di problemi di rendering sono causati da una modifica non corretta dello stato. Per semplificare l'individuazione dello stato modificato dopo la chiamata di disegno precedente, lo stato modificato è contrassegnato da un asterisco e visualizzato in rosso. Questo si applica non solo allo stato in sé, ma anche all'elemento di stato padre, in modo che sia possibile trovare più facilmente lo stato modificato al livello più elevato e quindi eseguire il drill-down ai dettagli.

### <a name="pinning-state"></a>Blocco dello stato
 Poiché molte app eseguono il rendering di oggetti simili in sequenza, modificando un set di stati noto, talvolta è utile bloccare sul posto gli stati che cambiano, in modo che sia possibile controllare le modifiche nel passaggio da una chiamata di disegno all'altra.

 Questo può essere utile anche se si è stabilito che l'origine di un problema è una modifica in un particolare stato.

##### <a name="to-pin-state-in-place"></a>Per bloccare lo stato sul posto

1. Nella finestra Stato individuare lo stato a cui si è interessati. Può essere necessario espandere lo stato di livello superiore per individuare i dettagli cercati.

2. Posizionare il cursore sullo stato a cui si è interessati. A sinistra dell'elemento di stato viene visualizzata un'icona Blocca.

3. Scegliere l'icona Blocca per bloccare l'elemento di stato sul posto.
