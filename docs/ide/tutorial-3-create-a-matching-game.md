---
title: 'Esercitazione 3: Creare un gioco di abbinamenti'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f64de3b95d21fdae87dd6b14754956381d60e9a3
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008242"
---
# <a name="tutorial-3-create-a-matching-game"></a>Esercitazione 3: Creare un gioco di abbinamenti

In questa esercitazione si compila un gioco delle coppie, in cui il giocatore deve riuscire ad accoppiare icone nascoste. Vengono illustrate le seguenti procedure:

-   Archiviare oggetti, ad esempio icone, in un oggetto <xref:System.Collections.Generic.List%601>.

-   Utilizzare un ciclo `foreach` in Visual C# o un ciclo `For Each` in Visual Basic per scorrere gli elementi di un elenco.

-   Tenere traccia dello stato di un form utilizzando variabili di riferimento.

-   Compilare un gestore eventi per rispondere a eventi utilizzabili con più oggetti.

-   Creare un timer con conto alla rovescia e quindi generare un evento subito dopo l'avvio.

Al termine di questa esercitazione, il programma sarà simile all'immagine che segue:

![Gioco che si creerà in questa esercitazione](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Collegamenti dell'esercitazione

Per scaricare una versione completa dell'esempio, vedere [Complete Matching Game tutorial sample](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) (Esercitazione di esempio completa per il gioco di abbinamenti).

> [!NOTE]
> In questa esercitazione sono trattati sia Visual C# sia Visual Basic; concentrarsi sulle informazioni specifiche del linguaggio di programmazione in uso.

In caso di blocchi improvvisi o dubbi a livello di programmazione, provare a pubblicare una domanda in uno dei forum MSDN. Vedere il [forum di Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) e il [forum di Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral). Sono inoltre disponibili utilissime risorse di formazione video gratuite. Per altre informazioni sulla programmazione in Visual Basic, vedere [Visual Basic Fundamentals: Development for Absolute Beginners](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Nozioni fondamentali di Visual Basic: sviluppo per principianti assoluti). Per altre informazioni sulla programmazione in Visual C#, vedere [C# Fundamentals: Development for Absolute Beginners](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) (Nozioni fondamentali di C#: sviluppo per principianti assoluti).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Passaggio 1: Creare un progetto e aggiungere una tabella al modulo](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Per iniziare, creare il progetto e aggiungere un controllo `TableLayoutPanel` per mantenere allineati i controlli.|
|[Passaggio 2: Aggiungere un oggetto casuale e un elenco di icone](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Aggiungere un oggetto `Random` e un oggetto `List` per creare un elenco di icone.|
|[Passaggio 3: Assegnare un'icona casuale a ogni etichetta](../ide/step-3-assign-a-random-icon-to-each-label.md)|Assegnare le icone in modo casuale ai controlli `Label`, in modo che ogni gioco sia diverso.|
|[Passaggio 4: Aggiungere un gestore dell'evento Click a ogni etichetta](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Aggiungere un gestore dell'evento `Click` che modifica il colore dell'etichetta sulla quale viene fatto clic.|
|[Passaggio 5: Aggiungere riferimenti alle etichette](../ide/step-5-add-label-references.md)|Aggiungere variabili di riferimento per tenere traccia delle etichette sulle quali viene fatto clic.|
|[Passaggio 6: Aggiungere un timer](../ide/step-6-add-a-timer.md)|Aggiungere un timer al form per tenere traccia del tempo trascorso durante il gioco.|
|[Passaggio 7: Mantenere le coppie visibili](../ide/step-7-keep-pairs-visible.md)|Mantenere le coppie di icone visibili se viene selezionata una coppia corrispondente.|
|[Passaggio 8: Aggiungere un metodo per verificare se il giocatore ha vinto](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Aggiungere un metodo `CheckForWinner()` per verificare se il giocatore ha vinto.|
|[Passaggio 9: Provare altre funzionalità](../ide/step-9-try-other-features.md)|Provare altre funzionalità, ad esempio modificare le icone e i colori oppure aggiungere una griglia e i suoni. Provare a ingrandire lo schema e a regolare il timer.|
