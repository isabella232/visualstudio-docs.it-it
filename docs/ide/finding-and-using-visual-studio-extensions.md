---
title: Trovare e installare le estensioni
description: Informazioni sulle estensioni Visual Studio e su come gestirle in modo da avere i controlli, gli esempi, i modelli, gli strumenti e altri componenti necessari.
ms.custom: SEO-VS-2020
ms.date: 09/18/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: b41f54d6e0b5750f32a4062d0915cbde1fe92cff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109227"
---
# <a name="manage-extensions-for-visual-studio"></a>Gestire le estensioni per Visual Studio

Le estensioni sono pacchetti di codice che vengono eseguiti Visual Studio e forniscono funzionalità nuove o migliorate. Le estensioni possono essere controlli, esempi, modelli, strumenti o altri componenti che aggiungono funzionalità a [Visual Studio,](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) ad esempio Live Share o [Visual Studio IntelliCode.](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode)

Per informazioni sulla creazione di Visual Studio, vedere [Visual Studio SDK.](../extensibility/visual-studio-sdk.md) Per informazioni sull'uso delle estensioni, vedere la pagina delle singole [estensioni Visual Studio Marketplace.](https://marketplace.visualstudio.com)

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

È possibile installare le estensioni [da Visual Studio Marketplace](https://marketplace.visualstudio.com) o dalla finestra di dialogo Estensioni e aggiornamenti in Visual Studio.

Per installare le estensioni dall'interno Visual Studio:

1. In **Strumenti**  >  **Estensioni e aggiornamenti** trovare l'estensione che si vuole installare. Se si conosce il nome o parte del nome dell'estensione, è possibile eseguire la ricerca nella **finestra** Cerca.

2. Selezionare **Download**.

   L'estensione viene pianificata per essere installata. L'estensione verrà installata dopo la chiusura di Visual Studio istanze di .

Se si tenta di installare un'estensione con dipendenze, il programma di installazione verifica se siano già installate. Se non sono installate, nella finestra di dialogo **Estensioni e aggiornamenti** verranno elencate tutte le dipendenze che devono essere installate prima dell'estensione.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Installare senza usare la finestra di dialogo Estensioni e aggiornamenti

Le estensioni che sono state incluse in file con estensione *vsix* possono essere disponibili in posizioni diverse da Visual Studio Marketplace. La **finestra** di dialogo Estensioni e aggiornamenti degli strumenti non è in grado di rilevare questi file, ma è possibile installare un file con estensione  >   *vsix* facendo doppio clic sul file o selezionandolo e premendo **INVIO.** Quindi, è sufficiente seguire le istruzioni. Una volta installata l'estensione, sarà possibile usare la finestra di dialogo **Estensioni e aggiornamenti** per abilitarla, disabilitarla o disinstallarla.

> [!NOTE]
> - Visual Studio Marketplace contiene estensioni VSIX e MSI. La finestra di dialogo Estensioni e aggiornamenti non può abilitare o disabilitare le estensioni basate su MSI.
> - Se un'estensione basata su MSI include un file *extension.vsixmanifest*, tale estensione viene visualizzata nella finestra di dialogo **Estensioni e aggiornamenti**.

::: moniker-end

::: moniker range=">=vs-2019"

È possibile installare le estensioni [da Visual Studio Marketplace](https://marketplace.visualstudio.com) o dalla finestra di dialogo Gestisci estensioni in Visual Studio.

Per installare le estensioni dall'interno Visual Studio:

1. In **Estensioni**  >  **Gestisci estensioni** trovare l'estensione che si vuole installare. (se si conosce il nome dell'estensione o parte di esso, è possibile eseguire la ricerca nella finestra di **ricerca**).

2. Selezionare **Download**.

   L'estensione viene pianificata per essere installata. L'estensione verrà installata dopo la chiusura di Visual Studio istanze di .

Se si tenta di installare un'estensione con dipendenze, il programma di installazione verifica se siano già installate. Se non sono installate, nella finestra di dialogo **Gestisci estensioni** verranno elencate tutte le dipendenze che devono essere installate prima dell'estensione.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Installare senza usare la finestra di dialogo Gestisci estensioni

Le estensioni che sono state incluse in file con estensione *vsix* possono essere disponibili in posizioni diverse da Visual Studio Marketplace. La **finestra di** dialogo Estensioni Gestisci estensioni non è in grado di rilevare questi file, ma è possibile installare un file con estensione  >   *vsix* facendo doppio clic sul file o selezionandolo e premendo **INVIO.** Quindi, è sufficiente seguire le istruzioni. Una volta installata l'estensione, sarà possibile usare la finestra di dialogo **Gestisci estensioni** per abilitarla, disabilitarla o disinstallarla.

> [!NOTE]
> - Visual Studio Marketplace contiene estensioni VSIX e MSI. La finestra di dialogo Gestisci estensioni non può abilitare o disabilitare le estensioni basate su MSI.
> - Se un'estensione basata su MSI include un file *extension.vsixmanifest*, tale estensione viene visualizzata nella finestra di dialogo **Gestisci estensioni**.

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Disinstallare o disabilitare un'estensione

Se si desidera interrompere l'utilizzo di un'estensione, è possibile disabilitarla o disinstallarla. Disabilitandola, un'estensione rimarrà installata ma non caricata. Trovare l'estensione e fare clic su **Disinstalla** o **Disabilita**. Per scaricare un'estensione disabilitata, è necessario riavviare Visual Studio.

> [!NOTE]
> È possibile disabilitare le estensioni VSIX, ma non le estensioni installate usando un file MSI. Le estensioni installate con MSI possono essere disinstallate solo.

## <a name="per-user-and-administrative-extensions"></a>Estensioni amministrative e per utente

La maggior parte delle estensioni è per utente e viene installata nella cartella *%LocalAppData%\Microsoft\VisualStudio \\<Visual Studio \> versione \Extensions. \\* Alcune estensioni sono estensioni amministrative e vengono installate nella *\<Visual Studio installation folder> cartella \Common7\IDE\Extensions. \\*

Per proteggere il sistema da estensioni che possono contenere errori o codice dannoso, è possibile limitare il caricamento delle estensioni per utente nei soli in casi in cui Visual Studio sia in esecuzione con autorizzazioni utente normali. Ciò significa che le estensioni per utente sono disabilitate quando Visual Studio viene eseguito con autorizzazioni elevate.

Per limitare il caricamento delle estensioni per utente:

1. Aprire la pagina delle opzioni delle estensioni (**Strumenti**  >  **Opzioni**  >  **Estensioni**  >  **ambiente**).

2. Deselezionare la **casella di controllo Carica estensioni per utente durante l'esecuzione come** amministratore .

3. Riavviare Visual Studio.

## <a name="automatic-extension-updates"></a>Aggiornamenti automatici delle estensioni

Le estensioni vengono aggiornate automaticamente quando è disponibile una nuova versione Visual Studio Marketplace. Dopo essere stata rilevata, la nuova versione dell'estensione viene installata in background. Alla successiva apertura di Visual Studio, verrà eseguita la nuova versione dell'estensione.

Se si desidera disabilitare gli aggiornamenti automatici, è possibile disabilitare la funzionalità per tutte le estensioni o solo per estensioni specifiche.

::: moniker range="vs-2017"

- Per disabilitare gli aggiornamenti automatici di tutte le estensioni, selezionare il collegamento **Modifica le impostazioni di estensioni e aggiornamenti** nella finestra di dialogo **Strumenti** > **Estensioni e aggiornamenti**. Nella finestra di dialogo **Opzioni** deselezionare **Aggiorna automaticamente le estensioni**.

- Per disabilitare gli aggiornamenti automatici per un'estensione specifica, deselezionare l'opzione **Aggiorna automaticamente questa estensione** nel riquadro dei dettagli dell'estensione sul lato destro della finestra di dialogo **Estensioni e aggiornamenti**.

::: moniker-end

::: moniker range=">=vs-2019"

- Per disabilitare gli aggiornamenti automatici di tutte le estensioni, selezionare il collegamento **Modifica le impostazioni di estensioni e aggiornamenti** nella finestra di dialogo **Estensioni** > **Gestisci estensioni**. Nella finestra di dialogo **Opzioni** deselezionare **Aggiorna automaticamente le estensioni**.

- Per disabilitare gli aggiornamenti automatici per un'estensione specifica, deselezionare l'opzione **Aggiorna automaticamente questa estensione** nel riquadro dei dettagli dell'estensione sul lato destro della finestra di dialogo **Gestisci estensioni**.

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Notifiche di arresto anomalo e blocco

Visual Studio invia una notifica all'utente se sospetta che un'estensione è stata coinvolta in un arresto anomalo del sistema durante una sessione precedente. Quando Visual Studio subisce un arresto anomalo del sistema, memorizza lo stack dell'eccezione. Al successivo avvio di Visual Studio, viene esaminato lo stack, a partire dal nodo foglia e procedendo verso la base. Se Visual Studio determina che un frame appartiene a un modulo che fa parte di un'estensione installata e abilitata, visualizza una notifica.

Visual Studio invia una notifica anche se sospetta che un'estensione sia la causa di un blocco dell'interfaccia utente.

Quando queste notifiche vengono visualizzate, è possibile ignorare la notifica o eseguire una delle azioni seguenti:

::: moniker range="vs-2017"

- Scegliere **Disabilita questa estensione**. Visual Studio disabilita l'estensione e comunica se è necessario riavviare il sistema per rendere effettiva la disabilitazione. Se si desidera, è possibile ri abilitare l'estensione nella finestra di dialogo Estensioni  >   e aggiornamenti degli strumenti .

::: moniker-end

::: moniker range=">=vs-2019"

- Scegliere **Disabilita questa estensione**. Visual Studio disabilita l'estensione e comunica se è necessario riavviare il sistema per rendere effettiva la disabilitazione. Se si desidera, è possibile ri abilitare l'estensione nella finestra di dialogo Estensioni gestisci  >   estensioni .

::: moniker-end

- Scegliere **Non visualizzare più questo messaggio**.

  - Se la notifica riguarda un arresto anomalo in una sessione precedente, Visual Studio non visualizza più una notifica quando si verifica un arresto anomalo associato a questa estensione. Visual Studio visualizzerà comunque le notifiche in caso di blocco associabile all'estensione o per arresti anomali o blocchi che possono essere associati ad altre estensioni.
  - Se la notifica riguarda la non risposta, l'ambiente di sviluppo integrato (IDE) non visualizza più una notifica quando questa estensione è associata alla non risposta. Visual Studio verranno comunque mostrate le notifiche relative all'arresto anomalo del sistema per questa estensione e le notifiche relative all'arresto anomalo e al blocco per altre estensioni.

- Scegliere **Altre informazioni** per passare a questa pagina.

- Scegliere il pulsante **X** al termine della notifica per ignorarla. Verrà visualizzata una nuova notifica per le istanze future dell'estensione associata a un arresto anomalo o al blocco dell'interfaccia utente.

> [!NOTE]
> Una notifica di blocco dell'interfaccia utente o di arresto anomalo significa solo che uno dei moduli dell'estensione si trovava nello stack quando si è verificato il blocco dell'interfaccia utente o l'arresto anomalo. Ciò non significa necessariamente che l'estensione stessa sia la causa. È possibile che l'estensione chiami codice che fa parte di Visual Studio, che a sua volta ha comportato un arresto anomalo o un'interfaccia utente non risponde. Tuttavia, la notifica può rivelarsi ancora utile se l'estensione che ha causato il blocco dell'interfaccia utente o l'arresto anomalo non è importante. In questo caso, la disabilitazione dell'estensione evita il blocco dell'interfaccia utente o l'arresto anomalo in futuro senza influire sulla produttività.

## <a name="samples"></a>Esempi

Quando si installa un esempio online, la soluzione viene memorizzata in due posizioni:

- Una copia di lavoro viene memorizzata nel percorso specificato al momento della creazione del progetto.

- Una copia master separata viene memorizzata nel computer.

::: moniker range="vs-2017"

È possibile usare la **finestra di** dialogo Estensioni > **e aggiornamenti** degli strumenti per eseguire queste attività correlate agli esempi:

::: moniker-end

::: moniker range=">=vs-2019"

È possibile usare la **finestra di** dialogo > **Estensioni gestione** estensioni per eseguire queste attività correlate agli esempi:

::: moniker-end

- Elencare le copie master degli esempi installati.

- Disabilitare o disinstallare la copia master di un esempio.

- Installare pacchetti di esempio, ovvero raccolte di esempi relativi a una tecnologia o una funzionalità.

- Installare singoli esempi online.

- Visualizzare notifiche di aggiornamenti quando vengono pubblicate modifiche al codice sorgente per gli esempi installati.

- Aggiornare la copia master di un esempio installato quando è disponibile una notifica di aggiornamento.

## <a name="see-also"></a>Vedi anche

- [Visual Studio Marketplace](https://marketplace.visualstudio.com)
- [Visual Studio Sdk](../extensibility/visual-studio-sdk.md)
