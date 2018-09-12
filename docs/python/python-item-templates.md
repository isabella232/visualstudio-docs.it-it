---
title: Modelli di elementi per progetti Python
description: Elenco di riferimento di modelli di elementi per progetti Python disponibili nella finestra di dialogo Aggiungi > Nuovo elemento in Visual Studio.
ms.date: 09/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 8319c99e5de12ce1c09a2c20fc5cf1b132f34092
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776035"
---
# <a name="python-item-templates"></a>Modelli di elementi Python

I modelli di elementi sono disponibili nei progetti Python tramite il comando di menu **Progetto** > **Aggiungi nuovo elemento** oppure tramite il comando **Aggiungi** > **Nuovo elemento** del menu di scelta rapida in **Esplora soluzioni**.

![Finestra di dialogo Aggiungi nuovo elemento](media/project-item-templates.png)

Usando il nome specificato per l'elemento, un modello in genere crea uno o più file e cartelle all'interno della cartella attualmente selezionata nel progetto (facendo clic con il pulsante destro del mouse su una cartella per visualizzare il menu di scelta rapida la cartella viene selezionata automaticamente). Un elemento aggiunto viene incluso nel progetto di Visual Studio e visualizzato in **Esplora soluzioni**.

La tabella seguente illustra brevemente l'effetto di ogni modello di elemento in un progetto Python:

| Modello | Oggetti creati dal modello |
| --- | --- |
| **File Python vuoto** | File vuoto con estensione *.py*. |
| **Classe Python** | File *.py* contenente una singola definizione di classe Python vuota. |
| **Pacchetto Python** | Cartella contenente un file *\_\_init\_\_.py*. |
| **Unit test Python** | File *.py* con un singolo unit test basato sul framework `unittest`, insieme a una chiamata a `unittest.main()` per eseguire i test nel file. |
| **Pagina HTML** | File *.html* con una struttura di pagina semplice composta da un elemento `<head>` e un elemento `<body>`. |
| **JavaScript** | File *.js* vuoto. |
| **Foglio di stile** | File *.css* contenente uno stile vuoto per `body`. |
| **File di testo** | File *.txt* vuoto. |
| **App Django 1.9**<br/>**App Django 1.4** | Cartella con il nome dell'app, contenente i file principali per un'app Django, come illustrato in [Informazioni su Django in Visual Studio, passaggio 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) per Django 1.9. Per Django 1.4, la cartella *migrations*, il file *admin.py* e il file *apps.py* non sono inclusi. |
| **Finestra WPF IronPython** | Finestra WPF costituita da due file side-by-side: un file *.xaml* che definisce un oggetto `<Window>` con un elemento `<Grid>` vuoto e un file *.py* associato che carica il file XAML usando la libreria `wpf`. Usato in genere in un progetto creato tramite uno dei modelli di progetto IronPython. Vedere [Gestire progetti Python - Modelli di progetto](managing-python-projects-in-visual-studio.md#project-templates). |
| **File di supporto del ruolo Web** | Cartella *bin* nella radice del progetto (indipendentemente dalla cartella selezionata nel progetto). La cartella contiene uno script di distribuzione predefinito e un file *web.config* per i ruoli Web del servizio cloud di Azure. Il modello include anche un file *readme.html* che illustra i dettagli. |
| **File di supporto del ruolo di lavoro** | Cartella *bin* nella radice del progetto (indipendentemente dalla cartella selezionata nel progetto). La cartella contiene uno script di distribuzione e avvio predefinito e un file *web.config* per i ruoli di lavoro del servizio cloud di Azure. Il modello include anche un file *readme.html* che illustra i dettagli. |
| **web.config di Azure (FastCGI)** | File *web.config* che contiene le voci per le app in cui viene usato un oggetto [WSGI](https://wsgi.readthedocs.io/en/latest/) per gestire le connessioni in ingresso. Questo file viene in genere distribuito nella radice di un server Web che esegue IIS, ad esempio Servizio app di Azure. Per altre informazioni, vedere [Eseguire la pubblicazione nel servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| **web.config di Azure (HttpPlatformHandler)** | File *web.config* che contiene le voci per le app in ascolto delle connessioni in ingresso su un socket. Questo file viene in genere distribuito nella radice di un server Web che esegue IIS, ad esempio Servizio app di Azure. Per altre informazioni, vedere [Eseguire la pubblicazione nel servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| **web.config di file statici di Azure** | File *web.config* aggiunto in genere a una cartella *static* o a un'altra cartella contenente elementi statici, per disabilitare la gestione di Python per tale cartella. Questo file config funziona in combinazione con uno dei file config precedenti, FastCGI o HttpPlatformHandler. Per altre informazioni, vedere [Eseguire la pubblicazione nel servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| **web.config di debug remoto di Azure** | File *web.config.debug* che consente il debug remoto tramite WebSockets, insieme a una libreria *Microsoft.PythonTools.WebRole.dll* e a una cartella *ptvsd* contenente i moduli da distribuire nel server per abilitare il debug remoto. In genere, si crea questo elemento nella stessa posizione del file *web.config*. Per altre informazioni, vedere [Debug remoto di codice Python in Azure](debugging-remote-python-code-on-azure.md). Vedere anche la nota seguente. |

> [!Note]
> Se si aggiunge il modello *web.config* di debug a un progetto e si intende usare il debug remoto di Python, è necessario pubblicare il sito nella configurazione **Debug**. Questa impostazione è diversa rispetto alla configurazione attiva corrente della soluzione ed è sempre contraddistinta dal valore predefinito **Versione**. Per cambiarla, aprire la scheda **Impostazioni** e usare la casella combinata **Configurazione** nella **Pubblicazione guidata**. Per altre informazioni sulla creazione e sulla distribuzione in App Web di Azure, vedere la [documentazione di Azure](https://azure.microsoft.com/develop/python/).
>
> ![Modifica della configurazione di pubblicazione](media/template-web-publish-config.png)

## <a name="see-also"></a>Vedere anche

- [Gestire progetti Python - Modelli di progetto](managing-python-projects-in-visual-studio.md#project-templates)
- [Modelli di progetto applicazione Web di Python](python-web-application-project-templates.md)
- [Eseguire la pubblicazione nel servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
