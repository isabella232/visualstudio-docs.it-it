---
title: Funzionalità supportate di Visual Studio (anteprima)
description: Informazioni sulle funzionalità dell'IDE di Visual Studio disponibili quando si lavora con gli spazi dei caratteri di GitHub.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: ebd64a314f1c4d6afd7b6e6fcc3b38148ff68225
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672969"
---
# <a name="supported-visual-studio-features-preview"></a>Funzionalità supportate di Visual Studio (anteprima)

> [!Important] 
> A partire dal 12 aprile 2021, la connessione agli spazi dei codebase di GitHub da Visual Studio 2019 non sarà più supportata e l'anteprima privata è stata conclusa. Ci stiamo concentrando sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e per le soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro di Visual Studio. Si consiglia di partecipare al [Forum della community degli sviluppatori](https://developercommunity.visualstudio.com/home) per Visual Studio per informazioni sulle future anteprime e informazioni di roadmap. 


Visual Studio offre un'esperienza di sviluppo completa quando ci si connette a un codespace. È possibile ottenere gli strumenti del ciclo interno di Visual Studio con cui si ha familiarità per modificare, eseguire il debug, testare e controllare la versione del codice sorgente, nonché le funzionalità di produttività, ad esempio modelli di progetto, esplorazione avanzata del codice e IntelliSense.

