---
title: Individuare e usare le estensioni
ms.date: 01/30/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e282cdfda27579fd83871153a19897652d55865
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62962061"
---
# <a name="find-and-use-visual-studio-extensions"></a>Individuare e usare le estensioni di Visual Studio

Le estensioni di Visual Studio sono pacchetti di codice eseguiti in Visual Studio che forniscono funzionalità di Visual Studio nuove o migliorate. Altre informazioni sulle estensioni di Visual Studio sono disponibili qui: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

::: moniker range="vs-2017"

Usare la finestra di dialogo **Estensioni e aggiornamenti** per installare e gestire le estensioni di Visual Studio. Per aprire la finestra di dialogo **Estensioni e aggiornamenti**, scegliere **Strumenti** > **Estensioni e aggiornamenti**, oppure digitare **Estensioni** nella casella di ricerca **Avvio veloce**.

::: moniker-end

::: moniker range=">=vs-2019"

Usare la finestra di dialogo **Gestisci estensioni** per installare e gestire le estensioni di Visual Studio. Per aprire la finestra di dialogo **Gestisci estensioni**, scegliere **Estensioni** > **Gestisci estensioni**. In alternativa, digitare **Estensioni** nella casella di ricerca e scegliere **Gestisci estensioni**.

::: moniker-end

![Finestra Estensioni in Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

Il riquadro a sinistra suddivide le estensioni in categorie in base a quelle installate, quelle disponibili in Visual Studio Marketplace (**Online**) e quelle che hanno aggiornamenti disponibili. In **Gestione roaming estensioni** sono elencate tutte le estensioni di Visual Studio installate in tutti i computer o istanze di Visual Studio. Questa opzione è studiata per poter trovare più facilmente le estensioni preferite.

## <a name="find-visual-studio-extensions"></a>Trovare le estensioni di Visual Studio

È possibile installare le estensioni da [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Le estensioni possono essere controlli, esempi, modelli, strumenti o altri componenti che aggiungono funzionalità a Visual Studio. In Visual Studio sono supportate estensioni nel formato di pacchetto VSIX. Queste includono modelli di progetto, modelli di elemento, elementi di **Casella degli strumenti** componenti MEF (Managed Extension Framework) e VSPackage.

::: moniker range="vs-2017"

È anche possibile scaricare le estensioni basate su MSI, ma la finestra di dialogo **Estensioni e aggiornamenti** non consente di abilitarle o disabilitarle. Visual Studio Marketplace contiene estensioni VSIX e MSI.

::: moniker-end

::: moniker range=">=vs-2019"

È anche possibile scaricare e installare le estensioni basate su MSI, ma la finestra di dialogo **Gestisci estensioni** non consente di abilitarle o disabilitarle. Visual Studio Marketplace contiene estensioni VSIX e MSI.

::: moniker-end

## <a name="install-or-uninstall-visual-studio-extensions"></a>Installare o disinstallare le estensioni di Visual Studio

::: moniker range="vs-2017"

In **Estensioni e aggiornamenti** trovare l'estensione che si vuole installare. (se si conosce il nome dell'estensione o parte di esso, è possibile eseguire la ricerca nella finestra di**ricerca**). Fare clic su **Download**. L'estensione viene pianificata per essere installata. L'estensione verrà installata dopo la chiusura di tutte le istanze di Visual Studio.

Se si tenta di installare un'estensione con dipendenze, il programma di installazione verifica se siano già installate. Se non sono installate, nella finestra di dialogo **Estensioni e aggiornamenti** verranno elencate tutte le dipendenze che devono essere installate prima dell'estensione.

::: moniker-end

::: moniker range=">=vs-2019"

In **Gestisci estensioni** trovare l'estensione che si vuole installare. (se si conosce il nome dell'estensione o parte di esso, è possibile eseguire la ricerca nella finestra di**ricerca**). Fare clic su **Download**. L'estensione viene pianificata per essere installata. L'estensione verrà installata dopo la chiusura di tutte le istanze di Visual Studio.

Se si tenta di installare un'estensione con dipendenze, il programma di installazione verifica se siano già installate. Se non sono installate, nella finestra di dialogo **Gestisci estensioni** verranno elencate tutte le dipendenze che devono essere installate prima dell'estensione.

::: moniker-end

Se si desidera interrompere l'utilizzo di un'estensione, è possibile disabilitarla o disinstallarla. Disabilitandola, un'estensione rimarrà installata ma non caricata. È possibile disabilitare solo le estensioni VSIX; le estensioni installate usando un file MSI possono solo essere disinstallate. Trovare l'estensione e fare clic su **Disinstalla** o **Disabilita**. Per scaricare un'estensione disabilitata, è necessario riavviare Visual Studio.

## <a name="per-user-and-administrative-extensions"></a>Estensioni amministrative e per utente

