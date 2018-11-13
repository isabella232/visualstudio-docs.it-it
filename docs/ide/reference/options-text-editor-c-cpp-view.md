---
title: Opzioni, Editor di testo, C/C++, Visualizza
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: mikeblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: 9cf1cde04a45df47627b8b8bf9a0fad7b9bef0c4
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673235"
---
# <a name="options-text-editor-cc-view"></a>Opzioni, Editor di testo, C/C++, Visualizza

Usare queste pagine delle proprietà per modificare il comportamento predefinito dell'editor di codice in fase di programmazione in C o C++.

Per accedere a questa pagina delle proprietà, scegliere **Strumenti** > **Opzioni**, espandere **Editor di testo**, **C/C++** e quindi scegliere **Visualizza**.

> [!NOTE]
> I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

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

## <a name="see-also"></a>Vedere anche

- [Impostazione delle opzioni dell'editor specifiche del linguaggio](../../ide/reference/setting-language-specific-editor-options.md)
- [Refactoring in C++ (VC Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
