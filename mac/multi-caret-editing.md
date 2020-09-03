---
title: Modifica di più punti di inserimento
description: Inserire il testo in più posizioni quando si modifica il codice in Visual Studio per Mac.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75451447"
---
# <a name="multi-caret-editing"></a>Modifica di più punti di inserimento

La funzionalità di modifica di più punti di inserimento consente _di aggiungere un_ numero di punti di inserimento in una sola volta. Quando si usa la modalità a più cursore, è possibile aggiungere ulteriori carriere al documento usando i clic del mouse o i comandi da tastiera. Il punto di inserimento primario è indicato da un cursore rosso, mentre quelli secondari sono presenti in un colore blu chiaro. La modalità di modifica del punto di inserimento può essere disabilitata tramite la `ESC` chiave.

## <a name="enabling-multi-caret-editing"></a>Abilitazione della modifica del punto di inserimento

### <a name="keyboard"></a>Tastiera

È possibile abilitare la modalità a più punti di inserimento tramite la tastiera in diversi modi. Nella tabella seguente sono riportati i tasti di scelta rapida disponibili per l'immissione di modalità specifiche di modifica del punto di inserimento:

| Tasto di scelta rapida  | Action                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Inserisci punto di inserimento corrispondente successivo    | 
|  ⌥⇧;   | Inserisci i punto di inserimento in corrispondenza di tutte le corrispondenze | 
|  ⌥⇧,   | Rimuovi ultimo punto di inserimento             | 
|  ⌥⇧/   | Sposta ultimo punto di inserimento in basso          | 

Ognuno di questi comportamenti è ancorato alla posizione corrente del punto di inserimento quando si richiama il comando. Ad esempio, se il punto di inserimento si trova all'inizio della parola "Name" e si richiama "Insert Caren all matching" (⌥ ⇧;) ogni istanza della parola "nome" nel documento corrente avrà un accento circonflesso inserito all'inizio della parola. Analogamente, se si richiama il comando "Insert Next matching" (⌥ ⇧), verrà inserito un accento circonflesso nell'istanza successiva della parola "Name". Questo comando può essere richiamato più volte.

![tastiera a più cursore](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Mouse/touchpad

Utilizzando il cursore, è possibile selezionare punti di inserimento specifici per più punti di inserimento. Mentre i tasti di scelta rapida sono associati alle stringhe corrispondenti, è possibile inserire manualmente un punto di inserimento nel documento con il cursore. Una volta impostati i set di lavoro, ciascuno restituirà le voci chiave digitate sulla tastiera.

Per usare il mouse per inserire più punti di inserimento, è necessario tenere premuto ⌘ ⌥ e fare clic su dove si desidera inserire i punti di inserimento. Si sarà in modalità di inserimento finché verranno mantenute le chiavi ⌘ ⌥. Se si inserisce un accento circonflesso in una posizione non corretta, è possibile rimuovere il cursore continuando a tenere ⌘ ⌥ e facendo nuovamente clic nella stessa area. Una volta che tutti i punti di inserimento si trovano nel punto in cui si desidera, interrompere la pressione dei tasti ⌘ ⌥ e iniziare a digitare. Il GIF seguente illustra sia la selezione di un set di punti di inserimento che la rimozione dei punti impostati erroneamente.

![mouse con più cursore](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Vedere anche

- [Azioni rapide (Visual Studio in Windows)](/visualstudio/ide/quick-actions)
- [Effettuare il refactoring del codice (Visual Studio in Windows)](/visualstudio/ide/refactoring-in-visual-studio)
