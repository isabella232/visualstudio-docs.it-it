---
title: Estendere una versione di valutazione o aggiornare una licenza
description: Informazioni su come estendere una versione di valutazione gratuita di Visual Studio, usare una sottoscrizione online o un codice Product Key per sbloccare Visual Studio e aggiornare una licenza obsoleta o scaduta.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: db0f75b3e4c2f066b7a9d79976a50efd3364d7bd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591372"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Estendere una versione di valutazione o aggiornare una licenza

È possibile valutare una versione di valutazione gratuita di [Visual Studio Professional o Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) per 30 giorni. Se si accede, è possibile estendere il periodo di valutazione a 90 giorni. La community di Visual Studio è gratuita senza un periodo di valutazione. Tuttavia, è necessario [accedere](signing-in-to-visual-studio.md) periodicamente per rendere aggiornata la [licenza](#update-a-stale-license).

Per continuare a usare Visual Studio al termine di un periodo di valutazione, sbloccarlo con una [sottoscrizione online](#use-an-online-subscription) o un [codice Product Key](#enter-a-product-key).

## <a name="use-an-online-subscription"></a>Usa una sottoscrizione online

1. Scegliere il pulsante **Accedi** nell'angolo superiore destro dell'IDE oppure passare a **file** > **Impostazioni account** per aprire la finestra di dialogo **Impostazioni account** e quindi scegliere il pulsante **Accedi** .

1. Immettere le credenziali per un account Microsoft oppure un account aziendale o dell'istituto di istruzione. Visual Studio individua una sottoscrizione di Visual Studio o un'organizzazione di Azure DevOps associata all'account.

> [!IMPORTANT]
> Visual Studio cerca automaticamente le sottoscrizioni online associate quando ci si connette a un'organizzazione di Azure DevOps dalla finestra dello strumento **Team Explorer**. Quando ci si connette a un'organizzazione di Azure DevOps, si può accedere sia con un account Microsoft, sia con un account aziendale o dell'istituto di istruzione. Se è disponibile un abbonamento online per l'account utente, Visual Studio sbloccherà automaticamente l'IDE.

Per ulteriori informazioni sulle sottoscrizioni di Visual Studio e sul relativo funzionamento, vedere la pagina relativa alle [domande frequenti sul supporto delle sottoscrizioni](https://visualstudio.microsoft.com/subscriptions/support/) .

## <a name="enter-a-product-key"></a>Immettere un codice Product Key

1. Selezionare **File** > **Impostazioni account** per aprire la finestra di dialogo **Impostazioni account** e quindi scegliere il collegamento **Licenza con codice Product Key**.

1. Immettere il codice Product Key nell'apposita casella.

> [!TIP]
> Le versioni preliminari di Visual Studio non includono codici Product Key. Per usare le versioni preliminari, è necessario accedere all'IDE.

Per altre informazioni sui codici Product Key di Visual Studio per Visual Studio e su come ottenerli, vedere la pagina relativa all' [uso di codici Product Key in sottoscrizioni di Visual Studio](/visualstudio/subscriptions/product-keys) .

## <a name="update-a-stale-license"></a>Aggiornare una licenza obsoleta

In Visual Studio potrebbe essere visualizzato un messaggio che indica che la licenza è diventata obsoleta e deve essere aggiornata.

![Messaggio di licenza non aggiornata di Visual Studio](../ide/media/vs2017_stale-license.png)

Questo messaggio indica che, anche se la sottoscrizione potrebbe essere ancora valida, il token di licenza usato da Visual Studio per mantenere aggiornato l'abbonamento non è stato aggiornato. Visual Studio segnala che la licenza non è aggiornata a causa di uno dei motivi seguenti:

* Visual Studio non è stato usato o non si è connessi a Internet per un lungo periodo di tempo.
* È stata effettuata la disconnessione da Visual Studio.

Prima che il token della licenza diventi obsoleto, Visual Studio visualizza un messaggio di avviso che richiede di immettere nuovamente le credenziali.

Se non si immettono nuovamente le credenziali, il token inizia a diventare obsoleto e la finestra di dialogo **Impostazioni account** indica il numero di giorni rimanenti prima della scadenza del token. Dopo la scadenza del token, è necessario immettere nuovamente le credenziali per l'account prima di continuare a usare Visual Studio.

> [!Important]
> Se si usa Visual Studio per lunghi periodi di tempo in ambienti con accesso a Internet assente o limitato, è consigliabile usare un codice Product Key per sbloccare Visual Studio ed evitare interruzioni.

## <a name="update-an-expired-license"></a>Aggiornare una licenza scaduta

Se la sottoscrizione è scaduta e non si dispone più dei diritti di accesso a Visual Studio, è necessario rinnovare la sottoscrizione o aggiungere un altro account che disponga di una sottoscrizione. Per visualizzare altre informazioni sulla licenza in uso, passare a **File** > **Impostazioni account** e quindi verificare le informazioni sulla licenza nella parte destra della finestra di dialogo. Se si ha un altro abbonamento associato a un account diverso, aggiungere l'account all'elenco **Tutti gli account** sul lato sinistro della finestra di dialogo selezionando il collegamento **Aggiungi un account**.

## <a name="get-support"></a>Supporto

Non sempre tutto funziona correttamente. Se si verifica un problema, di seguito sono riportate alcune opzioni di supporto:

* Segnalare i problemi del prodotto utilizzando lo strumento [segnala un problema](how-to-report-a-problem-with-visual-studio.md) .
* Domande frequenti su sottoscrizioni, account e fatturazione nelle domande frequenti sul [supporto per le sottoscrizioni](https://visualstudio.microsoft.com/subscriptions/support/).

## <a name="see-also"></a>Vedere anche

* [Accedere a Visual Studio](../ide/signing-in-to-visual-studio.md)
* [Confrontare le edizioni di Visual Studio](https://visualstudio.microsoft.com/vs/compare/)
* [Altre informazioni sulle sottoscrizioni di Visual Studio](/visualstudio/subscriptions/)
