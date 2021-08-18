---
title: Dati di IntelliTrace
description: Informazioni su come configurare l'adattatore dati di diagnostica per IntelliTrace per raccogliere informazioni di traccia di diagnostica specifiche Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/13/2016
ms.topic: how-to
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: f25c0b0e2ab80ac61b0256d1b4af2e95c02b2382
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092514"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Procedura: Raccogliere dati di IntelliTrace per agevolare il debug di problemi complessi

È possibile configurare l'adattatore dati di diagnostica per IntelliTrace per raccogliere informazioni di traccia di diagnostica specifiche Visual Studio. Questo adattatore può essere utilizzato nei test per raccogliere eventi di diagnostica significativi per l'applicazione, che uno sviluppatore può utilizzare successivamente per la traccia del codice allo scopo di individuare la causa di un bug. L'adattatore dati di diagnostica per IntelliTrace può essere utilizzato per i test manuali o per quelli automatizzati.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> IntelliTrace funziona solo in un'applicazione scritta utilizzando codice gestito. Se si esegue il test di un'applicazione Web in cui viene utilizzato un browser come client, non è necessario abilitare IntelliTrace per il client nelle impostazioni di test in quanto non è disponibile codice gestito da tracciare. In questo caso, è possibile configurare un ambiente e raccogliere dati IntelliTrace in modalità remota nel server Web.

I dati di IntelliTrace vengono archiviati in un file con estensione *.iTrace*. Quando si esegue il test e un passo del test non riesce, è possibile creare un bug. Il file di IntelliTrace contenente le informazioni di diagnostica verrà associato automaticamente al bug.

> [!NOTE]
> L'adattatore dati di diagnostica per IntelliTrace non crea un file di IntelliTrace per passi del test con esito positivo. Il file viene salvato solo in caso di errore del test case o quando si invia un bug.

I dati raccolti nel file di IntelliTrace consentono di migliorare la produttività del debug riducendo il tempo necessario per riprodurre e diagnosticare un errore nel codice. Dal momento che è possibile condividere il file di IntelliTrace con altri utenti affinché possano riprodurre la sessione locale nei propri computer, si riducono le probabilità che un bug risulti non riproducibile.

> [!NOTE]
> Se si abilita IntelliTrace nelle impostazioni di test, raccolta di dati di code coverage non funzionerà.

> [!WARNING]
> L'adattatore dati di diagnostica per IntelliTrace funziona tramite strumentazione di un processo gestito, che deve essere eseguito dopo il caricamento dei test per l'esecuzione dei test. Se il processo che si desidera monitorare è già stato avviato, non verrà raccolto alcun file di IntelliTrace perché il processo è già in esecuzione. Per ovviare a questo inconveniente, assicurarsi che il processo venga arrestato prima del caricamento dei test. Quindi, una volta caricati i test o avviato il primo test, avviare il processo.

::: moniker range="vs-2017"
Nella procedura seguente viene descritto come configurare i dati IntelliTrace che si desidera raccogliere. La procedura è valida sia per l'editor di configurazione in Microsoft Test Manager che per la finestra di dialogo Impostazioni test in Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
Nella procedura seguente viene descritto come configurare i dati IntelliTrace che si desidera raccogliere. Questi passaggi si applicano alla finestra di dialogo Impostazioni test in Visual Studio.
::: moniker-end

> [!NOTE]
> L'account utente per l'agente di test utilizzato per raccogliere dati IntelliTrace deve essere un membro del gruppo Administrators. Per altre informazioni, vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Configurazione dei dati da raccogliere con l'adattatore dati di diagnostica IntelliTrace

::: moniker range="vs-2017"
Prima di eseguire i passaggi della procedura, è necessario aprire le impostazioni test da Microsoft Test Manager o Visual Studio, quindi selezionare la pagina **Dati e diagnostica**.
::: moniker-end
::: moniker range=">=vs-2019"
Prima di eseguire i passaggi di questa procedura, è necessario aprire le impostazioni test da Visual Studio e selezionare la pagina **Dati e diagnostica**.
::: moniker-end

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Per configurare i dati da raccogliere con l'adattatore dati di diagnostica IntelliTrace

1. Selezionare il ruolo da utilizzare per raccogliere i dati di IntelliTrace.

2. Selezionare **IntelliTrace**.

