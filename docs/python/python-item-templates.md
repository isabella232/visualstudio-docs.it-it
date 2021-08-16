---
title: Modelli di elementi per progetti Python
description: Elenco di riferimento di modelli di elementi per progetti Python disponibili nella finestra di dialogo Aggiungi > Nuovo elemento in Visual Studio.
ms.date: 12/06/2018
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7effabe9323611685ef392820f4eb56f183a41d17245966b662ca7d1a2d3b63a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367740"
---
# <a name="python-item-templates"></a>Modelli di elementi Python

I modelli di elemento sono disponibili nei progetti Python tramite il comando di menu **Project** Aggiungi nuovo elemento o il comando Aggiungi nuovo elemento nel menu di scelta  >   rapida in   >   **Esplora soluzioni**.

![Finestra di dialogo Aggiungi nuovo elemento](media/project-item-templates.png)

Usando il nome specificato per l'elemento, un modello in genere crea uno o più file e cartelle all'interno della cartella attualmente selezionata nel progetto (facendo clic con il pulsante destro del mouse su una cartella per visualizzare il menu di scelta rapida la cartella viene selezionata automaticamente). Un elemento aggiunto viene incluso nel progetto di Visual Studio e visualizzato in **Esplora soluzioni**.

La tabella seguente illustra brevemente l'effetto di ogni modello di elemento in un progetto Python:

| Modello | Oggetti creati dal modello |
| --- | --- |
| **File Python vuoto** | File vuoto con estensione *.py*. |
| **Classe Python** | File *.py* contenente una singola definizione di classe Python vuota. |
| **Pacchetto Python** | Cartella che contiene un file *\_ \_ con estensione \_ \_ py init.* |
| **Unit test Python** | File *.py* con un singolo unit test basato sul framework `unittest`, insieme a una chiamata a `unittest.main()` per eseguire i test nel file. |
| **Pagina HTML** | File *.html* con una struttura di pagina semplice composta da un elemento `<head>` e un elemento `<body>`. |
| **JavaScript** | File *.js* vuoto. |
| **Foglio di stile** | File *.css* contenente uno stile vuoto per `body`. |
| **File di testo** | File *.txt* vuoto. |
| **App Django 1.9**<br/>**App Django 1.4** | Cartella con il nome dell'app, contenente i file principali per un'app Django, come illustrato in [Informazioni su Django in Visual Studio, passaggio 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) per Django 1.9. Per Django 1.4, la cartella *migrations*, il file *admin.py* e il file *apps.py* non sono inclusi. |
| **Finestra WPF IronPython** | Finestra WPF costituita da due file side-by-side: un file *.xaml* che definisce un oggetto `<Window>` con un elemento `<Grid>` vuoto e un file *.py* associato che carica il file XAML usando la libreria `wpf`. Usato in genere in un progetto creato tramite uno dei modelli di progetto IronPython. Vedere [Gestire progetti Python - Modelli di progetto](managing-python-projects-in-visual-studio.md#project-templates). |
| **File di supporto del ruolo Web** | Cartella *bin* nella radice del progetto (indipendentemente dalla cartella selezionata nel progetto). La cartella contiene uno script di distribuzione predefinito e un file *web.config* per i ruoli Web del servizio cloud di Azure. Il modello include anche un file *readme.html* che illustra i dettagli. |
| **File di supporto del ruolo di lavoro** | Cartella *bin* nella radice del progetto (indipendentemente dalla cartella selezionata nel progetto). La cartella contiene uno script di distribuzione e avvio predefinito e un file *web.config* per i ruoli di lavoro del servizio cloud di Azure. Il modello include anche un file *readme.html* che illustra i dettagli. |
| **web.config di Azure (FastCGI)** | File *web.config* che contiene le voci per le app in cui viene usato un oggetto [WSGI](https://wsgi.readthedocs.io/en/latest/) per gestire le connessioni in ingresso. Questo file viene in genere distribuito nella radice di un server Web che esegue IIS. Per altre informazioni, vedere [Configurare un'app per IIS](configure-web-apps-for-iis-windows.md). |
| **web.config di Azure (HttpPlatformHandler)** | File *web.config* che contiene le voci per le app in ascolto delle connessioni in ingresso su un socket. Questo file viene in genere distribuito nella radice di un server Web che esegue IIS, ad esempio Servizio app di Azure. Per altre informazioni, vedere [Configurare un'app per IIS](configure-web-apps-for-iis-windows.md). |
| **web.config di file statici di Azure** | File *web.config* aggiunto in genere a una cartella *static* o a un'altra cartella contenente elementi statici, per disabilitare la gestione di Python per tale cartella. Questo file config funziona in combinazione con uno dei file config precedenti, FastCGI o HttpPlatformHandler. Per altre informazioni, vedere [Configurare un'app per IIS](configure-web-apps-for-iis-windows.md). |
| **web.config di debug remoto di Azure** | Deprecato (usato per il debug remoto in Servizio app di Azure per Windows, che non è più supportato). |

## <a name="see-also"></a>Vedi anche

- [Gestire progetti Python - Modelli di progetto](managing-python-projects-in-visual-studio.md#project-templates)
- [Modelli di progetto applicazione Web di Python](python-web-application-project-templates.md)
- [Eseguire la pubblicazione nel servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
