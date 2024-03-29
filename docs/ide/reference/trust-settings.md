---
title: Attendibilità Impostazioni per file e cartelle
description: Informazioni su come modificare le impostazioni di attendibilità per file e cartelle in modo da mantenere protetto Visual Studio.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.date: 09/15/2021
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: cde67d54f7c70935f6012542406834ba6c423d78
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128430643"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Configurare le impostazioni di attendibilità per file e cartelle

::: moniker range=">=vs-2022"

In Visual Studio 2022 (anteprima 2) è stata rinnovata la funzionalità Trust Impostazioni per visualizzare un avviso ogni volta che nell'IDE sta per essere aperto codice non attendibile in file, cartelle, progetti e soluzioni.

:::image type="content" source="media/vs-2022/trusted-settings-warning-message.png" alt-text="Screenshot del messaggio di avviso Impostazioni trust":::

Si aggiungeranno altre informazioni a questa pagina mentre si continua ad aggiornare la funzionalità. Nel frattempo, per le ultime notizie, esaminare il post di blog più recente, Miglioramento della sicurezza degli sviluppatori con Visual Studio [2022.](https://devblogs.microsoft.com/visualstudio/improving-developer-security-with-visual-studio-2022/)

::: moniker-end

::: moniker range="<=vs-2019"

Visual Studio richiede l'approvazione dell'utente prima di aprire i progetti con [il contrassegno del Web](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85)). Per maggiore sicurezza, è anche possibile configurare Visual Studio in modo che richieda l'approvazione dell'utente prima di aprire un file o una cartella con l'indicatore dell'attributo Web o non designati come *attendibili*. I controlli di file e cartelle sono disabilitati per impostazione predefinita.

> [!WARNING]
> È comunque necessario assicurarsi che il file, la cartella o la soluzione provenga da una persona o un percorso attendibile prima di approvarli.

> [!NOTE]
> In Visual Studio 2022 (anteprima) è stata rinnovata la funzionalità Trust Impostazioni per visualizzare un avviso ogni volta che nell'IDE sta per essere aperto codice non attendibile in file, cartelle, progetti e soluzioni. Per altre informazioni, vedere il post di blog Improving developer security with Visual Studio 2022 (Migliorare la sicurezza degli sviluppatori [con Visual Studio 2022).](https://devblogs.microsoft.com/visualstudio/improving-developer-security-with-visual-studio-2022/)

## <a name="configure-trust-settings"></a>Configurare le impostazioni di attendibilità

Per modificare le impostazioni di attendibilità, seguire questa procedura:

1. Aprire **Strumenti Opzioni** Impostazioni e selezionare il collegamento Configura Impostazioni trust nel riquadro a >  >  destra. 

2. Scegliere il livello di controllo per i file e le cartelle. Si possono usare controlli diversi per ognuno di essi. Le opzioni sono:

   * **Nessuna verifica**: Visual Studio non esegue alcun controllo.

   * **Verifica indicatore dell'attributo Web**: se il file o la cartella ha l'indicatore dell'attributo Web, Visual Studio si blocca e chiede l'autorizzazione per aprire.

   * **Verifica attendibilità del percorso**: se il percorso del file o della cartella non è nell'elenco dei **percorsi attendibili**, Visual Studio si blocca e chiede l'autorizzazione per aprire.

   ![Opzioni di verifica dell'attendibilità](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Aggiungere percorsi attendibili

Per aggiungere percorsi attendibili, attenersi a questa procedura:

1. Aprire **Strumenti Opzioni** Impostazioni e selezionare il collegamento Configura Impostazioni trust nel riquadro a >  >  destra. 

2. Fare clic su **Aggiungi** nella finestra di dialogo **Impostazioni di attendibilità** e quindi selezionare **File** o **Cartella**.

3. Individuare e selezionare il file o la cartella da aggiungere all'elenco degli elementi attendibili.

   Il percorso del file o della cartella viene visualizzato nell'elenco dei **percorsi attendibili**.

   ![Percorsi attendibili aggiunti](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Rimuovere percorsi attendibili

Per rimuovere percorsi attendibili, attenersi a questa procedura:

1. Aprire **Strumenti Opzioni** Impostazioni e selezionare il collegamento Configura Impostazioni trust nel riquadro a >  >  destra. 

2. Selezionare il percorso da rimuovere nell'elenco dei **percorsi attendibili** e quindi fare clic su **Rimuovi**.

   > [!TIP]
   > Per selezionare più voci, tenere premuto **MAIUSC** mentre si selezionano i percorsi.

   I percorsi selezionati vengono rimossi dall'elenco dei **percorsi attendibili**.

::: moniker-end

## <a name="see-also"></a>Vedi anche

[Compilare un'applicazione in Visual Studio](../walkthrough-building-an-application.md)
