---
title: Utenti di Visual Studio per Mac per Windows
description: Introduzione delle funzionalità di accessibilità in Visual Studio per Mac e come possono essere abilitate.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/25/2019
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: b414026ba7297dd6c93fecdf56d9a9c58c99f294
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984263"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Utenti di Visual Studio per Mac per Windows

La migrazione da un sistema operativo a un altro può essere scoraggiante. Ci sono spesso sottili differenze nelle applicazioni multipiattaforma, dall'interfaccia utente alla categorizzazione delle voci di menu. Gli utenti avranno anche la curva di apprendimento di acclimatare all'interfaccia utente del nuovo sistema operativo. Qui si apprenderanno le differenze più comuni tra Visual Studio per Mac e Visual Studio per Windows. Imparerai anche alcune convenzioni diverse tra macOS e Windows.

## <a name="keyboard-shortcuts"></a>Tasti di scelta rapida

Come sviluppatori, molti di voi saranno abituati a utilizzare la tastiera per le attività e la navigazione. Alcuni tasti della tastiera sono comuni tra Mac e PC Windows. Si potrebbe essere perdonato per pensare che le azioni della tastiera come copia e incolla utilizzano le stesse combinazioni di tasti. Questo non è sempre il caso. Fortunatamente, è possibile modificare le associazioni di tasti in Visual Studio per Mac in modo che corrispondano da vicino a quelle di Visual Studio in Windows.

La prima volta che si esegue Visual Studio per Mac ![verrà visualizzata la finestra di selezione dei tasti di scelta rapida: finestra Associazioni tasti](media/ide-tour-2019-keyboard-shortcut.png)

Se si desidera modificare i tasti di scelta rapida in ![un secondo momento, è possibile trovare l'impostazione nelle preferenze: Preferenze associazioni di tasti](media/customizing-the-ide-image10a.png)

È importante notare che macOS utilizza diversi collegamenti a livello di sistema per Windows. La modifica delle preferenze di associazione dei tasti consentirà di usare i familiari collegamenti di Windows in Visual Studio per Mac.Changing the key binding preferences will will allow you to use familiar Windows shortcuts in Visual Studio for Mac. Tuttavia, in altre aree di macOS dovrai avere familiarità con le scorciatoie di macOS.

Il tasto di modifica comando di macOS (Sezione ) può in genere sostituire il tasto Ctrl in Windows. Ecco alcuni esempi e altri tasti di scelta rapida di uso comune:Here are some examples, and other commonly used shortcuts:

|Attività                   |Scelta rapida di Windows         |Scorciatoia macOS      |
|-----------------------|-------------------------|--------------------|
|Copiare                   |`Ctrl + C`               |`⌘ + C`             |
|Incolla                  |`Ctrl + V`               |`⌘ + V`             |
|Taglia                    |`Ctrl + X`               |`⌘ + X`             |
|Annullamento                   |`Ctrl + Z`               |`⌘ + Z`             |
|Ripristinare                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|Elimina a destra del cursore |`Delete`                 |`fn + Backspace`    |
|Elimina parola            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> Puoi trovare un elenco completo di scorciatoie per macOS sul sito web del [supporto Apple.](https://support.apple.com/en-us/HT201236)

## <a name="menus"></a>Menu

I menu in macOS sono organizzati in modo diverso rispetto ai menu in Windows. Visual Studio per Mac non fa eccezione. Puoi trovare alcune delle opzioni di menu più comuni qui:

|Attività                   |Visual Studio (Windows)                                              |Visual Studio per Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Preferenze (Opzioni)  |Strumenti > Opzioni...                                                   |Preferenze di Visual Studio >...       |
|Estensioni             |Estensioni > Gestire le estensioni                                       |Estensioni di Visual Studio >...        |
|Layout                |Finestra > Applica layout di finestra > [Seleziona layout]                       |Visualizza > [Seleziona layout]               |
|Aggiornamenti                |> della Guida verificare la disponibilità di aggiornamenti                                             |Visual Studio > Verifica disponibilità aggiornamenti... |
|Gestione pacchetti NuGet  |Strumenti > Gestione pacchetti NuGet > Gestisci pacchetti NuGet o soluzione... |Progetto > Gestisci pacchetti NuGet...   |
|Pad / Windows         |Visualizza > [Seleziona pad / finestra]                                         |Visualizza > Pads > [Seleziona pad / finestra]  |
|Trova strumenti             |Modifica > > di ricerca e sostituzione [Strumento Seleziona]                              |Cerca > [Strumento Di selezione]               |
|Informazioni su Visual Studio    |> della Guida su Microsoft Visual Studio                                 |Visual Studio > informazioni su Visual Studio  

> [!NOTE]
> È possibile trovare una panoramica delle funzionalità più comuni in Visual Studio per Mac nel [tour IDE](ide-tour.md)