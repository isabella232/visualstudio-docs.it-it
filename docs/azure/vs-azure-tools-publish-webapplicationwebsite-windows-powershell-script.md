---
title: Publish-WebApplicationWebSite (script di Windows PowerShell) | Documentazione Microsoft
description: Informazioni su come pubblicare un progetto Web in un sito Web di Azure. Se non sono presenti, lo script crea le risorse necessarie nella sottoscrizione di Azure.
author: ghogen
manager: jillfra
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.prod: visual-studio-dev15
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: b25317e26c13637ea0ed0757af11ca345132f9cb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55140692"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (script di Windows PowerShell)
## <a name="syntax"></a>Sintassi
Pubblica un progetto Web in un sito Web di Azure. Se non sono presenti, lo script crea le risorse necessarie nella sottoscrizione di Azure.

    Publish-WebApplicationWebSite
    –Configuration <configuration>
    -SubscriptionName <subscriptionName>
    -WebDeployPackage <packageName>
    -DatabaseServerPassword @{Name = "name"; Password = "password"}
    -SendHostMessagesToOutput
    -Verbose


## <a name="configuration"></a>Configurazione
Percorso del file di configurazione JSON che descrive i dettagli della distribuzione.

| Parametro | Valore predefinito |
| --- | --- |
| Alias |none |
| Obbligatorio? |true |
| Posizione |denominata |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Caratteri jolly accettati? |False |

## <a name="subscriptionname"></a>SubscriptionName
Nome della sottoscrizione di Azure in cui si vuole creare il sito Web.

| Parametro | Valore predefinito |
| --- | --- |
| Alias |none |
| Obbligatorio? |False |
| Posizione |denominata |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Caratteri jolly accettati? |False |

## <a name="webdeploypackage"></a>WebDeployPackage
Percorso al pacchetto di distribuzione Web da pubblicare nel sito Web. È possibile creare questo pacchetto usando la pubblicazione Web guidata di Visual Studio. Per ulteriori informazioni, vedere [Introduzione a Servizi cloud di Azure e ASP.NET](http://go.microsoft.com/fwlink/p/?LinkID=623089).

| Parametro | Valore predefinito |
| --- | --- |
| Alias |none |
| Obbligatorio? |False |
| Posizione |denominata |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Caratteri jolly accettati? |False |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
Nome utente e password per il database SQL di Azure.

| Parametro | Valore predefinito |
| --- | --- |
| Alias |none |
| Obbligatorio? |False |
| Posizione |denominata |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Caratteri jolly accettati? |False |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Se impostato su true, stampa i messaggi dallo script al flusso di output.

| Parametro | Valore predefinito |
| --- | --- |
| Alias |none |
| Obbligatorio? |False |
| Posizione |denominata |
| Valore predefinito |False |
| Input pipeline accettato? |False |
| Caratteri jolly accettati? |False |

## <a name="remarks"></a>Osservazioni
Per una spiegazione completa sull'uso dello script per creare ambienti di sviluppo e test, vedere [Uso degli script di Windows PowerShell per la pubblicazione in ambienti di sviluppo e test](vs-azure-tools-publishing-using-powershell-scripts.md).

Il file di configurazione JSON specifica i dettagli degli elementi da distribuire. Include le informazioni specificate al momento della creazione del progetto, ad esempio il nome e il nome utente per il sito Web. Se esiste, include anche il database di cui eseguire il provisioning. Il codice seguente mostra un esempio di file di configurazione JSON:

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

È possibile modificare il file di configurazione JSON per cambiare gli elementi da distribuire. La sezione webSite è obbligatoria, ma la sezione del database è facoltativa.

## <a name="next-steps"></a>Passaggi successivi
Per ulteriori informazioni, vedere [Publish-WebApplicationVM (script di Windows PowerShell)](vs-azure-tools-publish-webapplicationvm.md)