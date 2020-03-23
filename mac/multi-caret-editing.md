---
title: Modifica di più punti di inserimento
description: Inserisci testo in più posizioni quando modifichi il codice in Visual Studio per Mac.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451447"
---
# <a name="multi-caret-editing"></a>Modifica di più punti di inserimento

La modifica con cursore multiplo consente di aggiungere _n_ numero di punti di inserimento in una sola volta. In modalità con più cursori, è possibile aggiungere altri punti di inserimento al documento tramite clic del mouse o tramite comandi da tastiera. Il cursore primario è indicato da un cursore rosso, mentre i punti di inserimento secondari sono presenti in un colore azzurro. La modalità di modifica con `ESC` più elementi di sicurezza può essere disattivata tramite il tasto .

## <a name="enabling-multi-caret-editing"></a>Abilitazione della modifica con supporto e l'altro

### <a name="keyboard"></a>Tastiera

È possibile abilitare la modalità con più elementi di posta elettronica tramite la tastiera in diversi modi. Nella tabella seguente sono riportate le scelte rapide da tastiera disponibili per immettere modalità specifiche di modifica con cuore di posta elettronica:

| Tasto di scelta rapida  | Azione                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Inserisci il custode corrispondente successivo    | 
|  ⌥⇧;   | Inserisci i dati di inserimento | 
|  ⌥⇧,   | Rimuovere l'ultimo inserimento             | 
|  ⌥⇧/   | Sposta l'ultimo clic verso il basso          | 

Ognuno di questi comportamenti è ancorato alla posizione corrente del livello di inserimento quando si richiama il comando. Ad esempio, se il punto di inserimento si trova all'inizio della parola "nome" e si richiama "Inserisci punti di inserimento in corrispondenza" (sezione ;) ogni istanza della parola "nome" nel documento corrente avrà un punto di inserimento all'inizio della parola. Allo stesso modo, se si richiama il comando "Inserisci il successivo accento di posizione corrispondente" (Sezione ,) , un accento di posizione verrà inserito nell'istanza successiva della parola "nome". Questo comando può essere richiamato più volte.

![tastiera con più punciere](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Mouse/touchpad

Utilizzando il cursore, è possibile selezionare punti di inserimento specifici per i punti di inserimento multipli. Mentre i tasti di scelta rapida sono associati a stringhe corrispondenti, potete inserire manualmente un punto di inserimento in qualsiasi punto del documento con il cursore. Una volta impostati i punti di inserimento, ognuno riecheggia le voci dei tasti digitate sulla tastiera.

Per utilizzare il mouse per inserire più punti di inserimento, è necessario tenere premuto il tasto cancelletto e fare clic nel punto in cui si desidera inserire il cursore. Sarete in modalità di inserimento fino a quando i tasti di sè sono tenuti. Se si inserisce un punto di inserimento in una posizione errata, è possibile rimuovere il punto di inserimento continuando a tenere premuto il segno di sè e facendo di nuovo clic nella stessa area. Una volta che hai tutti i punti di inserimento dove vorresti che si desidera, smettere di premere i tasti di cancelletto e iniziare a digitare. La gif seguente dimostra sia la selezione di un set di punti di inserimento che la rimozione di punti erroneamente impostati.

![mouse con più scontrammi](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Vedere anche

- [Azioni rapide (Visual Studio in Windows)](/visualstudio/ide/quick-actions)
- [Effettuare il refactoring del codice (Visual Studio in Windows)](/visualstudio/ide/refactoring-in-visual-studio)
