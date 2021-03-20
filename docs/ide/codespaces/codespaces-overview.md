---
title: Panoramica degli spazi dei codespace di GitHub (anteprima)
description: Scopri di più sugli spazi dei valori di GitHub con Visual Studio e su come può aiutarti a estendere l'ambiente di sviluppo al cloud.
ms.topic: overview
ms.date: 09/04/2020
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: a4bf2cf948b6df65ee0407c1cc736e8056820a54
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672787"
---
# <a name="what-is-github-codespaces-preview"></a>Che cosa sono gli spazi di dati di GitHub? (Anteprima)

> [!Important] 
> A partire dal 12 aprile 2021, la connessione agli spazi dei codebase di GitHub da Visual Studio 2019 non sarà più supportata e l'anteprima privata è stata conclusa. Ci stiamo concentrando sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e per le soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro di Visual Studio. Si consiglia di partecipare al [Forum della community degli sviluppatori](https://developercommunity.visualstudio.com/home) per Visual Studio per informazioni sulle future anteprime e informazioni di roadmap. 

Benvenuti in codespaces. Siamo lieti di essere qui.

Gli spazi dei nomi in GitHub offrono un ambiente di sviluppo basato sul cloud per qualsiasi attività, indipendentemente dal fatto che si tratti di un progetto a lungo termine o da un'attività a breve termine come la revisione di una richiesta pull.

Inoltre, i codespace di GitHub offrono molti dei vantaggi di DevOps, ad esempio la ripetibilità e l'affidabilità, &mdash; che in genere sono stati riservati ai carichi &mdash; di lavoro di produzione in un ambiente di sviluppo. È anche possibile personalizzare gli spazi dei codebase di GitHub in modo che gli strumenti, i processi e le configurazioni che si preferisce e si affidino siano disponibili.

In questo documento vengono illustrati i concetti chiave e vengono introdotte le funzionalità di codespaces. Se si vuole iniziare, vedere [usare Visual Studio con una codespace](use-visual-studio-with-codespaces.md).

## <a name="concepts-and-features"></a>Concetti e funzionalità

Le funzionalità degli spazi dei termini di GitHub sono basate su alcuni concetti fondamentali. Questa sezione illustra i concetti e fornisce una breve panoramica delle funzionalità.

### <a name="remote-development"></a>Sviluppo remoto

Molti sviluppatori tentano oggi di scrivere codice in configurazioni remote o in macchine virtuali configurate con stack di sviluppo e di runtime specifici. Lo fanno perché è troppo complesso, troppo fastidioso e in alcuni casi, quasi impossibile configurare questi ambienti di sviluppo in locale. Inoltre, gli utenti vogliono provare le nuove tecnologie o i nuovi Framework senza la paura di "rovinare" i computer necessari per il lavoro quotidiano.

Quando si usano ambienti remoti e strumenti in grado di supportare gli sviluppatori, è spesso disponibile un sovraccarico di gestione del computer. La configurazione dell'ambiente spesso complica l'onboarding e il cambio del contesto. Gli spazi dei nomi di GitHub rimuovono le barriere al caricamento e al cambio di contesto rapidi, consentendo l'esistenza di molti ambienti contemporaneamente. 

Gli spazi dei codebase di GitHub forniscono soluzioni gestite che consentono di concentrarsi sulla produttività rispetto all'installazione. Gli spazi dei comandi di GitHub concettualmente e tecnicamente estendono Visual Studio 2019 per lo sviluppo remoto. 

### <a name="about-codespaces"></a>Informazioni sui codespace

Un codespace è la metà "back-end" degli spazi dei Codedi GitHub. Si tratta del punto in cui si verifica tutto il calcolo associato allo sviluppo software: compilazione, debug, ripristino e così via. La creazione di un codespace prepara tutti gli elementi necessari per completare un'attività, esaminare una richiesta pull o avviare un nuovo progetto. Codespaces consente di configurare il runtime, il compilatore, il debugger, l'editor, le configurazioni dotfile personalizzate e il codice sorgente necessari per lavorare a un progetto.

Gli spazi dei nomi ospitati nel cloud offrono i vantaggi seguenti:

- Sono veloci da creare e gettare. Creare il numero di richieste (fino a limiti di account) e quindi eliminarle al termine dell'operazione.
- Sono gestiti, riducendo così la manutenzione complessiva.
- Hanno prezzi prevedibili e paghi solo per ciò che usi. Per eliminare i costi di fuga, è disponibile la funzionalità di sospensione autonoma incorporata.
- Salvano le risorse di calcolo. Quando si sposta il carico di lavoro di sviluppo nel cloud, vengono liberate le risorse limitate nel computer personale.

## <a name="custom-configuration"></a>Configurazione personalizzata

Gli spazi dei caratteri di GitHub sono compilati per supportare la più ampia gamma di progetti o attività. È possibile iniziare con le funzionalità di configurazione intelligente che forniscono impostazioni predefinite comuni o ottimizzare uno spazio dei nomi con [configurazione personalizzata](customize-codespaces.md).

La configurazione flessibile consente agli sviluppatori di eseguire rapidamente l'onboarding nei progetti con configurazione e requisiti univoci difficili da applicare in un computer locale. Inoltre, gli spazi dei coderiproducibili eliminano i problemi "funziona nel computer".

## <a name="personal-configuration"></a>Configurazione personale

Sappiamo che la conservazione delle preferenze personali è fondamentale per fare in modo che lo sviluppo in un codespace ospitato nel cloud sia familiare e naturale. Gli spazi dei codebase di GitHub comportano personalizzazioni personalizzate sulla base di una configurazione codespace. Le preferenze e la configurazione personali per gli editor e i terminali sono supportati da spazi dei dati di GitHub.

È possibile creare uno spazio dei nomi con una raccolta specifica dell'utente di [Dotfiles personalizzati](https://docs.github.com/github/developing-online-with-codespaces/personalizing-codespaces-for-your-account) (ad esempio,, e `.bashrc` `.gitconfig` così via) e gli spazi dei nomi di GitHub sincronizzano automaticamente l'identità, i temi e le impostazioni di Git, in modo che ogni spazio dei nomi creato appaia e si senta nel modo desiderato, indipendentemente dalle funzionalità dell'ambiente specifiche del progetto.

## <a name="see-also"></a>Vedi anche

* [Come usare Visual Studio con un codespace](use-visual-studio-with-codespaces.md)
* [Come personalizzare uno spazio di codespace](customize-codespaces.md)
* [Funzionalità di Visual Studio supportate](supported-features-codespaces.md)
