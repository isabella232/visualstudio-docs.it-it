---
title: I progetti di database e di applicazione livello dati
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 2a86d9511e470c9a810ff58e80e4cae1f9a0cb11
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924643"
---
# <a name="database-projects-and-data-tier-applications"></a>Progetti di database e applicazioni livello dati

È possibile usare i progetti di database per creare nuovi database, le nuove applicazioni livello dati (DAC), nonché di aggiornare i database esistenti e le applicazioni livello dati. Sia i progetti di database e di applicazione livello dati consentono di applicare tecniche di gestione progetto e di controllo di versione per le tue attività di sviluppo di database in modo molto simile a come si applicano queste tecniche per codice gestito o nativo. Si consentono al team di sviluppo per gestire le modifiche al database e i server di database per la creazione di un progetto DAC, progetto di database o un progetto server e il relativo inserimento nel controllo della versione. I membri del team possono quindi estrarre i file per rendere, compilare e testare le modifiche in un ambiente di sviluppo isolato o sandbox, prima di condividerli con il team. Per garantire la qualità del codice, il team può terminare e testare tutte le modifiche per una particolare versione del database in un ambiente di staging prima di distribuire le modifiche nell'ambiente di produzione.

Per un elenco delle funzionalità di database supportate dalle applicazioni livello dati, vedere [il supporto dell'applicazione livello dati per oggetti di SQL Server](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Se si usano funzionalità nel database che non sono supportate dalle applicazioni livello dati, si dovrebbe usare invece un progetto di database per gestire le modifiche apportate al database.

## <a name="common-high-level-tasks"></a>Attività comuni di alto livello

| Attività di alto livello | Contenuto di supporto |
| - | - |
| **Iniziare a sviluppare un'applicazione livello dati:** con SQL Server 2008 è stato introdotto il concetto di un'applicazione livello dati (DAC). Un'applicazione livello dati contiene la definizione per un database di SQL Server e i supporto gli oggetti istanza utilizzati da un'applicazione a 3 livelli o il client e server. Un'applicazione livello dati include gli oggetti di database, ad esempio tabelle e viste, insieme alle entità di istanza, ad esempio gli account di accesso. È possibile usare Visual Studio per creare un progetto di applicazione livello dati, creare un file di pacchetto di applicazione livello dati e inviare il file del pacchetto dell'applicazione livello dati a un amministratore del database per la distribuzione in un'istanza del motore di database di SQL Server. | - [Applicazioni livello dati](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Eseguire lo sviluppo di database iterativo:** gli sviluppatori possono estrarre parti del progetto e aggiornarli in un ambiente di sviluppo isolato. Con questo tipo di ambiente, è possibile testare le modifiche senza influire su altri membri del team. Dopo aver complete le modifiche, estrarre i file in controllo della versione, in cui altri membri del team possono ottenere le modifiche e compilare e distribuirle a un server di prova. | - [Sviluppo di database offline orientato ai progetti (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Debugger Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **La creazione di prototipi, verifica risultati del test e modifica degli script di database e oggetti:** è possibile usare l'editor Transact-SQL per eseguire una di queste attività comuni. | - [Editor di query e di testo (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)