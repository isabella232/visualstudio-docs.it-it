---
title: Progetti di database e progetti di applicazione livello dati
description: Informazioni sui progetti di database e sulle applicazioni livello dati . Usare i progetti di database per creare nuovi database, creare nuove dac e aggiornare i database e le dac esistenti.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9eb21f68e3f843d4d05ef046dfc7de4c01ff5d12053cf8063eb4f805286fb050
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347428"
---
# <a name="database-projects-and-data-tier-applications"></a>Progetti di database e applicazioni livello dati

È possibile usare i progetti di database per creare nuovi database, nuove applicazioni livello dati (DAC) e aggiornare i database esistenti e le applicazioni livello dati. Sia i progetti di database che i progetti di applicazione livello dati consentono di applicare tecniche di controllo della versione e gestione dei progetti alle attività di sviluppo del database in modo molto identico a quelle applicate al codice gestito o nativo. È possibile aiutare il team di sviluppo a gestire le modifiche ai database e ai server di database creando un progetto di applicazione livello dati, un progetto di database o un progetto server e inserendolo nel controllo della versione. I membri del team possono quindi estrarre i file per apportare, compilare e testare le modifiche in un ambiente di sviluppo isolato o in una sandbox prima di condividerli con il team. Per garantire la qualità del codice, il team può completare e testare tutte le modifiche per una determinata versione del database in un ambiente di staging prima di distribuire le modifiche nell'ambiente di produzione.

Per un elenco delle funzionalità del database supportate dalle applicazioni livello dati, vedere Supporto [dell'applicazione](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions)livello dati per SQL Server oggetti . Se nel database si usano funzionalità non supportate dalle applicazioni livello dati, è consigliabile usare un progetto di database per gestire le modifiche apportate al database.

## <a name="common-high-level-tasks"></a>Attività comuni di alto livello

| High-Level attività | Contenuto di supporto |
| - | - |
| **Avviare lo sviluppo di un'applicazione livello dati:** Il concetto di applicazione livello dati è stato introdotto con SQL Server 2008. Un'applicazione livello dati contiene la definizione per un database SQL Server e gli oggetti istanza di supporto usati da un'applicazione client-server o a 3 livelli. Un'applicazione livello dati include oggetti di database, ad esempio tabelle e viste, insieme alle entità di istanza, ad esempio gli account di accesso. È possibile usare Visual Studio per creare un progetto di applicazione livello dati, compilare un file di pacchetto dell'applicazione livello dati e inviare il file del pacchetto di applicazione livello dati a un amministratore di database per la distribuzione in un'istanza del motore di database SQL Server database. | - [Applicazioni livello dati](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Esecuzione dello sviluppo iterativo del database:** Gli sviluppatori possono estrarre parti del progetto e aggiornarle in un ambiente di sviluppo isolato. Usando questo tipo di ambiente, è possibile testare le modifiche senza influire sugli altri membri del team. Al termine delle modifiche, archiviare di nuovo i file nel controllo della versione, in cui gli altri membri del team possono ottenere le modifiche e compilarle e distribuirle in un server di test. | - [Project sviluppo di database offline orientato SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Debugger Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Creazione di prototipi, verifica dei risultati dei test e modifica di oggetti e script di database:** È possibile usare l'editor transact-SQL per eseguire una di queste attività comuni. | - [Editor di query e di testo (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Vedi anche

- [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
