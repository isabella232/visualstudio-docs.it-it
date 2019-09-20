---
title: Trovare e installare le estensioni
ms.date: 09/18/2019
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
ms.openlocfilehash: 9f86aa6cf99ae910c9b10bc6e93c408ca2c85265
ms.sourcegitcommit: a2df993dc5e11c5131dbfcba686f0028a589068f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71150095"
---
# <a name="manage-extensions-for-visual-studio"></a>Gestire le estensioni per Visual Studio

Le estensioni sono pacchetti di codice eseguiti in Visual Studio e forniscono funzionalità nuove o migliorate. Le estensioni possono essere controlli, esempi, modelli, strumenti o altri componenti che aggiungono funzionalità a Visual Studio, ad esempio [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) o [Visual Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode).

Per informazioni sulla creazione di estensioni di Visual Studio, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Per informazioni sull'uso delle estensioni, vedere la pagina relativa all'estensione singola in [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Finestra di dialogo Estensioni e aggiornamenti

Usare la finestra di dialogo **Estensioni e aggiornamenti** per installare e gestire le estensioni di Visual Studio. Per aprire la finestra di dialogo **Estensioni e aggiornamenti**, scegliere **Strumenti** > **Estensioni e aggiornamenti**, oppure digitare **Estensioni** nella casella di ricerca **Avvio veloce**.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Finestra di dialogo Gestisci estensioni

Usare la finestra di dialogo **Gestisci estensioni** per installare e gestire le estensioni di Visual Studio. Per aprire la finestra di dialogo **Gestisci estensioni**, scegliere **Estensioni** > **Gestisci estensioni**. In alternativa, digitare **Estensioni** nella casella di ricerca e scegliere **Gestisci estensioni**.

::: moniker-end

![Finestra Estensioni in Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

Il riquadro a sinistra suddivide le estensioni in categorie in base a quelle installate, quelle disponibili in Visual Studio Marketplace (**Online**) e quelle che hanno aggiornamenti disponibili. In **Gestione roaming estensioni** sono elencate tutte le estensioni di Visual Studio installate in tutti i computer o istanze di Visual Studio. Questa opzione è studiata per poter trovare più facilmente le estensioni preferite.

## <a name="find-and-install-extensions"></a>Trovare e installare le estensioni

::: moniker range="vs-2017"

È possibile installare le estensioni da [Visual Studio Marketplace](https://marketplace.visualstudio.com) o dalla finestra di dialogo estensioni e aggiornamenti in Visual Studio.

Per installare le estensioni in Visual Studio:

1. In **Strumenti** > **Estensioni e aggiornamenti** trovare l'estensione che si vuole installare. Se si conosce il nome o parte del nome dell'estensione, è possibile eseguire la ricerca nella finestra di **ricerca** .

2. Selezionare **download**.

   L'estensione viene pianificata per essere installata. L'estensione verrà installata dopo la chiusura di tutte le istanze di Visual Studio.

Se si tenta di installare un'estensione con dipendenze, il programma di installazione verifica se siano già installate. Se non sono installate, nella finestra di dialogo **Estensioni e aggiornamenti** verranno elencate tutte le dipendenze che devono essere installate prima dell'estensione.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Installare senza usare la finestra di dialogo Estensioni e aggiornamenti

Le estensioni che sono state incluse in file con estensione *vsix* possono essere disponibili in posizioni diverse da Visual Studio Marketplace. La finestra di dialogo **strumenti** > **estensioni e aggiornamenti** non consente di rilevare questi file, ma è possibile installare un file *VSIX* facendo doppio clic sul file o selezionando il file e premendo **invio**. Quindi, è sufficiente seguire le istruzioni. Una volta installata l'estensione, sarà possibile usare la finestra di dialogo **Estensioni e aggiornamenti** per abilitarla, disabilitarla o disinstallarla.

> [!NOTE]
> - Visual Studio Marketplace contiene estensioni VSIX e MSI. La finestra di dialogo estensioni e aggiornamenti non consente di abilitare o disabilitare le estensioni basate su MSI.
> - Se un'estensione basata su MSI include un file *extension.vsixmanifest*, tale estensione viene visualizzata nella finestra di dialogo **Estensioni e aggiornamenti**.

::: moniker-end

::: moniker range=">=vs-2019"

È possibile installare le estensioni da [Visual Studio Marketplace](https://marketplace.visualstudio.com) o dalla finestra di dialogo Gestisci estensioni in Visual Studio.

Per installare le estensioni in Visual Studio:

1. In **Estensioni** > **Gestisci estensioni** trovare l'estensione che si vuole installare. (se si conosce il nome dell'estensione o parte di esso, è possibile eseguire la ricerca nella finestra di**ricerca**).

2. Selezionare **download**.

   L'estensione viene pianificata per essere installata. L'estensione verrà installata dopo la chiusura di tutte le istanze di Visual Studio.

Se si tenta di installare un'estensione con dipendenze, il programma di installazione verifica se siano già installate. Se non sono installate, nella finestra di dialogo **Gestisci estensioni** verranno elencate tutte le dipendenze che devono essere installate prima dell'estensione.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Installare senza usare la finestra di dialogo Gestisci estensioni

Le estensioni che sono state incluse in file con estensione *vsix* possono essere disponibili in posizioni diverse da Visual Studio Marketplace. La finestra di dialogo **estensioni** > **Gestione estensioni** non è in grado di rilevare questi file, ma è possibile installare un file *VSIX* facendo doppio clic sul file o selezionando il file e premendo **invio**. Quindi, è sufficiente seguire le istruzioni. Una volta installata l'estensione, sarà possibile usare la finestra di dialogo **Gestisci estensioni** per abilitarla, disabilitarla o disinstallarla.

> [!NOTE]
> - Visual Studio Marketplace contiene estensioni VSIX e MSI. La finestra di dialogo Gestisci estensioni non può abilitare o disabilitare le estensioni basate su MSI.
> - Se un'estensione basata su MSI include un file *extension.vsixmanifest*, tale estensione viene visualizzata nella finestra di dialogo **Gestisci estensioni**.

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Disinstallare o disabilitare un'estensione

Se si desidera interrompere l'utilizzo di un'estensione, è possibile disabilitarla o disinstallarla. Disabilitandola, un'estensione rimarrà installata ma non caricata. Trovare l'estensione e fare clic su **Disinstalla** o **Disabilita**. Per scaricare un'estensione disabilitata, è necessario riavviare Visual Studio.

> [!NOTE]
> È possibile disabilitare le estensioni VSIX ma non le estensioni installate usando un file MSI. Le estensioni installate con MSI possono essere disinstallate solo.

## <a name="per-user-and-administrative-extensions"></a>Estensioni amministrative e per utente

La maggior parte delle estensioni è per singolo utente e sono installate nella cartella *%LocalAppData%\Microsoft\VisualStudio\\<\>Visual\\ Studio versione \Extensions* . Alcune estensioni sono di tipo amministrativo e vengono installate nel percorso *\<Cartella di installazione di Visual Studio>\Common7\IDE\Extensions\\* .

Per proteggere il sistema da estensioni che possono contenere errori o codice dannoso, è possibile limitare il caricamento delle estensioni per utente nei soli in casi in cui Visual Studio sia in esecuzione con autorizzazioni utente normali. Ciò significa che le estensioni per utente sono disabilitate quando Visual Studio viene eseguito con autorizzazioni elevate.

Per limitare il caricamento delle estensioni per utente:

1. Aprire la pagina Opzioni estensioni (**strumenti** > **Opzioni** > **estensioni**di**ambiente** > ).

2. Deselezionare la casella **di controllo carica estensioni per utente quando viene eseguito come amministratore** .

3. Riavviare Visual Studio.

## <a name="automatic-extension-updates"></a>Aggiornamenti automatici delle estensioni

Le estensioni vengono aggiornate automaticamente quando è disponibile una nuova versione in Visual Studio Marketplace. Dopo essere stata rilevata, la nuova versione dell'estensione viene installata in background. Alla successiva apertura di Visual Studio, verrà eseguita la nuova versione dell'estensione.

Se si desidera disabilitare gli aggiornamenti automatici, è possibile disabilitare la funzionalità per tutte le estensioni o solo per estensioni specifiche.

::: moniker range="vs-2017"

- Per disabilitare gli aggiornamenti automatici di tutte le estensioni, selezionare il collegamento **Modifica le impostazioni di estensioni e aggiornamenti** nella finestra di dialogo **Strumenti** > **Estensioni e aggiornamenti**. Nella finestra di dialogo **Opzioni** deselezionare **Aggiorna automaticamente le estensioni**.

- Per disabilitare gli aggiornamenti automatici per un'estensione specifica, deselezionare l'opzione **Aggiorna automaticamente questa estensione** nel riquadro dei dettagli dell'estensione sul lato destro della finestra di dialogo **Estensioni e aggiornamenti**.

::: moniker-end

::: moniker range=">=vs-2019"

- Per disabilitare gli aggiornamenti automatici di tutte le estensioni, selezionare il collegamento **Modifica le impostazioni di estensioni e aggiornamenti** nella finestra di dialogo **Estensioni** > **Gestisci estensioni**. Nella finestra di dialogo **Opzioni** deselezionare **Aggiorna automaticamente le estensioni**.

- Per disabilitare gli aggiornamenti automatici per un'estensione specifica, deselezionare l'opzione **Aggiorna automaticamente questa estensione** nel riquadro dei dettagli dell'estensione sul lato destro della finestra di dialogo **Gestisci estensioni**.

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Notifiche di arresto anomalo e non risposta

Visual Studio invia una notifica all'utente se sospetta che un'estensione è stata coinvolta in un arresto anomalo del sistema durante una sessione precedente. Quando Visual Studio subisce un arresto anomalo del sistema, memorizza lo stack dell'eccezione. Al successivo avvio di Visual Studio, viene esaminato lo stack, a partire dal nodo foglia e procedendo verso la base. Se Visual Studio determina che un frame appartiene a un modulo che fa parte di un'estensione installata e abilitata, visualizza una notifica.

Visual Studio invia una notifica anche se sospetta che un'estensione sia la causa di un blocco dell'interfaccia utente.

Quando queste notifiche vengono visualizzate, è possibile ignorare la notifica o eseguire una delle azioni seguenti:

::: moniker range="vs-2017"

- Scegliere **Disabilita questa estensione**. Visual Studio disabilita l'estensione e comunica se è necessario riavviare il sistema per rendere effettiva la disabilitazione. Se lo si desidera è possibile riabilitare l'estensione nella finestra di dialogo **Strumenti** > **Estensioni e aggiornamenti**.

::: moniker-end

::: moniker range=">=vs-2019"

- Scegliere **Disabilita questa estensione**. Visual Studio disabilita l'estensione e comunica se è necessario riavviare il sistema per rendere effettiva la disabilitazione. Se lo si desidera è possibile riabilitare l'estensione nella finestra di dialogo **Estensioni** > **Gestisci estensioni**.

::: moniker-end

- Scegliere **Non visualizzare più questo messaggio**.

  - Se la notifica riguarda un arresto anomalo in una sessione precedente, Visual Studio non visualizza più una notifica quando si verifica un arresto anomalo associato a questa estensione. Visual Studio visualizzerà comunque le notifiche in caso di blocco associabile all'estensione o per arresti anomali o blocchi che possono essere associati ad altre estensioni.
  - Se la notifica riguarda la mancata risposta, il Integrated Development Environment (IDE) non Visualizza più una notifica quando questa estensione è associata alla mancata risposta. Visual Studio visualizzerà comunque le notifiche relative all'arresto anomalo per questa estensione e le notifiche relative all'arresto anomalo e non rispondenti per altre estensioni.

- Scegliere **altre informazioni** per passare a questa pagina.

- Scegliere il pulsante **X** al termine della notifica per ignorarla. Verrà visualizzata una nuova notifica per le istanze future dell'estensione associata a un arresto anomalo o al blocco dell'interfaccia utente.

> [!NOTE]
> Una notifica di blocco dell'interfaccia utente o di arresto anomalo significa solo che uno dei moduli dell'estensione si trovava nello stack quando si è verificato il blocco dell'interfaccia utente o l'arresto anomalo. Ciò non significa necessariamente che l'estensione stessa sia la causa. È possibile che l'estensione abbia chiamato codice che fa parte di Visual Studio, che a sua volta ha comportato la mancata risposta dell'interfaccia utente o un arresto anomalo. Tuttavia, la notifica può rivelarsi ancora utile se l'estensione che ha causato il blocco dell'interfaccia utente o l'arresto anomalo non è importante. In questo caso, la disabilitazione dell'estensione evita il blocco dell'interfaccia utente o l'arresto anomalo in futuro senza influire sulla produttività.

## <a name="samples"></a>Esempi

Quando si installa un esempio online, la soluzione viene memorizzata in due posizioni:

- Una copia di lavoro viene memorizzata nel percorso specificato al momento della creazione del progetto.

- Una copia master separata viene memorizzata nel computer.

::: moniker range="vs-2017"

È possibile usare la finestra di dialogo **Strumenti** > **Estensioni e aggiornamenti** per eseguire queste attività correlate agli esempi:

::: moniker-end

::: moniker range=">=vs-2019"

È possibile usare la finestra di dialogo **Estensioni** > **Gestisci estensioni** per eseguire queste attività correlate agli esempi:

::: moniker-end

- Elencare le copie master degli esempi installati.

- Disabilitare o disinstallare la copia master di un esempio.

- Installare pacchetti di esempio, ovvero raccolte di esempi relativi a una tecnologia o una funzionalità.

- Installare singoli esempi online.

- Visualizzare notifiche di aggiornamenti quando vengono pubblicate modifiche al codice sorgente per gli esempi installati.

- Aggiornare la copia master di un esempio installato quando è disponibile una notifica di aggiornamento.

## <a name="see-also"></a>Vedere anche

- [Visual Studio Marketplace](https://marketplace.visualstudio.com)
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)