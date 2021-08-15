---
title: Modifica di più punti di inserimento
description: Inserire testo in più posizioni quando si modifica il codice in Visual Studio per Mac.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: c04bb80ee6a0bf9e9d1699d9f1b0b85da727ad5bc8235ebafbf1d55369e82d16
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121266337"
---
# <a name="multi-caret-editing"></a>Modifica di più punti di inserimento

La modifica con più punti di inserimento consente di aggiungere _n_ punti di inserimento contemporaneamente. Quando si è in modalità multi-cursore, è possibile aggiungere altri cursori al documento tramite clic del mouse o tramite comandi da tastiera. Il cursore primario è denotato da un cursore rosso, mentre i punti di selezione secondari sono presenti in un colore blu chiaro. La modalità di modifica con più punti di sospensione può essere disabilitata tramite la `ESC` chiave.

## <a name="enabling-multi-caret-editing"></a>Abilitazione della modifica con più caret

### <a name="keyboard"></a>Tastiera

È possibile abilitare la modalità multi-caret tramite la tastiera in diversi modi. La tabella seguente fornisce i tasti di scelta rapida disponibili per immettere modalità specifiche di modifica con più caret:

| Tasto di scelta rapida  | Azione                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Inserire il successivo caret corrispondente    | 
|  ⌥⇧;   | Inserire i caratteri di inserimento in corrispondenza di tutte le corrispondenze | 
|  ⌥⇧,   | Rimuovere l'ultimo caret             | 
|  ⌥⇧/   | Spostare l'ultimo caret verso il basso          | 

Ognuno di questi comportamenti è ancorato alla posizione corrente del cursore quando si richiama il comando. Ad esempio, se il punto di inserimento si trova all'inizio della parola "name" e si richiama "Insert carets at all matching" (Inserisci caret in corrispondenza di tutte le corrispondenze) (⌥⇧;) Ogni istanza della parola "name" nel documento corrente avrà un punto di inserimento inserito all'inizio della parola. Analogamente, se si richiama il comando "Inserisci successivo punto di inserimento corrispondente" (⌥⇧.), verrà inserito un punto di inserimento nell'istanza successiva della parola "name". Questo comando può essere richiamato più volte.

![tastiera multi-caret](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Mouse/touchpad

Usando il cursore, è possibile liberare i punti di inserimento specifici per più punti di inserimento. Anche se i tasti di scelta rapida sono associati a stringhe corrispondenti, è possibile inserire manualmente un cursore in un punto qualsiasi del documento con il cursore. Dopo aver impostato i punti di caret, ognuno di essi risuccherà le voci dei tasti digitate sulla tastiera.

Per usare il mouse per inserire più punti di inserimento, è necessario tenere premuto⌥ e fare clic nel punto in cui si desidera inserire i punti di inserimento. Si sarà in modalità di inserimento fino a quando vengono mantenute le chiavi ⌥ chiavi. Se si inserisce un punto di inserimento in una posizione non corretta, è possibile rimuovere il punto di inserimento continuando a tenere premuto ⌥ e facendo di nuovo clic nella stessa area. Dopo aver posizionato tutti i tasti di inserimento nel punto in cui si desidera, interrompere la pressione dei tasti ⌥ e iniziare a digitare. La gif seguente illustra sia la selezione di un set di punti di inserimento che la rimozione di punti erroneamente impostati.

![mouse con più cursori](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Vedi anche

- [Azioni rapide (Visual Studio in Windows)](/visualstudio/ide/quick-actions)
- [Effettuare il refactoring del codice (Visual Studio in Windows)](/visualstudio/ide/refactoring-in-visual-studio)
