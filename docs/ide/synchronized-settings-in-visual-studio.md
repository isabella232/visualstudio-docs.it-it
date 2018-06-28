---
title: Sincronizzare le impostazioni
ms.date: 01/23/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 633767e66a4b3d976999574c885a3e6f7a06ddcf
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766129"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Sincronizzare le impostazioni di Visual Studio in più computer

Quando si usa lo stesso account di personalizzazione per accedere a Visual Studio da più computer, è possibile sincronizzare le proprie impostazioni in tutti i computer.

## <a name="synchronized-settings"></a>Impostazioni sincronizzate

Per impostazione predefinita, vengono sincronizzate le impostazioni seguenti:

- Impostazioni di sviluppo. È necessario selezionare un set di impostazioni la prima volta che si esegue Visual Studio, ma è possibile modificare la selezione in qualsiasi momento. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

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

Le impostazioni sincronizzate per Visual Studio sono attivate per impostazione predefinita. Per disattivare le impostazioni sincronizzate in un computer passare alla pagina **Strumenti** > **Opzioni** > **Ambiente** > **Account** e deselezionare **Sincronizza le impostazioni in tutti i dispositivi durante l'accesso a Visual Studio**. Se, ad esempio, si decide di non sincronizzare le impostazioni di Visual Studio nel computer "A", le modifiche delle impostazioni apportate nel computer "A" non verranno visualizzate nel computer "B" o nel computer "C". I computer "B" e "C" continueranno a sincronizzarsi tra di loro, ma non con il computer "A".

## <a name="reset-settings"></a>Reimpostare le impostazioni

È possibile reimpostare tutte le impostazioni su una raccolta di impostazioni predefinite seguendo questa procedura:

1. In Visual Studio selezionare **Strumenti** > **Importa/Esporta impostazioni** per aprire l'**Importazione/Esportazione guidata delle impostazioni**.

1. Nell'**Importazione/Esportazione guidata delle impostazioni** selezionare **Reimposta tutte le impostazioni** e quindi selezionare **Avanti**.

   ![Importazione/Esportazione guidata delle impostazioni in Visual Studio](media/reset-all-settings.png)

1. Nella pagina **Salvare le impostazioni correnti** selezionare **Sì** o **No** e quindi **Avanti**.

1. Nella pagina **Scegliere una raccolta di impostazioni predefinita** scegliere una raccolta e quindi selezionare **Fine**.

   ![Raccolte di impostazioni in Visual Studio](media/settings-collections.png)

1. Nella pagina **Reimpostazione completa** selezionare **Chiudi**.

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Sincronizzare le impostazioni tra prodotti e edizioni della famiglia Visual Studio

Le impostazioni possono essere sincronizzate tra tutte le edizioni di Visual Studio, compresa la Community Edition. Le impostazioni vengono sincronizzate anche tra prodotti della famiglia Visual Studio. Tuttavia, ogni prodotto di questa famiglia può avere impostazioni proprie che non vengono condivise con Visual Studio. Ad esempio, impostazioni specifiche di un prodotto nel computer "A" vengono condivise con un altro prodotto nel computer "B", ma non con Visual Studio nei computer "A" o "B".

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

[Personalizzare l'IDE](../ide/personalizing-the-visual-studio-ide.md)
