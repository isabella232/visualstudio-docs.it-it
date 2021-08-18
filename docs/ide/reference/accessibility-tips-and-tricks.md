---
title: Suggerimenti sull'accessibilità per Visual Studio
description: Altre informazioni su suggerimenti e consigli che consentono di rendere l'ambiente di sviluppo integrato (IDE) di Visual Studio più accessibile da usare per tutti gli utenti, compresi gli utenti disabili.
ms.date: 08/06/2019
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 899d44ff13ae9c94309757363a96b814e5e3e531
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041347"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Suggerimenti sull'accessibilità per Visual Studio

Visual Studio dispone di funzionalità di accessibilità integrate compatibili con utilità per la lettura dello schermo e altri tipi di Assistive Technology Program. Sia che si vogliano usare i tasti di scelta rapida per spostarsi nell'IDE o usare temi a contrasto elevato per migliorare la visibilità, in questa pagina è possibile trovare diversi suggerimenti che illustrano come fare.

Viene illustrato anche come usare le annotazioni per rivelare informazioni utili sul proprio codice e come impostare i segnali sonori per gli eventi di build e punti di interruzione.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Accessibilità per Visual Studio per Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Salvare le impostazioni IDE

È possibile personalizzare l'esperienza IDE salvando il layout delle finestre, lo schema di mappatura della tastiera e altre preferenze. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../../ide/personalizing-the-visual-studio-ide.md)

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Modificare l'IDE per la visualizzazione a contrasto elevato

Per alcuni, alcuni colori sono più difficili da vedere. Se si vuole aumentare il contrasto durante la compilazione, ma non si vuole usare i temi tipici a "Contrasto elevato", Microsoft offre il tema "Blu (massimo contrasto)".

  ![Confronto tra il tema Blu e il tema Blu (massimo contrasto)](media/blue-extra-contrast-theme.png "Screenshot che mostra un confronto tra il tema Blu e il tema Blu a contrasto aggiuntivo")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Usare le annotazioni per rivelare informazioni utili sul proprio codice

L'editor di Visual Studio comprende molte "aree di controllo" del testo che consentono di conoscere caratteristiche e funzionalità in determinati punti su una riga di codice, come icone a forma di cacciavite e lampadina, controlli durante la digitazione per errori e avvisi, segnalibri e altro ancora. È possibile usare il set di comandi "Mostra annotazioni riga" per scoprire queste aree di controllo e spostarsi dall'una all'altra.

  ![Usare il set di comandi Mostra annotazioni riga](media/show-line-annotations-command-set.png "Screenshot della voce di menu Mostra annotazioni riga")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>Accedere alle barre degli strumenti tramite tasti di scelta rapida

Come molte finestre degli strumenti, l'IDE di Visual Studio include alcune barre degli strumenti. I seguenti tasti di scelta rapida consentono di accedervi.

|Funzionalità|Descrizione|Tasti di scelta rapida|
|-------------|-----------------| - |
|Barre degli strumenti dell'IDE|Consente di selezionare il primo pulsante della barra degli strumenti Standard.|**ALT,**  + **CTRL+TAB**|
|Barre degli strumenti della finestra degli strumenti|Consentono di spostare lo stato attivo nelle barre degli strumenti in una finestra degli strumenti. <br> <br> **NOTA:** questo procedimento funziona per la maggior parte delle finestre degli strumenti, ma solo quando lo stato attivo è in una finestra degli strumenti. È anche necessario scegliere MAIUSC prima di ALT. In alcune finestre degli strumenti, ad esempio Team Explorer, è necessario tenere premuto MAIUSC per qualche istante prima di scegliere ALT.|**MAIUSC** + **ALT**|
|Barre degli strumenti|Consente di passare al primo elemento nella barra degli strumenti successiva (quando una barra degli strumenti ha lo stato attivo).|**CTRL** + **Scheda**|

### <a name="other-useful-keyboard-shortcuts"></a>Altri tasti di scelta rapida utili

Di seguito sono riportate altri tasti di scelta rapida utili.

