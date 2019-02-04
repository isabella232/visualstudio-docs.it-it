---
title: Opzioni, Editor di testo, C/C++, Sperimentale | Microsoft Docs
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 41be21f3b28cccfe735a2a908851ebe3b181ce7b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54762895"
---
# <a name="options-text-editor-cc-experimental"></a>Opzioni, Editor di testo, C/C++, Sperimentale
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Modificando queste opzioni è possibile modificare il comportamento correlato a IntelliSense e il database di esplorazione quando si programma in C o C++.  
  
 Per accedere a questa pagina, nel riquadro sinistro della finestra di dialogo **Opzioni** espandere **Editor di testo**e **C/C++**, quindi fare clic su **Sperimentale**.  
  
 Queste funzionalità sono disponibili in un'installazione di Visual Studio 2015 Update 1 RC.  
  
> [!NOTE]
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="browsingnavigation"></a>Esplorazione/Navigazione  
 **Abilita nuovo motore di database**  
 Questo dovrebbe velocizzare automaticamente il popolamento del database e tutte le operazioni di database (senza perdita di precisione) per operazioni come **Vai a definizione** e **Trova tutti i riferimenti**. Per applicare le modifiche è sufficiente chiudere e riaprire la soluzione; non è necessario riavviare Visual Studio.  
  
## <a name="intellisense"></a>IntelliSense  
 **Abilita sostituzione punto con freccia per elenco di membri**  
 sostituisce '.' con '->' quando applicabile per l'elenco membri.  
  
## <a name="refactoring"></a>Refactoring  
 **Abilita estrazione della funzione**  
 Estrarre il codice selezionato nella relativa funzione e sostituire il codice con una chiamata alla nuova funzione. Per accedere a questa funzionalità, fare clic sul codice selezionato e selezionare **Azioni rapide**oppure usare la combinazione di tasti predefinita Ctrl+punto [Ctrl+.].  
  
 **Abilita modifica della firma**  
 Aggiungere, riordinare ed eliminare parametri di una funzione e propagare le modifiche a tutti i siti di chiamata. Per accedere a questa funzionalità, fare clic su qualsiasi utilizzo della funzione e **Azioni rapide**oppure usare la combinazione di tasti predefinita Ctrl+punto [Ctrl+.].  
  
## <a name="text-editor"></a>Editor di testo  
 **Abilita espansione degli ambiti**  
 Se abilitata, è possibile racchiudere il testo selezionato tra parentesi graffe digitando '{' nell'editor di testo.  
  
 **Abilita espansione della precedenza**  
 Se abilitata, è possibile racchiudere il testo selezionato tra parentesi digitando '(' nell'editor di testo.  
  
 Per altre funzionalità dell'editor di testo in Visual Studio Gallery, vedere l'elenco disponibile [qui](http://go.microsoft.com/fwlink/?LinkId=692016). Un esempio è [Correzioni rapide per C++](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), che supporta quanto segue:  
  
- **Aggiunta di #include mancante** : suggerisce gli #include rilevanti per i simboli sconosciuti nel codice  
  
- **Aggiunta dell'uso dello spazio dei nomi/simbolo completo** : come l'elemento precedente, ma per gli spazi dei nomi  
  
- **Aggiunta del punto e virgola mancante**  
  
- **Guida di MSDN** : cercare i messaggi di errore in MSDN  
  
  È possibile passare il mouse su una sottolineatura ondulata per ottenere una lampadina oppure usare la combinazione di tasti predefinita Ctrl+punto (Ctrl+.). Per la combinazione di tasti, non è necessario che il punto di inserimento sia posizionato sull'errore specifico o token. È sufficiente trovarsi sulla stessa riga dell'errore per richiamare i suggerimenti per tutti gli elementi della riga.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazione delle opzioni dell'editor specifiche del linguaggio](../../ide/reference/setting-language-specific-editor-options.md)   
 [Refactoring in C++ (VC Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
