---
title: Visual Studio per Mac per gli utenti di Windows
description: Introduzione a Visual Studio per Mac per gli sviluppatori che hanno familiarità con l'uso di Visual Studio nel sistema operativo Windows.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: 880811c675aac34a18a65c6eccb8ee10f3347d4c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493374"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Visual Studio per Mac per gli utenti di Windows

La migrazione da un sistema operativo a un altro può risultare complessa. Le applicazioni multipiattaforma hanno spesso differenze minime, dall'interfaccia utente alla categorizzazione delle voci di menu. In questo articolo verranno illustrate le differenze più comuni tra Visual Studio per Mac e Visual Studio per Windows. Si apprenderanno anche alcune convenzioni diverse tra macOS e Windows.

## <a name="keyboard-shortcuts"></a>Tasti di scelta rapida

Per gli sviluppatori, molti di voi saranno abituati a usare la tastiera per le attività e la navigazione. Alcuni tasti sulla tastiera sono comuni tra i computer Mac e Windows. Si potrebbe essere perdonato per pensare che le azioni da tastiera come copia e incolla usino le stesse combinazioni di tasti. Questo non è sempre il caso. Per fortuna, è possibile modificare le combinazioni di tasti in Visual Studio per Mac in modo da corrispondere a quelle di Visual Studio in Windows.

La prima volta che si esegue Visual Studio per Mac verrà visualizzata la finestra di selezione scelte rapide da tastiera: finestra tasti di scelta rapida ![](media/ide-tour-2019-keyboard-shortcut.png)

Se si desidera modificare i tasti di scelta delle chiavi in un secondo momento, è possibile trovare l'impostazione nella pagina Preferenze: ![ combinazioni di tasti](media/customizing-the-ide-image10a.png)

È importante notare che macOS usa diversi collegamenti a livello di sistema a Windows. Se si modificano le preferenze di associazione chiave, sarà possibile utilizzare i collegamenti familiari di Windows in Visual Studio per Mac. Tuttavia, in altre aree di macOS è necessario avere familiarità con i collegamenti macOS.

Il tasto di modifica del comando macOS (⌘) può in genere sostituire la chiave di controllo in Windows. Di seguito sono riportati alcuni esempi e altri tasti di scelta rapida usati di frequente:

|Attività                   |Collegamento di Windows         |Collegamento macOS      |
|-----------------------|-------------------------|--------------------|
|Copia                   |`Ctrl + C`               |`⌘ + C`             |
|Incolla                  |`Ctrl + V`               |`⌘ + V`             |
|Taglia                    |`Ctrl + X`               |`⌘ + X`             |
|Annulla                   |`Ctrl + Z`               |`⌘ + Z`             |
|Ripristinare                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|Elimina a destra del cursore |`Delete`                 |`fn + Backspace`    |
|Elimina Word            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> È possibile trovare un elenco completo dei collegamenti macOS nel [sito Web del supporto Apple](https://support.apple.com/en-us/HT201236).

## <a name="menus"></a>Menu

I menu in macOS sono organizzati in modo diverso rispetto ai menu di Windows. Visual Studio per Mac non è un'eccezione. È possibile trovare alcune delle opzioni di menu più comuni:

|Attività                   |Visual Studio (Windows)                                              |Visual Studio per Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Preferenze (opzioni)  |Strumenti > opzioni...                                                   |Preferenze di Visual Studio >...       |
|Estensioni             |Estensioni > gestire le estensioni                                       |Estensioni di Visual Studio >...        |
|Layout                |Finestra > applicare il layout della finestra > [selezionare il layout]                       |Visualizzazione del layout > > [selezionare il layout]               |
|Aggiornamenti                |Guida > verificare la disponibilità di aggiornamenti                                             |Verifica della disponibilità di aggiornamenti in Visual Studio >... |
|Gestione pacchetti NuGet  |Strumenti > gestione pacchetti NuGet > gestire pacchetti NuGet o soluzioni... |Progetto > Gestisci pacchetti NuGet...   |
|Trova strumenti             |Modifica > trova e Sostituisci > [Seleziona strumento]                              |Cerca > [Seleziona strumento]               |
|Informazioni su Visual Studio    |> della guida sulle Microsoft Visual Studio                                 |Visual Studio > su Visual Studio  

> [!NOTE]
> Per una panoramica delle funzionalità più comuni, vedere Visual Studio per Mac nella presentazione dell' [IDE](ide-tour.md)