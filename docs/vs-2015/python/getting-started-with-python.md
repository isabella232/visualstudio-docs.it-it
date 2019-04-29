---
title: Introduzione a Python | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 9c18ae2731d92e6d128d13e7687bac77ae76dc8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575650"
---
# <a name="getting-started-with-python"></a>Introduzione a Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Python Tools for Visual Studio (PTVS), è disponibile gratuitamente, [open source](https://github.com/Microsoft/ptvs) plug-in per Visual Studio che verificano un sviluppo Python avanzato.  
  
## <a name="python-the-language"></a>Linguaggio Python
  
Python è un linguaggio di programmazione più diffusi che viene usato da molte università, data Scientist, autori di app, sviluppatori e gli sviluppatori professionisti, lavorando per le applicazioni, siti web e servizi cloud.

Come linguaggio di programmazione, Python è:
  
- Attendibile.
- In genere è utile per lo scripting di programmi rapidi, app script, le app desktop, server web, servizi web e calcolo scientifico.
- Facile da imparare e con un buon design in modo da semplificare la scrittura di codice. Molte università lo usano per i corsi di programmazione introduttivi.
- Flessibile, che supportano gli stili di programmazione imperativi, funzionali e orientata agli oggetti.
- Gratuito e open source.
- Funziona bene con tutti i principali sistemi operativi.  
- Supportato da numerose librerie gratuite, utili e ben progettate.  
- Supportato da un numero elevato di documentazione, esempi e una community di sviluppatori.  

Per altre informazioni sul linguaggio, iniziare con [Python per principianti](https://www.python.org/about/gettingstarted/) in python.org.

Per installare Python, visitare [ https://www.python.org/download/ ](https://www.python.org/download/).

## <a name="python-tools-for-visual-studio"></a>Python Tools per Visual Studio
  
Gli strumenti Python per Visual Studio, che è possibile installare dalla [visualstudio.com](https://www.visualstudio.com/explore/python-vs), offrono le funzionalità seguenti:  
  
- Supporto per più interpreti: varie versioni di CPython, IronPython e IPython  
- Sistema di progetto che rileva in modo implicito una struttura di cartelle del codice Python e che consente anche un controllo esplicito per distinguere chiaramente i vari elementi di codice dell'app, codice di test, pagine Web, JavaScript, script di compilazione e così via.  
- Modelli di progetto per console, Web, Azure, analisi scientifica dei dati e altri tipi di progetti.    
- Azure SDK per Python (vedere sotto)    
- Funzionalità avanzate di modifica e comprensione del codice, tra cui colorazione della sintassi, completamento automatico in tutto il codice, librerie, supporto di firme, visualizzazione delle classi, accesso alle definizioni, opzione per trovare tutti i riferimenti, refactoring e così via.    
- Una finestra interattiva (REPL)
- IPython con visualizzazioni dei dati.
- Supporto per IronPython e .NET/WPF.    
- Debug avanzato senza un progetto Visual Studio, collegamento a un eseguibile esistente, debug in modalità mista, debug remoto per Linux/Windows/Mac e debug all'interno della finestra interattiva.   
- Strumenti di profilatura.  
- Strumenti di test.  
  
Per acquisire familiarità, usare le risorse seguenti:

- [Guida all'installazione](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Brevi video introduttivi e dettagliati](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- Installazione e le funzionalità demo (27 minuti)] (https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Documentazione](https://github.com/Microsoft/PTVS/wiki)  

Si noti che Visual Studio non attualmente fornisce i mezzi per creare un file eseguibile autonomo usando Python, che significa essenzialmente un programma con un interprete Python incorporato. Tuttavia, esistono diversi metodi all'interno della community di Python per eseguire questa operazione, come descritto in [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython può anche essere incorporato in un'applicazione nativa, come descritto nel post del blog, [Using CPython's Embeddable Zip File](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/) (Uso del file ZIP incorporabile di CPython).
  
## <a name="building-ui-with-python"></a>Creazione dell'interfaccia utente con Python  

L'offerta principale per la creazione di un'interfaccia utente di Python è il [progetto Qt](https://www.qt.io/qt-for-application-development/), con le associazioni per Python note come [PySide (l'associazione ufficiale)](http://wiki.qt.io/PySide) (vedere anche [PySide downloads](https://download.qt.io/official_releases/pyside/.)) e [PyQt](https://wiki.python.org/moin/PyQt). Attualmente il supporto di Python in Visual Studio non include strumenti specifici per lo sviluppo dell'interfaccia utente.

## <a name="azure-sdk-for-python"></a>Azure SDK per Python
  
Azure SDK per Python, che supporta Windows, Mac e Linux, semplifica l'uso e la gestione dei servizi di Microsoft Azure. Per informazioni dettagliate, fare riferimento alle risorse seguenti: 

- Per installare l'SDK, usare l'[indice dei pacchetti Python](https://pypi.python.org/pypi/azure) o consultare la pagina sull'[installazione di Python e dell'SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) nella documentazione di Azure. 
- Il [centro per sviluppatori Azure SDK per Python](https://azure.microsoft.com/develop/python/) offre moltissime guide dall'installazione alla documentazione con esercitazioni.  Seguono alcune delle principali caratteristiche:  
- Guide pratiche:
  - [BLOB di archiviazione](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Coda di archiviazione](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Tabella di archiviazione](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Come usare le code del bus di servizio](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Come usare gli argomenti e le sottoscrizioni del bus di servizio](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Gestione dei servizi](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Calcolo scientifico

Oltre a tutte le librerie del data scientist Python, Python Tools per Visual Studio supporta IPython e IPython Notebook, che possono essere ospitati in Azure.

È consigliabile ottenere IPython e le librerie di calcolo scientifico (matplotlib, scipy, numpy e così via) dalla [University of California, Irvine](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>Vedere anche  

[Introduzione a PTVS: Impostazione di Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[Introduzione a PTVS: Avviare la codifica (progetti)](../python/getting-started-with-ptvs-start-coding-projects.md)
[Introduzione a PTVS: Modifica del codice](../python/getting-started-with-ptvs-editing-code.md)
[Introduzione a PTVS: Debugging](../python/getting-started-with-ptvs-debugging.md)
[Introduzione a PTVS: Python interattivo](../python/getting-started-with-ptvs-interactive-python.md)
[Introduzione a PTVS: Creazione di un sito Web in Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
