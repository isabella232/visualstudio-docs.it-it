---
title: Opzioni, Editor di testo, C/C++, Visualizza
description: Informazioni su come usare la pagina Visualizza nella sezione C/C++ per modificare il comportamento predefinito delle sottolineatura a sottolineatura del codice, del codice inattivo, della struttura e altro ancora all'interno Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: caa0b67c5c59474948a7abb18b391e42d18fbd3996e126175b5990bf63766a81
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447441"
---
# <a name="options-text-editor-cc-view"></a>Opzioni, Editor di testo, C/C++, Visualizza

Usare queste pagine delle proprietà per modificare il comportamento predefinito dell'editor di codice in fase di programmazione in C o C++.

Per accedere a questa pagina delle proprietà, **scegliere** Opzioni strumenti ed  >   espandere Editor di **testo**, **C/C++** e quindi **scegliere Visualizza.**

## <a name="code-squiggles"></a>Controllo ortografia codice

Per gestire la modalità di gestione del controllo ortografia codice per C e C++ da parte dell'editor di testo, è possibile abilitare o disabilitare le impostazioni seguenti:

- **Macro nelle aree di esplorazione ignorate**: consente di definire come evidenziare le macro incluse in aree ignorate dal database di esplorazione, ad esempio le macro le cui definizioni contengono parentesi graffe.

- **Macro convertibili in constexpr**: consente di definire come evidenziare le definizioni di macro che è possibile convertire in definizioni `constexpr`.

## <a name="inactive-code"></a>Codice inattivo

- **Mostra blocchi inattivi**: i blocchi inattivi per il preprocessore vengono colorati diversamente.

- **Disabilita opacità del codice inattivo**: per i blocchi di codice inattivi viene usato un colore a tinta unita anziché opacità.

- **Percentuale di opacità del codice inattivo**: percentuale di opacità per i blocchi di codice inattivo.

## <a name="miscellaneous"></a>Varie

- **Enumera attività di commento**: esegue la ricerca di token VS nei file di origine aperti e li segnala nella finestra Elenco attività.

- **Evidenzia token corrispondenti**: evidenzia le parentesi o la sintassi di inclusione corrispondente alla posizione del cursore.

## <a name="outlining"></a>struttura

- **Abilita struttura**: abilita la modalità struttura all'apertura di un file.

- **Struttura blocchi pragma region**: abilita la struttura automatica dei blocchi `#pragma` region.

- **Struttura blocchi di istruzioni**: abilita la struttura automatica dei blocchi di istruzioni.

## <a name="see-also"></a>Vedi anche

- [Impostazione delle Language-Specific dell'editor](../../ide/reference/setting-language-specific-editor-options.md)
- [Refactoring in C++ (VC Blog)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