La maggior parte delle estensioni sono per utente e sono installate nella cartella *%LocalAppData%\Microsoft\VisualStudio\\<Versione Visual Studio\>\Extensions\\*. Alcune estensioni sono di tipo amministrativo e vengono installate nel percorso *\<Cartella di installazione di Visual Studio>\Common7\IDE\Extensions\\*.

Per proteggere il sistema da estensioni che possono contenere errori o codice dannoso, è possibile limitare il caricamento delle estensioni per utente nei soli in casi in cui Visual Studio sia in esecuzione con autorizzazioni utente normali. Ciò significa che le estensioni per utente sono disabilitate quando Visual Studio viene eseguito con autorizzazioni utente amministrative. A questo scopo, passare alla pagina delle opzioni delle estensioni (**Strumenti** > **Opzioni** > **Ambiente** > **Estensioni**). Deselezionare la casella di controllo **Carica estensioni per utente se eseguite come amministratore** , quindi riavviare Visual Studio.

## <a name="automatic-extension-updates"></a>Aggiornamenti automatici delle estensioni

Le estensioni vengono aggiornate automaticamente quando è disponibile una nuova versione in Visual Studio Marketplace. Dopo essere stata rilevata, la nuova versione dell'estensione viene installata in background. Alla successiva apertura di Visual Studio, verrà eseguita la nuova versione dell'estensione.

Se si desidera disabilitare gli aggiornamenti automatici, è possibile disabilitare la funzionalità per tutte le estensioni o solo per estensioni specifiche.

::: moniker range="vs-2017"

- Per disabilitare gli aggiornamenti automatici di tutte le estensioni, selezionare il collegamento **Modifica le impostazioni di estensioni e aggiornamenti** nella finestra di dialogo **Estensioni e aggiornamenti**. Nella finestra di dialogo **Opzioni** deselezionare **Aggiorna automaticamente le estensioni**.

- Per disabilitare gli aggiornamenti automatici per un'estensione specifica, deselezionare l'opzione **Aggiorna automaticamente questa estensione** nel riquadro dei dettagli dell'estensione sul lato destro della finestra di dialogo **Estensioni e aggiornamenti**.

::: moniker-end

::: moniker range=">=vs-2019"

- Per disabilitare gli aggiornamenti automatici di tutte le estensioni, selezionare il collegamento **Modifica le impostazioni di estensioni e aggiornamenti** nella finestra di dialogo **Gestisci estensioni**. Nella finestra di dialogo **Opzioni** deselezionare **Aggiorna automaticamente le estensioni**.

- Per disabilitare gli aggiornamenti automatici per un'estensione specifica, deselezionare l'opzione **Aggiorna automaticamente questa estensione** nel riquadro dei dettagli dell'estensione sul lato destro della finestra di dialogo **Gestisci estensioni**.

::: moniker-end

## <a name="extension-crash-and-unresponsiveness-notifications"></a>Notifiche di arresto anomalo e rallentamento di un'estensione

Visual Studio invia una notifica all'utente se sospetta che un'estensione è stata coinvolta in un arresto anomalo del sistema durante una sessione precedente. Quando Visual Studio subisce un arresto anomalo del sistema, memorizza lo stack dell'eccezione. Al successivo avvio di Visual Studio, viene esaminato lo stack, a partire dal nodo foglia e procedendo verso la base. Se Visual Studio determina che un frame appartiene a un modulo che fa parte di un'estensione installata e abilitata, visualizza una notifica.

Visual Studio invia una notifica anche se sospetta che un'estensione sia la causa di un blocco dell'interfaccia utente.

Quando queste notifiche vengono visualizzate, è possibile ignorare la notifica o eseguire una delle azioni seguenti:

::: moniker range="vs-2017"

- Scegliere **Disabilita questa estensione**. Visual Studio disabilita l'estensione e comunica se è necessario riavviare il sistema per rendere effettiva la disabilitazione. Se lo si desidera è possibile riabilitare l'estensione nella finestra di dialogo **Estensioni e aggiornamenti**.

::: moniker-end

::: moniker range=">=vs-2019"

- Scegliere **Disabilita questa estensione**. Visual Studio disabilita l'estensione e comunica se è necessario riavviare il sistema per rendere effettiva la disabilitazione. Se lo si desidera è possibile riabilitare l'estensione nella finestra di dialogo **Gestisci estensioni**.

::: moniker-end

- Scegliere **Non visualizzare più questo messaggio**.

  - Se la notifica riguarda un arresto anomalo in una sessione precedente, Visual Studio non visualizza più una notifica quando si verifica un arresto anomalo associato a questa estensione. Visual Studio visualizzerà comunque le notifiche in caso di blocco associabile all'estensione o per arresti anomali o blocchi che possono essere associati ad altre estensioni.
  - Se la notifica riguarda un rallentamento, l'IDE non visualizza più una notifica quando questa estensione è associata al rallentamento. Visual Studio visualizzerà comunque notifiche correlate all'arresto anomalo per questa estensione e correlate ad arresti anomali o blocchi per altre estensioni.

