---
title: 'Documenti di Visual Studio: novità di agosto 2020 '
titleSuffix: ''
description: Novità della documentazione di Visual Studio per il 2020 agosto.
ms.date: 09/02/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 2411299fbab6dfba8ced0f689bd33825b62614af
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808981"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Documenti di Visual Studio: novità di agosto 2020

Introduzione alle novità di Visual Studio docs per il 2020 agosto. Questo articolo elenca alcune delle principali modifiche apportate a docs durante questo periodo. Per informazioni sulle novità dei mesi precedenti, vedere l'argomento Novità della [cronologia](whats-new-visual-studio-docs-history.md) .

## <a name="azure"></a>Azure

**Nuovi articoli**

- [Aggiungere applicazione Azure Insights usando i servizi connessi di Visual Studio servizi connessi](../azure/azure-app-insights-add-connected-service.md) per VS 2019 16,7
- [Aggiungere la cache di Azure per Redis usando](../azure/azure-cache-for-redis-add-connected-service.md) i servizi connessi a Visual Studio servizi connessi per VS 2019 16,7
- [Aggiungere Azure Cosmos DB all'app usando i servizi connessi di Visual Studio servizi connessi](../azure/azure-cosmosdb-add-connected-service.md) per VS 2019 16,7
- [Aggiungere Azure SignalR usando i servizi connessi di Visual Studio servizi connessi](../azure/azure-signalr-add-connected-service.md) per VS 2019 16,7
- [Aggiungere una connessione ai servizi connessi al database SQL di Azure](../azure/azure-sql-database-add-connected-service.md) per VS 2019 16,7

**Articoli aggiornati**

- [Aggiunta dell’archiviazione di Azure tramite Servizi connessi di Visual Studio](../azure/vs-azure-tools-connected-services-storage.md)
  - Servizi connessi per VS 2019 16,7
  - Articolo relativo ai servizi connessi di archiviazione di Azure: aggiornare i tipi di interfaccia utente e progetto supportati

## <a name="code-quality"></a>Qualità del codice

**Nuovi articoli**

- [Ca1310: specificare StringComparison per la correttezza](../code-quality/ca1310.md) -aggiungere la documentazione per ca1310 e aggiornare la documentazione per CA1307
- [Ca1837: usare Environment. ProcessId anziché Process. GetCurrentProcess (). ID](../code-quality/ca1837.md) -docs per ca1837
- [Ca1838: evitare `StringBuilder` i parametri per P/Invoke](../code-quality/ca1838.md) -aggiungere la documentazione per ca1838
- [Ca2008: non creare attività senza passare un TaskScheduler](../code-quality/ca2008.md) -aggiungere la documentazione per ca2008
- [CA2249: provare a usare String. Contains anziché String. IndexOf](../code-quality/ca2249.md) -docs per CA2249
- [CA2361: assicurarsi che la classe generata automaticamente contenente DataSet. ReadXml () non venga usata con dati non attendibili](../code-quality/ca2361.md) -altre regole DataSet/DataTable
- [CA2362: il set di dati o la DataTable unsafe nel tipo serializzabile generato automaticamente può essere vulnerabile agli attacchi di esecuzione di codice in modalità remota](../code-quality/ca2362.md) . altre regole DataSet/DataTable
- [IL3000: evitare di usare l'accesso al percorso del file di assembly quando si pubblica come](../code-quality/il3000.md) documentazione di aggiunta di un singolo file per IL3000
- [IL3001: evitare di accedere al percorso del file di assembly durante la pubblicazione come singolo file](../code-quality/il3001.md) : aggiungere documenti per IL3001

**Aggiornato**

- [CA1002: non esporre elenchi generici](../code-quality/ca1002.md) -sezione aggiunta di configurabilità-superficie API
- [CA1046: non eseguire l'overload dell'operatore uguale ai tipi di riferimento](../code-quality/ca1046.md) -sezione aggiunta di configurabilità-superficie API
- [CA1307: specificare StringComparison per maggiore chiarezza](../code-quality/ca1307.md) -aggiungere la documentazione per ca1310 e aggiornare la documentazione per CA1307
- [CA1700: non denominare i valori enum &#39;sezione&#39;riservata ](../code-quality/ca1700.md) -Aggiungi configurabilità-superficie API
- [CA1707: gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707.md) -sezione aggiunta di configurabilità-superficie API
- [CA1822: contrassegna i membri come statici](../code-quality/ca1822.md) -aggiunta di configurabilità-sezione di superficie dell'API
- [CA2351: assicurarsi che l'input di DataSet. ReadXml () sia attendibile](../code-quality/ca2351.md) -altre regole DataSet/DataTable
- [Installare gli analizzatori di terze parti](../code-quality/install-roslyn-analyzers.md) : struttura modificata e titoli per la documentazione di analisi del codice

## <a name="containers"></a>Contenitori

**Articoli aggiornati**

- [Distribuire un contenitore ASP.NET in un registro contenitori con Visual Studio](../containers/hosting-web-apps-in-docker.md) -aggiornamenti degli strumenti contenitore per l'interfaccia utente di pubblicazione di visual Studio 16,7
- [Introduzione agli strumenti di Visual Studio Kubernetes](../containers/tutorial-kubernetes-tools.md) -esercitazione su Kubernetes: aggiungere i passaggi per la rimozione

## <a name="deployment"></a>Distribuzione

**Nuovi articoli**

- [Estensione di progetti programma di installazione di Visual Studio e .net core 3,1](../deployment/installer-projects-net-core.md) -creazione di una nuova pagina della Guida per i progetti di installazione di .net core 3,1 funzionalità

**Articoli aggiornati**

- [Distribuire l'app in una cartella, IIS, Azure o in un'altra destinazione](../deployment/deploying-applications-services-and-components-resources.md) -aggiornamenti della distribuzione
- [Distribuzione in Visual Studio](../deployment/index.yml) -aggiornamenti della distribuzione

## <a name="extensibility"></a>Estendibilità

**Articoli aggiornati**
- [Sottotipi di progetto](../extensibility/internals/project-subtypes.md) -correzione rientri elementi elenco
- [Riferimento al valore del colore per Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) -AB # 1759333 correggere le intestazioni di colonna mancanti

## <a name="get-started"></a>Operazioni preliminari

**Articoli aggiornati**

- [Passaggio 5: distribuire l'app ASP.NET Core in Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) -aggiornamenti dell'esercitazione video per la nuova interfaccia utente di servizi connessi

## <a name="ide"></a>IDE

**Nuovi articoli**

- [Modificare il tasto Guida F1 in Visual Studio](./not-in-toc/change-f1-help-key.md) -pagina della Guida sensibile al contesto del refactoring
- [Guida sensibile al contesto per l'editor di testo](./not-in-toc/default-f1-text-editor.md) -pagina della Guida F1 predefinita
- [Convert `typeof` to `nameof` ](./reference/convert-typeof-to-nameof.md) -Convert typeof in refactoring NameOf
- [Semplificare l'espressione LINQ](./reference/simplify-linq-expression.md) -semplificare il refactoring dell'espressione LINQ

**Articoli aggiornati**

- [Personalizzare il layout delle finestre in Visual Studio](./customizing-window-layouts-in-visual-studio.md) -aggiungere informazioni sulle schede del documento verticale con moniker per personalizzare il layout delle finestre
- [Come segnalare un problema con Visual Studio o il programma di installazione di Visual Studio](./how-to-report-a-problem-with-visual-studio.md)
  - Sono state aggiunte altre informazioni a NMI
  - Pagina di un problema di report completa
- [Guida sensibile](./not-in-toc/default.md) al contesto refactoring-pagina della Guida F1 predefinita
- [Salvataggio automatico, ambiente, finestra di dialogo Opzioni](./reference/autorecover-environment-options-dialog-box.md) -Aggiungi informazioni sui percorsi dei file di salvataggio automatico aggiornati
- [Opzioni, editor di testo, di base (Visual Basic),](./reference/options-text-editor-basic-visual-basic.md) documentazione di base aggiunta in anticipo per gli hint per i nomi dei parametri inline
- [Opzioni, editor di testo, C#,](./reference/options-text-editor-csharp-advanced.md) documentazione di base aggiunta in anticipo per gli hint per i nomi dei parametri inline
- [Suggerimenti per le prestazioni di Visual Studio](./visual-studio-performance-tips-and-tricks.md) : aggiungere le informazioni su "Disabilita modalità mappa" e "Disabilita a capo automatico"
- [Novità di Visual studio 2019](./whats-new-visual-studio-2019.md) -aggiornamento delle novità di visual studio 2019 con le informazioni sulla versione GA di 16,7

## <a name="rtvs"></a>RTVS

**Articoli aggiornati**

- [Usare le tabelle SQL Server e con correzione R](../rtvs/integrating-sql-server-with-r.md) per includere le intestazioni di colonna

## <a name="community-contributors"></a>Collaboratori della community

Le persone seguenti hanno contribuito alla documentazione di Visual Studio durante questo periodo. Grazie! Per informazioni su come contribuire alla documentazione di Visual Studio, seguire le istruzioni riportate nella Guida per i [collaboratori](/contribute/).

- [AlexB-SheldonMFG](https://github.com/AlexB-SheldonMFG) -Alex nero (11)
- [Youssef1313](https://github.com/Youssef1313) -Youssef Victor (8)
- [hyoshioka0128](https://github.com/hyoshioka0128) -Hiroshi Yoshioka (3)
- [AstroChoco](https://github.com/AstroChoco) -Qian Lu (Chocolate) (1)
- [athyunnath](https://github.com/athyunnath) -athyunnath eleti (1)
- [caro-Oviedo](https://github.com/caro-oviedo) -caro Oviedo (1)
- [Evangelink](https://github.com/Evangelink) -Amaury levé (1)
- [jethas-bennettjones](https://github.com/jethas-bennettjones) -Jetha (1)
- [nebuk89](https://github.com/nebuk89) -ben de St Paer-Gotch (1)
- [pcartwright81](https://github.com/pcartwright81) (1)
- [pkulikov](https://github.com/pkulikov) -Petr Kulikov (1)
- [riQQ](https://github.com/riQQ) (1)
- [tcmetzger](https://github.com/tcmetzger) -timo Cornelius Metzger (1)
- [Weitzhandler](https://github.com/weitzhandler) -Shake (1)