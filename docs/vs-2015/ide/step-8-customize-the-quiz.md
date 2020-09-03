---
title: 'Passaggio 8: personalizzare il quiz | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ded65e85a2ae11e96c21fdd852ea12daa4bbcdf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299995"
---
# <a name="step-8-customize-the-quiz"></a>Passaggio 8: personalizzare il quiz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nell'ultima parte dell'esercitazione si esamineranno alcune modalità per personalizzare il quiz ed espandere ciò che è stato appreso. Ad esempio, si consideri la modalità mediante la quale tramite il programma vengono creati problemi di divisione casuali per cui la risposta non è mai una frazione. Per esercitarsi ulteriormente, modificare il colore del controllo `timeLabel` e offrire un suggerimento all'utente.

### <a name="to-customize-the-quiz"></a>Per personalizzare il quiz

- Quando rimangono solo cinque secondi in un quiz, modificare il colore del controllo **timeLabel** in rosso impostando la relativa proprietà **BackColor** (`timeLabel.BackColor = Color.Red;`). Reimpostare il colore quando il quiz è terminato.

- Fornire un suggerimento all'utente riproducendo un suono quando viene immessa la risposta corretta in un controllo NumericUpDown. È necessario scrivere un gestore di evento per l'evento `ValueChanged()` di ogni controllo, che viene attivato ogni qualvolta l'utente modifica il valore del controllo.

### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per passare all'esercitazione successiva, vedere [Esercitazione 3: creare un gioco delle coppie](../ide/tutorial-3-create-a-matching-game.md).

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 7: aggiungere problemi di moltiplicazione e divisione](../ide/step-7-add-multiplication-and-division-problems.md).
