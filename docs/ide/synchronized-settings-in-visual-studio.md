---
title: Sincronizzare le impostazioni
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7dcddc06233f439547f0725c1fb39fff26152237
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348419"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Sincronizzare le impostazioni di Visual Studio in più computer

Quando si usa lo stesso account di personalizzazione per accedere a Visual Studio da più computer, è possibile sincronizzare le proprie impostazioni in tutti i computer.

## <a name="synchronized-settings"></a>Impostazioni sincronizzate

Per impostazione predefinita, vengono sincronizzate le impostazioni seguenti:

- Impostazioni di sviluppo. La raccolta di impostazioni viene selezionata la prima volta che si apre Visual Studio, ma è possibile modificare la selezione in qualsiasi momento. Per altre informazioni, vedere [Impostazioni dell'ambiente](../ide/environment-settings.md).

- Alias di comandi definiti dall'utente. Per altre informazioni su come definire gli alias di comandi, vedere [Alias di comandi di Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Layout di finestra definiti dall'utente nella pagina **Finestra** > **Gestisci layout finestra**.

- Le opzioni seguenti nelle pagine **Strumenti** > **Opzioni**:

   - Impostazioni del tema e di maiuscole e minuscole nella barra dei menu nella pagina delle opzioni **Ambiente** > **Generale**.

   - Tutte le impostazioni nella pagina delle opzioni **Ambiente** > **Tipi di carattere e colori**.

   - Tutti i tasti di scelta rapida nella pagina delle opzioni **Ambiente** > **Tastiera**.

   - Tutte le impostazioni nella pagina delle opzioni **Ambiente** > **Schede e finestre**.

   - Tutte le impostazioni nella pagina delle opzioni **Ambiente** > **Avvio**.

   - Tutte le impostazioni nelle pagine delle opzioni **Editor di testo**.

   - Tutte le impostazioni nelle pagine delle opzioni della **finestra di progettazione XAML**.

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Disattivare le impostazioni sincronizzate per un computer specifico

Le impostazioni sincronizzate per Visual Studio sono attivate per impostazione predefinita. Per disattivare le impostazioni sincronizzate in un computer passare alla pagina **Strumenti** > **Opzioni** > **Ambiente** > **Account** e deselezionare **Sincronizza le impostazioni in tutti i dispositivi durante l'accesso a Visual Studio**.

Se, ad esempio, si decide di non sincronizzare le impostazioni di Visual Studio nel computer "A", le modifiche delle impostazioni apportate nel computer "A" non verranno visualizzate nel computer "B" o nel computer "C". I computer "B" e "C" continueranno a sincronizzarsi tra di loro, ma non con il computer "A".

> [!NOTE]
> Se si sceglie di non sincronizzare le impostazioni deselezionando l'opzione nella pagina **Strumenti** > **Opzioni** > **Ambiente** > **Account**, altre versioni o edizioni di Visual Studio in uso nello stesso computer non saranno interessate. Tali installazioni side-by-side di Visual Studio continueranno a sincronizzare le impostazioni (a meno che non si deseleziona anche l'opzione).

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Sincronizzare le impostazioni tra prodotti e edizioni della famiglia Visual Studio

Le impostazioni vengono sincronizzate nelle versioni e nelle edizioni di Visual Studio installate *side-by-side*. Le impostazioni vengono sincronizzate anche nei prodotti della famiglia Visual Studio, come ad esempio Blend per Visual Studio. Tuttavia, ogni prodotto di questa famiglia può avere impostazioni proprie che non vengono condivise con Visual Studio. Ad esempio, le impostazioni specifiche per Blend per Visual Studio nel computer "A"non vengono condivise con Visual Studio nei computer "A" o "B".

## <a name="side-by-side-synchronized-settings"></a>Impostazioni sincronizzate affiancate

In Visual Studio 2017 versione 15.3 e successive alcune impostazioni, ad esempio il layout della finestra degli strumenti, non vengono condivise tra le diverse installazioni side-by-side di Visual Studio 2017. Il file *CurrentSettings.vssettings* in *%userprofile%\Documents\Visual Studio 2017\Settings* si trova in una cartella specifica dell'installazione simile a *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*.

> [!NOTE]
> Per usare le impostazioni specifiche di una nuova installazione, eseguire una nuova installazione. Quando si esegue l'aggiornamento di un'installazione esistente di Visual Studio 2017 alla versione più recente, viene usato il percorso condiviso esistente.

Se attualmente sono presenti installazioni side-by-side di Visual Studio 2017 e si vuole usare il percorso del file delle impostazioni specifico della nuova installazione, seguire questa procedura:

1. Eseguire l'aggiornamento a Visual Studio 2017 versione 15.3 o successiva.

1. Usare l'**Importazione/Esportazione impostazioni** per esportare tutte le impostazioni esistenti in un percorso esterno alla cartella *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx*.

1. Aprire il **Prompt dei comandi per gli sviluppatori per VS 2017** dell'installazione aggiornata di Visual Studio ed eseguire `devenv /resetuserdata`.

1. Avviare Visual Studio e importare le impostazioni salvate dal file di impostazioni esportato.

## <a name="see-also"></a>Vedere anche

- [Personalizzare l'IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Impostazioni dell'ambiente](../ide/environment-settings.md)
- [Ambiente > Account, finestra di dialogo Opzioni](reference/accounts-environment-options-dialog-box.md)
