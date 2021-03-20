---
title: Domande frequenti
description: Domande frequenti per lo strumento devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 603d09de5a37ea7ea4f0ff10c377c56eb9a3d63e
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672193"
---
# <a name="frequently-asked-questions-for-devinit"></a>Domande frequenti su devinit

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione agli spazi dei codebase di GitHub da Visual Studio 2019 non sarà più supportata e l'anteprima privata è stata conclusa. Ci stiamo concentrando sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e per le soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro di Visual Studio. Come parte di questo `devinit` e gli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio per informazioni sulle future anteprime e informazioni di roadmap.

## <a name="is-devinit-just-for-github-codespaces"></a>La devinilica è sufficiente per gli spazi dei Codedi GitHub?

Per il momento, devinit è disponibile solo come parte della beta privata di GitHub codespaces. Tuttavia, è prevista la presenza di un programma di deproduzione in una versione imminente di Visual Studio 2019.

## <a name="is-it-windows-only"></a>Si tratta solo di Windows?
Sì, la devinit si concentra sulla creazione di ambienti di sviluppo che funzionano per gli sviluppatori che usano Visual Studio, il che significa Windows. Stiamo considerando altre piattaforme, ma molte di esse dispongono già di soluzioni eccezionali, per cui volevamo iniziare con Visual Studio e Windows.

## <a name="theres-no-tool-for-the-dependency-i-need"></a>Non è disponibile alcuno strumento per la dipendenza necessaria.

Siamo spiacenti. Se si fa parte della versione beta privata di GitHub codespaces, è possibile tornare a Microsoft tramite il canale di feedback per la versione beta privata. Se non si fa parte della versione beta privata, i commenti e i suggerimenti sugli elementi necessari verranno comunque segnalati ed è possibile inviare un problema alla [documentazione di Visual Studio](https://github.com/MicrosoftDocs/visualstudio-docs/) con l'etichetta `devinit` per richiedere supporto per lo strumento necessario.

## <a name="something-went-wrong-how-do-i-debug"></a>Si è verificato un errore, come si esegue il debug?

Se la deviniling ha esito negativo, il primo elemento da provare è il `--verbose / -v` flag per ottenere altre informazioni. È probabile che si verifichi un problema con lo strumento sottostante che viene chiamato da devinit. Le informazioni dettagliate sul log devono includere un indizio sulla posizione in cui eseguire la ricerca.

## <a name="why-not-just-a-script"></a>Perché non è solo uno script?

La configurazione di ambienti tramite uno script è una tecnica temporale obsoleta che può funzionare perfettamente. Se funziona, usare! devinit è un'altra opzione per gli sviluppatori quando gli script non sono la scelta migliore.

## <a name="why-not-a-container"></a>Perché non si tratta di un contenitore?

I contenitori e Docker sono strumenti ottimali per distribuire un ambiente tramite codice. Esistono alcuni motivi per cui i contenitori potrebbero non essere la soluzione ideale:

1. Se si desidera utilizzare un ambiente di sviluppo basato su desktop di Windows.
1. Se si dispone già di un sistema operativo e si vuole semplicemente apportare modifiche piuttosto che distribuire un nuovo ambiente.

Per questi motivi, è necessario personalizzare l'ambiente Windows attualmente disponibile.

## <a name="what-about-other-vm-creation-tools-for-example-terraform-packer-chef-vagrant-etc"></a>Cosa accade con altri strumenti di creazione di macchine virtuali, ad esempio bonifica, Packer, chef, vagabondo e così via.

Sono disponibili molti strumenti eccezionali per la creazione di immagini Windows ed è consigliabile usarli. Tuttavia, non è stato possibile trovare un oggetto che soddisfi tutti gli scenari di cui si è preso in considerazione. Per consentire agli sviluppatori di personalizzare il proprio ambiente in base a quanto è necessario per un particolare repository e di avere una grande integrazione con Visual Studio, invece di essere uno strumento per la creazione di immagini di macchina virtuale, si vuole che sia uno strumento per gli sviluppatori.

## <a name="what-about-winget"></a>Per quanto riguarda il wingt?

devinit non è un gestore di pacchetti come wingt e non lo si vuole. Si vuole essere in grado di usare Winger con devinit e stiamo lavorando a uno strumento.

## <a name="how-are-restarts-handled"></a>Come vengono gestiti i riavvii?

Se è necessario riavviare il sistema operativo, viene restituito un messaggio di errore nella console di per qualsiasi operazione di installazione eseguita da devinit. Sarà quindi necessario riavviare il sistema operativo in un momento appropriato. Dopo il riavvio, potrebbe essere necessario eseguire di nuovo il devinit se tutte le dipendenze non sono state installate.

## <a name="working-with-others"></a>Uso di altri utenti

per la distribuzione e la configurazione delle dipendenze dell'app, la delineatura è sufficiente per consentire l'uso dell'ampio ecosistema. Mentre la devinit presenta un'opinione sui vantaggi offerti da un file JSON dichiarativo, è prevalentemente per l'esecuzione di altri strumenti.

Oggi, la devinit è appena iniziata e l' [elenco di strumenti](devinit-tool-list.md) è solo un inizio.
