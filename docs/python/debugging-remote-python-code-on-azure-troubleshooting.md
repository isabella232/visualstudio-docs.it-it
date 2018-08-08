---
title: Risoluzione dei problemi del debug remoto di Azure per Python
description: Come risolvere i problemi durante il tentativo di eseguire il debug di un'applicazione Python in esecuzione in Servizio app di Azure con Visual Studio.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f545fa223aa929b79016352e799d112bceddaf1c
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341463"
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Risoluzione dei problemi di debug remoto per Python e Azure

Visual Studio non riesce a collegarsi a un [servizio app di Azure per il debug remoto](debugging-remote-python-code-on-azure.md) per uno qualsiasi dei motivi seguenti:

| Motivo | Risoluzione |
| --- | --- |
| Non sono disponibili Visual Studio 2013 Update 4 o versione successive. | Installare una versione appropriata da [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). |
| Il progetto distribuito nel servizio app non corrisponde a quello aperto in Visual Studio. | Caricare il progetto corretto in Visual Studio. |
| Il progetto non è stato distribuito con la configurazione **Debug**. | Ridistribuire l'applicazione facendo clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliendo **Pubblica**. Nella scheda **Impostazioni** assicurarsi che la configurazione selezionata sia **Debug**. |
| Il servizio app non è in esecuzione. | Avviarlo da **Esplora server** in Visual Studio o dal portale di Azure. |
| Il servizio app non è configurato con WebSocket. | Passare al [portale di Azure](https://portal.azure.com) e al servizio app in questione, scegliere **Impostazioni** > **Impostazioni applicazione**, impostare **Impostazioni generali** > **Web Socket** su **Attivato** e selezionare **Salva**. (Si noti che le opzioni **Debug** visualizzate in questo pannello *non* si applicano al debug Python.) |
| *web.debug.config* è stato modificato per disabilitare il proxy di debug. | Eliminare il file e ripubblicare il progetto nel servizio app. Durante l'operazione, Visual Studio ricrea il file. |

Vedere anche:

- [Debug remoto di codice Python in Azure](debugging-remote-python-code-on-azure.md)
