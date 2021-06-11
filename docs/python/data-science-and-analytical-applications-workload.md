---
title: Carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati
description: Questo carico di lavoro di Visual Studio riunisce Python, F# e le rispettive distribuzioni di runtime, tra cui Anaconda. Visual Studio 2017 include anche R.
ms.date: 02/28/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- python
- data-science
ms.openlocfilehash: 2c12c8a0979ab081ea2f09faeeccdb5a8a9d2175
ms.sourcegitcommit: 398b4d4e5ce0f978720f11990db05b209766aedc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2021
ms.locfileid: "112016307"
---
# <a name="install-data-science-support-in-visual-studio"></a>Installare il supporto per l'analisi scientifica in Visual Studio

Il carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati, che può essere selezionato e installato tramite il programma di installazione di Visual Studio, riunisce diversi linguaggi e le rispettive distribuzioni di runtime:

::: moniker range="vs-2017"
- [Python e Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F# con .NET Framework](/dotnet/fsharp/)
- [R e Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [F# con .NET Framework](/dotnet/fsharp/)
::: moniker-end

![Carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati nel programma di installazione di Visual Studio](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Python e R sono due dei principali linguaggi di scripting usati per le attività di data science. Entrambi i linguaggi sono facili da imparare e sono supportati da un nutrito ecosistema di pacchetti. Questi pacchetti soddisfano le esigenze di un'ampia gamma di scenari, ad esempio l'acquisizione e la pulizia dei dati, il training di modelli di dati, la distribuzione dei dati e i tracciati. F# è inoltre un linguaggio .NET potente e prima di tutto funzionale, adatto a una grande varietà di attività di elaborazione dati.
::: moniker-end

::: moniker range=">=vs-2019"
Python è un linguaggio di scripting fondamentale usato per le attività di data science. Python è facile da imparare ed è supportato da un nutrito ecosistema di pacchetti. Questi pacchetti soddisfano le esigenze di un'ampia gamma di scenari, ad esempio l'acquisizione e la pulizia dei dati, il training di modelli di dati, la distribuzione dei dati e i tracciati. F# è anche un potente linguaggio .NET funzionale adatto per un'ampia gamma di attività di elaborazione dati.
::: moniker-end

<!--Note link on the image because this one is large -->
[![Screenshot di Visual Studio con R, Python e F#](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Opzioni del carico di lavoro

Per impostazione predefinita, il carico di lavoro installa le opzioni seguenti, che è possibile modificare nella sezione di riepilogo per il carico di lavoro nel programma di installazione di Visual Studio:

::: moniker range=">=vs-2019"
- Supporto per il linguaggio F# desktop
- Python:
  - Supporto linguaggio Python
  - Supporto Web Python
::: moniker-end

::: moniker range="vs-2017"
- Supporto per il linguaggio F#
- Python:
  - Supporto linguaggio Python
  - [Anaconda3 a 64 bit](https://www.continuum.io), una distribuzione Python che include librerie di data science complete e un interprete Python.
  - Supporto Web Python
  - Supporto modello Cookiecutter
- R:
  - Supporto linguaggio R
  - Supporto runtime per strumenti di sviluppo R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (Interprete R di Microsoft supportato dalla community e completamente compatibile con librerie ScaleR per calcoli più veloci su singoli nodi o cluster. È anche possibile usare qualsiasi versione di R da [CRAN](https://cran.r-project.org/).)
::: moniker-end

## <a name="sql-server-integration"></a>Integrazione con SQL Server

::: moniker range="vs-2017"
SQL Server supporta l'uso di Python e R per eseguire attività di analisi avanzate direttamente all'interno di SQL Server. Il supporto di R è incluso in SQL Server 2016 e versioni successive, mentre il supporto di Python è disponibile in SQL Server 2017 CTP 2.0 e versioni successive.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server supporta l'uso di Python per eseguire attività di analisi avanzate direttamente all'interno di SQL Server. Il supporto di Python è disponibile in SQL Server 2017 CTP 2.0 e versioni successive.
::: moniker-end

L'esecuzione del codice nella posizione in cui si trovano già i dati offre i vantaggi seguenti:

- **Eliminazione dello spostamento dei dati:** invece di spostare i dati dal database all'applicazione o al modello, è possibile compilare applicazioni nel database. Questa funzionalità consente di evitare le barriere a livello di sicurezza, conformità, governance e integrità, oltre a una serie di problemi simili correlati allo spostamento di grandi quantità di dati. È anche possibile usare set di dati che non potrebbero essere gestiti con la memoria di un computer client.

- **Distribuzione semplice:** dopo aver pronto un modello, distribuirlo nell'ambiente di produzione è semplice incorporarlo in uno script T-SQL. Qualsiasi applicazione client SQL scritta in qualsiasi linguaggio può quindi sfruttare modelli e intelligence tramite una chiamata di stored procedure. Non sono necessarie integrazioni specifiche del linguaggio.

- **Scalabilità** e prestazioni di livello aziendale: è possibile usare le funzionalità avanzate di SQL Server, ad esempio gli indici di tabelle e archivi colonne in memoria, con le API scalabili ad alte prestazioni nei pacchetti RevoScale. Evitare gli spostamenti di dati significa anche evitare i vincoli di memoria client man mano che aumentano le dimensioni dei dati oppure se si desidera aumentare le prestazioni dell'applicazione.

- **Estendibilità** dettagliata: è possibile installare ed eseguire uno dei pacchetti open source più recenti in SQL Server per creare applicazioni di deep learning e intelligenza artificiale su enormi quantità di dati SQL Server. Installare un pacchetto in SQL Server è semplice come l'installazione di un pacchetto nel computer locale.

- **Ampia disponibilità senza** costi aggiuntivi: le integrazioni del linguaggio sono disponibili in tutte le edizioni di SQL Server 2017 e versioni successive, inclusa l'edizione Express.

Per sfruttare al meglio l'integrazione in SQL Server, usare il programma di installazione di Visual Studio per installare il carico di lavoro **Elaborazione ed archiviazione dati** con l'opzione **SQL Server Data Tools**. Questa opzione abilita SQL IntelliSense, l'evidenziazione della sintassi e la distribuzione.

![Carico di lavoro Elaborazione ed archiviazione dati](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Opzioni del carico di lavoro Elaborazione ed archiviazione dati](media/workload/data-storage-workload-options.png)

Per altre informazioni:

::: moniker range="vs-2017"
- [Usare SQL Server ed R](../rtvs/integrating-sql-server-with-r.md)
- [In-database Advanced Analytics with R in SQL Server 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/) (Analisi avanzata all'interno del database con R in SQL Server 2016)
::: moniker-end
- [Python in SQL Server 2017: enhanced in-database machine learning (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/) (Python in SQL Server 2017: funzionalità avanzate di Machine Learning all'interno del database)

## <a name="additional-services-and-sdks"></a>Servizi aggiuntivi e SDK

Oltre ai componenti inclusi direttamente nel carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati, per le esigenze di data science sono utili anche il servizio Azure Notebooks e Azure SDK per Python.

Azure SDK per Python semplifica l'uso e la gestione dei servizi di Microsoft Azure dalle applicazioni eseguite in Windows, Mac e Linux. Per altre informazioni, vedere [Azure SDK per Python](/azure/python/).

Azure Notebooks (attualmente in anteprima) consente l'accesso online gratuito ai notebook di Jupyter in esecuzione nel cloud in Microsoft Azure. Il servizio include notebook di esempio in Python, R e F# per iniziare. Visitare [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Screenshot di Azure Notebooks con l'esempio Introduction to R (Introduzione a R)](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
