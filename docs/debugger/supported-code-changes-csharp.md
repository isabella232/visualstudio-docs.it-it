---
title: Modifiche al codice supportate (C# e Visual Basic) | Microsoft Docs
description: Informazioni su quali modifiche del codice sono supportate quando si usa la funzionalità Modifica e continuazione durante il debug di un progetto C# o Visual Basic in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 9/03/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: abbb4141b4133ac2526d7922ec0e82f74d8286d6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058240"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Modifiche al codice supportate (C# e Visual Basic)
La funzionalità Modifica e continuazione è in grado di gestire la maggior parte dei tipi di modifiche al codice all'interno del corpo del metodo. Tuttavia, non è possibile applicare durante il debug la maggior parte delle modifiche all'esterno del corpo del metodo nonché alcune modifiche all'interno del corpo del metodo. Per applicare tali modifiche non supportate, interrompere il debug e riavviarlo utilizzando una versione aggiornata del codice.

## <a name="supported-changes-to-code"></a>Modifiche supportate al codice

La tabella seguente illustra le modifiche che possono essere apportate a C# e Visual Basic codice durante una sessione di debug senza riavviare la sessione.

|Elemento/funzionalità del linguaggio|Operazione di modifica supportata|Limitazioni|
|-|-|-|
|Tipi|Aggiungere metodi, campi, costruttori e altri|[Sì](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Iterators|Aggiungi o modifica|No|
|Espressioni async/await|Aggiungi o modifica|[Sì](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Oggetti dinamici|Aggiungi o modifica|No|
|espressioni lambda|Aggiungi o modifica|[Sì](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Espressioni LINQ|Aggiungi o modifica|[Come le espressioni lambda](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|

> [!NOTE]
> Le funzionalità del linguaggio più nuove, ad esempio l'interpolazione di stringhe e gli operatori condizionali Null, sono in genere supportate da Modifica e continuazione. Per le informazioni più aggiornate, vedere la pagina Modifiche supportate [da Enc.](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)

## <a name="unsupported-changes-to-code"></a>Modifiche al codice non supportate
 Le modifiche seguenti non possono essere applicate al codice C# Visual Basic durante una sessione di debug:

- Modifiche all'istruzione corrente o a qualsiasi altra istruzione attiva.

     Le istruzioni attive includono qualsiasi istruzione, nelle funzioni presenti nello stack di chiamate, che è stata chiamata per ottenere l'istruzione corrente.

     L'istruzione corrente è contrassegnata con uno sfondo giallo nella finestra del codice sorgente. Le altre istruzioni attive sono contrassegnate con uno sfondo ombreggiato e sono di sola lettura. È possibile cambiare i colori predefiniti nella finestra di dialogo **Opzioni**.

- La tabella seguente illustra le modifiche non supportate al codice in base all'elemento del linguaggio.

|Elemento/funzionalità del linguaggio|Operazione di modifica non supportata|
|-|-|
|Tutti gli elementi di codice|Ridenominazione|
|Spazi dei nomi|Add|
|Spazi dei nomi, tipi, membri|Elimina|
|Generics|Aggiungi o modifica|
|Interfacce|Modifica|
|Tipi|Aggiungere un membro astratto o virtuale, aggiungere l'override (vedere [i dettagli)](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Tipi|Aggiungi distruttore|
|Membri|Modificare un membro che fa riferimento a un tipo di interoperabilità incorporato|
|Membri|Modificare un membro statico dopo che è già stato eseguito l'accesso eseguendo il codice|
|Membri (Visual Basic)|Modificare un membro con l'istruzione On Error o Resume|
|Membri (Visual Basic)|Modificare un membro contenente una clausola di query LINQ Aggregate, Group By, Simple Join o Group Join|
|Metodi|Modificare le firme|
|Metodi|Rendere un metodo astratto non astratto aggiungendo un corpo del metodo|
|Metodi|Corpo del metodo Delete|
|Attributi|Aggiungi o modifica|
|Eventi o proprietà|Modificare un parametro di tipo, un tipo di base, un tipo delegato o un tipo restituito |
|Operatori o indicizzatori|Modificare un parametro di tipo, un tipo di base, un tipo delegato o un tipo restituito |
|blocchi catch|Modificare quando contiene un'istruzione attiva|
|Blocchi try-catch-finally|Modificare quando contiene un'istruzione attiva|
|utilizzo di istruzioni|Add|
|metodi/espressioni lambda asincrone|Modificare un metodo asincrono/lambda in un progetto che ha come destinazione .NET Framework 4 e inferiori (vedere [i dettagli](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|
|Iterators|Modificare un iteratore in un progetto che ha come destinazione .NET Framework 4 e inferiori (vedere [i dettagli](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|

## <a name="unsafe-code"></a>Codice di tipo unsafe
 Le modifiche a codice non sicuro hanno le stesse limitazioni delle modifiche a codice sicuro, con un'ulteriore restrizione: Modifica e continuazione non supporta modifiche a codice non sicuro all'interno di un metodo che contiene l'operatore `stackalloc`.

## <a name="unsupported-app-scenarios"></a>Scenari di app non supportati

Le app e le piattaforme non supportate includono Silverlight 5 e Windows 8.1. Gli scenari non supportati in ASP.NET e ASP.NET Core includono la modifica di file con estensione _aspx,_ _ascx,_ _cshtml_ e _razor._

> [!NOTE]
> Le app supportate includono la piattaforma UWP in Windows 10 e le app x86 e x64 che hanno come destinazione il desktop .NET Framework 4.6 o versioni successive (il .NET Framework è solo una versione desktop).

## <a name="unsupported-scenarios"></a>Scenari non supportati
 Modifica e continuazione non è disponibile nei seguenti scenari di debug:

- Debug in modalità mista (nativo/gestito).

- Debug SQL.

- Debug di un dump dr. Watson.

- Debug di un'applicazione di runtime incorporata.

- Eseguire il debug di un'applicazione usando **l'opzione Collega** a processo ( Debug > Associa a processo ) invece di eseguire l'applicazione scegliendo **Avvia** dal menu **Debug.**

- Debug di codice ottimizzato.

- Debug di una versione precedente del codice dopo l'esito negativo della compilazione di una nuova versione a causa di errori di compilazione.

## <a name="see-also"></a>Vedi anche
- [Modifica e continuazione (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Procedura: Usare Modifica e continuazione (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
