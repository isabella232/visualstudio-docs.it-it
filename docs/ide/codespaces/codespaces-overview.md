---
title: Panoramica di GitHub Codespaces (anteprima)
description: Altre informazioni su GitHub Codespaces con Visual Studio e su come può aiutare a estendere l'ambiente di sviluppo al cloud.
ms.topic: overview
ms.date: 09/04/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: ab50c3c2df2cfad6d489d800f47624503844dc9d
ms.sourcegitcommit: a667ce8394a800906d633737f4fcbc77f0fcba7b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2021
ms.locfileid: "108298743"
---
# <a name="what-is-github-codespaces-preview"></a>Che cos'è GitHub Codespaces? (Anteprima)

> [!Important]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Si consiglia di partecipare al forum della [community](https://developercommunity.visualstudio.com/home) per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Benvenuti in Codespaces. Siamo lieti che tu sia qui.

GitHub Codespaces offre un ambiente di sviluppo basato sul cloud per qualsiasi attività, che si tratta di un progetto a lungo termine o di un'attività a breve termine, ad esempio la revisione di una richiesta pull.

GitHub Codespaces offre inoltre molti dei vantaggi di DevOps, ad esempio la ripetibilità e l'affidabilità, che in genere sono stati riservati ai carichi di lavoro di produzione in &mdash; &mdash; un ambiente di sviluppo. È anche possibile personalizzare GitHub Codespaces in modo che siano presenti anche gli strumenti, i processi e le configurazioni che si preferisce e su cui si basano.

Questo documento illustra i concetti chiave e introduce le funzionalità di Codespaces. Se si sta cercando di iniziare, vedere Usare Visual Studio [con uno spazio di codice](use-visual-studio-with-codespaces.md).

## <a name="concepts-and-features"></a>Concetti e funzionalità

Le funzionalità di GitHub Codespaces si basano su alcuni concetti fondamentali. Questa sezione illustra questi concetti e offre una breve panoramica delle funzionalità.

### <a name="remote-development"></a>Sviluppo remoto

Molti sviluppatori provano attualmente a creare codice in configurazioni remote o macchine virtuali configurate con stack di runtime e sviluppo specifici. Lo fanno perché è troppo difficile, troppo dannoso e in alcuni casi quasi impossibile configurare questi ambienti di sviluppo in locale. Inoltre, gli utenti vogliono provare nuove tecnologie o nuovi framework senza il timore di "incasinare" le macchine necessarie per il lavoro quotidiano.

Anche se l'uso di ambienti remoti e strumenti con supporto remoto supporta gli sviluppatori, spesso la gestione dei computer è sovraccarica. La configurazione dell'ambiente spesso complica l'onboarding e il cambio di contesto. GitHub Codespaces elimina le barriere per il rapido onboarding e il cambio di contesto, consentendo la creazione simultanea di molti ambienti.

GitHub Codespaces offre soluzioni gestite che consentono di concentrarsi sulla produttività rispetto alla configurazione. GitHub Codespaces estende concettualmente e tecnicamente Visual Studio 2019 per lo sviluppo remoto.

### <a name="about-codespaces"></a>Informazioni sugli spazi di codice

Uno spazio di codice è la metà "back-end" di GitHub Codespaces. È qui che si verificano tutte le risorse di calcolo associate allo sviluppo software: compilazione, debug, ripristino e così via. La creazione di uno spazio di codice prepara tutto il necessario per completare un'attività, esaminare una richiesta pull o avviare un nuovo progetto. Gli spazi di codice configurano il runtime, il compilatore, il debugger, l'editor, le configurazioni dotfile personalizzate e il codice sorgente necessario per lavorare a un progetto.

Gli spazi di codice ospitati nel cloud offrono i vantaggi seguenti:

- Sono veloci da creare ed eliminabili. Creare tutti gli elementi necessari (fino ai limiti dell'account) e quindi eliminarli al termine dell'operazione.
- Vengono gestiti, riducendo così la manutenzione complessiva per l'utente.
- Hanno prezzi prevedibili e si paga solo per ciò che si usa. È anche presente l'opzione autosuspend incorporata per eliminare i costi invasi.
- Salvano le risorse di calcolo. Quando si sposta il carico di lavoro di sviluppo nel cloud, vengono liberate le risorse limitate nel computer personale.

## <a name="custom-configuration"></a>Configurazione personalizzata

GitHub Codespaces è progettato per supportare la più ampia gamma di progetti o attività. È possibile iniziare con funzionalità di configurazione intelligente che forniscono impostazioni predefinite comuni o ottimizzare uno spazio di codice con [la configurazione personalizzata](customize-codespaces.md).

La configurazione flessibile consente agli sviluppatori di eseguire rapidamente l'onboard di progetti con requisiti e configurazione univoci difficili da applicare in un computer locale. Inoltre, gli spazi di codice riproducibili eliminano i problemi di "funziona nel computer".

## <a name="personal-configuration"></a>Configurazione personale

È noto che mantenere le preferenze personali è fondamentale per fare in modo che lo sviluppo in uno spazio di codice ospitato nel cloud sia familiare e naturale. GitHub Codespaces livelli personalizzazioni individualizzate in una configurazione dello spazio di codice. Le preferenze e la configurazione personali per editor e terminali sono supportate da GitHub Codespaces.

È possibile creare uno spazio di codice con una raccolta specifica dell'utente di [file dotfile](https://docs.github.com/github/developing-online-with-codespaces/personalizing-codespaces-for-your-account) personalizzati (ad `.bashrc` esempio, , e così via) e `.gitconfig` GitHub Codespaces sincronizza automaticamente l'identità, i temi e le impostazioni di Git in modo che ogni spazio di codice creato appai e si senta come si desidera, indipendentemente dalle funzionalità dell'ambiente specifico del progetto.

## <a name="see-also"></a>Vedi anche

* [Come usare Visual Studio con uno spazio di codice](use-visual-studio-with-codespaces.md)
* [Come personalizzare uno spazio di codice](customize-codespaces.md)
* [Funzionalità di Visual Studio supportate](supported-features-codespaces.md)
