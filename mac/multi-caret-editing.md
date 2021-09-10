---
title: Modifica di più punti di inserimento
description: Inserire testo in più posizioni quando si modifica il codice in Visual Studio per Mac.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964578"
---
# <a name="multi-caret-editing"></a>Modifica di più punti di inserimento

La modifica di più punti di inserimento consente di aggiungere _n_ punti di inserimento contemporaneamente. In modalità più cursori, è possibile aggiungere altri cursori al documento tramite clic del mouse o comandi da tastiera. Il cursore primario è denotato da un cursore rosso, mentre i punti di selezione secondari sono presenti in un colore blu chiaro. La modalità di modifica con più punti di selezione può essere disabilitata tramite `ESC` la chiave.

## <a name="enabling-multi-caret-editing"></a>Abilitazione della modifica con più caret

### <a name="keyboard"></a>Tastiera

È possibile abilitare la modalità multi-caret tramite la tastiera in diversi modi. Nella tabella seguente sono elencati i tasti di scelta rapida disponibili per l'immissione di modalità specifiche di modifica con più tasti di scelta rapida:

| Tasto di scelta rapida  | Azione                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Inserire il successivo caret corrispondente    | 
|  ⌥⇧;   | Inserire i caratteri di inserimento in corrispondenza di tutte le corrispondenze | 
|  ⌥⇧,   | Rimuovere l'ultimo caret             | 
|  ⌥⇧/   | Spostare l'ultimo caret verso il basso          | 

Ognuno di questi comportamenti è ancorato alla posizione corrente del cursore quando si richiama il comando. Ad esempio, se il punto di inserimento si trova all'inizio della parola "nome" e si richiama "Inserisci caret in corrispondenza di tutte le corrispondenze" (⌥⇧;) A ogni istanza della parola "name" nel documento corrente verrà inserito un punto di inserimento all'inizio della parola. Analogamente, se si richiama il comando "Insert next matching caret" (⌥⇧.), verrà inserito un punto di inserimento in corrispondenza dell'istanza successiva della parola "name". Questo comando può essere richiamato più volte.

![tastiera con più tasti di scelta rapida](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Mouse/touchpad

Usando il cursore, è possibile liberare i punti di inserimento specifici selezionati per più punti di inserimento. Anche se i tasti di scelta rapida sono associati a stringhe corrispondenti, è possibile inserire manualmente un cursore in un punto qualsiasi del documento con il cursore. Dopo aver impostato i punti di accesso, ognuno di essi riecheggia le voci dei tasti digitate sulla tastiera.

Per usare il mouse per inserire più punti di inserimento, è necessario tenere premuto ⌘⌥ e fare clic nel punto in cui si desidera inserire i punti di inserimento. Si sarà in modalità di inserimento fino a quando vengono mantenute le ⌥ di sospensione. Se si inserisce un punto di inserimento in una posizione non corretta, è possibile rimuovere il punto di inserimento continuando a tenere premuto ⌘⌥ e facendo di nuovo clic nella stessa area. Dopo aver posizionato tutti i punto di inserimento nel punto in cui si desidera, interrompere la pressione dei tasti ⌘⌥ e iniziare a digitare. La gif seguente illustra sia la selezione di un set di punti di inserimento che la rimozione di punti impostati erroneamente.

![mouse con più cursori](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Vedi anche

- [Azioni rapide (Visual Studio in Windows)](/visualstudio/ide/quick-actions)
- [Effettuare il refactoring del codice (Visual Studio in Windows)](/visualstudio/ide/refactoring-in-visual-studio)
