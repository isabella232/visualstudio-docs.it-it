---
title: 'Passaggio 8: Personalizzare il quiz'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86fb0b7d22e02e563fe022b470651e2c335e4000
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079456"
---
# <a name="step-8-customize-the-quiz"></a>Passaggio 8: Personalizzare il quiz

Nell'ultima parte dell'esercitazione si esamineranno alcune modalità per personalizzare il quiz ed espandere ciò che è stato appreso. Ad esempio, si consideri la modalità mediante la quale tramite il programma vengono creati problemi di divisione casuali per cui la risposta non è mai una frazione. Per esercitarsi ulteriormente, modificare il colore del controllo `timeLabel` e offrire un suggerimento all'utente.

> [!NOTE]
> Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base.
> - Per una panoramica dell'esercitazione, vedere [Esercitazione 2: Creare un quiz matematico a tempo (C#)](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Per scaricare una versione completa del codice, vedere l' [esempio di esercitazione completa per i quiz matematici](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-customize-the-quiz"></a>Per personalizzare il quiz

- Quando rimangono solo cinque secondi in un quiz, attivare il controllo **timeLabel** in rosso impostando la relativa proprietà **BackColor** .

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  > [!IMPORTANT]
  > Usare il controllo linguaggio di programmazione nella parte superiore destra della pagina per visualizzare il C# frammento di codice o il frammento di codice Visual Basic.<br><br>![Controllo del linguaggio di programmazione per Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

  Reimpostare il colore quando il quiz è terminato.

- Fornire un suggerimento all'esecutore del quiz riproducendo un suono quando viene immessa la risposta corretta in un controllo <xref:System.Windows.Forms.NumericUpDown>. È necessario scrivere un gestore di evento per l'evento <xref:System.Windows.Forms.NumericUpDown.ValueChanged> di ogni controllo, che viene attivato ogni qualvolta l'utente modifica il valore del controllo.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per passare all'esercitazione successiva, vedere  **[l'esercitazione 3: Creare un gioco](../ide/tutorial-3-create-a-matching-game.md)** di abbinamenti.

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 7: Aggiungere problemi di moltiplicazione e divisione](../ide/step-7-add-multiplication-and-division-problems.md).
