---
title: Controllo della versione di Team Foundation
description: Guida alla risoluzione dei problemi del controllo della versione di Team Foundation e di macOS.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/02/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: 11b0788317cd0a20dd27159aa241db32e3818daf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710467"
---
# <a name="does-visual-studio-for-mac-support-team-foundation-version-control"></a>Visual Studio per Mac supporta il controllo della versione di Team Foundation?

> [!CAUTION]
> L'anteprima dell'estensione del controllo della versione di Team Foundation per Visual Studio per Mac non è più supportata in Visual Studio 2019 per Mac.


## <a name="alternative-version-control-options-in-visual-studio-for-mac"></a>Opzioni di controllo della versione alternative in Visual Studio per Mac

Per una migliore esperienza di controllo della versione in macOS, è consigliabile usare **Git** anziché controllo della versione di Team Foundation (TFVC). 

Git è supportato in Visual Studio per Mac e rappresenta l'opzione predefinita per i repository ospitati in Team Foundation Server (TFS) o Azure DevOps. Per altre informazioni sull'uso di Git con TFS/Azure DevOps, vedere la guida [Impostazione di un repository Git](./set-up-git-repository.md).

## <a name="unsupported-workarounds-for-tfvc"></a>Soluzioni alternative non supportate per il controllo della versione di Team Foundation

Sebbene Visual Studio per Mac non supporti ufficialmente il controllo della versione di Team Foundation, la parte restante di questa guida illustra alcune soluzioni alternative per l'uso di tale controllo in macOS. Se attualmente si usa il controllo della versione di Team Foundation, ecco alcune soluzioni che è possibile adottare per accedere al codice sorgente ospitato nel controllo della versione di Team Foundation:

* Opzione 1. [Usare Visual Studio Code e l'estensione Azure Repos, per un'interfaccia utente grafica](#use-visual-studio-code-and-the-azure-repos-extension)
* Opzione 2. [Connettersi al repository usando il client della riga di comando Team Explorer Everywhere (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)

### <a name="option-1--use-visual-studio-code-and-the-azure-repos-extension"></a>Opzione 1. <a id="use-visual-studio-code-and-the-azure-repos-extension"></a>Usare Visual Studio Code e l'Azure Repos predefinita

Se si preferisce lavorare con un'interfaccia grafica per gestire i file nel controllo della versione, l'estensione Azure Repos per Visual Studio Code offre una soluzione supportata da Microsoft. Per iniziare, scaricare [Visual Studio Code](https://code.visualstudio.com) e quindi scoprire come [configurare l'estensione Azure Repos](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

### <a name="option-2--connecting-using-the-team-explorer-everywhere-command-line-client"></a>Opzione 2. <a id="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Connessione tramite il Team Explorer Everywhere client della riga di comando

> [!IMPORTANT]
> In base al file LEGGIMI di Team Explorer Everywhere, questo progetto [non viene più mantenuto](https://github.com/microsoft/team-explorer-everywhere).

Se si ha familiarità con il Terminale macOS, il client della riga di comando Team Explorer Everywhere (TEE-CLC) offre un metodo supportato per la connessione all'origine nel controllo della versione di Team Foundation.

È possibile seguire la procedura seguente per configurare la connessione al controllo della versione di Team Foundation ed eseguire il commit delle modifiche.

#### <a name="setting-up-the-tee-clc"></a>Configurare TEE-CLC

Esistono due modi per configurare TEE-CLC.

* Usare Homebrew per installare il client, o
* Scaricare e installare manualmente il client

La soluzione più semplice prevede l'**uso di HomeBrew**, ovvero una gestione pacchetti per macOS. Per eseguire l'installazione con questo metodo:

1. Avviare l'applicazione Terminale di macOS.
1. Installare Homebrew con il Terminale e seguendo le istruzioni riportate nella [home page di Homebrew](https://brew.sh/).
1. Dopo aver installato Homebrew, eseguire il comando seguente dal Terminale: `brew install tee-clc`

Per **configurare manualmente TEE-CLC**:

1. [Scaricare la versione più recente di TEE-CLC](https://github.com/Microsoft/team-explorer-everywhere/releases) dalla pagina delle versioni del repository di GitHub per Team Explorer Everywhere (ad esempio tee-clc-14.134.0.zip al momento della stesura di questo articolo).
1. Estrarre il contenuto del file ZIP in una cartella su disco.
1. Aprire l'app Terminale di macOS e usare il comando `cd` per passare alla cartella usata nel passaggio precedente.
1. Da questa cartella eseguire il comando `./tf` per verificare che il client della riga di comando possa essere eseguito. Potrebbe essere richiesto di installare Java o altre dipendenze.

Dopo aver installato TEE-CLC, è possibile eseguire il comando `tf eula` per visualizzare e accettare il contratto di licenza per il client.

Infine, per l'autenticazione nell'ambiente TFS/Azure DevOps, sarà necessario creare un token di accesso personale nel server. Altre informazioni sull'[autenticazione con token di accesso personali](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops&preserve-view=true). Quando si crea un token di accesso personale da usare con il controllo della versione di Team Foundation, assicurarsi di assegnare l'accesso completo quando si configura il token.

#### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Uso di TEE-CLC per la connessione al repository

Per connettersi al codice sorgente, è innanzitutto necessario creare un'area di lavoro usando il comando `tf workspace`. I comandi seguenti, ad esempio, consentono la connessione a un'organizzazione in Azure DevOps Services chiamata "MyOrganization": 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

L'impostazione di ambiente `TF_AUTO_SAVE_CREDENTIALS` viene usata per salvare le credenziali in modo che non venga richiesto di immetterle più volte. Quando viene richiesto un nome utente, usare il token di accesso personale creato nella sezione precedente e una password vuota.

Per creare un mapping dei file di origine in una cartella locale, si userà il comando `tf workfold`. Nell'esempio seguente verrà eseguito il mapping di una cartella denominata "WebApp.Services" dal progetto di controllo della versione di Team Foundation "MyRepository" e tale cartella verrà configurata per la copia nella cartella ~/Projects/ locale (ad esempio una cartella "Progetti" nella home directory degli utenti correnti).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Infine, si usa il comando seguente per ottenere i file di origine dal server e copiarli in locale:

```bash
tf get
```

#### <a name="committing-changes-using-the-tee-clc"></a>Eseguire il commit delle modifiche tramite TEE-CLC

Dopo aver apportato le modifiche ai file in Visual Studio per Mac, è possibile tornare al Terminale per archiviare le modifiche. Il comando `tf add` viene usato per aggiungere file all'elenco delle modifiche in sospeso da archiviare e il comando `tf checkin` esegue l'archiviazione effettiva nel server. Il comando `checkin` include parametri per aggiungere un commento o associare un elemento di lavoro correlato. Nel frammento di codice seguente vengono aggiunti tutti i file in una cartella `WebApp.Services`, in modo ricorsivo, al processo di archiviazione. Il codice viene quindi archiviato con un commento e associato a un elemento di lavoro con ID "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Per altre informazioni sui comandi qui indicati o su altri comandi, è possibile usare il comando seguente dal Terminale:

`tf help`

## <a name="see-also"></a>Vedi anche

- [Sviluppare e condividere il codice nel controllo della versione di Team Foundation usando Visual Studio (in Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)