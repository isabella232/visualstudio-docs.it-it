---
title: Trovare le modifiche apportate al codice e altri elementi della cronologia con CodeLens
description: Informazioni su CodeLens e su come usarlo per esplorare la cronologia del codice senza dover uscire dall'editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.CodeLens
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 54054e39a9211bf63d6c187a250a47dcb1ed751c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094529"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Trovare le modifiche apportate al codice e altri elementi della cronologia con CodeLens

CodeLens consente di rimanere concentrati sulle proprie attività mentre si cercano informazioni sul codice senza uscire dall'editor. È possibile trovare i riferimenti a un frammento di codice, le modifiche apportate al codice, i bug collegati, gli elementi di lavoro, le revisioni del codice e gli unit test.

::: moniker range=">=vs-2019"

> [!NOTE]
> CodeLens è disponibile nella versione Visual Studio Community, ma gli *indicatori* di controllo del codice sorgente non sono disponibili in questa edizione.

::: moniker-end

::: moniker range="vs-2017"

> [!NOTE]
> CodeLens è disponibile solo nelle edizioni Visual Studio Enterprise e Visual Studio Professional. Non è disponibile nell'edizione Community di Visual Studio.

::: moniker-end

Vedere dove e come vengono usate le singole parti di codice nella soluzione:

