---
title: 'Passaggio 5: Aggiungere riferimenti alle etichette'
description: Informazioni su come aggiungere riferimenti all'etichetta al form.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 393f71c3360371122e86dc078aaa97c6963db325
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296274"
---
# <a name="step-5-add-label-references"></a>Passaggio 5: Aggiungere riferimenti alle etichette
Il programma deve tenere traccia dei controlli Label scelti dal giocatore. Al momento il programma mostra tutte le etichette scelte dal giocatore, ma è possibile modificare questa impostazione. Una volta scelta la prima etichetta, il programma dovrebbe visualizzarne l'icona. Una volta scelta la seconda etichetta, il programma dovrebbe visualizzare entrambe le icone per un istante, quindi renderle nuovamente invisibili. Il programma terrà ora traccia del controllo Label scelto per primo e di quello scelto per secondo usando *variabili di riferimento*.

## <a name="to-add-label-references"></a>Per aggiungere riferimenti alle etichette

1. Aggiungere i riferimenti alle etichette nel form utilizzando il codice seguente.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet5":::

     > [!IMPORTANT]
     > Usare il controllo linguaggio di programmazione nella parte superiore destra della pagina per visualizzare il frammento di codice C# o il frammento di codice Visual Basic.<br><br>![Controllo del linguaggio di programmazione per Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Queste variabili di riferimento sono simili alle istruzioni utilizzate in precedenza per aggiungere oggetti (ad esempio oggetti <xref:System.Windows.Forms.Timer>, <xref:System.Collections.Generic.List%601> e <xref:System.Random>) al form. Queste istruzioni, tuttavia, non comportano la visualizzazione di due controlli Label aggiuntivi nel modulo, perché in nessuna delle due istruzioni è usata la parola chiave `new`. Senza la parola chiave `new` non viene creato alcun oggetto. Per questo motivo gli oggetti `firstClicked` e `secondClicked` sono detti variabili di riferimento: tengono semplicemente traccia degli oggetti Label o vi fanno riferimento.

     Quando una variabile non tiene traccia di un oggetto, viene impostata su un valore riservato speciale, ovvero `null` in C# e `Nothing` in Visual Basic. Quando il programma viene avviato, quindi, `firstClicked` e `secondClicked` vengono impostati su `null` o `Nothing`, il che significa che le variabili non tengono traccia di alcun oggetto.

2. Modificare il gestore dell'evento <xref:System.Windows.Forms.Control.Click> per usare la nuova variabile di riferimento `firstClicked`. Rimuovere l'ultima istruzione nel metodo del gestore degli eventi `label_Click()` (`clickedLabel.ForeColor = Color.Black;`) e sostituirla con l'istruzione `if` seguente. Assicurarsi di includere il commento e l'intera istruzione `if`.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet6":::

3. Salvare ed eseguire il programma. Scegliere uno dei controlli etichetta; verrà visualizzata la relativa icona.

4. Scegliere il controllo etichetta successivo. Non accadrà nulla. Il programma sta già tenendo traccia della prima etichetta scelta dal giocatore, pertanto `firstClicked` non è uguale a `null` in C# o `Nothing` in Visual Basic. Quando l'istruzione `if` controlla `firstClicked` per stabilire se sia uguale a `null` o `Nothing`, rileva che non lo è e non esegue le istruzioni contenute nell'istruzione `if`. Quindi, solo la prima icona scelta è nera e le altre icone sono invisibili, come illustrato nella figura seguente.

     ![Gioco di abbinamenti con un'icona visualizzata](../ide/media/express_tut4step5.png)<br/>
***Gioco corrispondente** _ _showing un'icona *

     Questa situazione verrà corretta nel passaggio successivo dell'esercitazione aggiungendo un controllo **Timer**.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[passaggio 6: aggiungere un timer](../ide/step-6-add-a-timer.md)**.

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 4: Aggiungere un gestore dell'evento Click a ogni etichetta](../ide/step-4-add-a-click-event-handler-to-each-label.md).
