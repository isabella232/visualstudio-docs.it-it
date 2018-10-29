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
ms.openlocfilehash: 16c92111fc29071447d4af5e736b881fa7c7a769
ms.sourcegitcommit: e680e8ac675f003ebcc8f8c86e27f54ff38da662
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356743"
---
# <a name="options-text-editor-c-advanced"></a>Opzioni, Editor di testo, C#, Avanzate

Usare la pagina di opzioni **Avanzate** per modificare le impostazioni di formattazione dell'editor, di refactoring del codice e dei commenti in formato documentazione XML per C#. Per accedere a questa pagina di opzioni, scegliere **Strumenti** > **Opzioni** e quindi scegliere **Editor di testo** > **C#** > **Avanzate**.

> [!NOTE]
> È possibile che non tutte le opzioni siano elencate.

## <a name="analysis"></a>Analisi

- Abilita analisi della soluzione completa

   Abilita l'analisi del codice per tutti i file nella soluzione e non solo per i file di codice aperti. Per altre informazioni, vedere [Analisi della soluzione completa](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Direttive using

- Inserisci prima le direttive 'System' durante l'ordinamento delle direttive using

   Se selezionata, il comando **Rimuovi e ordina using** nel menu di scelta rapida ordina le direttive `using` e posiziona gli spazi dei nomi "System" all'inizio dell'elenco

   Prima di ordinare:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```
   
   Dopo aver ordinato:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```
   
- Separa gruppi di direttive using

   Se selezionata, il comando **Rimuovi e ordina using** nel menu di scelta rapida separa le direttive `using` inserendo una riga vuota tra gruppi di direttive che hanno lo stesso spazio dei nomi radice.

   Prima di ordinare:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```
   
   Dopo aver ordinato:
   
   ```csharp
   using AutoMapper;
   
   using FluentValidation;
   
   using Newtonsoft.Json;
   
   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```
   
- Aggiungere le direttive using per i tipi in assembly di riferimento e pacchetti NuGet 

   Se selezionata, è disponibile un'[azione rapida](../quick-actions.md) per installare un pacchetto NuGet e aggiungere una direttiva `using` per i tipi senza riferimenti.

   ![Azione rapida per installare il pacchetto NuGet in Visual Studio](media/nuget-lightbulb.png)
  
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
