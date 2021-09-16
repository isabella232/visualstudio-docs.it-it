---
title: Modificare Visual Studio, componenti, & Language Pack
titleSuffix: ''
description: Informazioni dettagliate su come modificare Visual Studio.
ms.date: 09/14/2021
ms.topic: how-to
ms.custom: vs-acquisition
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 692b1aedf5c55d2162a28e96ae9cdbdadd9529e6
ms.sourcegitcommit: 811e4ee80311433fefbe6d6223bf72c431008403
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2021
ms.locfileid: "127890649"
---
# <a name="modify-visual-studio-workloads-components-and-language-packs"></a>Modificare Visual Studio carichi di lavoro, componenti e Language Pack

::: moniker range=">=vs-2019"

Visual Studio può essere facilmente modificato in modo da includere solo gli elementi desiderati, quando sono necessari. A tale scopo, aprire il Programma di installazione di Visual Studio e quindi aggiungere o rimuovere carichi di lavoro, componenti e Language Pack.

::: moniker-end

::: moniker range="vs-2017"

Oltre ad aver semplificato la personalizzazione di Visual Studio in base alle attività da eseguire, è stata semplificata anche la modifica di Visual Studio. A tale scopo, aprire il nuovo Programma di installazione di Visual Studio e apportare le modifiche desiderate.

::: moniker-end

## <a name="prerequisites"></a>Prerequisiti

- Per installare, modificare o aggiornare Visual Studio, è necessario eseguire il Programma di installazione di Visual Studio come amministratore. Se si tenta di modificare Visual Studio utente tipico, si otterrà un avviso di controllo dell'account utente che richiede le credenziali di amministratore. Per altre informazioni, vedere [Autorizzazioni utente e Visual Studio](../ide/user-permissions-and-visual-studio.md).

