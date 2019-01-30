---
title: Suggerimenti sull'accessibilità per Visual Studio
description: Altre informazioni su suggerimenti e consigli che consentono di rendere l'ambiente di sviluppo integrato (IDE) di Visual Studio più accessibile da usare per tutti gli utenti, compresi gli utenti disabili.
ms.date: 09/15/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6451b45f8bb98232ea0c3a1b3cb96d37cf303ccc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010389"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Suggerimenti sull'accessibilità per Visual Studio

> [!TIP]
> Per altre informazioni sugli aggiornamenti di accessibilità recenti, visitare il post di blog sui [miglioramenti dell'accessibilità di Visual Studio 2017 (versione 15.3)](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/).

Visual Studio dispone di funzionalità di accessibilità integrate compatibili con utilità per la lettura dello schermo e altri tipi di Assistive Technology Program. Questo argomento elenca le comuni combinazioni di tasti di scelta rapida che è possibile usare per eseguire attività solo con la tastiera e comprende informazioni sull'uso di temi a contrasto elevato per migliorare la visibilità. Illustra anche come usare le annotazioni per rivelare informazioni utili sul proprio codice e come impostare i segnali sonori per gli eventi di build e punti di interruzione.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Accessibilità per Visual Studio per Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Salvare le impostazioni IDE

 È possibile personalizzare l'esperienza IDE salvando il layout delle finestre, lo schema di mappatura della tastiera e altre preferenze. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Modificare l'IDE per la visualizzazione a contrasto elevato

Per alcuni, alcuni colori sono più difficili da vedere. Se si desidera aumentare il contrasto durante la compilazione, ma non si desidera usare i temi tipici a "Contrasto elevato", Microsoft offre il tema "Blu (massimo contrasto)".

  ![Confronto tra il tema Blu e il tema Blu (massimo contrasto)](media/blue-extra-contrast-theme.png)

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Usare le annotazioni per rivelare informazioni utili sul proprio codice

L'editor di Visual Studio comprende molte "aree di controllo" del testo che consentono di conoscere caratteristiche e funzionalità in determinati punti su una riga di codice, come lampadine, controlli durante la digitazione per errori e avvisi, segnalibri e altro ancora. È possibile usare il set di comandi "Mostra annotazioni riga" per scoprire queste aree di controllo e spostarsi dall'una all'altra.

  ![Usare il set di comandi Mostra annotazioni riga](media/show-line-annotations-command-set.png)

## <a name="access-toolbars-by-using-shortcut-key-combinations"></a>Accedere alle barre degli strumenti tramite combinazioni di tasti

Come molte finestre degli strumenti, l'IDE di Visual Studio include alcune barre degli strumenti. Le combinazioni di tasti di scelta rapida seguenti consentono di accedervi.

|Funzionalità|Description|Combinazione di tasti|
|-------------|-----------------| - |
|Barre degli strumenti dell'IDE|Consente di selezionare il primo pulsante della barra degli strumenti Standard.|**ALT**, **CTRL** + **TAB**|
|Barre degli strumenti della finestra degli strumenti|Consentono di spostare lo stato attivo nelle barre degli strumenti in una finestra degli strumenti. <br> <br> **NOTA:** questo procedimento funziona per la maggior parte delle finestre degli strumenti, ma solo quando lo stato attivo è in una finestra degli strumenti. È anche necessario scegliere MAIUSC prima di ALT. In alcune finestre degli strumenti, ad esempio Team Explorer, è necessario tenere premuto MAIUSC per qualche istante prima di scegliere ALT.|**MAIUSC** + **ALT**|
|Barre degli strumenti|Consente di passare al primo elemento nella barra degli strumenti successiva (quando una barra degli strumenti ha lo stato attivo).|**CTRL** + **TAB**|

### <a name="other-useful-shortcut-key-combinations"></a>Altre combinazioni di tasti utili

Tra le altre combinazioni di tasti utili ricordiamo le seguenti.

|Funzionalità|Description|Combinazione di tasti|
|-------------|-----------------| - |
|IDE|Consente di attivare e disattivare l'impostazione Contrasto elevato. <br> <br> **NOTA:** scelta rapida standard di Windows|**ALT di sinistra + MAIUSC di sinistra + STAMP**|
|Finestra di dialogo|Consente di selezionare o deselezionare l'opzione di una casella di controllo in una finestra di dialogo. <br> <br> **NOTA:** scelta rapida standard di Windows|**BARRA SPAZIATRICE**|
|Menu di scelta rapida|Consentono di aprire un menu di scelta rapida (clic con il pulsante destro del mouse). <br> <br> **NOTA:** scelta rapida standard di Windows|**MAIUSC** + **F10**|
|Menu|Consente di accedere rapidamente a una voce di menu con i rispettivi tasti di scelta rapida. Scegliere **ALT** seguito dalle lettere sottolineate in un menu per attivare il comando. Ad esempio, per visualizzare la finestra di dialogo Apri progetto in Visual Studio selezionare **ALT** + **F** + **O** + **P**.  <br><br> **NOTA:** scelta rapida standard di Windows|**ALT** + **[lettera]**|
|Finestra della casella degli strumenti|Consente di passare da una scheda all'altra della casella degli strumenti.|**CTRL** + **Freccia SU**<br /><br /> e<br /><br /> **CTRL** + **Freccia GIÙ**|
|Finestra della casella degli strumenti|Consente di aggiungere un controllo della casella degli strumenti a un form o finestra di progettazione.|**INVIO**|
|Tastiera, Ambiente, finestra di dialogo Opzioni|Consente di eliminare una combinazione di tasti immessa nell'opzione **Premi tasti di scelta rapida**.|**BACKSPACE**|

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Usare l'applet Suono per impostare suggerimenti di compilazione e punti di interruzione

Per assegnare un suono a eventi di Visual Studio, è possibile usare l'applet Suono in Windows. In particolare, è possibile assegnare suoni agli eventi seguenti:

 * Punto di interruzione raggiunto
 * Compilazione annullata
 * Compilazione non riuscita
 * Compilazione completata

Ecco come fare.

1. Nella casella **Ricerca** in un computer con Windows 10, digitare **Cambia segnali acustici emessi dal sistema**.

   ![Casella di ricerca in Windows 10](media/type-here-to-search.png)

   (In alternativa, se è abilitato Cortana, pronunciare "Ehi Cortana", quindi pronunciare "Cambia segnali acustici emessi dal sistema".)

2. Fare doppio clic su **Cambia segnali acustici emessi dal sistema**.

   ![Risultati della ricerca in Windows 10](media/change-system-sounds.png)

3. Nella finestra di dialogo **Suono**, fare clic sulla scheda **Suoni**. <br><br>
   Quindi, in **Eventi**, scorrere fino a **Microsoft Visual Studio**e selezionare i suoni che si desidera applicare agli eventi scelti.

   ![Scheda Suoni dell'applet Audio in Windows 10](media/sound-applet.png)

4. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

* [Funzionalità di accessibilità di Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Procedura: Personalizzare menu e barre degli strumenti in Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Accessibilità Microsoft](https://www.microsoft.com/Accessibility)
* [Accessibilità (Visual Studio per Mac)](/visualstudio/mac/accessibility)