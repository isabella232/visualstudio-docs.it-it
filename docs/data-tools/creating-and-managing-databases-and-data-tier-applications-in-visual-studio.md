---
title: Progetti di database e progetti DAC
description: Informazioni sui progetti di database e le applicazioni livello dati (DAC). Utilizzare i progetti di database per creare nuovi database, creare nuove DAC e aggiornare i database e le applicazioni livello dati esistenti.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 57b889f025b06e127e8e4bb38be311f6bbe55952
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436602"
---
# <a name="database-projects-and-data-tier-applications"></a>Progetti di database e applicazioni livello dati

È possibile utilizzare i progetti di database per creare nuovi database, nuove applicazioni del livello dati (DAC) e per aggiornare i database esistenti e le applicazioni del livello dati. I progetti di database e di applicazione livello dati consentono di applicare tecniche di controllo della versione e di gestione dei progetti allo sviluppo del database in modo analogo all'applicazione di tali tecniche a codice gestito o nativo. È possibile consentire al team di sviluppo di gestire le modifiche apportate ai database e ai server di database creando un progetto di applicazione livello dati, un progetto di database o un progetto server e inserendolo nel controllo della versione. I membri del team possono quindi estrarre i file per creare, compilare e testare le modifiche in un ambiente di sviluppo isolato, o sandbox, prima di condividerli con il team. Per garantire la qualità del codice, il team può completare e testare tutte le modifiche per una particolare versione del database in un ambiente di gestione temporanea prima di distribuire le modifiche in produzione.

Per un elenco delle funzionalità di database supportate dalle applicazioni livello dati, vedere [supporto DAC per oggetti SQL Server](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Se si utilizzano le funzionalità del database non supportate dalle applicazioni livello dati, è necessario utilizzare un progetto di database per gestire le modifiche apportate al database.

## <a name="common-high-level-tasks"></a>Attività di alto livello comuni

| Attività High-Level | Contenuto di supporto |
| - | - |
| **Avviare lo sviluppo di un'applicazione livello dati:** Il concetto di applicazione livello dati (DAC) è stato introdotto con SQL Server 2008. Un'applicazione livello dati contiene la definizione per un database di SQL Server e gli oggetti istanza di supporto utilizzati da un'applicazione client-server o a tre livelli. Un'applicazione livello dati include oggetti di database, ad esempio tabelle e viste, insieme a entità di istanza quali gli account di accesso. È possibile utilizzare Visual Studio per creare un progetto DAC, compilare un file di pacchetto di applicazione livello dati e inviare il file del pacchetto di applicazione livello dati a un amministratore di database per la distribuzione in un'istanza del motore di database SQL Server. | - [Applicazioni livello dati](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Esecuzione dello sviluppo iterativo di database:** Gli sviluppatori possono estrarre parti del progetto e aggiornarle in un ambiente di sviluppo isolato. Utilizzando questo tipo di ambiente, è possibile testare le modifiche senza influire sugli altri membri del team. Una volta completate le modifiche, è possibile archiviare nuovamente i file nel controllo della versione, in modo che gli altri membri del team possano ottenere le modifiche e compilarle e distribuirle in un server di prova. | - [Sviluppo di database offline orientato ai progetti (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Debugger Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Prototipi, verifica dei risultati dei test e modifica degli script e degli oggetti di database:** È possibile utilizzare l'editor Transact-SQL per eseguire una di queste attività comuni. | - [Editor di query e di testo (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Vedere anche

- [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
