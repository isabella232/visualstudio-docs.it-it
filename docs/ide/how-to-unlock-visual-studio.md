---
title: Estendere una versione di valutazione o aggiornare una licenza
description: Informazioni su come estendere una versione di valutazione gratuita di Visual Studio, usare una sottoscrizione online o un codice Product Key per sbloccare Visual Studio e aggiornare una licenza non aggiornati o scaduta.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e75c0a2e75fc9207967501d0fae4a670f06e362f4f907438db1f84678c1d9173
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121232978"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Estendere una versione di valutazione o aggiornare una licenza

È possibile valutare una versione di valutazione gratuita [di Visual Studio Professional o Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) per 30 giorni. E se si accede, è possibile estendere il periodo di valutazione a 90 giorni. (Visual Studio Community è gratuito senza un periodo di valutazione. Tuttavia, è necessario [accedere](signing-in-to-visual-studio.md) periodicamente per mantenere aggiornata [la licenza.](#update-a-stale-license)

Per continuare a usare Visual Studio termine di un periodo di valutazione, sbloccarlo con una [sottoscrizione online](#use-an-online-subscription) o un codice [Product Key.](#enter-a-product-key)

## <a name="use-an-online-subscription"></a>Usare una sottoscrizione online

1. Scegliere **il** pulsante Accedi nell'angolo superiore destro dell'IDE (oppure passare a **Account file** Impostazioni per aprire la finestra di dialogo Account Impostazioni e quindi scegliere il pulsante  >    Accedi). 

1. Immettere le credenziali per un account Microsoft oppure un account aziendale o dell'istituto di istruzione. Visual Studio individua una sottoscrizione di Visual Studio o un'organizzazione di Azure DevOps associata all'account.

> [!IMPORTANT]
> Visual Studio cerca automaticamente le sottoscrizioni online associate quando ci si connette a un'organizzazione di Azure DevOps dalla finestra dello strumento **Team Explorer**. Quando ci si connette a un'organizzazione di Azure DevOps, si può accedere sia con un account Microsoft, sia con un account aziendale o dell'istituto di istruzione. Se è disponibile un abbonamento online per l'account utente, Visual Studio sbloccherà automaticamente l'IDE.

Per altre informazioni sulle sottoscrizioni Visual Studio e sul loro funzionamento, vedere la pagina Delle domande [frequenti sul supporto delle](https://visualstudio.microsoft.com/subscriptions/support/) sottoscrizioni.

## <a name="enter-a-product-key"></a>Immettere un codice Product Key

1. Selezionare **Account** Impostazioni file per aprire la finestra di dialogo Account Impostazioni e quindi scegliere il  >   collegamento Licenza con un codice Product **Key.** 

1. Immettere il codice Product Key nell'apposita casella.

> [!TIP]
> Le versioni preliminari di Visual Studio non includono codici Product Key. Per usare le versioni preliminari, è necessario accedere all'IDE.

Per altre informazioni su Visual Studio codici Product Key per Visual Studio e su come ottenerli, vedere la pagina [Using product keys in Visual Studio subscriptions (Uso](/visualstudio/subscriptions/product-keys) dei codici Product Key nelle sottoscrizioni Visual Studio prodotto).

## <a name="update-a-stale-license"></a>Aggiornare una licenza non aggiornato

Potrebbe essere visualizzato un messaggio Visual Studio che indica che la licenza non è più aggiornata e deve essere aggiornata.

![Messaggio di licenza non aggiornata di Visual Studio](../ide/media/vs2017_stale-license.png)

Questo messaggio indica che, anche se la sottoscrizione potrebbe essere ancora valida, il token di licenza che Visual Studio per mantenere aggiornata la sottoscrizione non è stato aggiornato. Visual Studio segnala che la licenza non è disponibile per uno dei motivi seguenti:

* Non è stato usato Visual Studio o non si è connessi a Internet per un periodo di tempo prolungato.
* È stata effettuata la disconnessione da Visual Studio.

Prima che il token della licenza diventi obsoleto, Visual Studio visualizza un messaggio di avviso che richiede di immettere nuovamente le credenziali.

Se le credenziali non vengono nuovamente specificate, il token inizia a non essere più recente e la finestra di dialogo Account Impostazioni indica **il** numero di giorni rimasti prima della scadenza del token. Dopo la scadenza del token, è necessario immettere nuovamente le credenziali per l'account prima di continuare a usare Visual Studio.

> [!Important]
> Se si usa Visual Studio per lunghi periodi di tempo in ambienti con accesso a Internet assente o limitato, è consigliabile usare un codice Product Key per sbloccare Visual Studio ed evitare interruzioni.

## <a name="update-an-expired-license"></a>Aggiornare una licenza scaduta

Se la sottoscrizione è scaduta e non si dispone più dei diritti di accesso Visual Studio, è necessario rinnovare la sottoscrizione o aggiungere un altro account con una sottoscrizione. Per altre informazioni sulla licenza in uso, passare a **Account** file Impostazioni e esaminare le informazioni sulla licenza sul lato  >   destro della finestra di dialogo. Se è associata un'altra sottoscrizione a un  account diverso, aggiungerlo all'elenco Tutti gli account sul lato sinistro della finestra di dialogo selezionando il collegamento Aggiungi **un account.**

## <a name="get-support"></a>Supporto

Non sempre tutto funziona correttamente. Se si verifica un problema, ecco alcune opzioni di supporto:

* Segnalare i problemi del prodotto usando lo [strumento Segnala](how-to-report-a-problem-with-visual-studio.md) un problema.
* Per risposte alle domande su sottoscrizioni, account e fatturazione, vedere Le domande [frequenti sul supporto per le sottoscrizioni](https://visualstudio.microsoft.com/subscriptions/support/).

## <a name="see-also"></a>Vedi anche

* [Accedi a Visual Studio](../ide/signing-in-to-visual-studio.md)
* [Confrontare Visual Studio edizioni](https://visualstudio.microsoft.com/vs/compare/)
* [Altre informazioni sulle sottoscrizioni Visual Studio](/visualstudio/subscriptions/)
