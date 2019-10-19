---
title: Opzioni, Editor di testo, C#, Avanzate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f2d11e78c2402a6541bc87748ed6ba348ba80fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662327"
---
# <a name="options-text-editor-c-advanced"></a>Opzioni, Editor di testo, C#, Avanzate
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usare questa finestra di dialogo per modificare le impostazioni di formattazione dell'editor, di refactoring del codice e dei commenti della documentazione XML per Visual C#. Per accedere a questa finestra di dialogo, fare clic su **Opzioni** nel menu **Strumenti**, spandere la cartella **Editor di testo**, espandere **C#** e quindi fare clic su **Avanzate**.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="outlining"></a>struttura
 Attiva modalità struttura all'apertura dei file quando viene selezionata, descrive automaticamente il file di codice, che crea blocchi comprimibili di codice. Alla prima apertura di un file, i blocchi #regions e i blocchi di codice inattivi vengono compressi.

## <a name="editor-help"></a>Guida Editor
 Gli errori di sottolineatura nell'editor identificano gli errori di compilazione nel codice. Quando questa opzione è selezionata, vengono visualizzate sottolineature ondulate con colori che hanno un significato specifico:

- Gli errori di analisi sono visualizzati in rosso.

- Gli errori di compilazione sono visualizzati in blu.

- Gli avvisi di compilazione sono visualizzati in verde.

- Le modifiche [Modifica e continuazione](../../debugger/edit-and-continue.md) non valide sono visualizzate in viola.

  Spostare il puntatore sul segmento di codice sottolineato per visualizzare una descrizione comando con informazioni sull'errore.

  Mostra errori semantici dinamici identifica determinati errori di compilazione senza compilazione esplicita, ad esempio, dichiarando e utilizzando un tipo sconosciuto o facendo riferimento a una proprietà sconosciuta.

  Evidenziare i riferimenti al simbolo sotto il cursore quando il cursore è posizionato all'interno di un simbolo o quando si fa clic su un simbolo, vengono evidenziate tutte le istanze del simbolo nel file di codice.

## <a name="refactoring"></a>Refactoring
 Verifica risultati del refactoring consente di visualizzare la finestra di dialogo **Risultati verifica** quando si tenta di effettuare il refactoring del codice che contiene errori di compilazione o quando il refactoring causa l'associazione di un riferimento al codice a elementi diversi dall'associazione originale.

 Avvisa in caso di membri con riferimenti generati dal compilatore Visualizza una finestra di dialogo di avviso quando si tenta di effettuare il refactoring di un membro con lo stesso nome di un riferimento generato dal compilatore.

## <a name="xml-documentation-comments"></a>Commenti relativi alla documentazione XML
 Genera commenti in formato documentazione XML per///se selezionato, inserisce i tag di inizio e di fine > automaticamente per \<summary i commenti relativi alla documentazione XML dopo aver digitato l'introduzione del commento. Per altre informazioni sulla documentazione XML, vedere [Commenti relativi alla documentazione XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).

## <a name="implement-interface"></a>Implementa interfaccia
 Il codice generato da Racchiudi con #region inserisce una #region \<*nome dell'interfaccia*> membro attorno ai metodi quando viene usata l'interfaccia implementa interfaccia o implementa l'interfaccia in modo esplicito.

## <a name="organize-usings"></a>Organizza using
 Inserire prima le direttive ' System ' durante l'ordinamento delle direttive using, `System` le direttive using vengono visualizzate prima delle altre direttive using. Per altre informazioni, vedere [Ordina using](../../misc/sort-usings.md).

## <a name="see-also"></a>Vedere anche
 [Commenti relativi alla documentazione XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [impostazione delle opzioni dell'editor specifiche del linguaggio](../../ide/reference/setting-language-specific-editor-options.md) [ C# Visual IntelliSense](../../ide/visual-csharp-intellisense.md)
