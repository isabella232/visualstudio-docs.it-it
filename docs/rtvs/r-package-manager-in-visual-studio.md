---
title: Gestione pacchetti per R
description: Come usare Gestione pacchetti R in Visual Studio per installare e gestire pacchetti R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: d35bfd45e862912ff78ae600eed01ce8dc002493
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931585"
---
# <a name="package-manager"></a>Gestione pacchetti

Gestione pacchetti di R Tools per Visual Studio (RTVS) è un'interfaccia utente per la gestione dei pacchetti R. Per aprirla, selezionare **R Tools** > **Finestre** > **Pacchetti** o premere **CTRL**+**7**.

Gestione pacchetti contiene tre schede. Ogni scheda visualizza a sinistra un elenco di pacchetti pertinenti e a destra i dettagli specifici del pacchetto selezionato, ad esempio la versione, la descrizione, la licenza, il percorso di installazione, nonché collegamenti ad altre informazioni pertinenti. La casella di ricerca in alto a destra consente di filtrare l'elenco.

> [!Tip]
> Il termine nella casella di ricerca rimane attivo quando si passa da una scheda all'altra.

- La scheda **Disponibile** consente di sfogliare i pacchetti da installare. Se un pacchetto è già installato, il pulsante **Installa** a destra diventa **Disinstalla**.

    ![Scheda dei pacchetti disponibili in Gestione pacchetti di R Tools per Visual Studio](media/package-manager-available.png)

- La scheda **Installato** visualizza tutti i pacchetti installati e caricati. Un punto verde accanto a un pacchetto indica che questo è caricato nella sessione di R. Per disinstallare il pacchetto è possibile usare l'icona X di colore rosso nell'elenco a sinistra o il pulsante **Disinstalla** a destra. Se è disponibile una versione più recente di un pacchetto installato, la freccia di colore blu a destra del pacchetto esegue l'aggiornamento.

    ![Scheda dei pacchetti installati in Gestione pacchetti di R Tools per Visual Studio](media/package-manager-installed.png)

- La scheda **Caricato** visualizza solo i pacchetti caricati nella sessione di R, che presentano tutti un punto verde. In questa scheda è anche possibile disinstallare e aggiornare i pacchetti.

    ![Scheda dei pacchetti caricati in Gestione pacchetti di R Tools per Visual Studio](media/package-manager-loaded.png)

## <a name="package-locations"></a>Percorsi dei pacchetti

I pacchetti vengono installati nei percorsi seguenti:

- I pacchetti di base inclusi in RTVS vengono installati in *C:\Programmi\Microsoft\R Client\R_SERVER\library*
- I pacchetti aggiuntivi vengono installati in *%userprofile%\Documents\R\win-library\3.3*
