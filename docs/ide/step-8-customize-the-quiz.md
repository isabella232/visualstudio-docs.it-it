---
title: 'Passaggio 8: Personalizzare il quiz'
description: Informazioni su come trasformare il controllo timeLabel in un colore diverso e assegnare un suggerimento al quiz taker.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 028bf80fc32bac728463f3f1fdc7748914a45666
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048492"
---
# <a name="step-8-customize-the-quiz"></a>Passaggio 8: Personalizzare il quiz

Nell'ultima parte dell'esercitazione si esamineranno alcune modalità per personalizzare il quiz ed espandere ciò che è stato appreso. Ad esempio, si consideri la modalità mediante la quale tramite il programma vengono creati problemi di divisione casuali per cui la risposta non è mai una frazione. Per esercitarsi ulteriormente, modificare il colore del controllo `timeLabel` e offrire un suggerimento all'utente.

> [!NOTE]
> Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: Creare un quiz matematico a tempo.](../ide/tutorial-2-create-a-timed-math-quiz.md)

## <a name="to-customize-the-quiz"></a>Per personalizzare il quiz

- Quando in un quiz rimangono solo cinque secondi, attivare il **controllo timeLabel** in rosso impostandone la **proprietà BackColor.**

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

- Per passare all'esercitazione successiva, vedere **[Esercitazione 3: Creare un gioco corrispondente.](../ide/tutorial-3-create-a-matching-game.md)**

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 7: Aggiungere problemi di moltiplicazione e divisione](../ide/step-7-add-multiplication-and-division-problems.md).
