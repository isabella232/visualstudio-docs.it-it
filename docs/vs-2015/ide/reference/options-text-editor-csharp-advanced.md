---
title: Opzioni, Editor di testo, C#, Avanzate | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 51707a1df9c9f7144dc9a3af021262ca818f03b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850516"
---
# <a name="options-text-editor-c-advanced"></a>Opzioni, Editor di testo, C#, Avanzate
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Usare questa finestra di dialogo per modificare le impostazioni di formattazione dell'editor, di refactoring del codice e dei commenti della documentazione XML per Visual C#. Per accedere a questa finestra di dialogo, fare clic su **Opzioni** nel menu **Strumenti**, spandere la cartella **Editor di testo**, espandere **C#** e quindi fare clic su **Avanzate**.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="outlining"></a>Struttura  
 Attiva modalità struttura all'apertura del file  
 Se selezionata, visualizza automaticamente la struttura del file di codice che consente di creare blocchi comprimibili del codice. Alla prima apertura di un file, i blocchi #regions e i blocchi di codice inattivi vengono compressi.  
  
## <a name="editor-help"></a>Guida Editor  
 Sottolinea errori nell'editor  
 Identifica gli errori di compilazione nel codice. Quando questa opzione è selezionata, vengono visualizzate sottolineature ondulate con colori che hanno un significato specifico:  
  
- Gli errori di analisi sono visualizzati in rosso.  
  
- Gli errori di compilazione sono visualizzati in blu.  
  
- Gli avvisi di compilazione sono visualizzati in verde.  
  
- Le modifiche [Modifica e continuazione](../../debugger/edit-and-continue.md) non valide sono visualizzate in viola.  
  
  Spostare il puntatore sul segmento di codice sottolineato per visualizzare una descrizione comando con informazioni sull'errore.  
  
  Mostra errori di semantica in tempo reale  
  Identifica alcuni errori di compilazione senza compilazione esplicita, ad esempio la dichiarazione e l'uso di un tipo sconosciuto o il riferimento a una proprietà sconosciuta.  
  
  Evidenzia riferimenti a simbolo sotto il cursore  
  Quando il cursore viene posizionato all'interno di un simbolo o quando si fa clic su un simbolo, vengono evidenziate tutte le istanze del simbolo nel file di codice.  
  
## <a name="refactoring"></a>Refactoring  
 Verifica risultati del refactoring  
 Visualizza la finestra di dialogo **Risultati verifica** quando si tenta di eseguire il refactoring di codice contenente errori di compilazione o quando il refactoring fa in modo che un riferimento di codice venga associato a un elemento diverso dal binding originale.  
  
 Avvisa in caso di membri con riferimenti generati dal compilatore  
 Visualizza una finestra di dialogo di avviso quando si tenta di eseguire il refactoring di un membro che ha lo stesso nome del riferimento generato dal compilatore.  
  
## <a name="xml-documentation-comments"></a>Commenti relativi alla documentazione XML  
 Genera commenti relativi alla documentazione XML per ///  
 Se selezionata, questa opzione inserisce automaticamente i tag \<summary> di inizio e di fine per i commenti della documentazione XML dopo che è stata digitata l'introduzione di commento ///. Per altre informazioni sulla documentazione XML, vedere [Commenti relativi alla documentazione XML](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).  
  
## <a name="implement-interface"></a>Implementa interfaccia  
 Racchiudi il codice generato tra #region  
 Inserisce un membro #region \<*nome interfaccia*> prima e dopo i metodi quando viene usata Implementa interfaccia o Implementa interfaccia in modo esplicito.  
  
## <a name="organize-usings"></a>Organizza using  
 Inserisci prima le direttive 'System' durante l'ordinamento delle direttive using  
 Se selezionata, le direttive using `System` vengono visualizzate prima delle altre direttive using. Per altre informazioni, vedere [Ordina using](../../misc/sort-usings.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Commenti relativi alla documentazione XML](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [Impostazione delle opzioni dell'editor specifiche del linguaggio](../../ide/reference/setting-language-specific-editor-options.md)   
 [IntelliSense per Visual C#](../../ide/visual-csharp-intellisense.md)



