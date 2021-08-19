---
title: Windows Visualizzare | Microsoft Docs
description: Windows La visualizzazione mostra un albero di tutte le finestre e di tutti i controlli. Usarlo come punto di partenza per ottenere informazioni sulle finestre di interesse.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5450783c5279c28af49aec901176452d14ff11fd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146485"
---
# <a name="windows-view"></a>Visualizzazione finestre
Quando si apre Spy++, Windows visualizzazione visualizza un albero di tutte le finestre e i controlli nel sistema. Vengono visualizzati l'handle di finestra e il nome della classe. La finestra desktop corrente si trova nella parte superiore dell'albero. Tutte le altre finestre sono elementi figlio del desktop e sono elencate in base alla gerarchia di finestre standard. Le finestre di pari livello vengono visualizzate in elenchi espansi rientrati sotto i relativi elementi padre.

 La figura seguente mostra una tipica visualizzazione di spy++ Windows con il nodo superiore espanso.

 ![Visualizzazione&#43;&#43; Windows Spy](../debugger/media/spy--_windowsview.png "Spy++_WindowsView") Visualizzazione Windows Spy++

 La finestra desktop corrente si trova nella parte superiore dell'albero. Tutte le altre finestre sono elementi figlio del desktop e sono elencate in base alla gerarchia di finestre standard, con finestre di pari livello ordinate in base all'ordine Z. È possibile espandere o comprimere qualsiasi nodo padre dell'albero facendo clic sul simbolo + o - accanto al nodo.

 Quando Windows visualizzazione ha lo stato attivo, è possibile [](../debugger/window-search-dialog-box.md) usare lo strumento Finder nella finestra di dialogo Ricerca finestra per visualizzare informazioni da qualsiasi finestra aperta nel sistema.

## <a name="in-this-section"></a>Contenuto della sezione
 [Procedura: Usare lo strumento Finder](../debugger/how-to-use-the-finder-tool.md) Mostra in che modo questo strumento analizza le finestre per cercare proprietà o messaggi.

 [Procedura: Cercare una finestra in Windows predefinita](../debugger/how-to-search-for-a-window-in-windows-view.md) Viene illustrato come trovare una finestra specifica in Windows visualizzazione.

 [Procedura: Visualizzare le proprietà della finestra](../debugger/how-to-display-window-properties.md) m Procedure per l'apertura della finestra di dialogo Proprietà finestra.

## <a name="related-sections"></a>Sezioni correlate
 [Visualizzazioni di Spy++](../debugger/spy-increment-views.md) Illustra le visualizzazioni albero di Spy++ di finestre, messaggi, processi e thread.

 [Uso di Spy++](../debugger/using-spy-increment.md) Introduce lo strumento Spy++ e spiega come può essere usato.

 [Finestra di dialogo Trova finestra](../debugger/find-window-dialog-box.md) Consente di visualizzare le proprietà o i messaggi da una finestra specifica.

 [Finestra di dialogo Ricerca finestre](../debugger/window-search-dialog-box.md) Usato per trovare il nodo per una finestra specifica nella Windows visualizzazione.

 [Finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md) Consente di visualizzare le proprietà di una finestra selezionata Windows visualizzazione.

 [Informazioni di riferimento su Spy++](../debugger/spy-increment-reference.md) Include sezioni che descrivono ogni menu e finestra di dialogo di Spy++.