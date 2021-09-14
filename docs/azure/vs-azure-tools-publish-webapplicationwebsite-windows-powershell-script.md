---
title: Pubblicare un'app Web usando uno script di PowerShell
description: Informazioni su come pubblicare un progetto Web in un sito Web di Azure. Se non sono presenti, lo script crea le risorse necessarie nella sottoscrizione di Azure.
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 30197480c1108340a9b27c5fc28f874699defa9d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633067"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (script di Windows PowerShell)
## <a name="syntax"></a>Sintassi
Pubblica un progetto Web in un sito Web di Azure. Se non sono presenti, lo script crea le risorse necessarie nella sottoscrizione di Azure.

```
Publish-WebApplicationWebSite
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

## <a name="configuration"></a>Configurazione
Percorso del file di configurazione JSON che descrive i dettagli della distribuzione.

| Parametro | Valore predefinito |
| --- | --- |
| Alias |Nessuno |
| Necessaria? |true |
| Posizione |denominata |
| Valore predefinito |Nessuno |
| Accettare input da pipeline? |false |
| Accettare caratteri jolly? |false |

## <a name="subscriptionname"></a>SubscriptionName
Nome della sottoscrizione di Azure in cui si vuole creare il sito Web.

| Parametro | Valore predefinito |
| --- | --- |
| Alias |Nessuno |
| Necessaria? |false |
| Posizione |denominata |
| Valore predefinito |Nessuno |
| Accettare input da pipeline? |false |
| Accettare caratteri jolly? |false |

## <a name="webdeploypackage"></a>WebDeployPackage
Percorso al pacchetto di distribuzione Web da pubblicare nel sito Web. È possibile creare questo pacchetto usando la pubblicazione Web guidata di Visual Studio. Per ulteriori informazioni, vedere [Introduzione a Servizi cloud di Azure e ASP.NET](vs-azure-tools-publish-webapplicationwebsite-windows-powershell-script.md).

| Parametro | Valore predefinito |
| --- | --- |
| Alias |Nessuno |
| Necessaria? |false |
| Posizione |denominata |
| Valore predefinito |Nessuno |
| Accettare input da pipeline? |false |
| Accettare caratteri jolly? |false |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
Nome utente e password per il database SQL di Azure.

| Parametro | Valore predefinito |
| --- | --- |
| Alias |Nessuno |
| Necessaria? |false |
| Posizione |denominata |
| Valore predefinito |Nessuno |
| Accettare input da pipeline? |false |
| Accettare caratteri jolly? |false |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Se impostato su true, stampa i messaggi dallo script al flusso di output.

| Parametro | Valore predefinito |
| --- | --- |
| Alias |Nessuno |
| Necessaria? |false |
| Posizione |denominata |
| Valore predefinito |false |
| Accettare input da pipeline? |false |
| Accettare caratteri jolly? |false |

## <a name="remarks"></a>Commenti
Per una spiegazione completa sull'uso dello script per creare ambienti di sviluppo e test, vedere [Uso degli script di Windows PowerShell per la pubblicazione in ambienti di sviluppo e test](vs-azure-tools-publishing-using-powershell-scripts.md).

Il file di configurazione JSON specifica i dettagli degli elementi da distribuire. Include le informazioni specificate al momento della creazione del progetto, ad esempio il nome e il nome utente per il sito Web. Se esiste, include anche il database di cui eseguire il provisioning. Il codice seguente mostra un esempio di file di configurazione JSON:

```json
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
```

È possibile modificare il file di configurazione JSON per cambiare gli elementi da distribuire. La sezione webSite è obbligatoria, ma la sezione del database è facoltativa.

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni, vedere [Publish-WebApplicationVM (Windows PowerShell script).](vs-azure-tools-publish-webapplicationvm.md)