- Le procedure seguenti presuppongono che si abbia una connessione Internet. Per altre informazioni su come modificare un'installazione offline creata [in precedenza](create-an-offline-installation-of-visual-studio.md) di Visual Studio, vedere:
  - [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
  - [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md)

## <a name="launch-the-installer-to-modify-your-installation"></a>Avviare il programma di installazione per modificare l'installazione

Per modificare l Visual Studio installazione, è prima di tutto necessario avviare il Programma di installazione di Visual Studio e quindi selezionare un'Visual Studio di installazione da modificare.

::: moniker range="vs-2017"

1. Individuare il programma di installazione di Visual Studio all'interno del computer in uso.

     Ad esempio, in un computer che esegue Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

     ![Screenshot che mostra la Programma di installazione di Visual Studio nella Windows 10 menu Start.](media/locate-the-visual-studio-installer.png "Individuare il programma Microsoft Visual Studio installazione")

     >[!TIP]
     >In alcuni computer il programma di installazione di Visual Studio potrebbe trovarsi sotto la lettera **"M"** come **Microsoft Visual Studio: programma di installazione**.<br/><br/> In alternativa, è possibile trovare il programma di installazione di Visual Studio nel percorso seguente: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Aprire il programma di installazione e quindi scegliere **Modifica**.

     ![Screenshot che mostra il pulsante Modifica nel Programma di installazione di Visual Studio.](media/modify-visual-studio.png "Modificare Visual Studio 2017")

     > [!IMPORTANT]
     > Se è presente un aggiornamento in sospeso, il pulsante Modifica si trova in una posizione diversa. In questo modo è possibile modificare Visual Studio senza aggiornarlo, se si preferisce. Fare clic su **Altro** e scegliere **Modifica**.
     >
     > ![Screenshot che mostra il pulsante Modifica nel Programma di installazione di Visual Studio, che si trova nel menu a discesa Altro quando un aggiornamento è in sospeso.](media/modify-or-update-visual-studio.png "Aggiornare o modificare Visual Studio 2017")

::: moniker-end

::: moniker range="vs-2019"

1. Individuare il **programma di installazione di Visual Studio** all'interno del computer in uso.

     Nel menu Start di Windows è possibile cercare "programma di installazione".

     ![Screenshot che mostra il risultato di una menu Start ricerca del Programma di installazione di Visual Studio.](media/vs-2019/visual-studio-installer.png "Cercare il Programma di installazione di Visual Studio")

     > [!NOTE]
     > È anche possibile trovare il programma di installazione di Visual Studio nella posizione seguente:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In questo caso, seguire i prompt.

1. Nel programma di installazione cercare l'edizione di Visual Studio installata e quindi scegliere **Modifica**.

     ![Screenshot che mostra un elenco Visual Studio installazioni nel Programma di installazione di Visual Studio.](media/vs-2019/vs-installer-modify.png "Scegliere Visual Studio 2019 e quindi modificare")

     > [!IMPORTANT]
     > Se è presente un aggiornamento in sospeso, il pulsante Modifica si trova in una posizione diversa. In questo modo, è possibile Visual Studio senza aggiornarlo, se necessario. Scegliere **Altro** e quindi **Modifica**.
     >
     > ![Screenshot che mostra il pulsante Modifica nel Programma di installazione di Visual Studio, che si trova nel menu a discesa Altro quando un aggiornamento è in sospeso.](media/vs-2019/modify-update-visual-studio.png "Aggiornare o modificare Visual Studio 2019")

::: moniker-end

::: moniker range=">=vs-2022"

1. Esistono molti modi per aprire il Programma di installazione di Visual Studio:

   - Nell'Windows menu Start è possibile cercare "installer" e quindi selezionare Programma di installazione di Visual Studio **dai** risultati.

     ![Screenshot che mostra il risultato di una menu Start ricerca del Programma di installazione di Visual Studio.](media/vs-2022/vs-installer.png "Cercare il Programma di installazione di Visual Studio")

   - Eseguire il Programma di installazione di Visual Studio eseguibile, che si trova in questo percorso:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   - Se è stato aperto Visual Studio, **selezionare** Strumenti Ottieni strumenti e funzionalità... , che apre il > Programma di installazione di Visual Studio.

     ![Screenshot che mostra il menu Visual Studio strumenti di 2022.](media/vs-2022/vs-tools-menu.png "Visual Studio menu Strumenti di Visual Studio 2022")

   Potrebbe essere richiesto di aggiornare il Programma di installazione di Visual Studio prima di continuare. In questo caso, seguire i prompt.

1. Nel Programma di installazione di Visual Studio cercare l'installazione Visual Studio da modificare e quindi scegliere **il pulsante** Modifica.

     ![Screenshot che mostra un elenco Visual Studio installazioni nel Programma di installazione di Visual Studio.](media/vs-2022/vs-installer-modify.png "Scegliere un Visual Studio installazione da modificare")

::: moniker-end

## <a name="change-workloads-or-individual-components"></a>Modificare carichi di lavoro o singoli componenti

::: moniker range="vs-2017"

 [I carichi](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) di lavoro contengono le funzionalità necessarie per il linguaggio di programmazione o la piattaforma in uso. Usare i carichi di lavoro per modificare Visual Studio in modo che supporti il lavoro da eseguire quando desiderato.

1. Nel Programma di installazione di Visual Studio scegliere la scheda **Carichi** di lavoro e quindi selezionare o deselezionare i carichi di lavoro desiderati.

   In alternativa, se non si vogliono usare i carichi di lavoro per personalizzare l'installazione di Visual Studio, scegliere la scheda **Singoli** componenti e selezionare i componenti desiderati e quindi seguire le istruzioni.

    ![Screenshot che mostra la scheda Carichi di lavoro del Programma di installazione di Visual Studio.](media/modify-workloads.png "Scegliere un carico di lavoro in Visual Studio 2017")

1. Scegliere se accettare l'opzione predefinita **Installa durante il download** o selezionare l'opzione **Scarica tutto, quindi installa**.

    ![Screenshot che mostra le opzioni di download e installazione nel Programma di installazione di Visual Studio.](media/vs-2019/vs-installer-choose-install-or-download.png "Scegliere di eseguire l'installazione durante il download o di scaricare prima e installare in un secondo momento")

    L'opzione "Scarica tutto, quindi installa" è utile se si preferisce scaricare prima tutto il software e quindi installarlo in un secondo momento.

1. Scegliere **Modifica**.

1. Se lo si desidera, scegliere la scheda **Carichi** di lavoro e quindi selezionare o deselezionare i carichi di lavoro desiderati.

1. Dopo aver installato i nuovi carichi di lavoro, **scegliere** Avvia dal Programma di installazione di Visual Studio per aprire Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

 I carichi di lavoro contengono le funzionalità necessarie per il linguaggio di programmazione o la piattaforma in uso. Usare i carichi di lavoro per modificare Visual Studio in modo che supporti il lavoro da eseguire quando desiderato.

 > [!TIP]
>Per altre informazioni sui bundle di strumenti e componenti necessari per lo sviluppo, vedere Visual Studio [carichi di lavoro](https://visualstudio.microsoft.com/vs/#workloads).

1. Nel Programma di installazione di Visual Studio scegliere la scheda **Carichi** di lavoro e quindi selezionare o deselezionare i carichi di lavoro desiderati.

    ![Screenshot che mostra la scheda Carichi di lavoro del Programma di installazione di Visual Studio.](media/vs-2019/vs-installer-modify-workloads.png "Scegliere un carico di lavoro in Visual Studio 2019")

1. Scegliere se accettare l'opzione predefinita **Installa durante il download** o selezionare l'opzione **Scarica tutto, quindi installa**.

    ![Screenshot che mostra le opzioni di download e installazione nel Programma di installazione di Visual Studio.](media/vs-2019/vs-installer-choose-install-or-download.png "Scegliere di eseguire l'installazione durante il download o di scaricare prima e installare in un secondo momento")

    L'opzione "Scarica tutto, quindi installa" è utile se si preferisce scaricare prima tutto il software e quindi installarlo in un secondo momento.

1. Scegliere **Modifica**.

1. Dopo aver installato i nuovi carichi di lavoro, **scegliere** Avvia dal Programma di installazione di Visual Studio per aprire Visual Studio.

::: moniker-end

::: moniker range=">=vs-2022"

I carichi di lavoro contengono i componenti necessari per il linguaggio di programmazione o la piattaforma in uso. Usare i carichi di lavoro per modificare Visual Studio in modo che supporti il lavoro da eseguire quando desiderato.

> [!TIP]
> Per altre informazioni sugli strumenti e i bundle di componenti necessari per lo sviluppo, vedere Visual Studio [carichi di lavoro](https://visualstudio.microsoft.com/vs/#workloads).

1. Nel Programma di installazione di Visual Studio scegliere la scheda **Carichi** di lavoro e quindi selezionare o deselezionare i carichi di lavoro desiderati.

    ![Screenshot che mostra la scheda Carichi di lavoro del Programma di installazione di Visual Studio.](media/vs-2022/vs-installer-modify-workloads.png "Scegliere i carichi di lavoro nella Programma di installazione di Visual Studio")

1. Per aggiungere più componenti di quelli installati da un carico di lavoro, scegliere la scheda **Singoli** componenti e quindi selezionare o deselezionare i singoli componenti desiderati.

    ![Screenshot che mostra la scheda Singoli componenti del Programma di installazione di Visual Studio.](media/vs-2022/vs-installer-individual-components.png "Scegliere i singoli componenti nella Programma di installazione di Visual Studio")

1. Scegliere se si vuole eseguire **l'installazione durante il download** o **scaricare tutto, quindi installare**. L'opzione predefinita Installa **durante il download** consente di risparmiare tempo complessivo avviando l'installazione in precedenza.

    ![Screenshot che mostra le opzioni di download e installazione nel Programma di installazione di Visual Studio.](media/vs-2022/vs-installer-choose-install-or-download.png "Scaricare e installare le opzioni della sequenza nel Programma di installazione di Visual Studio")

1. Scegliere **Modifica**.

1. Dopo aver installato i carichi di  lavoro o i componenti modificati, scegliere Avvia dalla Programma di installazione di Visual Studio per aprire Visual Studio 2022 Preview.

::: moniker-end

> [!TIP]
> Per informazioni sul componente SQL Server Data Tools (SSDT), vedere Scaricare e installare [SSDT per](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true)Visual Studio .

## <a name="modify-language-packs"></a>Modificare i Language Pack

Il Programma di installazione di Visual Studio seleziona un language pack predefinito per Visual Studio corrispondente alla lingua del sistema operativo. Tuttavia, è possibile modificare la lingua predefinita ogni volta che si vuole.

A tale scopo, procedere nel seguente modo:

1. Scegliere la **scheda Language Pack** nel Programma di installazione di Visual Studio.
1. Selezionare la lingua preferita.
1. Seguire le istruzioni.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Elenco degli ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