![Indicatori CodeLens nell'editor del codice](../ide/media/codelens-overview.png)

È anche possibile contattare il team in merito alle modifiche al codice senza uscire dall'editor:

![CodeLens - Contattare il team](../ide/media/codelens-contact-info.png)

Per scegliere gli indicatori da visualizzare o per disattivare CodeLens e attivarlo, passare a Strumenti Opzioni Editor di testo Editor di testo Tutti i  >    >    >    >  **linguaggi CodeLens**.

## <a name="find-references-to-your-code"></a>Individuare i riferimenti del codice

È possibile trovare i riferimenti nel codice C# o Visual Basic.

1. Scegliere **l'indicatore** dei riferimenti o **premere ALT** + **2.**

   ![Riferimenti CodeLens](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > Se l'indicatore specifica che i **riferimenti sono pari a 0**, non sono disponibili riferimenti dal codice C# o Visual Basic. Questo non include riferimenti da altri elementi, ad esempio file *XAML* e *ASPX*.

2. Per visualizzare il codice con riferimenti, posizionare il mouse sul riferimento nell'elenco.

   ![CodeLens - Selezionare un riferimento](../ide/media/codelens-peek-reference.png)

3. Per aprire il file che contiene il riferimento, fare doppio clic sul riferimento.

### <a name="code-maps"></a>Mappe codice

Per visualizzare le relazioni tra il codice e i relativi riferimenti, [creare una mappa del codice](../modeling/map-dependencies-across-your-solutions.md). Nel menu di scelta rapida della mappa del codice, selezionare **Mostra tutti i riferimenti**.

![CodeLens - Riferimenti sulla mappa codici](../ide/media/codelensmappedreferences.png)

## <a name="find-changes-in-your-code"></a>Individuare le modifiche nel codice

Esaminare la cronologia del codice per scoprire cosa è successo oppure esaminare le modifiche prima che vengano unite nel codice per ottenere altre informazioni sull'eventuale impatto di modifiche in altri rami sul codice.

È necessario:

- Visual Studio Enterprise o Professional

- Azure DevOps Services, Team Foundation Server 2013 o versioni successive o Git

- [Skype for Business](/skypeforbusiness/) per contattare il team dall'editor di codice

Per il codice C# o Visual Basic archiviato con il controllo della versione di Team Foundation (TFVC) o Git, si ricevono dettagli CodeLens a livello di classe e metodo (indicatori *a livello di elemento codice*). Se il repository Git è ospitato in TfGit, è anche possibile ottenere collegamenti negli elementi di lavoro TFS.

![Indicatori a livello di elemento di codice](../ide/media/codelens-element-level-indicators.png)

Per i tipi di file diversi da *CS* o *VB* si ricevono dettagli CodeLens per l'intero file in un'unica posizione nella parte inferiore della finestra (indicatori *a livello di file*).

![Indicatori CodeLens a livello di file](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>Indicatori a livello di elemento di codice

Gli indicatori a livello di elemento di codice consentono di vedere chi ha modificato il codice e quali modifiche sono state apportate. Gli indicatori a livello di elemento di codice sono disponibili per il codice C# e Visual Basic.

È ciò che viene visualizzato quando si usa il controllo della versione di Team Foundation in Team Foundation Server o Azure DevOps Services:

![CodeLens- Ottenere la cronologia delle modifiche per il codice nel controllo della versione di Team Foundation](../ide/media/codelens-code-changes.png)

Il periodo di tempo predefinito è 12 secondi. Se il codice è archiviato in Team Foundation Server, è possibile modificare il periodo di tempo eseguendo il [comando TFSConfig](/azure/devops/server/command-line/tfsconfig-cmd) con il [comando CodeIndex](../ide/codeindex-command.md) e il flag **/indexHistoryPeriod**.

Per visualizzare una cronologia dettagliata di tutte le modifiche, comprese quelle di più di un anno fa, scegliere **Mostra tutte le modifiche apportate ai file**:

![Mostra tutte le modifiche del codice](../ide/media/codelens-show-all-file-changes.png)

Viene aperta la finestra **Cronologia**:

![Finestra Cronologia per tutte le modifiche del codice](../ide/media/codelenscodechangeshistory.png)

Quando i file si trovano in un repository Git e si sceglie l'indicatore di modifiche a livello di elemento di codice, questo è ciò che viene visualizzato:

![CodeLens - Ottenere la cronologia delle modifiche per il codice in GIT](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>Indicatori a livello di file

Individuare le modifiche di un intero file negli indicatori a livello di file nella parte inferiore della finestra:

![CodeLens - Ottenere i dettagli sul file del codice](../ide/media/codelens-file-level.png)

> [!NOTE]
> Gli indicatori a livello di file non sono disponibili per i file di C# e Visual Basic.

Per ottenere altre informazioni su una modifica, fare clic con il pulsante destro del mouse su tale elemento. A seconda se si usa TFVC o Git, sono disponibili opzioni per confrontare le versioni del file, visualizzare i dettagli e tenere traccia delle modifiche, ottenere la versione selezionata del file e inviare un messaggio di posta elettronica all'autore della modifica. Alcuni di questi dettagli vengono visualizzati in **Team Explorer**.

È possibile anche visualizzare l'utente che ha modificato il codice nel tempo, consentendo di individuare i criteri delle modifiche del team e di valutarne l'impatto.

![CodeLens: visualizzare la cronologia delle modifiche del codice sotto forma di grafico](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>Individuare le modifiche nel branch corrente

Il team può essere costituito da più branch, ad esempio un branch principale e un branch figlio di sviluppo, per ridurre il rischio di danneggiare la stabilità del codice.

![CodeLens: trovare le modifiche nel ramo corrente](../ide/media/codelensfirstbranchconceptual.png)

È possibile scoprire quante persone hanno modificato il codice e quante modifiche sono state apportate nel ramo principale premendo + **ALT+6:**

![CodeLens: individuazione del numero di modifiche nel branch corrente](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>Individuare il punto in cui il codice è stato sottoposto a branching

Per sapere quando il codice è stato sottoposto a branching, passare al codice nel branch figlio. Selezionare quindi l'indicatore delle **modifiche** o premere **ALT**+**6**:

![CodeLens: individuare il punto in cui il codice è stato sottoposto a branching](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>Individuare le modifiche in arrivo da altri branch

![CodeLens: individuare le modifiche apportate al codice in altri branch](../ide/media/codelensbranchchangecheckinconceptual.png)

È possibile visualizzare le modifiche in ingresso. Nella schermata seguente è stato corretto un bug nel branch "Dev":

![CodeLens: modifica verificata in un altro ramo](../ide/media/codelens-branch-changes-dev.png)

È possibile esaminare la modifica senza uscire dal branch corrente ("Main"):

![CodeLens: visualizzazione della modifica in arrivo da un altro ramo](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>Scoprire quando sono state unite le modifiche

È possibile vedere quando sono state unite le modifiche, in modo da poter determinare quali modifiche sono incluse nel branch:

![CodeLens- Trovare quando le modifiche sono state unite](../ide/media/codelensbranchmergedconceptual.png)

Ad esempio, il codice nel branch principale include ora la correzione di bug del branch di sviluppo ("Dev"):

![CodeLens - Merge delle modifiche tra branch](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>Confrontare una modifica in arrivo con la versione locale

Confrontare una modifica in ingresso con la versione locale premendo **MAIUSC** F10 o facendo + doppio clic sull'insieme di modifiche.

![CodeLens: confronto della modifica in arrivo con quella locale](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>Icone di branch

L'icona visualizzata nella colonna **Branch** indica in che modo il branch è correlato al branch in uso.

|**Icona**|**La modifica proviene da:**|
|--------------| - |
|![CodeLens: icona di modifica da branch corrente](../ide/media/codelensbranchcurrenticon.png)|Branch corrente|
|![CodeLens: icona di modifica da branch padre](../ide/media/codelensbranchparenticon.png)|Branch padre|
|![CodeLens: icona di modifica da branch figlio](../ide/media/codelensbranchchildicon.png)|Branch figlio|
|![CodeLens: icona di modifica da branch peer](../ide/media/codelensbranchpeericon.png)|Branch peer|
|![CodeLens: icona di modifica da branch più lontano](../ide/media/codelensbranchfurtherawayicon.png)|Branch più lontano rispetto a un branch padre, figlio o peer|
|![CodeLens: icona di merge da branch padre](../ide/media/codelensbranchmergefromparenticon.png)|Unione dal branch padre in un branch figlio|
|![CodeLens: icona di merge da branch figlio](../ide/media/codelensbranchmergefromchildicon.png)|Unione da un branch figlio nel branch padre|
|![CodeLens: icona di merge da branch non correlato](../ide/media/codelensbranchmergefromunrelatedicon.png)|Unione da un branch non correlato (unione senza base)|

## <a name="linked-work-items"></a>Elementi di lavoro collegati

Per trovare elementi di lavoro collegati, selezionare l'indicatore degli **elementi di lavoro** o premere **ALT**+**8**.

![CodeLens - Trovare gli elementi di lavoro per un codice specifico](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Revisioni del codice collegate

Per individuare le revisioni del codice collegate, selezionare l'indicatore delle **revisioni**. Per usare la tastiera, tenere premuto il testo **ALT** quindi premere la **freccia SINISTRA** o la **freccia DESTRA** per spostarsi tra le opzioni dell'indicatore.

![CodeLens - Visualizzare le richieste di revisione del codice](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Bug collegati

Per trovare i bug collegati, selezionare l'indicatore dei **bug** o premere **ALT**+**7**.

![CodeLens - Trovare bug collegati agli insiemi di modifiche](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Contattare il proprietario di un elemento

Per trovare l'autore di un elemento, selezionare l'indicatore degli **autori** o premere **ALT**+**5**.

![Contattare il proprietario di un elemento](../ide/media/codelens-contact-item-owner.png)

Aprire il menu di scelta rapida di un elemento per visualizzare le opzioni di contatto. Se è installato Lync o Skype per Business, è possibile visualizzare queste opzioni:

![Opzioni di contatto per un elemento](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>Unit test associati

È possibile individuare gli unit test disponibili per il codice C# o Visual Basic senza dover aprire **Test Explorer**.

1. Accedere all'applicazione contenente il [codice di unit test](../test/unit-test-your-code.md) associato.

2. Se non se ne ha già uno, compilare l'applicazione per caricare gli indicatori test di CodeLens.

3. Esaminare i test per il codice premendo **ALT** + **3.**

     ![CodeLens - Scegliere lo stato del test nell'editor del codice](../ide/media/codelens-choose-test-indicator.png)

4. Se viene visualizzata un'icona di avviso ![icona di avviso](../ide/media/codelenstestwarningicon.png), i test non sono ancora stati eseguiti, quindi eseguirli.

     ![CodeLens - Visualizzare gli unit test non ancora in esecuzione](../ide/media/codelens-tests-not-yet-run.png)

5. Per esaminare la definizione di un test, fare doppio clic sull'elemento di test nella finestra dell’indicatore CodeLens per aprire il file di codice nell'editor.

     ![CodeLens - Passare alla definizione di unit test](../ide/media/codelens-unit-test-definition.png)

6. Per esaminare i risultati del test, scegliere l'indicatore di stato del test ( icona test non superato o icona test superato ![ ](../ide/media/codelenstestfailedicon.png) ) oppure premere ![ ](../ide/media/codelenstestpassedicon.png) **ALT** + **1.**

     ![CodeLens - Visualizzare il risultato dello unit test](../ide/media/codelens-unit-test-result.png)

7. Per vedere quante persone hanno modificato il test, gli autori delle modifiche o il numero di modifiche apportate al test, [individuare la cronologia del codice](#find-changes-in-your-code) e gli elementi collegati.

## <a name="keyboard-shortcuts"></a>Scelte rapide da tastiera

Per usare la tastiera per selezionare gli indicatori, premere e tenere premuto il tasto **ALT** per visualizzare i tasti numerici correlati, quindi premere il numero che corrisponde all'indicatore da selezionare.

![Numeri di accesso da tastiera](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> Per selezionare l'indicatore delle **revisioni**, tenere premuto il tasto **ALT** mentre si usano le frecce DESTRA e SINISTRA per spostarsi.

## <a name="q--a"></a>Domande e risposte

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>D: Ricerca per categorie disattivare o attivare CodeLens o scegliere quali indicatori visualizzare?

**R:**  È possibile attivare o disattivare tutti gli indicatori, ad eccezione di Riferimenti. Passare a **Strumenti Opzioni**  >  **Editor di**  >  **testo** Tutti  >  **i linguaggi**  >  **CodeLens.**

Quando gli indicatori sono attivati, è possibile anche aprire le opzioni CodeLens dagli indicatori.

![CodeLens - Attivare o disattivare gli indicatori](../ide/media/codelensturnoffonindicatorsfromcode.png)

Attivare gli indicatori CodeLens a livello di file e disattivare l’utilizzo delle icone con la freccia di espansione nella parte inferiore della finestra dell'editor.

![Attivare e disattivare gli indicatori a livello di file](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>D: Dove si trova CodeLens?

**R:** CodeLens viene visualizzato nel codice C# e Visual Basic a livello di metodo, classe, indicizzatore e proprietà. CodeLens viene visualizzato a livello di file per tutti gli altri tipi di file.

- Assicurarsi che CodeLens sia attivato. Passare a **Strumenti Opzioni**  >  **Editor di**  >  **testo** Tutti  >  **i linguaggi**  >  **CodeLens.**

- Se il codice è archiviato in TFS, assicurarsi che l'indicizzazione del codice sia attivata usando il [comando CodeIndex](../ide/codeindex-command.md) con il [comando Config di TFS](/azure/devops/server/command-line/tfsconfig-cmd).

- Gli indicatori DevOps vengono visualizzati solo quando gli elementi di lavoro sono collegati al codice e quando l'utente è autorizzato ad aprire gli elementi di lavoro collegati. Verificare di disporre delle autorizzazioni [per i membri del team](/azure/devops/organizations/security/view-permissions?view=vsts&preserve-view=true).

- Gli indicatori di unit test non vengono visualizzati quando il codice dell'applicazione non contiene unit test. Gli indicatori di stato del test vengono visualizzati automaticamente nei progetti di test. Se si sa che il codice dell'applicazione include unit test, ma gli indicatori di test non vengono visualizzati, provare a compilare la soluzione (**CTRL** + **MAIUSC** + **B).**

::: moniker range=">=vs-2019"

> [!TIP]
> CodeLens è disponibile in Visual Studio Community edition, ma gli *indicatori* del controllo del codice sorgente non sono disponibili in questa edizione.

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> CodeLens non è disponibile nell'edizione Visual Studio Community.

::: moniker-end

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>D: Perché non vengono visualizzati i dettagli degli elementi di lavoro per un commit?

**R:** Questo problema potrebbe verificarsi perché CodeLens non è in grado di trovare gli elementi di lavoro in Azure Boards o TFS. Verificare di essere connessi al progetto che include quegli elementi di lavoro e di essere autorizzati a visualizzare tali elementi. I dettagli degli elementi di lavoro possono non apparire anche se la descrizione di commit contiene informazioni non corrette sugli ID elemento di lavoro in Azure Boards o TFS.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>D: perché gli indicatori di Skype non sono visualizzati?

**R:** gli indicatori di Skype non vengono visualizzati se non si è connessi a Skype for Business, il programma non è installato o la configurazione non è supportata. È comunque possibile inviare messaggi di posta elettronica:

![CodeLens - Contattare il proprietario dell'insieme di modifiche per posta](../ide/media/codelenscodesendmailchangesetnolync1.png)

**Quali configurazioni di Skype e Lync sono supportate?**

- Skype per Business (32 bit o 64 bit)

- Lync 2010 o nelle versioni successive da solo (32 bit o 64 bit), ma non Lync Basic 2013 con Windows 8.1

CodeLens non supporta l'installazione di versioni di Lync o Skype diverse. Potrebbero non essere stati localizzati per tutte le versioni localizzate di Visual Studio.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>D: Come si modifica il tipo di carattere e il colore per CodeLens?

**R:** passare a **Strumenti** > **Opzioni** > **Ambiente** > **Tipi di carattere e colori**.

![CodeLens - Modificare le impostazioni di colore e tipo di carattere](../ide/media/codelensoptionsfontscolorssettings.png)

Per usare la tastiera:

1. Premere  + **ALT+O** +  per aprire la **finestra di** dialogo Opzioni.

2. Premere **Freccia SU** o **Freccia GIÙ** per passare al nodo **Ambiente** , quindi premere **Freccia SINISTRA** per espandere il nodo.

3. Premere **Freccia GIÙ** da passare a **Tipi di carattere e colori**.

4. Premere **TAB** per passare all'elenco **Mostra impostazioni** per e quindi premere **Freccia** GIÙ per **selezionare CodeLens.**

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>D: È possibile spostare l'heads-up display CodeLens?

**R:** sì, scegliere l'![icona di ancoraggio](../ide/media/codelensdockwindow.png) per ancorare CodeLens come una finestra.

![Pulsante di ancoraggio della finestra degli indicatori CodeLens](../ide/media/codelensselectdockwindow.png)

![Finestra Riferimenti CodeLens ancorata](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>D: come si aggiornano gli indicatori?

**R:** Dipende dall'indicatore:

- **Riferimenti**: questo indicatore viene aggiornato automaticamente in caso di modifica del codice. Se l'indicatore **Riferimenti** è ancorato come finestra separata, è possibile aggiornarlo selezionando **Aggiorna**:

   ![Pulsante Aggiorna nei riferimenti CodeLens](../ide/media/codelensviewreferencesdocked.png)

- **Team**: aggiornare questi indicatori selezionando **Aggiorna indicatori team CodeLens** dal menu di scelta rapida:

   ![Voce di menu Aggiorna indicatori team CodeLens](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Test**: [trovare unit test per il codice](#associated-unit-tests) per aggiornare l'indicatore **Test**.

### <a name="q-whats-local-version"></a>D: Qual è la "versione locale"?

**R:** la freccia **Versione locale** punta al set di modifiche più recente nella versione locale di un file. Quando il server ha insiemi di modifiche più recenti, vengono visualizzati sopra o sotto la freccia **Versione locale** , a seconda dell'ordine usato per ordinare gli insiemi di modifiche.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>D: È possibile gestire la modalità di elaborazione del codice in CodeLens per visualizzare la cronologia e gli elementi collegati?

**R:** Sì. Se il codice è disponibile in TFS, usare il [comando CodeIndex](../ide/codeindex-command.md) con il [comando Config di TFS](/azure/devops/server/command-line/tfsconfig-cmd).

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>D: Gli indicatori test di CodeLens non vengono più visualizzati nel file quando si apre la soluzione per la prima volta. Come possono essere caricati?

**R:** Ricompilare il progetto per ottenere gli indicatori test di CodeLens da caricare nel file. Per migliorare le prestazioni, Visual Studio non recupera più le informazioni sull'origine per gli indicatori test quando vengono caricati file di codice. Gli indicatori test vengono caricati dopo una compilazione o quando si seleziona un test facendo doppio clic in **Esplora Test**.

## <a name="see-also"></a>Vedi anche

- [Funzionalità dell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)
