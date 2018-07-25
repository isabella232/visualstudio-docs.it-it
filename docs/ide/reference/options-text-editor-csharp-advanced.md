---
title: Opzioni, Editor di testo, C#, Avanzate
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: ab08de0c6993f57c719f69ccf27e30e3cbe41c32
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433302"
---
# <a name="options-text-editor-c-advanced"></a>Opzioni, Editor di testo, C#, Avanzate

Usare la pagina di opzioni **Avanzate** per modificare le impostazioni di formattazione dell'editor, di refactoring del codice e dei commenti in formato documentazione XML per C#. Per accedere a questa pagina di opzioni, scegliere **Strumenti** > **Opzioni** e quindi scegliere **Editor di testo** > **C#** > **Avanzate**.

> [!NOTE]
> È possibile che non tutte le opzioni siano elencate.

## <a name="analysis"></a>Analisi

- Abilita analisi della soluzione completa

   Abilita l'analisi del codice per tutti i file nella soluzione e non solo per i file di codice aperti. Per altre informazioni, vedere [Analisi della soluzione completa](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="highlighting"></a>Evidenziazione

- Evidenzia riferimenti a simbolo sotto il cursore

   Quando il cursore viene posizionato all'interno di un simbolo o quando si fa clic su un simbolo, vengono evidenziate tutte le istanze del simbolo nel file di codice.

## <a name="outlining"></a>struttura

- Attiva modalità struttura all'apertura del file

   Se selezionata, visualizza automaticamente la struttura del file di codice che consente di creare blocchi comprimibili del codice. Alla prima apertura di un file, i blocchi #regions e i blocchi di codice inattivi vengono compressi.

## <a name="editor-help"></a>Guida Editor

- Genera commenti relativi alla documentazione XML per ///

   Se selezionata, questa opzione inserisce elementi XML per i commenti in formato documentazione XML dopo la digitazione dell'introduzione al commento `///`. Per altre informazioni sulla documentazione XML, vedere [Commenti in formato documentazione XML (Guida per programmatori C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Vedere anche

- [Procedura: Inserire commenti XML per la generazione di documentazione](../../ide/reference/generate-xml-documentation-comments.md)
- [Commenti in formato documentazione XML (Guida per programmatori C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentare il codice con commenti XML (Guida a C#)](/dotnet/csharp/codedoc)
- [Impostare opzioni dell'editor specifiche del linguaggio](../../ide/reference/setting-language-specific-editor-options.md)
- [IntelliSense per C#](../../ide/visual-csharp-intellisense.md)