---
title: Opzioni, Editor di testo, C#, Avanzate
description: Informazioni su come usare la pagina Avanzate nella sezione C# per modificare le impostazioni per la formattazione dell'editor, il refactoring del codice e i commenti della documentazione XML per C#.
ms.custom: SEO-VS-2020
ms.date: 06/01/2021
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: b8406499b96e20e97577069f1b52819e6f7b148a738042553051bf02c03f220a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447525"
---
# <a name="options-text-editor-c-advanced"></a>Opzioni, Editor di testo, C#, Avanzate

Usare la pagina di opzioni **Avanzate** per modificare le impostazioni di formattazione dell'editor, di refactoring del codice e dei commenti in formato documentazione XML per C#. Per accedere a questa pagina delle opzioni, scegliere **Opzioni** strumenti e quindi Editor  >   **di testo**  >  **C#**  >  **Avanzate**.

> [!NOTE]
> È possibile che non tutte le opzioni siano elencate.

## <a name="analysis"></a>Analisi

- Analisi del codice live o ambito di analisi in background

   Configurare l'ambito di analisi in background per il codice gestito. Per altre informazioni, vedere [Procedura: Configurare l'ambito di](../../code-quality/configure-live-code-analysis-scope-managed-code.md)analisi del codice in tempo reale per il codice gestito.

## <a name="using-directives"></a>Direttive using

- Inserisci prima le direttive 'System' durante l'ordinamento delle direttive using

   Se selezionato, il comando **Rimuovi e ordina using** nel menu di scelta rapida ordina le direttive `using` e posiziona gli spazi dei nomi "System" all'inizio dell'elenco.

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

::: moniker range=">=vs-2019"                                              
- Suggerire l'uso di per i tipi .NET Framework assembly
::: moniker-end
                                         
::: moniker range="vs-2017"                                                
- Suggerisci le direttive using per i tipi in assembly di riferimento
::: moniker-end                                                            

- Suggerisci le direttive using per i tipi in pacchetti NuGet

   Se queste opzioni sono selezionate, è disponibile un'[azione rapida](../quick-actions.md) per installare un pacchetto NuGet e aggiungere una direttiva `using` per i tipi senza riferimenti.

   ![Azione rapida per installare il pacchetto NuGet in Visual Studio](media/nuget-lightbulb.png)

- Aggiungi direttive using mancanti dopo operazione Incolla

    Quando questa opzione è selezionata, le direttive vengono aggiunte automaticamente al codice `using` quando si incolla un tipo in un file.

## <a name="highlighting"></a>Evidenziazione

- Evidenzia riferimenti a simbolo sotto il cursore

   Quando il cursore viene posizionato all'interno di un simbolo o quando si fa clic su un simbolo, vengono evidenziate tutte le istanze del simbolo nel file di codice.

## <a name="outlining"></a>struttura

- Attiva modalità struttura all'apertura dei file

   Se selezionata, visualizza automaticamente la struttura del file di codice che consente di creare blocchi comprimibili del codice. Alla prima apertura di un file, i blocchi #regions e i blocchi di codice inattivi vengono compressi.

- Mostra separatori di riga routine

   L'editor di testo indica l'ambito visivo delle routine. Viene tracciata una linea nei file di origine con estensione *cs* del progetto nelle posizioni indicate nella tabella seguente:

   |Posizione nel file di origine cs|Esempio di posizione della linea|
   |---------------------------------|------------------------------|
   |Dopo la chiusura di un costrutto di dichiarazione di blocco|- Alla fine di una classe, struttura, modulo, interfaccia o enumerazione<br />- Dopo una proprietà, funzione o sub<br />- Non tra le clausole get e set in una proprietà|
   |Dopo un set di costrutti a riga singola|- Dopo le istruzioni di importazione, prima di una definizione di tipo in un file di classe<br />- Dopo le variabili dichiarate in una classe, prima di qualsiasi routine|
   |Dopo le dichiarazioni a riga singola (dichiarazioni non block-level)|- Dopo le istruzioni di importazione, le istruzioni inherits, le dichiarazioni di variabili, le dichiarazioni di eventi, le dichiarazioni di delegati e le istruzioni di dichiarazione di DLL|

## <a name="block-structure-guides"></a>Guide per strutture a blocchi

Selezionare queste caselle di controllo per visualizzare le linee verticali tratteggiate tra le parentesi graffe ( **{}** ) nel codice. È quindi possibile visualizzare facilmente singoli blocchi di codice per i costrutti a livello di dichiarazione e a livello di codice.

## <a name="comments"></a>Commenti

- Genera commenti relativi alla documentazione XML per ///

   Se selezionata, questa opzione inserisce elementi XML per i commenti in formato documentazione XML dopo la digitazione dell'introduzione al commento `///`. Per altre informazioni sulla documentazione XML, vedere [Commenti in formato documentazione XML (Guida per programmatori C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

::: moniker range=">=vs-2019"

## <a name="inline-hints"></a>Suggerimenti inline

- Suggerimenti per i nomi di parametri inline 
    
    Quando questa opzione è selezionata, inserisce hint per i nomi dei parametri per valori letterali, valori letterali cast e istanze di oggetti prima di ogni argomento nelle chiamate di funzione.  
    
    ![Hint per i nomi dei parametri inline per CSharp](media/inline-parameter-name-hints-csharp.png)

- Suggerimenti per il tipo inline 
    
    Se selezionata, inserisce hint di tipo per le variabili con tipi dedosi e tipi di parametri lambda.  
    
    ![Hint di tipo inline per CSharp](media/inline-type-hints-csharp.png)

## <a name="inheritance-margin"></a>Margine di ereditarietà 

- Quando questa opzione è selezionata, aggiunge icone ai margini che rappresentano le implementazioni e gli override del codice. Facendo clic sulle icone del margine di ereditarietà verranno visualizzate le opzioni di ereditarietà che è possibile selezionare per passare.

    ![Margine di ereditarietà](media/inheritance-margin.png)

::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Procedura: Inserire commenti XML per la generazione di documentazione](../../ide/reference/generate-xml-documentation-comments.md)
- [Commenti in formato documentazione XML (Guida per programmatori C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentare il codice con commenti XML (Guida a C#)](/dotnet/csharp/codedoc)
- [Impostare opzioni dell'editor specifiche del linguaggio](../../ide/reference/setting-language-specific-editor-options.md)
- [IntelliSense per C#](../../ide/visual-csharp-intellisense.md)