|Funzionalità|Descrizione|Tasti di scelta rapida|
|-------------|-----------------| - |
|IDE|Consente di attivare e disattivare l'impostazione Contrasto elevato. <br> <br> **NOTA:** Tasto di scelta Windows standard|**ALT di sinistra** + **Spostamento a sinistra** + **PrtScn**|
|Finestra di dialogo|Consente di selezionare o deselezionare l'opzione di una casella di controllo in una finestra di dialogo. <br> <br> **NOTA:** Tasto di scelta Windows standard|**BARRA SPAZIATRICE**|
|Menu di scelta rapida|Consentono di aprire un menu di scelta rapida (clic con il pulsante destro del mouse). <br> <br> **NOTA:** Tasto di scelta Windows standard|**MAIUSC** + **F10**|
|Menu|Consente di accedere rapidamente a una voce di menu con i rispettivi tasti di scelta rapida. Premere **ALT** seguito dalle lettere sottolineate in un menu per attivare il comando. Ad esempio, per visualizzare la finestra di Project apri in Visual Studio, scegliere **ALT** + **F** + **O** + **P**.  <br><br> **NOTA:** Tasto di scelta Windows standard|**ALT**  +  **[lettera]**|
|Casella di ricerca|Usare la funzionalità di ricerca in Visual Studio.|**CTRL** + **Q**|
|Finestra della casella degli strumenti|Consente di passare da una scheda all'altra della casella degli strumenti.|**CTRL** + **Freccia SU**<br /><br /> e<br /><br /> **CTRL** + **Freccia GIÙ**|
|Finestra della casella degli strumenti|Consente di aggiungere un controllo della casella degli strumenti a un form o finestra di progettazione.|**INVIO**|
|Finestra di dialogo Opzioni: Ambiente > tastiera|Consente di eliminare una combinazione di tasti immessa nell'opzione **Premi tasti di scelta rapida**.|**Backspace**|
|Finestra degli strumenti Notifiche|Aprire la finestra degli strumenti Notifiche usando due combinazioni di tasti di scelta rapida, una dopo l'altra. Quindi, visualizzare una notifica usando i tasti di direzione per selezionarla.| **CTRL** + **&#92;**, **CTRL** + **N**|

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso.

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>Accedere alle notifiche tramite tasti di scelta rapida

Di seguito viene illustrato come accedere alla finestra notifiche tramite tasti di scelta rapida quando viene visualizzata una notifica nell'IDE:

1. Da qualsiasi punto dell'IDE premere i due tasti di scelta rapida seguenti in sequenza, uno dopo l'altro: **CTRL** + **&#92;** e **quindi CTRL** + **N**.

   Verrà visualizzata la finestra **Notifiche**.

   ![Finestra degli strumenti notifiche nell'IDE Visual Studio notifiche](media/toast-notification.png "Screenshot della finestra Notifiche nell'IDE Visual Studio")

1. Usare il tasto **TAB** o i tasti di direzione per selezionare una notifica.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Usare l'applet Suono per impostare suggerimenti di compilazione e punti di interruzione

Per assegnare un suono a eventi di Visual Studio, è possibile usare l'applet Suono in Windows. In particolare, è possibile assegnare suoni agli eventi seguenti:

* Punto di interruzione raggiunto
* Compilazione annullata
* Compilazione non riuscita
* Compilazione completata

Ecco come:

1. Nella casella **Ricerca** in un computer con Windows 10, digitare **Cambia segnali acustici emessi dal sistema**.

   ![Casella di ricerca in Windows 10](media/type-here-to-search.png "Screenshot della casella di ricerca in Windows 10")

   (In alternativa, se è abilitato Cortana, pronunciare "Ehi Cortana", quindi pronunciare "Cambia segnali acustici emessi dal sistema".)

1. Fare doppio clic su **Cambia segnali acustici emessi dal sistema**.

   ![Risultati della ricerca in Windows 10](media/change-system-sounds.png "Screenshot dei risultati della ricerca &quot;Cambia suoni di sistema&quot; in Windows 10")

1. Nella finestra di dialogo **Suono**, fare clic sulla scheda **Suoni**.

1. In **Eventi** scorrere fino a **Microsoft Visual Studio** e quindi selezionare i suoni che si vogliono applicare agli eventi scelti.

   ![Scheda Suoni dell'applet Audio in Windows 10](media/sound-applet.png "Scheda Suoni dell'applet Audio in Windows 10")

1. Fare clic su **OK**.

::: moniker range="vs-2017"

> [!TIP]
> Per altre informazioni sugli aggiornamenti di accessibilità, visitare il post di blog sui [miglioramenti dell'accessibilità di Visual Studio 2017 versione 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/).

::: moniker-end

## <a name="see-also"></a>Vedi anche

* [Funzionalità di accessibilità di Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Procedura: Personalizzare menu e barre degli strumenti in Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Accessibilità (Visual Studio per Mac)](/visualstudio/mac/accessibility)
* [Accessibilità Microsoft](https://www.microsoft.com/Accessibility)
