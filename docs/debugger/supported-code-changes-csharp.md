---
title: Modifiche al codice supportate (C# e Visual Basic) | Microsoft Docs
description: Informazioni sulle modifiche al codice supportate quando si usa la funzionalità modifica e continuazione durante il debug di un progetto C# o Visual Basic in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/11/2018
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 267d9097ebe53b4074bed6c5caf4077006c946eb
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149209"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Modifiche al codice supportate (C# e Visual Basic)
La funzionalità Modifica e continuazione è in grado di gestire la maggior parte dei tipi di modifiche al codice all'interno del corpo del metodo. Tuttavia, non è possibile applicare durante il debug la maggior parte delle modifiche all'esterno del corpo del metodo nonché alcune modifiche all'interno del corpo del metodo. Per applicare tali modifiche non supportate, interrompere il debug e riavviarlo utilizzando una versione aggiornata del codice.

## <a name="supported-changes-to-code"></a>Modifiche supportate al codice

La tabella seguente illustra le modifiche che possono essere apportate a C# e Visual Basic codice durante una sessione di debug senza riavviare la sessione.

|Elemento/funzionalità del linguaggio|Operazione di modifica supportata|Limitazioni|
|-|-|-|
|Tipi|Aggiungere metodi, campi, costruttori, et al|[Sì](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Iterators|Aggiungi o modifica|No|
|espressioni async/await|Aggiungi o modifica|[Sì](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Oggetti dinamici|Aggiungi o modifica|No|
|espressioni lambda|Aggiungi o modifica|[Sì](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Espressioni LINQ|Aggiungi o modifica|[Uguale alle espressioni lambda](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|

> [!NOTE]
> Le funzionalità del linguaggio più recenti, ad esempio l'interpolazione di stringhe e gli operatori condizionali null, sono generalmente supportate da modifica e continuazione. Per informazioni aggiornate, vedere la pagina relativa alle [modifiche supportate da ENC](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md) .

## <a name="unsupported-changes-to-code"></a>Modifiche non supportate al codice
 Le modifiche seguenti non possono essere applicate a C# e Visual Basic codice durante una sessione di debug:

- Modifiche all'istruzione corrente o a qualsiasi altra istruzione attiva.

     Le istruzioni attive includono qualsiasi istruzione, nelle funzioni presenti nello stack di chiamate, che è stata chiamata per ottenere l'istruzione corrente.

     L'istruzione corrente è contrassegnata con uno sfondo giallo nella finestra del codice sorgente. Le altre istruzioni attive sono contrassegnate con uno sfondo ombreggiato e sono di sola lettura. È possibile cambiare i colori predefiniti nella finestra di dialogo **Opzioni**.

- Nella tabella seguente vengono illustrate le modifiche non supportate al codice in base all'elemento del linguaggio.

|Elemento/funzionalità del linguaggio|Operazione di modifica non supportata|
|-|-|
|Tutti gli elementi di codice|Ridenominazione|
|Spazi dei nomi|Aggiungi|
|Spazi dei nomi, tipi, membri|Delete|
|Generics|Aggiungi o modifica|
|Interfacce|Modifica|
|Tipi|Aggiungi membro astratto o virtuale, Aggiungi override (vedere [i dettagli](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|
|Tipi|Aggiungi distruttore|
|Membri|Modificare un membro che fa riferimento a un tipo di interoperabilità incorporato|
|Membri|Modificare un membro statico dopo che è già stato eseguito l'accesso eseguendo codice|
|Membri (Visual Basic)|Modificare un membro con l'istruzione On Error o Resume|
|Membri (Visual Basic)|Modificare un membro contenente una clausola di query LINQ aggregate, Group by, join semplice o gruppo join|
|Metodi|Modificare le firme|
|Metodi|Fare in modo che un metodo astratto diventi non astratto aggiungendo il corpo di un metodo|
|Metodi|Elimina corpo metodo|
|Attributi|Aggiungi o modifica|
|Eventi o proprietà|Modificare un parametro di tipo, un tipo di base, un tipo delegato o un tipo restituito |
|Operatori o indicizzatori|Modificare un parametro di tipo, un tipo di base, un tipo delegato o un tipo restituito |
|blocchi catch|Modificare quando contiene un'istruzione attiva|
|blocchi try-catch-finally|Modificare quando contiene un'istruzione attiva|
|utilizzo di istruzioni|Aggiungi|
|metodi o espressioni lambda asincrone|Modificare un metodo/lambda asincrono in un progetto destinato a .NET Framework 4 e inferiore (vedere [i dettagli](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|
|Iterators|Modificare un iteratore in un progetto destinato a .NET Framework 4 e inferiore (vedere [i dettagli](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|

## <a name="unsafe-code"></a>Codice di tipo unsafe
 Le modifiche a codice non sicuro hanno le stesse limitazioni delle modifiche a codice sicuro, con un'ulteriore restrizione: Modifica e continuazione non supporta modifiche a codice non sicuro all'interno di un metodo che contiene l'operatore `stackalloc`.

## <a name="unsupported-app-scenarios"></a>Scenari di app non supportati

Le app e le piattaforme non supportate includono ASP.NET 5, Silverlight 5 e Windows 8.1.

> [!NOTE]
> Le app supportate includono UWP in Windows 10 e app x86 e x64 destinate a .NET Framework 4,6 desktop o versioni successive (il .NET Framework è solo una versione desktop).

## <a name="unsupported-scenarios"></a>Scenari non supportati
 Modifica e continuazione non è disponibile nei seguenti scenari di debug:

- Debug in modalità mista (nativo/gestito).

- Debug SQL.

- Debug di un dump di Dr. Watson.

- Debug di un'applicazione di runtime incorporata.

- Debug di un'applicazione mediante Connetti a processo (**Debug > Connetti a processo**) invece di eseguire l'applicazione scegliendo **Avvia** dal menu **debug** .

- Debug di codice ottimizzato.

- Debug di una versione precedente del codice dopo l'esito negativo della compilazione di una nuova versione a causa di errori di compilazione.

## <a name="see-also"></a>Vedere anche
- [Modifica e continuazione (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Procedura: Usare Modifica e continuazione (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)