- Scegliere **Altre informazioni** per visualizzare questa pagina.

- Scegliere il pulsante **X** al termine della notifica per ignorarla. Verrà visualizzata una nuova notifica per le istanze future dell'estensione associata a un arresto anomalo o al blocco dell'interfaccia utente.

> [!NOTE]
> Una notifica di blocco dell'interfaccia utente o di arresto anomalo significa solo che uno dei moduli dell'estensione si trovava nello stack quando si è verificato il blocco dell'interfaccia utente o l'arresto anomalo. Ciò non significa necessariamente che l'estensione stessa sia la causa. È possibile che l'estensione abbia chiamato codice che fa parte di Visual Studio, che a sua volta ha causato il blocco dell'interfaccia utente o l'arresto anomalo. Tuttavia, la notifica può rivelarsi ancora utile se l'estensione che ha causato il blocco dell'interfaccia utente o l'arresto anomalo non è importante. In questo caso, la disabilitazione dell'estensione evita il blocco dell'interfaccia utente o l'arresto anomalo in futuro senza influire sulla produttività.

## <a name="sample-master-copies-and-working-copies"></a>Copie master e copie di lavoro di esempio

Quando si installa un esempio online, la soluzione viene memorizzata in due posizioni:

- Una copia di lavoro viene memorizzata nel percorso specificato al momento della creazione del progetto.

- Una copia master separata viene memorizzata nel computer.

::: moniker range="vs-2017"

È possibile usare la finestra di dialogo **Estensioni e aggiornamenti** per eseguire queste attività correlate agli esempi:

::: moniker-end

::: moniker range=">=vs-2019"

È possibile usare la finestra di dialogo **Gestisci estensioni** per eseguire queste attività correlate agli esempi:

::: moniker-end

- Elencare le copie master degli esempi installati.

- Disabilitare o disinstallare la copia master di un esempio.

- Installare pacchetti di esempio, ovvero raccolte di esempi relativi a una tecnologia o una funzionalità.

- Installare singoli esempi online.

- Visualizzare notifiche di aggiornamenti quando vengono pubblicate modifiche al codice sorgente per gli esempi installati.

- Aggiornare la copia master di un esempio installato quando è disponibile una notifica di aggiornamento.

::: moniker range="vs-2017"

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Installazione senza usare la finestra di dialogo Estensioni e Aggiornamenti

Le estensioni che sono state incluse in file con estensione *vsix* possono essere disponibili in posizioni diverse da Visual Studio Marketplace. Benché la finestra di dialogo **Estensioni e aggiornamenti** non permetta di individuare questi file, è possibile installare un file con estensione *vsix* facendovi doppio clic sopra oppure selezionandolo e quindi premendo **INVIO**. Quindi, è sufficiente seguire le istruzioni. Una volta installata l'estensione, sarà possibile usare la finestra di dialogo **Estensioni e aggiornamenti** per abilitarla, disabilitarla o disinstallarla.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Tipi di estensione non supportati dalla finestra di dialogo Estensioni e aggiornamenti

Visual Studio continua a supportare le estensioni installate da Microsoft Installer (MSI) ma non tramite la finestra di dialogo **Estensioni e aggiornamenti** senza modifica.

> [!TIP]
> Se un'estensione basata su MSI include un file *extension.vsixmanifest*, tale estensione viene visualizzata nella finestra di dialogo **Estensioni e aggiornamenti**.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="installing-without-using-the-manage-extensions-dialog-box"></a>Installazione senza usare la finestra di dialogo Gestisci estensioni

Le estensioni che sono state incluse in file con estensione *vsix* possono essere disponibili in posizioni diverse da Visual Studio Marketplace. Benché la finestra di dialogo **Gestisci estensioni** non permetta di individuare questi file, è possibile installare un file con estensione *vsix* facendovi doppio clic sopra oppure selezionandolo e quindi premendo **INVIO**. Quindi, è sufficiente seguire le istruzioni. Una volta installata l'estensione, sarà possibile usare la finestra di dialogo **Gestisci estensioni** per abilitarla, disabilitarla o disinstallarla.

## <a name="extension-types-not-supported-by-the-manage-extensions-dialog-box"></a>Tipi di estensione non supportati dalla finestra di dialogo Gestisci estensioni

Visual Studio continua a supportare le estensioni installate da Microsoft Installer (MSI) ma non tramite la finestra di dialogo **Gestisci estensioni** senza modifica.

> [!TIP]
> Se un'estensione basata su MSI include un file *extension.vsixmanifest*, tale estensione viene visualizzata nella finestra di dialogo **Gestisci estensioni**.

::: moniker-end