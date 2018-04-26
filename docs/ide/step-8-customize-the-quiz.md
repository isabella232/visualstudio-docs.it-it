---
title: 'Passaggio 8: personalizzare il quiz'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82e059383a706c45e6882b97611f680a3d49baeb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="step-8-customize-the-quiz"></a>Passaggio 8: personalizzare il quiz
Nell'ultima parte dell'esercitazione si esamineranno alcune modalità per personalizzare il quiz ed espandere ciò che è stato appreso. Ad esempio, si consideri la modalità mediante la quale tramite il programma vengono creati problemi di divisione casuali per cui la risposta non è mai una frazione. Per esercitarsi ulteriormente, modificare il colore del controllo `timeLabel` e offrire un suggerimento all'utente.  

### <a name="to-customize-the-quiz"></a>Per personalizzare il quiz  

-   Quando rimangono solo cinque secondi in un quiz, modificare il colore del controllo **timeLabel** in rosso impostando la relativa proprietà **BackColor** (`timeLabel.BackColor = Color.Red;`). Reimpostare il colore quando il quiz è terminato.  

-   Fornire un suggerimento all'utente riproducendo un suono quando viene immessa la risposta corretta in un controllo NumericUpDown. È necessario scrivere un gestore di evento per l'evento `ValueChanged()` di ogni controllo, che viene attivato ogni qualvolta l'utente modifica il valore del controllo.  

### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  

-   Per scaricare una versione completa del quiz, vedere [Complete Math Quiz tutorial sample](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c) (Esempio di esercitazione per un quiz matematico completo).  

-   Per passare all'esercitazione successiva, vedere [Esercitazione 3: creare un gioco delle coppie](../ide/tutorial-3-create-a-matching-game.md).  

-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 7: aggiungere problemi di moltiplicazione e divisione](../ide/step-7-add-multiplication-and-division-problems.md).
