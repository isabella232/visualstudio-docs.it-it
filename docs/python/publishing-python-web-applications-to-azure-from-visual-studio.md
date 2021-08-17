---
title: Pubblicare un'app Python in Servizio app di Azure
description: Opzioni per la pubblicazione di un'app Python in Servizio app di Azure, inclusi distribuzione GIT e contenitori per Linux, e per la distribuzione in IIS.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f8338ea3810c45758029694fd3725e0ecf924b01
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027305"
---
# <a name="publish-to-azure-app-service"></a>Eseguire la pubblicazione nel servizio app di Azure

Al momento, Python è supportato in Servizio app di Azure per Linux ed è possibile pubblicare app usando la [distribuzione Git](#publish-to-app-service-on-linux-using-git-deploy) e i [contenitori](#publish-to-app-service-on-linux-using-containers), come descritto in questo articolo.

> [!Note]
> Il supporto di Python in Servizio app di Azure per Windows è ufficialmente deprecato. Di conseguenza, il comando **Pubblica** in Visual Studio è ufficialmente supportato solo per una [destinazione IIS](#publish-to-iis) e il debug remoto in Servizio app di Azure non è più supportato ufficialmente.
>
> Tuttavia, le funzionalità di [pubblicazione nel servizio app in Windows](publish-to-app-service-windows.md) continuano a funzionare per il momento, in quanto le estensioni Python per il servizio app in Windows rimangono disponibili, anche se non vengono aggiornate e non è disponibile il supporto.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Eseguire la pubblicazione nel servizio app in Linux tramite la distribuzione Git

La distribuzione Git connette un servizio app in Linux a un ramo specifico di un repository Git. Il commit del codice in tale ramo comporta la distribuzione automatica nel servizio app e il servizio app installa automaticamente le dipendenze elencate in *requirements.txt*. In questo caso, il servizio app in Linux esegue il codice in un'immagine del contenitore preconfigurata che usa il server Web Gunicorn. Al momento, questo servizio è disponibile in anteprima e non è supportato per l'uso in ambienti di produzione.

Per altre informazioni, vedere gli articoli seguenti nella documentazione di Azure:

- [Guida introduttiva: Creare un'app Web Python nel servizio app](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) fornisce un breve procedura dettagliata del processo di distribuzione Git usando una semplice app Flask e la distribuzione da un repository Git locale.
- [Come configurare Python](/azure/app-service/containers/how-to-configure-python) descrive le caratteristiche del servizio app nel contenitore Linux e come personalizzare il comando di avvio Gunicorn per l'app.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Eseguire la pubblicazione nel servizio app in Linux tramite contenitori

Invece di usare il contenitore predefinito con il servizio app in Linux, è possibile fornire un contenitore personalizzato. Questa opzione consente di scegliere quali server Web usare e di personalizzare il comportamento del contenitore.

Ci sono due opzioni per creare e gestire i contenitori ed eseguirne il push:

- Usare Visual Studio Code e l'estensione Docker, come descritto in [Deploy Python using Docker Containers](https://code.visualstudio.com/docs/python/tutorial-deploy-containers) (Distribuire Python usando contenitori Docker). Anche se non si usa Visual Studio Code, l'articolo fornisce informazioni dettagliate utili per la creazione di immagini dei contenitori per le app Flask e Django usando i server Web nginx e uwsgi pronti per la produzione. È quindi possibile distribuire lo stesso contenitore usando l'interfaccia della riga di comando di Azure.

- Usare la riga di comando e l'interfaccia della riga di comando di Azure, come descritto in [Usare un'immagine Docker personalizzata](/azure/app-service/containers/tutorial-custom-docker-image) nella documentazione di Azure. Questa guida tuttavia è generica e non specifica di Python.

## <a name="publish-to-iis"></a>Eseguire la pubblicazione in IIS

Da Visual Studio, è possibile eseguire la pubblicazione in una macchina virtuale Windows o in un altro computer che supporta IIS usando il comando **Pubblica**. Quando si usa IIS, assicurarsi di creare o modificare un file *web.config* nell'app che indichi a IIS dove trovare l'interprete Python. Per altre informazioni, vedere [Configurare app Web per IIS](configure-web-apps-for-iis-windows.md).
