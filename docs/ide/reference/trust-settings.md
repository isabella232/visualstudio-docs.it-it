---
title: Impostazioni di attendibilità per file e cartelle
description: Informazioni su come modificare le impostazioni di attendibilità per file e cartelle in modo da mantenere protetto Visual Studio.
author: abuchholtzau
ms.author: allisb
ms.date: 09/05/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: 011673bca7be569b5b350dc264148d5a7890d39c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789642"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Configurare le impostazioni di attendibilità per file e cartelle

Visual Studio richiede l'approvazione dell'utente prima di aprire i progetti con l'[attributo Web](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85)). Per maggiore sicurezza, è anche possibile configurare Visual Studio in modo che richieda l'approvazione dell'utente prima di aprire un file o una cartella con l'indicatore dell'attributo Web o non designati come *attendibili*. I controlli di file e cartelle sono disabilitati per impostazione predefinita.

> [!WARNING]
> È comunque necessario assicurarsi che il file, la cartella o la soluzione provenga da una persona o un percorso attendibile prima di approvarli.

## <a name="configure-trust-settings"></a>Configurare le impostazioni di attendibilità

Per modificare le impostazioni di attendibilità, seguire questa procedura:

1. Aprire **Strumenti** > **Opzioni** > **Impostazioni di attendibilità** e selezionare il collegamento **Configurare impostazioni di attendibilità** nel riquadro a destra.

2. Scegliere il livello di controllo per i file e le cartelle. Si possono usare controlli diversi per ognuno di essi. È possibile scegliere:

   * **Nessuna verifica**: Visual Studio non esegue alcun controllo.

   * **Verifica indicatore dell'attributo Web**: se il file o la cartella ha l'indicatore dell'attributo Web, Visual Studio si blocca e chiede l'autorizzazione per aprire.

   * **Verifica attendibilità del percorso**: se il percorso del file o della cartella non è nell'elenco dei **percorsi attendibili**, Visual Studio si blocca e chiede l'autorizzazione per aprire.

   ![Opzioni di verifica dell'attendibilità](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Aggiungere percorsi attendibili

Per aggiungere percorsi attendibili, attenersi a questa procedura:

1. Aprire **Strumenti** > **Opzioni** > **Impostazioni di attendibilità** e selezionare il collegamento **Configurare impostazioni di attendibilità** nel riquadro a destra.

2. Fare clic su **Aggiungi** nella finestra di dialogo **Impostazioni di attendibilità** e quindi selezionare **File** o **Cartella**.

3. Individuare e selezionare il file o la cartella da aggiungere all'elenco degli elementi attendibili.

   Il percorso del file o della cartella viene visualizzato nell'elenco dei **percorsi attendibili**.

   ![Percorsi attendibili aggiunti](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Rimuovere percorsi attendibili

Per rimuovere percorsi attendibili, attenersi a questa procedura:

1. Aprire **Strumenti** > **Opzioni** > **Impostazioni di attendibilità** e selezionare il collegamento **Configurare impostazioni di attendibilità** nel riquadro a destra.

2. Selezionare il percorso da rimuovere nell'elenco dei **percorsi attendibili** e quindi fare clic su **Rimuovi**.

   > [!TIP]
   > Per selezionare più voci, tenere premuto **MAIUSC** mentre si selezionano i percorsi.

   I percorsi selezionati vengono rimossi dall'elenco dei **percorsi attendibili**.
