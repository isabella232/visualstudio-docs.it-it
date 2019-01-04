---
title: Panoramica di estendibilità di Visual Studio Apri cartella | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2bb74703f639848d643f536edf620e30b1836310
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986011"
---
# <a name="open-folder-extensibility"></a>Estendibilità di Apri cartella

Il [Apri cartella](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) funzionalità consente agli utenti di aprire qualsiasi codebase in Visual Studio senza la necessità di file di soluzione o progetto. Apri cartella offre che le funzionalità si aspettano da Visual Studio, ad esempio:

* Ricerca e integrazione di Esplora soluzioni
* Colorazione di editor
* Vai a spostamento
* Ricerca in ricerca di file

Se usato con i carichi di lavoro ad esempio per lo sviluppo di .NET e C++, ottengono anche gli utenti:

* Intellisense avanzato
* Funzionalità specifiche della lingua

Con Apri cartella, gli autori delle estensioni possono creare numerose funzionalità per qualsiasi linguaggio. Sono disponibili le API per il supporto di compilazione, debug e ricerca dei simboli per codebase di un utente di tutti i file del. Dispositivi Extender corrente è possibile aggiornare le funzionalità esistenti di Visual Studio per comprendere il codice senza il supporto di progetti o di una soluzione.

## <a name="an-api-without-project-systems"></a>Un'API senza i sistemi di progetto

In passato, Visual Studio compreso solo i file in una soluzione e i relativi progetti usando i sistemi di progetto. Un sistema di progetto è responsabile per le interazioni di funzionalità e l'utente di un progetto caricato. Riconosce i file di progetto contiene la rappresentazione visiva del contenuto del progetto, le dipendenze da altri progetti, e file di progetto di modifica dell'oggetto sottostante. È tramite le gerarchie e le funzionalità che gli altri componenti eseguono operazioni per conto dell'utente. Non tutte le basi di codice sono anche rappresentati in una struttura di progetto e soluzione. Linguaggi di scripting e il codice open source scritto in C++ per Linux sono ottimi esempi. Con Apri cartella, Visual Studio offre agli utenti un nuovo modo di interagire con il codice sorgente.

Le API di cartella aperta sono sotto il `Microsoft.VisualStudio.Workspace.*` dello spazio dei nomi e sono disponibili per i dispositivi Extender produrre e usare i dati o le azioni per i file all'interno di Apri cartella. Le estensioni possono usare queste API per fornire funzionalità per molte aree, tra cui:

- [Le aree di lavoro](workspaces.md) - l'avvio di estendibilità di punto di Apri cartella è l'area di lavoro e le relative API.
- [File contesti e le azioni](workspace-file-contexts.md) -intelligence codice specifico fornito tramite i contesti di file del File.
- [L'indicizzazione](workspace-indexing.md) : raccogliere e rendere persistenti i dati sulle aree di lavoro di Apri cartella.
- [Servizi di linguaggio](workspace-language-services.md) -integrare servizi di linguaggio nelle aree di lavoro di Apri cartella.
- [Compilare](workspace-build.md) -crea supporto per le aree di lavoro di Apri cartella.

Le funzionalità che usano i tipi seguenti saranno necessario adottare nuove API per il supporto di Apri cartella:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Commenti e suggerimenti, commenti, i problemi

Apri cartella e il `Microsoft.VisualStudio.Workspace.*` API sono in fase di sviluppo. Se viene visualizzato un comportamento imprevisto, quindi verificare i problemi noti per la versione di interesse. [Community degli sviluppatori](https://developercommunity.visualstudio.com) è la posizione consigliata per votare e creare problemi. Per ogni commenti e suggerimenti, è consigliabile una descrizione dettagliata del problema. Includere la versione di Visual Studio per che si sta sviluppando le API in uso (che cosa è stato implementato e ciò che si interagisce con), il risultato previsto e il risultato effettivo. Se possibile, includere un dump del processo devenv.exe. Usare monitoraggio di commenti e suggerimenti su questo dei problemi di GitHub e documentazione correlata.

## <a name="next-steps"></a>Passaggi successivi

* [Le aree di lavoro](workspaces.md) -informazioni su area di lavoro di Apri cartella API.