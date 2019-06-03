---
title: Aggiornare Visual Studio secondo una baseline di manutenzione
titleSuffix: ''
description: Informazioni su come aggiornare Visual Studio secondo una baseline di manutenzione.
ms.date: 05/22/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: doughall
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8928feffed77f8bfbb3787bd9a20737b9c7b3f9e
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66213782"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Aggiornare Visual Studio secondo una baseline di manutenzione

Per Visual Studio 2019 verranno pubblicati aggiornamenti frequenti durante il [ciclo di vita del prodotto](/visualstudio/productinfo/release-rhythm.md#release-channel-updates). Tali aggiornamenti includeranno sia aggiornamenti di versione secondari (ad esempio: dalla versione 16.0 alla versione 16,1) che possono includere nuove funzionalità e nuovi componenti, sia aggiornamenti di manutenzione (ad esempio: dalla versione 16.0.4 alla versione 16.0.5) che contengono solo correzioni mirate per problemi critici. 

Gli amministratori dell'organizzazione possono scegliere di mantenere i client su una baseline di manutenzione, supportata con gli aggiornamenti di manutenzione per un anno dopo il rilascio della baseline di manutenzione successiva. Ciò consente una maggiore flessibilità per gli sviluppatori e gli amministratori per l'adozione di nuove funzionalità, correzioni di bug o componenti inclusi nei nuovi aggiornamenti secondari. La prima baseline di manutenzione è 16.0.x. Per altre informazioni, vedere [Opzioni di supporto per i clienti Enterprise e Professional](/visualstudio/releases/2019/servicing.md#support-options-for-enterprise-and-professional-customers).

## <a name="how-to-get-onto-a-servicing-baseline"></a>Come adottare una baseline di manutenzione

Per iniziare a usare una baseline di manutenzione, scaricare un programma di bootstrap del programma di installazione di Visual Studio con versione fissa da [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Questi programmi di bootstrap includono collegamenti alle configurazioni, ai carichi di lavoro e ai componenti del progetto per la versione specifica. 

> [!NOTE]
> Prestare attenzione a distinguere tra il programma di bootstrap con versione fissa e i programmi di bootstrap normali. I programmi di bootstrap normali sono configurati per usare la versione più recente disponibile di Visual Studio e hanno un numero nel nome di file (ad esempio: vs_enterprise__123456789 123456789.exe) quando vengono scaricati da my.visualstudio.com.

Durante l'installazione, gli amministratori dell'organizzazione devono configurare i client per impedirne l'aggiornamento alla versione più recente. Questa operazione può essere eseguita [modificando l'impostazione channelUri nel file di configurazione di risposta](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) per usare un manifesto del canale nel layout o nella cartella locale [modificando il valore di channelUri tramite l'esecuzione della riga di comando](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) per un file inesistente o tramite l'[impostazione di criteri nel sistema client per disabilitare gli aggiornamenti](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating) per impedire l'aggiornamento in autonomia dei client. 

### <a name="install-a-servicing-baseline-on-a-network"></a>Installare una baseline di manutenzione in una rete

Gli amministratori che usano un'installazione con layout di rete possono modificare il valore di channelUri in `response.json` nel layout per usare il file channelmanifest.json disponibile nella stessa cartella. Per istruzioni dettagliate, vedere [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md). La modifica di channelUri consente ai client di cercare gli aggiornamenti nella posizione del layout. 

### <a name="install-a-servicing-baseline-via-the-internet"></a>Installare una baseline di manutenzione tramite Internet

Nel caso di un'installazione basata su Internet, aggiungere `--channelUri` con un manifesto di canale inesistente alla riga di comando usata per avviare il programma di installazione. In questo modo si impedisce a Visual Studio di usare la versione più recente disponibile per un aggiornamento. Ecco un esempio:

  ```cmd
   vs_enterprise.exe --channelUri c:\doesnotexist.chman 
  ```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Usare le impostazioni dei criteri per impedire ai client di installare gli aggiornamenti

Un'altra opzione per controllare gli aggiornamenti in un client consiste nel [disattivare le notifiche di aggiornamento](controlling-updates-to-visual-studio-deployments.md). Usare questa opzione se il valore channelUri non è stato modificato durante l'installazione. In questo modo i client non potranno ricevere i collegamenti alla versione più recente disponibile. Un programma di bootstrap con versione fissa è comunque necessario per eseguire l'aggiornamento a una versione specifica nel client.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Come mantenere una baseline di manutenzione

Quando diventa disponibile un aggiornamento per una baseline di manutenzione, vengono resi disponibili file del programma di bootstrap per l'aggiornamento di manutenzione da [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Questi file possono essere usati in diversi scenari.

Gli amministratori che eseguono la distribuzione tramite un'installazione con layout di rete vorranno aggiornare la [posizione del layout](update-a-network-installation-of-visual-studio.md). I client installati da tale posizione riceveranno le notifiche per gli aggiornamenti. Se l'aggiornamento deve essere distribuito ai client, seguire [queste istruzioni](update-a-network-installation-of-visual-studio.md#how-to-deploy-an-update-to-client-machines). Quando si modifica il file 'response.json' per un aggiornamento, non aggiungere altri carichi di lavoro, componenti o lingue. La gestione di queste impostazioni deve essere eseguita come una distribuzione di 'modifica' dopo aver aggiornato il prodotto. 

Nel caso di un'installazione basata su Internet, eseguire il nuovo programma di bootstrap con versione fissa con il parametro `--channelUri` che punta a un manifesto del canale inesistente nel client. Se l'aggiornamento viene distribuito in modalità non interattiva o passiva, usare due comandi separati:

1. Aggiornare prima il programma di installazione di Visual Studio: <br>```vs_enterprise.exe --quiet --update```
2. Aggiornare quindi l'applicazione Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio](install-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Strumenti per il rilevamento e la gestione di istanze di Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Come definire impostazioni in un file di risposta](automated-installation-with-response-file.md)
* [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Ciclo di vita del prodotto e manutenzione di Visual Studio](/visualstudio/releases/2019/servicing/)
