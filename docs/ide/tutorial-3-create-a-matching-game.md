---
title: 'Esercitazione 3: Creare un gioco di abbinamenti'
description: Informazioni su come creare un gioco corrispondente, in cui il giocatore deve corrispondere a coppie di icone nascoste.
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 596236c1770623b244219164c2d8c555b413c620
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040593"
---
# <a name="tutorial-3-create-a-matching-game"></a>Esercitazione 3: Creare un gioco di abbinamenti

In questa esercitazione si compila un gioco delle coppie, in cui il giocatore deve riuscire ad accoppiare icone nascoste.

> [!NOTE]
> Questa esercitazione illustra sia C# che Visual Basic, quindi concentrarsi sulle informazioni specifiche del linguaggio di programmazione in uso.

Questa esercitazione illustra le attività seguenti:

- Archiviare oggetti, ad esempio icone, in un oggetto <xref:System.Collections.Generic.List%601>.

- Usare un `foreach` ciclo in C# o un ciclo in Visual Basic scorrere gli elementi in un `For Each` elenco.

- Tenere traccia dello stato di un form utilizzando variabili di riferimento.

- Compilare un gestore eventi per rispondere a eventi utilizzabili con più oggetti.

- Creare un timer con conto alla rovescia e quindi generare un evento subito dopo l'avvio.

Al termine, l'app dovrebbe essere simile all'immagine seguente:

![Gioco che si creerà in questa esercitazione](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Collegamenti dell'esercitazione

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
|[Passaggio 9: Provare altre funzionalità](../ide/step-9-try-other-features.md)|Provare altre funzionalità, ad esempio modificare le icone e i colori oppure aggiungere una griglia e i suoni. Provare a ingrandire la lavagna e a regolare il timer.|

Sono disponibili anche risorse di video learning gratuite. Per altre informazioni sulla programmazione in C#, vedere [Nozioni fondamentali su C#: Sviluppo per principianti assoluti.](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) Per altre informazioni sulla programmazione in Visual Basic, vedere [Visual Basic Fundamentals: Development for Absolute Beginners](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Nozioni fondamentali di Visual Basic: sviluppo per principianti assoluti).

## <a name="next-steps"></a>Passaggi successivi

Per iniziare l'esercitazione, iniziare **[con Passaggio 1: Creare un progetto e aggiungere una tabella al modulo](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)**.

## <a name="see-also"></a>Vedi anche

* [Altre esercitazioni su C#](../get-started/csharp/index.yml)
* [Visual Basic esercitazioni](../get-started/visual-basic/index.yml)
* [Esercitazioni su C++](/cpp/get-started/tutorial-console-cpp)