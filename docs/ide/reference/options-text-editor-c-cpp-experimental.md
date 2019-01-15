---
title: Opzioni, Editor di testo, C/C++, Sperimentale
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: mikeblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.workload:
- cplusplus
ms.openlocfilehash: 13bcc65b3d8ffe4872c8b7d5f18b1bbf13bc67c5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893328"
---
# <a name="options-text-editor-cc-experimental"></a>Opzioni, Editor di testo, C/C++, Sperimentale

Modificando queste opzioni è possibile modificare il comportamento correlato a IntelliSense e il database di esplorazione quando si programma in C o C++. Queste funzionalità sono davvero sperimentali. È possibile che vengano modificate o rimossa da Visuali Studio in una versione futura. In questo argomento vengono descritte le opzioni di Visual Studio 2017. Per Visual Studio 2015, selezionare **2015** nel selettore sopra il sommario.

Per accedere a questa pagina delle proprietà, premere **CTRL + Q** per attivare `Quick Launch` e quindi digitare "sperimentale". Avvio veloce troverà la pagina dopo le prime lettere. È anche possibile accedere scegliendo **Strumenti | Opzioni**, espandendo **Editor di testo** e **C/C++** e quindi scegliendo **Sperimentale**.

In un'installazione di Visual Studio 2017 sono disponibili queste funzionalità.

> [!NOTE]
> I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Abilita IntelliSense predittivo

IntelliSense predittivo limita il numero di risultati visualizzati nell'elenco a discesa di IntelliSense, in modo che siano visualizzati solo i risultati pertinenti al contesto. Se ad esempio si digita <code>int x =</code> e si richiama l'elenco a discesa di IntelliSense, vengono visualizzati solo numeri interi o funzioni che restituiscono numeri interi. Per impostazione predefinita, IntelliSense predittivo è disattivato.

## <a name="enable-faster-project-load"></a>Abilita caricamento più rapido del progetto

**Visual Studio 2017 versione 15.3 e successive**: questa funzionalità è ora denominata **Abilita Caching progetto** ed è stata spostata nella pagina delle proprietà [Impostazioni di progetto di VC++](vcpp-project-settings-projects-and-solutions-options-dialog-box.md).
Questa opzione consente a Visual Studio di memorizzare nella cache i dati di progetto in modo che alla successiva apertura del progetto sia possibile caricare i dati presenti nella cache anziché rielaborare i dati dai file di progetto. L'uso dei dati memorizzati nella cache può accelerare i tempi di caricamento del progetto in modo significativo.

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Altre funzionalità in Visual Studio Marketplace

È possibile scoprire altre funzionalità dell'editor di testo in [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Un esempio è [Correzioni rapide per C++](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017), che supporta quanto segue:

- **Aggiunta di #include mancante** : suggerisce gli #include rilevanti per i simboli sconosciuti nel codice

- **Aggiunta dell'uso dello spazio dei nomi/simbolo completo** : come l'elemento precedente, ma per gli spazi dei nomi

- **Aggiunta del punto e virgola mancante**

- **Guida in linea**: cercare informazioni online per i messaggi di errore

- E molto altro ancora.

## <a name="see-also"></a>Vedere anche

- [Impostazione delle opzioni dell'editor specifiche del linguaggio](../../ide/reference/setting-language-specific-editor-options.md)
- [Refactoring in C++ (VC Blog)](https://blogs.msdn.microsoft.com/vcblog/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview/)
