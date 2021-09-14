---
title: Importare o esportare configurazioni di installazione
titleSuffix: ''
description: Informazioni su come esportare la configurazione di installazione in un file con estensione vsconfig da condividere con altri utenti e su come eseguire l'importazione da clonare.
ms.date: 05/18/2019
ms.topic: how-to
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fda4d25c164a91614c35b6cb3f2622235bbbb02a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627066"
---
# <a name="import-or-export-installation-configurations"></a>Importare o esportare configurazioni di installazione

È possibile configurare Visual Studio a livello di organizzazione con file di configurazione dell'installazione. A tale scopo, è sufficiente esportare le informazioni sui carichi di lavoro e i componenti in un file con estensione vsconfig tramite il programma di installazione di Visual Studio. Sarà quindi possibile importare la configurazione in installazioni nuove o esistenti e condividerla con altri utenti.

Ecco come.

::: moniker range="vs-2017"

> [!NOTE]
> Questa funzionalità è disponibile solo in Visual Studio 2017 versione 15.9 e versioni successive.

::: moniker-end

## <a name="export-a-configuration"></a>Esportare una configurazione

È possibile scegliere di esportare un file di configurazione dell'installazione da un'istanza di Visual Studio installata in precedenza o di cui si sta eseguendo l'installazione.

1. Aprire il programma di installazione di Visual Studio.

1. Nella scheda del prodotto fare clic sul pulsante **Altro** e quindi selezionare **Esporta configurazione**.

   ![Esportare la configurazione dalla scheda del prodotto nel programma di installazione di Visual Studio](../install/media/vs-2019/vs-installer-export-config.png)

1. Selezionare o digitare il percorso in cui si salvare il file con estensione vsconfig e quindi scegliere **Esamina dettagli**.

   ![Esportare la configurazione dal programma di installazione di Visual Studio](../install/media/vs-2019/export-configuration-confirmation.png)

1. Assicurarsi di avere ottenuto i carichi di lavoro e i componenti desiderati e quindi scegliere **Esporta**.

## <a name="import-a-configuration"></a>Importare una configurazione

Quando si è pronti per importare un file di configurazione dell'installazione, attenersi alla procedura seguente.

1. Aprire il programma di installazione di Visual Studio.

1. Nella scheda del prodotto fare clic sul pulsante **Altro** e quindi selezionare **Importa configurazione**.

1. Individuare il file con estensione vsconfig da importare e quindi scegliere **Esamina dettagli**.

1. Assicurarsi di avere ottenuto i carichi di lavoro e i componenti desiderati e quindi scegliere **Chiudi**.

::: moniker range=">=vs-2019"

## <a name="automatically-install-missing-components"></a>Installare automaticamente i componenti mancanti

**Novità di Visual Studio 2019:** quando si salva un file con estensione vsconfig nella directory radice della soluzione e quindi si apre una soluzione, Visual Studio rileva automaticamente i componenti mancanti e richiede di installarli.

![Esplora soluzioni suggerisce componenti aggiuntivi](../install/media/vs-2019/solution-explorer-config-file.png)

È anche possibile generare un file con estensione vsconfig direttamente da Esplora soluzioni.

1. Fare clic con il pulsante destro del mouse sul file della soluzione.

1. Scegliere **Aggiungi file** di configurazione > **dell'installazione**.

1. Verificare il percorso in cui si salvare il file con estensione vconfig e quindi scegliere **Esamina dettagli**.

1. Assicurarsi di avere ottenuto i carichi di lavoro e i componenti desiderati e quindi scegliere **Esporta**.

::: moniker-end

> [!NOTE]
> Per altre informazioni, vedere il post di blog [Configure Visual Studio across your organization with .vsconfig](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/) (Configurare Visual Studio a livello di organizzazione con .vsconfig).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Controllare gli aggiornamenti delle distribuzioni di Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Impostare i valori predefiniti per le distribuzioni aziendali](set-defaults-for-enterprise-deployments.md)
