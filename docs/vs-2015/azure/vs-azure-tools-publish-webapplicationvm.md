---
title: Publish-WebApplicationVM | Microsoft Docs
description: Informazioni su come distribuire un'applicazione web a una macchina virtuale. Questo script crea le risorse necessarie nella sottoscrizione di Azure se non sono presenti.
author: ghogen
manager: douge
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: c2383e6d7b14d801a391a725f0482736fb926cd1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003001"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (script di Windows PowerShell)
Consente di distribuire un'applicazione web in una macchina virtuale. Se non sono presenti, lo script crea le risorse necessarie nella sottoscrizione di Azure.

```
Publish-WebApplicationVM
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-VMPassword @{Name = "name"; Password = "password")
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

### <a name="configuration"></a>Configurazione
Il percorso del file di configurazione JSON che descrive i dettagli della distribuzione.

| Alias | none |
| --- | --- |
| Obbligatorio? |true |
| Posizione |denominati |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Accettare caratteri jolly? |False |

### <a name="subscriptionname"></a>SubscriptionName
Il nome della sottoscrizione di Azure in cui si desidera creare la macchina virtuale.

| Alias | none |
| --- | --- |
| Obbligatorio? |False |
| Posizione |denominati |
| Valore predefinito |Usa la prima sottoscrizione nel file di sottoscrizione |
| Input pipeline accettato? |False |
| Accettare caratteri jolly? |False |

### <a name="webdeploypackage"></a>WebDeployPackage
Il percorso al pacchetto di distribuzione web da pubblicare nella macchina virtuale. È possibile creare il pacchetto usando la procedura guidata Pubblica sito Web in Visual Studio. Visualizzare [procedura: creare un pacchetto di distribuzione Web in Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx).

| Alias | none |
| --- | --- |
| Obbligatorio? |False |
| Posizione |denominati |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Accettare caratteri jolly? |False |

### <a name="allowuntrusted"></a>AllowUntrusted
Se true, consente l'uso di certificati che non sono firmati da un'autorità radice attendibile.

| Alias | none |
| --- | --- |
| Obbligatorio? |False |
| Posizione |denominati |
| Valore predefinito |False |
| Input pipeline accettato? |False |
| Accettare caratteri jolly? |False |

### <a name="vmpassword"></a>VMPassword
Le credenziali per l'account della macchina virtuale. Esempio: - VMPassword @{Name = "admin"; Password = "password"}

| Alias | none |
| --- | --- |
| Obbligatorio? |False |
| Posizione |denominati |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Accettare caratteri jolly? |False |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Le credenziali per il database SQL di Azure. Esempio: - DatabaseServerPassword @{Name = "admin"; Password = "password"}

| Alias | none |
| --- | --- |
| Obbligatorio? |False |
| Posizione |denominati |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Accettare caratteri jolly? |False |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Se true, stampa i messaggi dallo script nel flusso di output.

| Alias | none |
| --- | --- |
| Obbligatorio? |False |
| Posizione |denominati |
| Valore predefinito |False |
| Input pipeline accettato? |False |
| Accettare caratteri jolly? |False |

## <a name="remarks"></a>Note
Per una spiegazione completa di come usare lo script per creare ambienti di sviluppo e Test, vedere [usando gli script di PowerShell di Windows eseguire la pubblicazione in ambienti di Test e sviluppo](vs-azure-tools-publishing-using-powershell-scripts.md).

Il file di configurazione JSON specifica i dettagli delle novità per la distribuzione. Include le informazioni specificate durante la creazione del progetto, quali il nome, gruppo di affinità, immagine del disco rigido virtuale e le dimensioni della macchina virtuale. Inoltre include gli endpoint nella macchina virtuale, i database per effettuare il provisioning, se presente e i parametri di distribuzione web. Il codice seguente illustra un file di configurazione JSON di esempio:

```
{
    "environmentSettings": {
        "cloudService": {
            "name": "myvmname",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myvmname",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Windows-Server-2012-R2-201404.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [
                    {
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [
            {
                "connectionStringName": "",
                "databaseName": "",
                "serverName": "",
                "user": "",
                "password": ""
            }
        ],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

È possibile modificare il file di configurazione JSON per modificare gli elementi del provisioning. Sono necessari una macchina virtuale e un servizio cloud, ma la sezione del database è facoltativa.