3. Se si aggiunge IntelliTrace per un ruolo client Web o per un'applicazione Web ASP.NET, è necessario selezionare anche ASP.NET **Client Proxy per IntelliTrace** e Impatto test .

     Questo proxy consente di raccogliere informazioni sulle chiamate http da un client a un server Web per gli adattatori dati di diagnostica di IntelliTrace e impatto test.

    > [!WARNING]
    > Se si decide di usare un account personalizzato per l'identità usata per il pool di applicazioni in Internet Information Server (IIS) dove si desidera raccogliere dati IntelliTrace, è necessario creare il profilo dell'utente locale nel computer IIS per l'account personalizzato in uso. Il profilo locale per l'account personalizzato può essere creato accedendo localmente al computer IIS una volta o eseguendo la riga di comando seguente utilizzando le credenziali dell'account personalizzato:
    >
    > **runas /user:domain\name /profile cmd.exe**

4. Scegliere **Configura** per **IntelliTrace** per modificare le impostazioni predefinite di IntelliTrace.

     Verrà visualizzata la finestra di dialogo per configurare i dati da raccogliere.

    > [!WARNING]
    > Se si abilita la raccolta di dati di IntelliTrace, la raccolta di dati di code coverage non funzionerà.

5. Scegliere la **scheda** Generale. Selezionare **Eventi IntelliTrace solo per** registrare eventi di diagnostica significativi che hanno un impatto minimo sulle prestazioni durante il test.

     -oppure-

     Selezionare **Eventi IntelliTrace e informazioni sulle chiamate** per registrare eventi di diagnostica e traccia a livello di metodo in cui vengono mostrate le informazioni sulle chiamate. Questo livello di traccia potrebbe avere un impatto sulle prestazioni quando si eseguono i test.

6. Per raccogliere dati dall'applicazione ASP.NET in esecuzione su Internet Information Services, selezionare **Raccogli dati da applicazioni ASP.NET in esecuzione su Internet Information Services**. Impostare e configurare l'agente di test sul ruolo del server Web. Vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).

7. Scegliere la **scheda** Moduli. Selezionare Raccogli **dati da tutti i moduli tranne** i seguenti e usare **Aggiungi** per aggiungere all'elenco di moduli e **Rimuovi** per rimuovere un modulo. Questa opzione consente di includere tutti i moduli in esecuzione nel sistema, ad eccezione di quelli specificati.

     -oppure-

     Selezionare **Raccogli dati solo dai seguenti moduli** e usare **Aggiungi** per aggiungere moduli all'elenco e **Rimuovi** per rimuovere i moduli. Questa opzione consente di specificare esattamente i moduli desiderati.

    > [!NOTE]
    > Se possibile, selezionare i processi specifici che si desidera monitorare. Si tratta dell'operazione consigliata per prestazioni ottimali.

8. Scegliere **la scheda Processi.** Selezionare **Raccogli dati da tutti i processi tranne** i seguenti e usare **Aggiungi** per aggiungere all'elenco di processi e **Rimuovi** per rimuovere un processo. Questa opzione consente di includere tutti i processi in esecuzione nel sistema, ad eccezione di quelli specificati.

     -oppure-

     Selezionare **Raccogli dati solo dai processi specificati** e usare **Aggiungi** per aggiungere processi all'elenco e **Rimuovi** per rimuovere i processi. Questa opzione consente di specificare esattamente i processi desiderati.

9. (Facoltativo) Scegliere la **scheda Eventi IntelliTrace.** Selezionare o deselezionare ogni categoria di eventi IntelliTrace che si vuole includere o escludere quando si raccolgono eventi di diagnostica.

10. (Facoltativo) Espandere ogni categoria di eventi IntelliTrace e selezionare o deselezionare i singoli eventi che si desidera includere o escludere.

11. (Facoltativo) Scegliere la **scheda** Avanzate. Scegliere quindi la freccia accanto a **Quantità** massima di spazio su disco per la registrazione e selezionare le dimensioni massime da abilitare per il file IntelliTrace da usare.

    > [!NOTE]
    > Se si aumenta la dimensione della registrazione, si potrebbe verificare un problema di timeout quando si salva la registrazione con i risultati test.

12. Se si usa Microsoft Test Manager (deprecato in Visual Studio 2017), scegliere **Salva**. Se si usa Visual Studio, scegliere **OK**. Le impostazioni di IntelliTrace saranno quindi configurate e salvate per le impostazioni di test.

    ::: moniker range="vs-2017"
    > [!NOTE]
    > Per reimpostare la configurazione dell'adattatore dati di diagnostica, scegliere **Reimposta configurazione predefinita** per Visual Studio o **Ripristina predefinito** per Microsoft Test Manager.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!NOTE]
    > Per reimpostare la configurazione per questo adattatore dati di diagnostica, scegliere **Ripristina la configurazione predefinita** in Visual Studio.
    ::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Raccogliere dati di diagnostica durante i test (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [Raccogliere dati di diagnostica nei test manuali (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)
- [Raccogliere dati IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)
