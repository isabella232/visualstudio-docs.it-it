---
title: 'Passaggio 8: Personalizzare il quiz'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cee7b855256f352c9ac9ed39994191f4a9e6d946
ms.sourcegitcommit: 98b02f87c7aa1f5eb7f0d1c86bfa36efa8580c57
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314217"
---
# <a name="step-8-customize-the-quiz"></a>Passaggio 8: Personalizzare il quiz

Nell'ultima parte dell'esercitazione si esamineranno alcune modalità per personalizzare il quiz ed espandere ciò che è stato appreso. Ad esempio, si consideri la modalità mediante la quale tramite il programma vengono creati problemi di divisione casuali per cui la risposta non è mai una frazione. Per esercitarsi ulteriormente, modificare il colore del controllo `timeLabel` e offrire un suggerimento all'utente.

> [!NOTE]
> Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base.
> - Per una panoramica dell'esercitazione, vedere [Esercitazione 2: creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Per scaricare una versione completa del codice, vedere l' [esempio di esercitazione completa per i quiz matematici](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-customize-the-quiz"></a>Per personalizzare il quiz

- Quando rimangono solo cinque secondi in un quiz, attivare il controllo **timeLabel** in rosso impostando la relativa proprietà **BackColor** .

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  Reimpostare il colore quando il quiz è terminato.

- Fornire un suggerimento all'esecutore del quiz riproducendo un suono quando viene immessa la risposta corretta in un controllo <xref:System.Windows.Forms.NumericUpDown>. È necessario scrivere un gestore di evento per l'evento <xref:System.Windows.Forms.NumericUpDown.ValueChanged> di ogni controllo, che viene attivato ogni qualvolta l'utente modifica il valore del controllo.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per passare all'esercitazione successiva, vedere **[esercitazione 3: creare un gioco di abbinamenti](../ide/tutorial-3-create-a-matching-game.md)** .

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 7: Aggiungere problemi di moltiplicazione e divisione](../ide/step-7-add-multiplication-and-division-problems.md).
