---
title: Opzioni, Editor di testo, C/C++, Formattazione
description: Informazioni su come usare la pagina Opzioni di formattazione e le relative pagine secondarie per impostare le opzioni per la formattazione del codice nell'editor di codice durante la programmazione in C e C++.
ms.custom: SEO-VS-2020
ms.date: 04/30/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
- ClangFormat
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: d5b342ac7533928c979b8346f4d2155b9c5de85b0509c4d86aa5261dae5bb338
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357070"
---
# <a name="options-text-editor-cc-formatting"></a>Opzioni, Editor di testo, C/C++, Formattazione

Usare queste pagine delle proprietà per modificare il comportamento predefinito dell'editor di codice in fase di programmazione in C o C++.

![Pagine delle proprietà di formattazione di C++](media/cpp-formatting.png)

Per accedere a questa pagina, nel riquadro sinistro della finestra di dialogo **Opzioni** espandere **Editor di testo** e **C/C++**, quindi fare clic su **Formattazione**.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../../ide/personalizing-the-visual-studio-ide.md)

## <a name="general-page"></a>Pagina Generale

Questa pagina include opzioni di formattazione di istruzioni e blocchi durante la digitazione.

::: moniker range="vs-2017"

**Visual Studio 2017 versione 15.7 e successive:**

::: moniker-end

la pagina include anche opzioni per la configurazione del supporto di [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) versione 5.0. ClangFormat è un'utilità che semplifica l'applicazione di stili e la formattazione del codice in base a un set di regole che è possibile configurare in un file con estensione clang-format o _clang-format.

### <a name="configuring-clangformat-options"></a>Configurazione delle opzioni di ClangFormat

::: moniker range="vs-2017"

**Visual Studio 2017 versione 15.7 e successive:**

::: moniker-end

Il supporto di ClangFormat è abilitato per impostazione predefinita. È possibile scegliere quali di queste convenzioni di formattazione comuni applicare a tutti i progetti: LLVM, Google, Chromium, Mozilla o WebKit. È anche possibile creare un file con estensione clang-format o _clang-format con una definizione di formato personalizzata. Se questo file è presente nella cartella di un progetto, Visual Studio lo usa per formattare tutti i file di codice sorgente contenuti nella cartella e nelle relative sottocartelle.

Per impostazione predefinita, Visual Studio esegue clangformat.exe in background e applica la formattazione durante la digitazione. È anche possibile specificare di eseguirlo solo per i comandi di formattazione richiamati manualmente **Formatta documento (CTRL+K, CTRL+D)** o **Formatta selezione (CTRL + K, CTRL + F)**.

## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Pagine Rientro, Nuove righe, Spaziatura, Ritorno a capo

Queste pagine consentono di personalizzare la formattazione in vari modi, ma vengono ignorate se ClangFormat è abilitato.

## <a name="see-also"></a>Vedi anche

- [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
- [Uso di IntelliSense](../../ide/using-intellisense.md)
