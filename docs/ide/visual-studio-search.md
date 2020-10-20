---
title: Usare la ricerca di Visual Studio
description: Informazioni su come usare la ricerca di Visual Studio per trovare impostazioni, menu e codice.
ms.date: 10/08/2020
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.QuickLaunch
- IDE navigator
ms.assetid: 3870a8fd-4afa-4f1e-a811-9fdf41a9e82d
monikerRange: vs-2019
author: profexorgeek
ms.author: jusjohns
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9f8182646af4facb0f2f86c74f95dff091d55d1
ms.sourcegitcommit: cea9e5787ff33e0e18aa1942bf4236748e0ef547
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2020
ms.locfileid: "92199654"
---
# <a name="use-visual-studio-search"></a>Usare la ricerca di Visual Studio

Visual Studio Integrated Development Environment (IDE) include molti menu, opzioni e funzionalità, che possono essere difficili da ricordare. La funzionalità di ricerca di Visual Studio è una singola casella di ricerca che aiuta gli sviluppatori a trovare opzioni e menu IDE, eseguendo anche ricerche nel codice. Se non si ha familiarità con Visual Studio o con uno sviluppatore esperto, questa funzionalità offre un modo rapido per eseguire ricerche tra le funzionalità dell'IDE e il codice.

Usare la **combinazione di tasti CTRL** + **Q** per accedere alla casella di ricerca oppure fare clic sulla casella di input di ricerca di Visual Studio, posizionata accanto alla barra dei menu per impostazione predefinita:

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Casella di ricerca di Visual Studio" lightbox="media/visual-studio-search.png":::

> [!NOTE]
> Il comando eseguito dalla ricerca di Visual Studio è `Window.QuickLaunch` e potrebbe essere visualizzata questa funzionalità denominata ricerca rapida o avvio veloce.

A differenza di altre funzionalità di ricerca, ad esempio cerca nei file o Cerca in Esplora soluzioni, i risultati della ricerca in Visual Studio includono funzionalità IDE, opzioni di menu, nomi file e altro ancora. Le sezioni seguenti illustrano i diversi tipi di risultati che è possibile trovare in Visual Studio search.

## <a name="search-menus-options-and-windows"></a>Cerca menu, opzioni e finestre

È possibile usare la casella di ricerca di Visual Studio per trovare le impostazioni, le opzioni e gli elementi di configurazione simili. Cercare, ad esempio, *Cambia tema* per trovare e aprire rapidamente la finestra di dialogo che consente di modificare il tema colori di Visual Studio, come illustrato nello screenshot seguente:

:::image type="content" source="media/visual-studio-search-options.png" alt-text="Casella di ricerca di Visual Studio":::

> [!TIP]
> Nella maggior parte dei casi, la ricerca di Visual Studio ti ricorda anche il menu, i tasti di scelta rapida e la posizione di ogni elemento nei risultati.

È possibile usare la casella di ricerca di Visual Studio per trovare voci di menu e comandi. Ad esempio, cercare *Clean Sol* per trovare ed eseguire rapidamente il comando Pulisci soluzione. I risultati della ricerca offrono inoltre un promemoria di come trovare questo comando nei menu, come illustrato nello screenshot seguente:

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="Casella di ricerca di Visual Studio":::

Infine, è possibile cercare finestre o pannelli che potrebbero essere stati chiusi accidentalmente. Ad esempio, cercare *test* per trovare e aprire la finestra Esplora test:

:::image type="content" source="media/visual-studio-search-window.png" alt-text="Casella di ricerca di Visual Studio":::

## <a name="search-files-and-code"></a>Cerca file e codice

Ricerca di Visual Studio cerca anche gli elementi della soluzione per nome file, codice, metodo e altre corrispondenze. Nella schermata seguente, una ricerca di *Markdown* ha trovato il file MarkdownMetaExtractor.cs, la `MarkdownMetaExtractor` classe e due metodi all'interno della soluzione:

:::image type="content" source="media/visual-studio-search-files.png" alt-text="Casella di ricerca di Visual Studio":::

È anche possibile eseguire una ricerca di "Camel case". Nella schermata seguente, una ricerca di *FSS* ha rilevato un file, una classe e**S**un metodo**di ize,** classe e metodo di **F**Older:

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="Casella di ricerca di Visual Studio":::

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](reference/visual-studio-commands.md)