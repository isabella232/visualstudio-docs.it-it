---
title: Sincronizzare le impostazioni
ms.date: 12/10/2018
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f7183f20139df82d14f80ee4b57e28b4aed3a66
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566787"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Sincronizzare le impostazioni di Visual Studio in più computer

Quando si usa lo stesso account di personalizzazione per accedere a Visual Studio da più computer, è possibile sincronizzare le proprie impostazioni in tutti i computer.

## <a name="synchronized-settings"></a>Impostazioni sincronizzate

Per impostazione predefinita, vengono sincronizzate le impostazioni seguenti:

- Impostazioni di sviluppo. La raccolta di impostazioni viene selezionata la prima volta che si apre Visual Studio, ma è possibile modificare la selezione in qualsiasi momento. Per altre informazioni, vedere [Impostazioni dell'ambiente](../ide/environment-settings.md).

- Alias di comandi definiti dall'utente. Per altre informazioni su come definire gli alias di comandi, vedere [Alias di comandi di Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Layout di finestra definiti dall'utente **nella** > pagina**Gestisci layout di finestra.**

- Nelle pagine Opzioni **degli strumenti,** > **Options** le seguenti opzioni sono disponibili:

  - Impostazioni del tema e della barra dei menu nella pagina delle opzioni**Generale** **ambiente.** > 

  - Tutte le impostazioni nella pagina delle opzioni**Tipi di carattere e colori** **dell'ambiente.** > 

  - Tutti i tasti di scelta rapida nella pagina delle opzioni**Tastiera** **ambiente.** > 

  - Tutte le **Environment** > impostazioni nella pagina**Schede ambiente e opzioni di Windows.**

  - Tutte le impostazioni nella pagina delle opzioni**di avvio** **dell'ambiente.** > 

  - Tutte le impostazioni nella pagina delle opzioni **Editor di testo**, ad esempio le [preferenze di stile per il codice](code-styles-and-code-cleanup.md).

  - Tutte le impostazioni nelle pagine delle opzioni della **finestra di progettazione XAML.**

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Disattivare le impostazioni sincronizzate per un computer specifico

Le impostazioni sincronizzate per Visual Studio sono attivate per impostazione predefinita. È possibile disattivare le impostazioni sincronizzate in un computer accedendo alla**pagina** **Tools** > **Strumenti Opzioni** > **account ambiente** > e deselezionando **Sincronizza impostazioni tra dispositivi dopo l'accesso a Visual Studio**.

Se, ad esempio, si decide di non sincronizzare le impostazioni di Visual Studio nel computer "A", le modifiche delle impostazioni apportate nel computer "A" non verranno visualizzate nel computer "B" o nel computer "C". I computer "B" e "C" continueranno a sincronizzarsi tra di loro, ma non con il computer "A".

> [!NOTE]
> Se si sceglie di non sincronizzare le impostazioni deselezionando l'opzione nella pagina **Strumenti** > **Opzioni** > **account** **di ambiente,** > altre versioni o edizioni di Visual Studio disponibili nello stesso computer non sono interessate. Tali installazioni side-by-side di Visual Studio continueranno a sincronizzare le impostazioni (a meno che non si deseleziona anche l'opzione).

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Sincronizzare le impostazioni tra prodotti e edizioni della famiglia Visual Studio

Le impostazioni vengono sincronizzate nelle versioni e nelle edizioni di Visual Studio installate *side-by-side*. Le impostazioni vengono sincronizzate anche nei prodotti della famiglia Visual Studio, come ad esempio Blend per Visual Studio. Tuttavia, ogni prodotto di questa famiglia può avere impostazioni proprie che non vengono condivise con Visual Studio. Ad esempio, le impostazioni specifiche per Blend per Visual Studio nel computer "A"non vengono condivise con Visual Studio nei computer "A" o "B".

## <a name="side-by-side-synchronized-settings"></a>Impostazioni sincronizzate affiancate

::: moniker range="vs-2017"

Alcune impostazioni, ad esempio il layout delle finestre degli strumenti, non vengono condivise tra diverse installazioni side-by-side di Visual Studio. Il file *CurrentSettings.vssettings* in *%userprofile%\Documents\Visual Studio 2017\Settings* si trova in una cartella specifica dell'installazione simile a *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*.

> [!NOTE]
> Per usare le impostazioni specifiche di una nuova installazione, eseguire una nuova installazione. Quando si aggiorna un'installazione esistente di Visual Studio, usa il percorso condiviso esistente.

Se attualmente sono presenti installazioni side-by-side di Visual Studio e si vuole usare il percorso del file delle impostazioni specifico della nuova installazione, seguire questa procedura:

1. Eseguire l'aggiornamento a Visual Studio 2017 versione 15.3 o successiva.

2. Usare l'**Importazione/Esportazione guidata delle impostazioni** per esportare tutte le impostazioni esistenti in un percorso esterno alla cartella *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx*.

3. Aprire il **Prompt dei comandi per gli sviluppatori per VS 2017** ed eseguire `devenv /resetuserdata`.

1. Aprire Visual Studio e importare le impostazioni salvate dal file di impostazioni esportato.

::: moniker-end

::: moniker range=">=vs-2019"

Alcune impostazioni, ad esempio il layout delle finestre degli strumenti, non vengono condivise tra diverse installazioni side-by-side di Visual Studio. Il file *CurrentSettings.vssettings* in *%userprofile%\Documenti\Visual Studio 2019\Settings* si trova in una cartella specifica dell'installazione simile a *%localappdata%\Microsoft\VisualStudio\16.0_xxxxxxxx\Settings*.

::: moniker-end

## <a name="reset-synchronized-settings"></a>Reimpostare le impostazioni sincronizzate

Per ripristinare tutte le impostazioni predefinite, accedere a Visual Studio, quindi selezionare **Strumenti** > **importa/Esporta impostazioni** per aprire l'Importazione/Esportazione guidata **impostazioni**. Selezionare **Reimposta tutte le impostazioni** e quindi seguire i passaggi rimanenti della procedura guidata.

## <a name="see-also"></a>Vedere anche

- [Personalizzare l'IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Impostazioni di ambiente](../ide/environment-settings.md)
- [Ambiente > Account, finestra di dialogo Opzioni](reference/accounts-environment-options-dialog-box.md)
