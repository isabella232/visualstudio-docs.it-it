---
title: Novità del debugger in Visual Studio 2017 | Microsoft Docs
titleSuffix: ''
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
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 130387fedce065948ebe09ea605e32cf89ad820b
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71210596"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Novità relative al debugger di Visual Studio 2017

Il debugger include le nuove funzionalità seguenti:

- Novità della versione 15,5, il **snapshot debugger** crea uno snapshot delle app in produzione quando viene eseguito il codice a cui si è interessati. Per indicare al debugger di creare uno snapshot, impostare punti di ancoraggio e punti di registrazione nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

    La raccolta di snapshot è disponibile per le seguenti app Web in esecuzione in Servizio app di Azure:

  * Applicazioni ASP.NET in esecuzione in .NET Framework 4.6.1 o versioni successive.
  * Applicazioni ASP.NET Core in esecuzione in .NET Core 2.0 o versioni successive in Windows.

    Per altre informazioni, vedere [Debug live ASP.NET apps using the Snapshot Debugger](../debugger/debug-live-azure-applications.md) (Eseguire il debug di app ASP.NET attive usando Snapshot Debugger).

- Novità della versione 15,5 solo in Visual Studio Enterprise, **IntelliTrace** esegue automaticamente uno snapshot dell'applicazione a ogni punto di interruzione e evento del debugger. Gli snapshot registrati consentono di tornare indietro ai punti di interruzione o ai passaggi precedenti e visualizzare stati passati dell'applicazione. La funzionalità per tornare indietro di IntelliTrace può consentire di risparmiare tempo quando si vuole visualizzare uno stato precedente dell'applicazione senza riavviare il debug o ricreare lo stato dell'app desiderato.

    È possibile esplorare e visualizzare gli snapshot tramite i pulsanti **Vai indietro** e **Vai avanti** sulla barra degli strumenti di Debug. Questi pulsanti consentono di spostarsi tra gli eventi visualizzati nella scheda **Eventi** della finestra **Strumenti di diagnostica**.

    ![Pulsanti Passo indietro e Passo avanti](../debugger/media/intellitrace-step-back-icons-description.png  "Pulsanti Passo indietro e Passo avanti")

    Per altre informazioni, vedere la pagina [Visualizzare lo stato precedente dell'applicazione con IntelliTrace](../debugger/view-historical-application-state.md).

- L' **Helper eccezioni** sostituisce le informazioni sulle eccezioni e viene visualizzato in una finestra di dialogo non modale in cui si è verificato l'errore. L' **Helper eccezioni** fornisce un accesso più rapido a eventuali eccezioni interne, ulteriori analisi da parte del debugger (se disponibili) e accesso immediato alle **impostazioni delle eccezioni** per l'eccezione. L'helper eccezioni può essere trascinato anche in una visualizzazione a virgola mobile se blocca qualcosa che è necessario visualizzare.

    Ad esempio, un' **eccezione NullReferenceException** Mostra ora la variabile con il riferimento null (informazioni aggiuntive).

    ![Helper eccezioni del debugger](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Per altre informazioni, vedere il post del blog relativo all'[uso del nuovo supporto eccezione in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

- È ora possibile eseguire fino a una riga di codice mentre viene sospesa nel debugger selezionando l'icona della freccia **su Esegui esecuzione fino a qui** (l'icona viene visualizzata al passaggio del mouse su una riga di codice). In questo modo si elimina la necessità di impostare punti di interruzione temporanei.

    ![Esecuzione del debugger fino al clic](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- È possibile impostare le condizioni per le eccezioni nella finestra di dialogo **Impostazioni eccezioni** . a tale scopo, è possibile utilizzare l'icona **Modifica condizione** nella finestra di dialogo Impostazioni eccezioni oppure utilizzare il menu di scelta rapida per l'eccezione. Le condizioni attualmente supportate includono i nomi di modulo da includere o escludere per l'eccezione.

    ![Condizioni in un'eccezione](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- La finestra di dialogo Connetti a processo include una nuova funzionalità di ricerca che consente di identificare più rapidamente il processo a cui è necessario connettersi.

    ![Cerca in Connetti a processo](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Per ulteriori informazioni su queste nuove funzionalità, vedere le [Note sulla versione [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]di ](/visualstudio/releasenotes/vs2017-relnotes).

## <a name="see-also"></a>Vedere anche

- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)