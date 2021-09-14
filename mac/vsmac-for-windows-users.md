---
title: Visual Studio per Mac per Windows utenti
description: Introduzione al Visual Studio per Mac per gli sviluppatori che hanno familiarità con l'Visual Studio nel Windows operativo.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: 880811c675aac34a18a65c6eccb8ee10f3347d4c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710443"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Visual Studio per Mac per Windows utenti

La migrazione da un sistema operativo a un altro può essere un'attività disgraziata. Esistono spesso piccole differenze nelle applicazioni multipiattaforma, dall'interfaccia utente alla categorizzazione delle voci di menu. Di seguito vengono apprese le differenze più comuni tra Visual Studio per Mac e Visual Studio per Windows. Verranno inoltre apprese alcune convenzioni diverse tra macOS e Windows.

## <a name="keyboard-shortcuts"></a>Tasti di scelta rapida

Gli sviluppatori sono abituati a usare la tastiera per le attività e la navigazione. Alcuni tasti della tastiera sono comuni tra Mac e Windows PC. Si potrebbe pensare che le azioni da tastiera, ad esempio copia e incolla, usino le stesse combinazioni di tasti. Questo non è sempre il caso. Fortunatamente, è possibile modificare i tasti di scelta Visual Studio per Mac in modo che corrispondano a quelli Visual Studio in Windows.

La prima volta che si esegue Visual Studio per Mac verrà visualizzata la finestra di selezione dei tasti di scelta rapida: ![ Tasti di scelta rapida](media/ide-tour-2019-keyboard-shortcut.png)

Se si vogliono modificare i tasti di scelta in un secondo momento, è possibile trovare l'impostazione nelle preferenze: ![ Preferenze dei tasti di scelta](media/customizing-the-ide-image10a.png)

È importante notare che macOS usa diversi collegamenti a livello di sistema per Windows. La modifica delle preferenze di tasti di scelta rapida consentirà di usare i tasti di scelta Windows in Visual Studio per Mac. Tuttavia, in altre aree di macOS è necessario avere familiarità con i tasti di scelta rapida di macOS.

Il tasto di modifica comando macOS (⌘) può in genere sostituire il tasto CTRL in Windows. Ecco alcuni esempi e altri tasti di scelta rapida di uso comune:

|Attività                   |Windows Scelta rapida         |Collegamento macOS      |
|-----------------------|-------------------------|--------------------|
|Copia                   |`Ctrl + C`               |`⌘ + C`             |
|Incolla                  |`Ctrl + V`               |`⌘ + V`             |
|Taglia                    |`Ctrl + X`               |`⌘ + X`             |
|Annulla                   |`Ctrl + Z`               |`⌘ + Z`             |
|Ripeti                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|Elimina a destra del cursore |`Delete`                 |`fn + Backspace`    |
|Eliminare una parola            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> È possibile trovare un elenco completo dei collegamenti macOS nel sito Web [del supporto apple.](https://support.apple.com/en-us/HT201236)

## <a name="menus"></a>Menu

I menu in macOS sono organizzati in modo diverso rispetto ai menu in Windows. Visual Studio per Mac non è un'eccezione. Alcune delle opzioni di menu più comuni sono disponibili qui:

|Attività                   |Visual Studio (Windows)                                              |Visual Studio per Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Preferenze (opzioni)  |Strumenti > opzioni...                                                   |Visual Studio > preferenze...       |
|Estensioni             |Estensioni > gestione estensioni                                       |Visual Studio >...        |
|Layout                |Finestra > Applica layout finestra > [Seleziona layout]                       |Visualizzare > layout > [Selezionare il layout]               |
|Aggiornamenti                |Guida > verificare la disponibilità di aggiornamenti                                             |Visual Studio > verificare la disponibilità di aggiornamenti... |
|Gestione pacchetti NuGet  |Strumenti > NuGet Gestione pacchetti > gestione NuGet pacchetti o soluzione... |Project > gestire NuGet pacchetti...   |
|Trovare gli strumenti             |Modifica > trova e sostituisci > [strumento Seleziona]                              |Cerca > [strumento Seleziona]               |
|Informazioni su Visual Studio    |Guida > informazioni Microsoft Visual Studio                                 |Visual Studio > informazioni Visual Studio  

> [!NOTE]
> È possibile trovare una panoramica delle funzionalità più comuni in Visual Studio per Mac nella presentazione [dell'IDE](ide-tour.md)