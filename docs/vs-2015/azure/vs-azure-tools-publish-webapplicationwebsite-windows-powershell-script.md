---
title: Publish-WebApplicationWebSite (script di Windows PowerShell) | Microsoft Docs
description: Informazioni su come pubblicare un progetto web in un sito Web di Azure. Questo script crea le risorse necessarie nella sottoscrizione di Azure se non sono presenti.
author: ghogen
manager: douge
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 175181d5d866e9d7fab51eaf7c3262e47d0ed6a8
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002891"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (script di Windows PowerShell)
## <a name="syntax"></a>Sintassi
Pubblica un progetto web in un sito Web di Azure. Se non sono presenti, lo script crea le risorse necessarie nella sottoscrizione di Azure.

    Publish-WebApplicationWebSite
    –Configuration <configuration>
    -SubscriptionName <subscriptionName>
    -WebDeployPackage <packageName>
    -DatabaseServerPassword @{Name = "name"; Password = "password"}
    -SendHostMessagesToOutput
    -Verbose


## <a name="configuration"></a>Configurazione
Il percorso del file di configurazione JSON che descrive i dettagli della distribuzione.

| Parametro | Valore predefinito |
| --- | --- |
| Alias |none |
| Obbligatorio? |true |
| Posizione |denominati |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Accettare caratteri jolly? |False |

## <a name="subscriptionname"></a>SubscriptionName
Il nome della sottoscrizione di Azure che si desidera creare il sito Web in.

| Parametro | Valore predefinito |
| --- | --- |
| Alias |none |
| Obbligatorio? |False |
| Posizione |denominati |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Accettare caratteri jolly? |False |

## <a name="webdeploypackage"></a>WebDeployPackage
Il percorso al pacchetto di distribuzione web da pubblicare nel sito Web. È possibile creare il pacchetto usando la procedura guidata Pubblica sito Web in Visual Studio. Per altre informazioni, vedere [Introduzione a servizi Cloud di Azure e ASP.NET](http://go.microsoft.com/fwlink/p/?LinkID=623089).

| Parametro | Valore predefinito |
| --- | --- |
| Alias |none |
| Obbligatorio? |False |
| Posizione |denominati |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Accettare caratteri jolly? |False |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
Il nome utente e password per il database SQL di Azure.

| Parametro | Valore predefinito |
| --- | --- |
| Alias |none |
| Obbligatorio? |False |
| Posizione |denominati |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Accettare caratteri jolly? |False |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Se true, stampa i messaggi dallo script nel flusso di output.

| Parametro | Valore predefinito |
| --- | --- |
| Alias |none |
| Obbligatorio? |False |
| Posizione |denominati |
| Valore predefinito |False |
| Input pipeline accettato? |False |
| Accettare caratteri jolly? |False |

## <a name="remarks"></a>Note
Per una spiegazione completa di come usare lo script per creare ambienti di sviluppo e Test, vedere [usando gli script di PowerShell di Windows eseguire la pubblicazione in ambienti di Test e sviluppo](vs-azure-tools-publishing-using-powershell-scripts.md).

Il file di configurazione JSON specifica i dettagli delle novità per la distribuzione. Include le informazioni specificate durante la creazione del progetto, quali il nome e il nome utente per il sito Web. Contiene inoltre il database per il provisioning, se presente. Il codice seguente illustra un file di configurazione JSON di esempio:

    {
        "environmentSettings": {
            "webSite": {
                "name": "WebApplication10554",
                "location": "West US"
            },
            "databases": [
                {
                    "connectionStringName": "DefaultConnection",
                    "databaseName": "WebApplication10554_db",
                    "serverName": "iss00brc88",
                    "user": "sqluser2",
                    "password": "",
                    "edition": "",
                    "size": "",
                    "collation": "",
                    "location": "West US"
                }
            ]
        }
    }

È possibile modificare il file di configurazione JSON per modificare gli elementi da distribuire. Una sezione webSite è obbligatoria, ma la sezione del database è facoltativa.

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni, vedere [Publish-WebApplicationVM (script di Windows PowerShell)](vs-azure-tools-publish-webapplicationvm.md)

