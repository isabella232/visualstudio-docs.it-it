---
title: Visualizzazione di Windows | Microsoft Docs
description: Visualizzazione Windows Mostra un albero di tutte le finestre e i controlli. Utilizzarlo come punto di partenza per ottenere informazioni su Windows di interesse.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.windowsview
helpviewer_keywords:
- Windows view
ms.assetid: 154786ce-c803-4bfb-8198-f7962a900363
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 717c0f18d5443f712151a2f8318c56a8e738f6d7
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205372"
---
# <a name="windows-view"></a>Visualizzazione finestre
Alla prima apertura di Spy + +, visualizzazione di Windows visualizza un albero di tutte le finestre e i controlli nel sistema. Vengono visualizzati l'handle della finestra e il nome della classe. La finestra del desktop corrente si trova nella parte superiore dell'albero. Tutte le altre finestre sono elementi figlio del desktop e sono elencate in base alla gerarchia standard della finestra. Le finestre di pari livello vengono visualizzate negli elenchi di espandibili rientrate sotto gli elementi padre.

 Nella figura seguente viene illustrata una tipica visualizzazione Windows di Spy + + con il nodo principale espanso.

 ![Spy&#43;&#43; visualizzazione di Windows](../debugger/media/spy--_windowsview.png "_WindowsView di Spy + +") Visualizzazione Windows di Spy + +

 La finestra del desktop corrente si trova nella parte superiore dell'albero. Tutte le altre finestre sono elementi figlio del desktop e sono elencate in base alla gerarchia standard della finestra, con finestre di pari livello ordinate in base all'ordine Z. È possibile espandere o comprimere qualsiasi nodo padre dell'albero facendo clic sul simbolo + o-accanto al nodo.

 Quando la visualizzazione di Windows ha lo stato attivo, è possibile usare lo strumento di ricerca nella finestra di [dialogo ricerca finestre](../debugger/window-search-dialog-box.md) per visualizzare le informazioni da qualsiasi finestra aperta nel sistema.

## <a name="in-this-section"></a>Contenuto della sezione
 [Procedura: utilizzare lo strumento di ricerca](../debugger/how-to-use-the-finder-tool.md) Mostra in che modo questo strumento analizza le finestre per le proprietà o i messaggi.

 [Procedura: cercare una finestra nella visualizzazione di Windows](../debugger/how-to-search-for-a-window-in-windows-view.md) Viene illustrato come trovare una finestra specifica nella visualizzazione di Windows.

 [Procedura: visualizzare le proprietà della finestra](../debugger/how-to-display-window-properties.md) m procedure per aprire la finestra di dialogo Proprietà finestra.

## <a name="related-sections"></a>Sezioni correlate
 [Viste di Spy + +](../debugger/spy-increment-views.md) Illustra le visualizzazioni ad albero di Spy + + di Windows, i messaggi, i processi e i thread.

 [Uso di Spy + +](../debugger/using-spy-increment.md) Introduce lo strumento Spy + + e spiega come può essere usato.

 [Finestra di dialogo Trova finestra](../debugger/find-window-dialog-box.md) Utilizzato per visualizzare le proprietà o i messaggi da una finestra specifica.

 [Finestra di dialogo ricerca finestre](../debugger/window-search-dialog-box.md) Utilizzato per trovare il nodo per una finestra specifica nella visualizzazione di Windows.

 [Finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md) Utilizzato per visualizzare le proprietà di una finestra selezionata nella visualizzazione di Windows.

 [Riferimenti per Spy + +](../debugger/spy-increment-reference.md) Include sezioni che descrivono ogni menu e finestra di dialogo di Spy + +.