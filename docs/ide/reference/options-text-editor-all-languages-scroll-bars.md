---
title: Opzioni, Editor di testo, Tutti i linguaggi, Barre di scorrimento
description: Informazioni su come usare la pagina Barre di scorrimento nella sezione Tutti i linguaggi per modificare il comportamento predefinito delle barre di scorrimento dell'editor di codice all'interno Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/25/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Basic.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSharp.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.F%2523.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTMLX.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JavaScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.TypeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.LESS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.ResJSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SCSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.U-SQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XAML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XML.ScrollBars
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 111fd2231d775b4c69c7510568c8a9aea5e97188
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056277"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Opzioni, Editor di testo, Tutti i linguaggi, Barre di scorrimento
Questa finestra di dialogo consente di modificare il comportamento predefinito della barra di scorrimento dell'editor del codice. Per visualizzare queste opzioni, selezionare **Opzioni** dal menu **Strumenti**. All'interno della cartella **Editor di testo** espandere la sottocartella **Tutti i linguaggi** e quindi scegliere **Barre di scorrimento**.

> [!CAUTION]
> Questa pagina consente di impostare le opzioni predefinite per tutti i linguaggi di sviluppo. La reimpostazione di un'opzione in questa finestra di dialogo comporta la reimpostazione delle opzioni delle barre di scorrimento in tutti i linguaggi in base alle scelte operate qui. Per modificare le opzioni dell'editor di testo per un solo linguaggio, espandere la sottocartella per tale linguaggio e selezionare le pagine relative alle opzioni.

## <a name="show-horizontal-scroll-bar"></a>Mostra barra di scorrimento orizzontale

Quando questa opzione è selezionata, viene visualizzata una barra di scorrimento orizzontale che consente di scorrere da un lato all'altro per visualizzare gli elementi al di fuori dell'area di visualizzazione dell'editor. Se non sono disponibili barre di scorrimento orizzontali, per scorrere è possibile utilizzare i tasti di direzione.

## <a name="show-vertical-scroll-bar"></a>Mostra barra di scorrimento verticale

Quando questa opzione è selezionata, viene visualizzata una barra di scorrimento verticale che consente di scorrere verso l'alto e verso il basso per visualizzare gli elementi al di fuori dell'area di visualizzazione dell'editor. Se non sono disponibili barre di scorrimento verticali, per scorrere è possibile usare i tasti PGSU e PGGIÙ e i tasti di direzione.

## <a name="display"></a>Visualizza

### <a name="show-annotations-over-vertical-scroll-bar"></a>Mostra annotazioni su barra di scorrimento verticale

Selezionare se la barra di scorrimento verticale mostra le annotazioni seguenti:

- modifiche
- contrassegni
- errori
- posizione del cursore

> [!TIP]
> L'opzione **Mostra contrassegni** include punti di interruzione e segnalibri.

È possibile provarla aprendo un file di codice di grandi dimensioni e sostituendo una stringa di testo presente in diverse posizioni nel file. La barra di scorrimento mostra l'effetto delle sostituzioni, pertanto è possibile annullare le modifiche se è stato sostituito qualche elemento che non doveva essere sostituito.

Vedere il post di blog sulla [barra di scorrimento avanzata](/archive/blogs/cdnstudents/visual-studio-tips-and-tricks-enhanced-scroll-bar) per informazioni sul significato dei vari colori e simboli durante la modifica di codice.

## <a name="behavior"></a>Comportamento

La barra di scorrimento ha due modalità: modalità barra (impostazione predefinita) e modalità mappa.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Usa modalità barra per barra di scorrimento verticale

La *modalità barra* visualizza indicatori di annotazione sulla barra di scorrimento. Facendo clic sulla barra di scorrimento, è possibile scorrere la pagina verso l'alto o verso il basso, ma non passare alla posizione corrispondente nel file.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Usa modalità mappa per barra di scorrimento verticale

Quando in *modalità mappa* si fa clic su una posizione sulla barra di scorrimento, il cursore passa alla posizione nel file anziché scorrere semplicemente la pagina verso l'alto o verso il basso. Sulla barra di scorrimento vengono visualizzate, in miniatura, righe di codice. È possibile scegliere la larghezza della colonna della mappa selezionando un valore in **Panoramica origine**. Per abilitare un'anteprima di dimensioni maggiori del codice quando si posiziona il puntatore del mouse sulla mappa, selezionare l'opzione **Mostra descrizione comando anteprima**. Le aree compresse hanno un'ombreggiatura diversa e si espandono quando si fa doppio clic su di esse.

> [!TIP]
> È possibile disattivare la visualizzazione del codice in miniatura in modalità mappa impostando **Panoramica origine** su **Disattivata**. Se l'opzione **Mostra descrizione comando anteprima** è selezionata, viene comunque visualizzata un'anteprima del codice in tale posizione quando si posiziona il puntatore del mouse sulla barra di scorrimento e il cursore passa comunque alla posizione nel file quando si fa clic.

## <a name="see-also"></a>Vedi anche

- [Procedura: Personalizzare la barra di scorrimento](../how-to-track-your-code-by-customizing-the-scrollbar.md)