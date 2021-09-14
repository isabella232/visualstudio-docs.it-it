---
title: Progetti di database e progetti di applicazione livello dati
description: Informazioni sui progetti di database e sulle applicazioni livello dati (DAC). Usare i progetti di database per creare nuovi database, creare nuove dac e aggiornare database e DAC esistenti.
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
ms.openlocfilehash: 0d9ed2d258fba0e8c6e1970bc758d0285bb4276c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631446"
---
# <a name="database-projects-and-data-tier-applications"></a>Progetti di database e applicazioni livello dati

È possibile usare i progetti di database per creare nuovi database, nuove applicazioni livello dati (DAC) e per aggiornare i database esistenti e le applicazioni livello dati. Sia i progetti di database che i progetti di applicazione livello dati consentono di applicare tecniche di controllo della versione e gestione dei progetti alle attività di sviluppo del database in modo molto identico all'applicazione di tali tecniche al codice gestito o nativo. È possibile aiutare il team di sviluppo a gestire le modifiche apportate ai database e ai server di database creando un progetto di applicazione livello dati, un progetto di database o un progetto server e inserendolo nel controllo della versione. I membri del team possono quindi estrarre i file per apportare, compilare e testare le modifiche in un ambiente di sviluppo isolato, o sandbox, prima di condividerli con il team. Per garantire la qualità del codice, il team può completare e testare tutte le modifiche per una determinata versione del database in un ambiente di gestione temporanea prima di distribuire le modifiche nell'ambiente di produzione.

Per un elenco delle funzionalità di database supportate dalle applicazioni livello dati, vedere Supporto dell'applicazione livello dati [per SQL Server oggetti](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Se nel database si usano funzionalità non supportate dalle applicazioni livello dati, è consigliabile usare invece un progetto di database per gestire le modifiche apportate al database.

## <a name="common-high-level-tasks"></a>Attività comuni di alto livello

| High-Level attività | Contenuto di supporto |
| - | - |
| **Avviare lo sviluppo di un'applicazione livello dati:** Il concetto di applicazione livello dati è stato introdotto con SQL Server 2008. Un'applicazione livello dati contiene la definizione per un database SQL Server e gli oggetti istanza di supporto utilizzati da un'applicazione client-server o a 3 livelli. Un'applicazione livello dati include oggetti di database, ad esempio tabelle e viste, insieme a entità di istanza, ad esempio account di accesso. È possibile usare Visual Studio per creare un progetto di applicazione livello dati, compilare un file di pacchetto di applicazione livello dati e inviare il file del pacchetto di applicazione livello dati a un amministratore di database per la distribuzione in un'istanza del motore di database di SQL Server. | - [Applicazioni livello dati](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Esecuzione dello sviluppo di database iterativo:** Gli sviluppatori possono estrarre parti del progetto e aggiornarle in un ambiente di sviluppo isolato. Usando questo tipo di ambiente, è possibile testare le modifiche senza influire sugli altri membri del team. Al termine delle modifiche, è possibile archiviare i file nel controllo della versione, in modo che altri membri del team possano ottenere le modifiche e compilarle e distribuirle in un server di prova. | - [Project sviluppo di database offline orientato al database (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Debugger Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Creazione di prototipi, verifica dei risultati dei test e modifica di oggetti e script di database:** È possibile usare l'editor transact-SQL per eseguire una di queste attività comuni. | - [Editor di query e di testo (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Vedi anche

- [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
