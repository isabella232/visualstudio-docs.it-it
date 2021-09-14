---
title: Usare la ricerca di Visual Studio
description: Informazioni su come usare Visual Studio ricerca per trovare impostazioni, menu e codice.
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 1299810fa015f9e54d418209e13d366ff47bfb33
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628470"
---
# <a name="use-visual-studio-search"></a>Usare Visual Studio ricerca

L Visual Studio ide (Integrated Development Environment) include molti menu, opzioni e funzionalità, che possono essere difficili da ricordare. La Visual Studio di ricerca è un'unica casella di ricerca che consente agli sviluppatori di trovare menu e opzioni IDE, eseguendo anche ricerche nel codice. Se non si ha esperienza con Visual Studio o uno sviluppatore esperto, questa funzionalità offre un modo rapido per eseguire ricerche tra le funzionalità dell'IDE e il codice.

Usare il **tasto di** scelta rapida CTRL Q per accedere alla casella di ricerca o fare clic sulla casella di input Visual Studio Cerca, che si trova accanto alla barra dei menu per +  impostazione predefinita:

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Visual Studio casella di ricerca" lightbox="media/visual-studio-search.png":::

> [!NOTE]
> Il comando eseguito da Visual Studio ricerca è ed è possibile che questa funzionalità venga definita ricerca rapida o `Window.QuickLaunch` avvio rapido.

A differenza di altre funzionalità di ricerca, ad esempio Trova nei file o Cerca Esplora soluzioni, la ricerca nei risultati di Visual Studio include funzionalità IDE, opzioni di menu, nomi di file e altro ancora. Le sezioni seguenti illustrano i diversi tipi di risultati che Visual Studio ricerca.

## <a name="search-menus-options-and-windows"></a>Menu, opzioni e finestre di ricerca

È possibile usare la casella Visual Studio ricerca per trovare impostazioni, opzioni ed elementi di configurazione simili. Ad esempio, cercare *Cambia* tema per trovare e aprire rapidamente la finestra di dialogo che consente di modificare il tema colori Visual Studio, come illustrato nello screenshot seguente:

:::image type="content" source="media/visual-studio-search-options.png" alt-text="Cercare Visual Studio impostazioni e opzioni":::

> [!TIP]
> Nella maggior parte Visual Studio ricerca ricorda anche il menu, i tasti di scelta rapida e la posizione di ogni elemento nei risultati.

È possibile usare la casella Visual Studio ricerca per trovare voci di menu e comandi. Ad esempio, cercare *sol pulito per* trovare ed eseguire rapidamente il comando Pulisci soluzione. I risultati della ricerca offrono anche un promemoria della posizione in cui trovare questo comando nei menu, come illustrato nello screenshot seguente:

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="Cercare Visual Studio comandi e voci di menu":::

Infine, è possibile cercare finestre o pannelli che potrebbero essere stati chiusi accidentalmente. Ad esempio, cercare *test per* trovare e aprire la finestra Esplora test:

:::image type="content" source="media/visual-studio-search-window.png" alt-text="Cercare Visual Studio finestre e pannelli":::

## <a name="search-files-and-code"></a>Cercare file e codice

Visual Studio ricerca anche nome file, codice, metodo e altre corrispondenze degli elementi della soluzione. Nello screenshot seguente, una ricerca di *markdown* ha trovato il file MarkdownMetaExtractor.cs, la classe e due metodi `MarkdownMetaExtractor` all'interno della soluzione:

:::image type="content" source="media/visual-studio-search-files.png" alt-text="Eseguire ricerche nei file Visual Studio ricerca":::

È anche possibile eseguire una ricerca "camel case". Nello screenshot seguente, una ricerca di *FSS* ha trovato un file, una classe e un metodo S **ize****S** meno recenti di **F:**

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="Ricerca gobba camel con Visual Studio ricerca":::

## <a name="see-also"></a>Vedi anche

- [Comandi di Visual Studio](reference/visual-studio-commands.md)