---
title: Azure SDK per Python
description: Azure SDK per Python semplifica l'utilizzo dei servizi di Microsoft Azure dalle applicazioni Python eseguite su qualsiasi piattaforma.
ms.date: 12/06/2018
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
ms.openlocfilehash: b9c8f5193e55d86ea4ff5e4d68fb7a66a1044d2e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062884"
---
# <a name="consume-azure-services-using-the-azure-sdk-for-python"></a>Usare i servizi di Azure con Azure SDK per Python

Azure SDK per Python semplifica l'utilizzo e la gestione dei servizi di Microsoft Azure dalle applicazioni in esecuzione in Windows, MacOS e Linux.

## <a name="installation"></a>Installazione

Azure SDK può essere installato da [Python Package Index](https://pypi.python.org/pypi/azure) (Indice dei pacchetti Python).

Installare la **versione stabile più recente** che supporta Python 2.7 e 3.x, come indicato di seguito:

```command
pip install azure
```

È anche possibile seguire le indicazioni in [Installazione di Python e dell'SDK](https://docs.microsoft.com/azure/python-how-to-install/) nella documentazione di Azure.

## <a name="documentation"></a>Documentazione

Anche nella sezione [Azure SDK per Python del Centro per sviluppatori Python](https://docs.microsoft.com/python/azure/?view=azure-python) sono disponibili numerose risorse utili, incluse alcune esercitazioni:

- [Creazione di app Web in Servizio app di Azure in Linux](/azure/app-service/containers/quickstart-python).
- [Archiviazione - BLOB](/azure/storage/blobs/storage-quickstart-blobs-python)
- [Archiviazione - Tabelle](/azure/cosmos-db/table-storage-how-to-use-python)
- [Archiviazione - Code](/azure/storage/storage-python-how-to-use-queue-storage)
- [Azure Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- [Code del bus di servizio](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Argomenti e sottoscrizioni del bus di servizio con Python](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Gestione dei servizi](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Per le API pubbliche senza documentazione, gli unit test nel [repository GitHub dell'SDK](https://github.com/Azure/azure-sdk-for-python) sono una buona fonte di informazioni:

- [Unit test per l'archiviazione](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Unit test per il bus di servizio](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Unit test per la gestione dei servizi](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)

## <a name="support"></a>Supporto

Il repository GitHub per l'SDK si trova in [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

Per qualsiasi problema o domanda relativi all'uso dell'SDK, [registrare i problemi nel repository](https://github.com/Azure/azure-sdk-for-python/issues).
