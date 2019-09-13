---
title: Modifiche al codice supportateC# (e Visual Basic) | Microsoft Docs
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
ms.openlocfilehash: c5f54a2b50447125b0abffd8cc62ba9c2a1d2b37
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887782"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Modifiche al codice supportateC# (e Visual Basic)
La funzionalità Modifica e continuazione è in grado di gestire la maggior parte dei tipi di modifiche al codice all'interno del corpo del metodo. Tuttavia, non è possibile applicare durante il debug la maggior parte delle modifiche all'esterno del corpo del metodo nonché alcune modifiche all'interno del corpo del metodo. Per applicare tali modifiche non supportate, interrompere il debug e riavviarlo utilizzando una versione aggiornata del codice.

## <a name="supported-changes-to-code"></a>Modifiche supportate al codice

Nella tabella seguente vengono illustrate le modifiche che possono essere C# apportate e Visual Basic codice durante una sessione di debug senza riavviare la sessione.

|Elemento/funzionalità del linguaggio|Operazione di modifica supportata|Limitazioni|
|-|-|-|
|Tipi|Aggiungere metodi, campi, costruttori, et al|[Sì](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterators|Aggiungi o modifica|No|
|espressioni async/await|Aggiungi o modifica|[Sì](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Oggetti dinamici|Aggiungi o modifica|No|
|espressioni lambda|Aggiungi o modifica|[Sì](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Espressioni LINQ|Aggiungi o modifica|[Uguale alle espressioni lambda](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Le funzionalità del linguaggio più recenti, ad esempio l'interpolazione di stringhe e gli operatori condizionali null, sono generalmente supportate da modifica e continuazione. Per informazioni aggiornate, vedere la pagina relativa alle [modifiche supportate da ENC](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) .

## <a name="unsupported-changes-to-code"></a>Modifiche non supportate al codice
 Le modifiche seguenti non possono essere applicate C# a e Visual Basic codice durante una sessione di debug:

- Modifiche all'istruzione corrente o a qualsiasi altra istruzione attiva.

     Le istruzioni attive includono qualsiasi istruzione, nelle funzioni presenti nello stack di chiamate, che è stata chiamata per ottenere l'istruzione corrente.

     L'istruzione corrente è contrassegnata con uno sfondo giallo nella finestra del codice sorgente. Le altre istruzioni attive sono contrassegnate con uno sfondo ombreggiato e sono di sola lettura. È possibile cambiare i colori predefiniti nella finestra di dialogo **Opzioni**.

- Nella tabella seguente vengono illustrate le modifiche non supportate al codice in base all'elemento del linguaggio.

|Elemento/funzionalità del linguaggio|Operazione di modifica non supportata|
|-|-|
|Tutti gli elementi di codice|Ridenominazione|
|Spazi dei nomi|Aggiunta|
|Spazi dei nomi, tipi, membri|Eliminare|
|Generics|Aggiungi o modifica|
|Interfacce|Modifica|
|Tipi|Aggiungi membro astratto o virtuale, Aggiungi override (vedere [i dettagli](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Tipi|Aggiungi distruttore|
|Members|Modificare un membro che fa riferimento a un tipo di interoperabilità incorporato|
|Members|Modificare un membro statico dopo che è già stato eseguito l'accesso eseguendo codice|
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
|utilizzo di istruzioni|Aggiunta|
|metodi o espressioni lambda asincrone|Modificare un metodo/lambda asincrono in un progetto destinato a .NET Framework 4 e inferiore (vedere [i dettagli](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterators|Modificare un iteratore in un progetto destinato a .NET Framework 4 e inferiore (vedere [i dettagli](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|

## <a name="unsafe-code"></a>Codice di tipo unsafe
 Le modifiche al codice di tipo unsafe sono soggette alle stesse limitazioni delle modifiche al codice di tipo safe, con l'aggiunta della seguente: La funzionalità modifica e continuazione non supporta le modifiche apportate al codice unsafe che termina all' `stackalloc` interno di un metodo che contiene l'operatore.

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