Nella [versione beta](https://github.com/features/codespaces)corrente di GitHub codespaces pubblica, alcune funzionalità di Visual Studio potrebbero non avere un supporto completo o potrebbero mancare inizialmente. Le sezioni seguenti illustrano le funzionalità che è possibile aspettarsi con Visual Studio e la versione beta di GitHub codespaces e gli elementi che è possibile visualizzare in futuro. 

Questo **non è destinato a essere un elenco esaustivo**, ma per illustrare le funzionalità generali di Visual Studio quando si è connessi a uno spazio.

> [!NOTE]
> Se è presente una funzionalità mancante durante l'uso degli spazi dei numeri con Visual Studio, è possibile segnalare aprendo un problema nella community degli [sviluppatori di Visual Studio](https://aka.ms/feedback/suggest?space=8). In questo modo è possibile classificare in ordine di priorità le funzionalità più desiderate.

> [!NOTE]
> Le funzionalità descritte di seguito si riportano per Visual Studio e non per altri due client di codespace GitHub. Visual Studio Code e l'editor nel browser.

## <a name="edit-and-navigation"></a>Modifica e navigazione

Si noti che la modifica del codice sorgente in uno spazio dei codici è leggermente diversa quando si ottengono funzionalità di linguaggio intelligente come IntelliSense, esplorazione del codice, diagnostica e suggerimenti.

* IntelliSense
* Esplorazione del codice *
* Formattazione del codice con il documento di formato
* Evidenziazione della sintassi
* Informazioni rapide *
* HTML, CSS, editor Razor *-supporto parziale.
* Editor JavaScript e TypeScript *-supporto parziale.

Non ancora disponibile:

* IntelliSense *-alcuni filtri di completamento automatico/elenco di membri non sono disponibili. Il completamento per i tipi non importati e IntelliSense nella finestra espressioni di controllo non è ancora disponibile.
* Esplorazione del codice *: la maggior parte dei comandi è supportata. Vai a base e trova nei file con specifica del percorso non sono ancora supportati.
* Informazioni rapide *-la colorazione nelle informazioni rapide non è supportata.
* HTML, CSS, editor Razor *-diagnostica, completamento IntelliSense, informazioni rapide, rientro intelligente. Attualmente nessun supporto per la colorazione semantica, i comandi di navigazione e così via.
* JavaScript e TypeScript editor *-i blocchi di script (ad esempio, il contenuto JavaScript nei file HTML e CSHTML) e l'evidenziazione semantica non sono ancora supportati. Problemi noti relativi alle funzionalità della lampadina.
* Visualizzazione destinazioni CMake
* Editor impostazioni progetto CMake
* CTRL + F7 (compila file)
* CodeLens
* Frammenti di codice
* IntelliCode

## <a name="application-types-and-configuration"></a>Tipi di applicazioni e configurazione

Sono supportati la maggior parte dei tipi di applicazione e delle configurazioni di progetto, ma è necessario modificare direttamente il codice del progetto senza l'ausilio delle finestre di progettazione visiva. Per altre indicazioni sulla configurazione, vedere [How to Customize a codespace](customize-codespaces.md).

* Modelli di progetti e di elementi
* Progetti .NET Core e ASP.NET Core
* App console C++: supporto per CMake e vcxproj
* App C++ destinate a Linux, principalmente supportate per non GUI. Possibilità di installare ed eseguire il provisioning di WSL, IntelliSense specifico per la piattaforma e compilazione.
* Modifica del file di progetto: principalmente supportata. Mancano alcune funzionalità di completamento, evidenziazione della sintassi e modifica avanzata.
* Account GitHub: è possibile usare per creare e connettere gli spazi dei nomi e accedere alle risorse disponibili per l'account su GitHub.
* INTERFACCIA della riga di comando di Azure: non condivide gli account di identità o keychain di Visual Studio connessi. L'account di accesso basato su browser non è supportato, ma è possibile eseguire l'autenticazione all'interno del terminale integrato usando: `az login --use-device-code` .

Non ancora disponibile:

* Finestre di progettazione interfaccia utente-WinForms, WPF e progettazione risorse
* Il cast dell'app per progetti WinForms e WPF è disponibile solo in un flag funzionalità
* Progetti Visual Basic e F #
* .NET Framework progetti di destinazione
* Progetti Docker Compose
* Pagina delle proprietà del progetto
* Opzioni di autenticazione nei modelli di ASP.NET Core
* App che richiedono l'installazione di un'interfaccia utente grafica: qualsiasi elemento che può essere installato con il terminale è supportato (incluso il programma di installazione di Chocolate), ma l'interfaccia utente grafica effettiva non sarà immediatamente disponibile. L'abilitazione dell'Live Share a schermo intero per accedere a GUI è una soluzione alternativa corrente. Le console di amministrazione non sono accessibili. Le app che richiedono un riavvio per l'installazione non sono supportate.
* Identità gestite per le risorse di Azure in Visual Studio
* Risorse Intranet (rete privata)-attualmente gli spazi dei nomi non saranno in grado di connettersi a qualsiasi risorsa che richiede una VPN.
* Estensioni: nessuna estensione è supportata quando si usano gli spazi dei nomi con Visual Studio.

## <a name="debugging"></a>Debug

Il debug del ciclo interno essenziale è supportato, inclusa l'impostazione di punti di interruzione, l'esecuzione di un'istruzione di base nel codice, il controllo delle variabili e le finestre locali, auto ed espressioni di controllo. Alcune finestre, personalizzazioni e visualizzatori aggiuntivi non sono supportati.

* Interruzione
* Istruzione di base
* Variabili locali, auto, espressioni di controllo *-supporto parziale.
* I suggerimenti per i dati server di simboli, server di origine e importazione/esportazione sono parzialmente supportati.

Non ancora disponibile:

* Punti di interruzione *: le etichette dei punti di interruzione, i punti di interruzione dei dati e il punto di interruzione impostato nella finestra Disassembly sono in corso. L'importazione e l'esportazione di punti di interruzione sono parzialmente supportati.
* Variabili locali, auto, espressioni di controllo *: alcune funzionalità, ad esempio il completamento delle istruzioni nella casella di ricerca e l'esplorazione della casella di ricerca.
* Personalizzazioni dell'interfaccia utente: le proprietà aggiungibili e Nascondi parametri modello non sono supportate.
* Visualizzatori-C++ natvis parzialmente supportati. La finestra Disassembly, la diagnostica visiva XAML, i visualizzatori .NET personalizzati e i visualizzatori del set di dati non sono supportati.
* Windows debugger aggiuntivo-processi Windows parzialmente supportati. Finestra stack in parallelo: la visualizzazione attività, l'hub diagnostica e la finestra di dialogo Trova origine/simbolo non sono supportate.
* Alcuni flussi di lavoro del debugger, ovvero Connetti a processo, debugger JIT (just-in-Time), debug del dump, profilatura e IntelliTrace, non sono supportati. L'esecuzione del Just My Code C++ è parzialmente supportata.
* Modifica e continuazione: non supportato sia per il codice gestito che per quello nativo.
* Funzionalità di threading: i thread di blocco/sblocco, Rinomina thread e Mostra thread nell'origine non sono supportati.
* Funzionalità per l'esecuzione di istruzioni aggiuntive: l'esecuzione automatica delle proprietà e degli operatori (.NET Core) e l'esecuzione di istruzioni specifiche non sono supportate. 

## <a name="features"></a>Funzionalità

Quando si usa Visual Studio connesso a uno spazio dei servizi, si ottengono le stesse funzionalità di accessibilità di quando si lavora localmente.

* Controllo del codice sorgente: supporto Git completo tramite la nuova [esperienza git integrata](../git-with-visual-studio.md). Per poter clonare i moduli secondari git in un codespace, potrebbe essere necessario eseguire `git submodule update` dal terminale.
* Accessibilità: esiste un problema noto con la tecnologia di accesso facilitato che non è in grado di accedere alla appcasting di un'app sottoposta a debug. Oltre a questa limitazione, non riteniamo che esistano altri problemi di compatibilità che non esistono già nell'esperienza locale di Visual Studio. Segnalare eventuali bug segnalando un problema nella [community degli sviluppatori](https://aka.ms/feedback/report?space=8).
* Pubblicazione: è supportata la pubblicazione in Azure tramite azioni di GitHub.
* Servizi connessi: le informazioni dettagliate su app, l'insieme di credenziali delle applicazioni, l'archivio, SQL, Redis, Cosmos, openAPI e gRPC sono parzialmente supportate.
* Esplora test *-principalmente supportata.

Non ancora disponibile:

* Esplora test *: alcune funzionalità, ad esempio la selezione dell'architettura predefinita, eseguono test in parallelo, playlist e così via. Problemi noti relativi al debug di un unit test, alle impostazioni di esecuzione e ad altre funzionalità aziendali. Gli unit test di profilatura non sono supportati.
* Interfaccia utente di gestione pacchetti NuGet: la riga di comando NuGet è supportata.
* Funzionalità di test aziendali: Live Unit Testing, Microsoft Fakes, code coverage e IntelliTest non sono supportati.
* Scenari di pubblicazione avanzati: pubblicazione selettiva, pubblicazione FTP, modifiche in anteprima, barra degli strumenti di pubblicazione rapida e così via.

## <a name="see-also"></a>Vedi anche

* [Che cosa sono gli spazi di dati di GitHub?](codespaces-overview.md)
* [Come usare Visual Studio con un codespace](use-visual-studio-with-codespaces.md)
* [Come personalizzare uno spazio di codespace](customize-codespaces.md)
