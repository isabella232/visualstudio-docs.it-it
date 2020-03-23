---
title: Estendere una versione di valutazione o aggiornare una licenza
description: Informazioni su come estendere una versione di valutazione gratuita di Visual Studio, usare una sottoscrizione online o un codice Product Key per sbloccare Visual Studio e aggiornare una licenza non aggiornata o scaduta.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 8e11d77a94c7c1d3d7b038ecea1a6c61646e371f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027572"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Estendere una versione di valutazione o aggiornare una licenza

È possibile valutare una versione di valutazione gratuita di [Visual Studio Professional o Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) per 30 giorni. E se accedi, puoi estendere il periodo di prova a 90 giorni. (Visual Studio Community è gratuito senza un periodo di prova. Tuttavia, è necessario [accedere](signing-in-to-visual-studio.md) periodicamente per mantenere [aggiornata](#update-a-stale-license)la licenza .)

Per continuare a utilizzare Visual Studio al termine di un periodo di prova, sbloccarlo con una [sottoscrizione online](#use-an-online-subscription) o un codice [Product Key](#enter-a-product-key).

## <a name="use-an-online-subscription"></a>Usare un abbonamento online

1. Scegliere il pulsante **Accedi** nell'angolo superiore destro dell'IDE oppure passare a**Impostazioni account** **file** > per aprire la finestra di dialogo **Impostazioni account** e quindi scegliere il pulsante **Accedi.**

1. Immettere le credenziali per un account Microsoft oppure un account aziendale o dell'istituto di istruzione. Visual Studio individua una sottoscrizione di Visual Studio o un'organizzazione di Azure DevOps associata all'account.

> [!IMPORTANT]
> Visual Studio cerca automaticamente le sottoscrizioni online associate quando ci si connette a un'organizzazione di Azure DevOps dalla finestra dello strumento **Team Explorer**. Quando ci si connette a un'organizzazione di Azure DevOps, si può accedere sia con un account Microsoft, sia con un account aziendale o dell'istituto di istruzione. Se è disponibile un abbonamento online per l'account utente, Visual Studio sbloccherà automaticamente l'IDE.

Per altre informazioni sulle sottoscrizioni di Visual Studio e sul loro funzionamento, vedere la pagina Domande frequenti sul [supporto per le sottoscrizioni.](https://visualstudio.microsoft.com/subscriptions/support/)

## <a name="enter-a-product-key"></a>Immettere un codice Product Key

1. Selezionare**Impostazioni account** **file** > per aprire la finestra di dialogo **Impostazioni account,** quindi scegliere il collegamento **Licenza con codice Product Key.**

1. Immettere il codice Product Key nell'apposita casella.

> [!TIP]
> Le versioni preliminari di Visual Studio non includono codici Product Key. Per usare le versioni preliminari, è necessario accedere all'IDE.

Per altre informazioni sui codici Product Key di Visual Studio per Visual Studio e su come ottenerli, vedere la pagina Utilizzo dei codici Product Key nelle sottoscrizioni di Visual Studio.For more information about Visual Studio product keys for Visual Studio and how to get them, see the [Using product keys in Visual Studio subscriptions](/visualstudio/subscriptions/product-keys) page.

## <a name="update-a-stale-license"></a>Aggiornare una licenza non aggiornata

È possibile che venga visualizzato un messaggio in Visual Studio che indica che la licenza è diventata obsoleta e deve essere aggiornata.

![Messaggio di licenza non aggiornata di Visual Studio](../ide/media/vs2017_stale-license.png)

Questo messaggio indica che, sebbene la sottoscrizione potrebbe essere ancora valida, il token di licenza utilizzato da Visual Studio per mantenere aggiornata la sottoscrizione non è stato aggiornato. Visual Studio segnala che la licenza non è aggiornata a causa di uno dei seguenti motivi:

* Visual Studio non è stato usato o non si è connessi a Internet per un periodo di tempo prolungato.
* È stata effettuata la disconnessione da Visual Studio.

Prima che il token della licenza diventi obsoleto, Visual Studio visualizza un messaggio di avviso che richiede di immettere nuovamente le credenziali.

Se non si reinserisse le credenziali, il token inizia a non essere aggiornato e la finestra di dialogo **Impostazioni account** indica quanti giorni sono rimasti prima della scadenza del token. Dopo la scadenza del token, è necessario immettere nuovamente le credenziali per l'account prima di continuare a usare Visual Studio.

> [!Important]
> Se si usa Visual Studio per lunghi periodi di tempo in ambienti con accesso a Internet assente o limitato, è consigliabile usare un codice Product Key per sbloccare Visual Studio ed evitare interruzioni.

## <a name="update-an-expired-license"></a>Aggiornare una licenza scaduta

Se la sottoscrizione è scaduta e non si dispone più dei diritti di accesso a Visual Studio, è necessario rinnovare la sottoscrizione o aggiungere un altro account con una sottoscrizione. Per ulteriori informazioni sulla licenza in uso, passare a**Impostazioni account** **file** > e controllare le informazioni sulla licenza sul lato destro della finestra di dialogo. Se si dispone di un'altra sottoscrizione associata a un account diverso, aggiungere tale account all'elenco **Tutti gli account** sul lato sinistro della finestra di dialogo selezionando il collegamento Aggiungi un **account.**

## <a name="get-support"></a>Supporto

Non sempre tutto funziona correttamente. Se si verifica un problema, ecco alcune opzioni di supporto:If you experience a problem, here are some support options:

* Segnalare i problemi relativi al prodotto utilizzando lo strumento [Segnala un problema.](how-to-report-a-problem-with-visual-studio.md)
* Per trovare le risposte alle domande su abbonamenti, account e fatturazione, fare clic su Domande frequenti sul [supporto per gli abbonamenti.](https://visualstudio.microsoft.com/subscriptions/support/)

## <a name="see-also"></a>Vedere anche

* [Accesso a Visual Studio](../ide/signing-in-to-visual-studio.md)
* [Confrontare le edizioni di Visual Studio](https://visualstudio.microsoft.com/vs/compare/)
* [Altre informazioni sulle sottoscrizioni di Visual StudioLearn more about Visual Studio subscriptions](/visualstudio/subscriptions/)
