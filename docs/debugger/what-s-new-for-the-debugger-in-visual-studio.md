---
title: Novità del debugger in Visual Studio 2017 | Microsoft Docs
titleSuffix: ''
description: Vedere le nuove funzionalità nel debugger versione 15.5. Sono inclusi gli snapshot del codice selezionato delle app in produzione e il passaggio indietro di Intellitrace.
ms.custom: SEO-VS-2020
ms.date: 01/22/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 7a743d43459e124d2377339a57756d8c0410a344
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112269"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Novità relative al debugger di Visual Studio 2017

Il debugger include queste nuove funzionalità:

- Novità della versione 15.5, il Snapshot Debugger crea uno snapshot delle app in produzione quando viene eseguito il codice a cui si è interessati.  Per indicare al debugger di creare uno snapshot, impostare punti di ancoraggio e punti di registrazione nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

    La raccolta di snapshot è disponibile per le seguenti app Web in esecuzione in Servizio app di Azure:

  * Applicazioni ASP.NET in esecuzione in .NET Framework 4.6.1 o versioni successive.
  * Applicazioni ASP.NET Core in esecuzione in .NET Core 2.0 o versioni successive in Windows.

    Per altre informazioni, vedere [Debug live ASP.NET apps using the Snapshot Debugger](../debugger/debug-live-azure-applications.md) (Eseguire il debug di app ASP.NET attive usando Snapshot Debugger).

- Novità della versione 15.5 in Visual Studio Enterprise, **intelliTrace** esegue automaticamente uno snapshot dell'applicazione a ogni punto di interruzione e a ogni evento del passaggio del debugger. Gli snapshot registrati consentono di tornare indietro ai punti di interruzione o ai passaggi precedenti e visualizzare stati passati dell'applicazione. La funzionalità per tornare indietro di IntelliTrace può consentire di risparmiare tempo quando si vuole visualizzare uno stato precedente dell'applicazione senza riavviare il debug o ricreare lo stato dell'app desiderato.

    È possibile esplorare e visualizzare gli snapshot tramite i pulsanti **Vai indietro** e **Vai avanti** sulla barra degli strumenti di Debug. Questi pulsanti consentono di spostarsi tra gli eventi visualizzati nella scheda **Eventi** della finestra **Strumenti di diagnostica**.

    ![Pulsanti Indietro e Avanti](../debugger/media/intellitrace-step-back-icons-description.png  "Pulsanti Indietro e Avanti")

    Per altre informazioni, vedere la pagina [Visualizzare lo stato precedente dell'applicazione con IntelliTrace](view-historical-application-state.md).

- **L'helper eccezioni** sostituisce Exception Assistant e viene visualizzato in una finestra di dialogo non modale in cui si è verificato l'errore. **L'helper** eccezioni fornisce un accesso più rapido a eventuali eccezioni interne,  un'analisi aggiuntiva da parte del debugger (se disponibile) e l'accesso immediato al Impostazioni eccezioni per l'eccezione. L'helper eccezioni può anche essere trascinato in una visualizzazione mobile se blocca un elemento che è necessario visualizzare.

    Ad esempio, **un'eccezione NullReferenceException** mostra ora la variabile con il riferimento Null (informazioni aggiuntive).

    ![Helper eccezioni del debugger](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Per altre informazioni, vedere il post del blog relativo all'[uso del nuovo supporto eccezione in Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/).

- È ora possibile eseguire su una riga di codice  mentre è in pausa nel debugger selezionando l'icona a forma di freccia verde Esegui l'esecuzione qui (l'icona viene visualizzata mentre si passa il puntatore del mouse su una riga di codice). In questo modo si elimina la necessità di impostare punti di interruzione temporanei.

    ![Esecuzione del debugger su cui fare clic](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- È possibile impostare condizioni per le eccezioni nella finestra di dialogo Exception  **Impostazioni** (A tale scopo, è possibile usare l'icona Modifica condizione nella finestra di dialogo Exception Impostazioni o usando il menu di scelta rapida nell'eccezione). Le condizioni attualmente supportate includono i nomi dei moduli da includere o escludere per l'eccezione.

    ![Condizioni per un'eccezione](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- La finestra di dialogo Collega a processo include una nuova funzionalità di ricerca che consente di identificare più rapidamente il processo a cui è necessario connettersi.

    ![Cercare in Collega a processo](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Per altre informazioni su queste nuove funzionalità, vedere le [note sulla versione per [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes).

## <a name="see-also"></a>Vedi anche

- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)