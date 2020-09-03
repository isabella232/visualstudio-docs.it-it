---
title: Panoramica dell'estendibilità delle cartelle aperte di Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: overview
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: d213a7add358c46f7088f504d8c54352cda44a1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905972"
---
# <a name="open-folder-extensibility"></a>Estendibilità Apri cartella

La funzionalità [Apri cartella](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) consente agli utenti di aprire qualsiasi codebase in Visual Studio senza la necessità di file di progetto o di soluzione. Apri cartella fornisce le funzionalità che gli utenti si aspettano da Visual Studio, ad esempio:

* Esplora soluzioni l'integrazione e la ricerca
* Colorazione dell'editor
* Vai a navigazione
* Ricerca nei file

Quando viene usato con carichi di lavoro, ad esempio per lo sviluppo di .NET e C++, gli utenti ottengono anche:

* IntelliSense avanzato
* Funzionalità specifiche della lingua

Con Apri cartella gli autori delle estensioni possono creare funzionalità avanzate per qualsiasi linguaggio. Sono disponibili API per supportare la compilazione, il debug e la ricerca di simboli per qualsiasi file nella codebase di un utente. Gli Extender correnti possono aggiornare le funzionalità di Visual Studio esistenti per comprendere il codice senza il supporto di progetti o di una soluzione.

## <a name="an-api-without-project-systems"></a>API senza sistemi di progetto

In passato, Visual Studio comprendeva solo i file in una soluzione e i relativi progetti che usano sistemi di progetto. Un sistema di progetto è responsabile della funzionalità e delle interazioni utente di un progetto caricato. Comprende i file contenuti nel progetto, la rappresentazione visiva del contenuto del progetto, le dipendenze da altri progetti e la modifica del file di progetto sottostante. Si tratta di gerarchie e funzionalità che altri componenti funzionano per conto dell'utente. Non tutte le codebase sono rappresentate correttamente in una struttura di progetto e di soluzione. I linguaggi di scripting e il codice open source scritto in C++ per Linux sono ottimi esempi. Con Apri cartella, Visual Studio offre agli utenti un nuovo modo per interagire con il codice sorgente.

Le API Apri cartella si trovano nello `Microsoft.VisualStudio.Workspace.*` spazio dei nomi e sono disponibili per le estensioni per produrre e utilizzare i dati o le azioni per i file all'interno di una cartella aperta. Le estensioni possono usare queste API per fornire funzionalità per molte aree, tra cui:

- [Aree di lavoro](workspaces.md) : il punto di partenza per l'estendibilità di Apri cartella è l'area di lavoro e le relative API.
- [Contesti di file e azioni](workspace-file-contexts.md) : informazioni specifiche sul codice del file fornite tramite i contesti di file.
- [Indicizzazione](workspace-indexing.md) : raccolta e salvataggio permanente dei dati sulle aree di lavoro Apri cartella.
- [Servizi di linguaggio](workspace-language-services.md) -integrare i servizi di linguaggio in aree di lavoro Apri cartella.
- [Compilazione](workspace-build.md) : supporto della compilazione per le aree di lavoro Apri cartella.

Le funzionalità che usano i seguenti tipi dovranno adottare nuove API per supportare la cartella Open:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Commenti, commenti, problemi

Apri cartella e le `Microsoft.VisualStudio.Workspace.*` API sono in fase di sviluppo attivo. Se viene visualizzato un comportamento imprevisto, vedere i problemi noti per il rilascio di interesse. La [community degli sviluppatori](https://developercommunity.visualstudio.com) è la posizione consigliata per votare e creare eventuali problemi. Per ogni feedback, si consiglia vivamente una descrizione dettagliata del problema. Includere la versione di Visual Studio che si sta sviluppando per, le API in uso (sia ciò che è stato implementato che quello con cui si sta interagendo), il risultato previsto e il risultato effettivo. Se possibile, includere un dump del processo di devenv.exe. Usare il rilevamento dei problemi di GitHub per fornire commenti e suggerimenti su questa e documentazione correlata.

## <a name="next-steps"></a>Passaggi successivi

* [Aree di lavoro](workspaces.md) : informazioni sull'API dell'area di lavoro Apri cartella.