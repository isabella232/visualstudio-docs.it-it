---
title: Le modifiche al codice supportate (C# e Visual Basic) | Microsoft Docs
ms.date: 10/11/2017
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
ms.openlocfilehash: 5e5a4791b6703db72f67c9b18abcb3b0592916be
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945060"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Le modifiche al codice supportate (C# e Visual Basic)
La funzionalità Modifica e continuazione è in grado di gestire la maggior parte dei tipi di modifiche al codice all'interno del corpo del metodo. Tuttavia, non è possibile applicare durante il debug la maggior parte delle modifiche all'esterno del corpo del metodo nonché alcune modifiche all'interno del corpo del metodo. Per applicare tali modifiche non supportate, interrompere il debug e riavviarlo utilizzando una versione aggiornata del codice.

## <a name="supported-changes-to-code"></a>Modifiche supportate al codice

La tabella seguente illustra le modifiche apportate a C# e il codice Visual Basic durante una sessione di debug senza riavviare la sessione.

|Elemento/funzionalità del linguaggio|Operazione di modifica supportati|Limitazioni|
|-|-|-|
|Tipi|Aggiungere i metodi, campi, costruttori, et al|[Sì](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterators|Aggiungi o modifica|No|
|espressioni di Async/await|Aggiungi o modifica|[Sì](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Oggetti dinamici|Aggiungi o modifica|No|
|espressioni lambda|Aggiungi o modifica|[Sì](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Espressioni LINQ|Aggiungi o modifica|[Uguale a espressioni lambda](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Funzionalità del linguaggio più recenti, ad esempio l'interpolazione di stringhe e gli operatori condizionali con valori null sono in genere supportate in modifica e continuazione. Per informazioni aggiornate, vedere la [supportato modifica Enc](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) pagina.

## <a name="unsupported-changes-to-code"></a>Modifiche non supportate al codice
 Impossibile applicare le modifiche seguenti a C# e il codice Visual Basic durante una sessione di debug:  
  
-   Modifiche all'istruzione corrente o a qualsiasi altra istruzione attiva.  
  
     Le istruzioni attive includono qualsiasi istruzione, nelle funzioni presenti nello stack di chiamate, che è stata chiamata per ottenere l'istruzione corrente.  
  
     L'istruzione corrente è contrassegnata con uno sfondo giallo nella finestra del codice sorgente. Le altre istruzioni attive sono contrassegnate con uno sfondo ombreggiato e sono di sola lettura. È possibile cambiare i colori predefiniti nella finestra di dialogo **Opzioni**.

- La tabella seguente illustra le modifiche non supportate al codice dall'elemento di linguaggio.

|Elemento/funzionalità del linguaggio|Operazione di modifica non supportata|
|-|-|
|Tutti gli elementi di codice|Ridenominazione|
|Spazi dei nomi|Aggiunta|
|Spazi dei nomi, tipi, membri|Eliminare|
|Generics|Aggiungi o modifica|
|Interfacce|Modifica|
|Tipi|Aggiungere membri astratti o virtuali, aggiungere l'override (vedere [dettagli](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Tipi|Aggiungi distruttore|
|Membri|Modificare un membro che fanno riferimento a un tipo di interoperabilità incorporato|
|Membri (Visual Basic)|Modificare un membro con l'istruzione On Error o Resume|
|Membri (Visual Basic)|Modificare un membro contenente una clausola di query Aggregate, Group By, Join semplice o gruppo Join LINQ|
|Metodi|Modificare le firme|
|Metodi|Rendere una metodo astratto diventano non astratta tramite l'aggiunta di un corpo del metodo|
|Metodi|Eliminazione del corpo (metodo)|
|Attributi|Aggiungi o modifica|
|Gli eventi o proprietà|Modificare un parametro di tipo, tipo di base, il tipo delegato o tipo restituito |
|Operatori o gli indicizzatori|Modificare un parametro di tipo, tipo di base, il tipo delegato o tipo restituito |
|blocchi catch|Modificare quando contiene un'istruzione attiva|
|blocchi try-catch-finally|Modificare quando contiene un'istruzione attiva|
|utilizzo di istruzioni|Aggiunta|
|metodi/espressioni lambda asincrone|Modificare una metodo/espressione lambda asincrona in un progetto destinato a .NET Framework 4 e ridurre (vedere [dettagli](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterators|Modificare un iteratore in un progetto destinato a .NET Framework 4 e ridurre (vedere [dettagli](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
  
## <a name="unsafe-code"></a>Codice di tipo unsafe  
 Le modifiche al codice di tipo unsafe sono soggette alle stesse limitazioni delle modifiche al codice di tipo safe, con l'aggiunta della seguente: Modifica e continuazione non supporta le modifiche al codice di tipo unsafe esistente all'interno di un metodo che contiene il `stackalloc` operatore.  

## <a name="unsupported-app-scenarios"></a>Scenari con app non supportato

Piattaforme e applicazioni non supportate includono ASP.NET 5, Silverlight 5 e Windows 8.1.

> [!NOTE]
> Le app supportate includono UWP in x86 e x64 App destinate a .NET Framework 4.6 e Windows 10 desktop o versioni successive (.NET Framework è solo una versione desktop).
  
## <a name="unsupported-scenarios"></a>Scenari non supportati  
 Modifica e continuazione non è disponibile nei seguenti scenari di debug:  
  
-   Debug in modalità mista (nativo/gestito).  
  
-   Debug SQL.  
  
-   Debug di un dump di Dr. Watson.  
  
-   Debug di un'applicazione di runtime incorporata.  
  
-   Debug di un'applicazione che usa Connetti a processo (**Debug > Connetti a processo**) invece di eseguire l'applicazione da **avviare** dal **Debug** menu.  
  
-   Debug di codice ottimizzato.  
  
-   Debug di una versione precedente del codice dopo l'esito negativo della compilazione di una nuova versione a causa di errori di compilazione.
  
## <a name="see-also"></a>Vedere anche  
 [Modifica e continuazione (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Procedura: Usare Modifica e continuazione (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)