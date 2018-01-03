---
title: Python in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: hero-article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: 8cd00fe33cf463227dd09f93047350a96cee3b92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-python-in-visual-studio"></a>Uso di Python in Visual Studio

Python è un linguaggio di programmazione molto diffuso affidabile, flessibile, facile da imparare, il cui uso è gratuito in tutti i sistemi operativi e supportato sia da un'attiva community di sviluppatori che da numerose librerie gratuite. Python supporta tutte le modalità di sviluppo, tra cui applicazioni Web, servizi Web, app desktop, script e calcolo scientifico. Viene usato in molte università, nonché da scienziati, sviluppatori professionisti e non professionisti. Per altre informazioni sul linguaggio, vedere [python.org](https://www.python.org) e [Python for Beginners](https://www.python.org/about/gettingstarted/) (Python per principianti).

Visual Studio in Windows offre supporto [open source](https://github.com/Microsoft/ptvs) per il linguaggio Python attraverso lo sviluppo di Python e i carichi di lavoro Data Science (Visual Studio 2017), altre all'estensione gratuita Python Tools for Visual Studio (Visual Studio 2015 e versioni precedenti). Python non è attualmente supportato in Visual Studio per Mac, ma viene offerto su Mac e Linux tramite Visual Studio Code (vedere le [Domande e risposte](#questions-and-answers) riportate di seguito).

Per iniziare:

- Seguire le [istruzioni di installazione](installation.md) per configurare il carico di lavoro di Python.
- Eseguire una o più guide introduttive per creare un progetto. In caso di dubbi, iniziare con [Creare un progetto da un modello](quickstart-02-project-from-template.md).
- Seguire l'esercitazione [Uso di Python in Visual Studio](vs-tutorial-01-01.md) per un'esperienza completa.
- Usare quindi i collegamenti seguenti per esplorare le funzionalità correlate a Python e le funzionalità di Visual Studio.

| Funzionalità | Descrizione | Documentazione generale su Visual Studio | 
| --- | --- | --- |
| [Sistema del progetto di Visual Studio](python-projects.md) | Rileva in modo implicito una struttura di cartelle del codice Python consentendo anche un controllo esplicito per distinguere chiaramente i vari elementi di codice dell'app, codice di test, pagine Web, JavaScript, script di compilazione e così via. | [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Modelli di progetto](python-projects.md#project-templates) | Consente di creare rapidamente la struttura del progetto per console, Web, Azure, analisi scientifica dei dati e altri tipi di progetti. | [Modelli di Visual Studio](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| Supporto per più interpreti | Supporta diverse versioni di CPython e IronPython. | N/D |
| Supporto di IPython | Include il supporto per IPython/Jupyter in REPL per grafici inline, .NET e Windows Presentation Foundation (WPF). | N/D |
| [Modifica avanzata, IntelliSense e comprensione del codice](code-editing.md) | Colorazione della sintassi, completamento automatico in tutto il codice e in tutte le librerie, [formattazione del codice](code-formatting.md), supporto per la firma, visualizzazione delle classi, accesso alle definizioni, opzione per trovare tutti i riferimenti, frammenti di codice, [refactoring](code-refactoring.md), [PyLint](code-pylint.md) e altro ancora. | [Writing Code in the Code and Text Editor](../ide/writing-code-in-the-code-and-text-editor.md) (Scrittura di codice nell'Editor di testo e del codice) |
| [Finestra interattiva](interactive-repl.md) | Fornisce un'esperienza rapida di REPL per Python e consente di evidenziare facilmente una parte del codice e di inviarla alla finestra interattiva. | N/D |
| [Debug con funzionalità complete](debugging.md) | Il debug può essere eseguito con o senza un progetto di Visual Studio. Include la funzionalità per eseguire il debug di un eseguibile esistente, il [debug Python/C++ in modalità mista](debugging-mixed-mode.md), il [debug remoto](debugging-cross-platform-remote.md) in Linux/Windows/Mac, il [debug remoto in Azure](debugging-azure-remote.md) e il debug all'interno della finestra interattiva. | [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md) |
| [Strumenti di profilatura con funzionalità complete di creazione report](profiling.md) | Esamina l'uso del tempo nell'applicazione e consente di confrontare le prestazioni tra diverse esecuzioni della profilatura. | [Strumenti di profilatura](../profiling/profiling-tools.md) (non tutte le funzionalità di profilatura di Visual Studio sono disponibili per Python) |
| [Strumenti per unit test](unit-testing.md) | Consentono di individuare, eseguire e gestire i test in Esplora test di Visual Studio e di eseguire facilmente il debug di unit test. | [Eseguire unit test del codice](../test/unit-test-your-code.md) |

Il carico di lavoro Python include anche [Azure SDK per Python](azure-sdk-for-python.md), che semplifica l'uso dei servizi Azure da applicazioni Windows, Mac OS X e Linux.

Per un video introduttivo, vedere il breve corso [Python Tools for Visual Studio](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) su Microsoft Virtual Academy (circa 22 minuti in totale). 

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567]


## <a name="questions-and-answers"></a>Domande e risposte

**D. Il supporto di Python è disponibile in Visual Studio per Mac?**

Un  Non in questo momento, sebbene sia richiesto in [UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac/suggestions/18670291-python-tools-for-visual-studio-mac). La documentazione di [Visual Studio per Mac](https://docs.microsoft.com/visualstudio/mac/) identifica gli attuali tipi di sviluppo che supporta. Nel frattempo, Visual Studio Code su Windows, Mac e Linux [funziona bene con Python mediante le estensioni disponibili](https://code.visualstudio.com/docs/languages/python).

**D. Cosa si può usare per compilare un'interfaccia utente con Python?**

Un  La proposta migliore in questo campo è il [progetto Qt](https://www.qt.io/qt-for-application-development/), con le associazioni per Python note come [PySide (l'associazione ufficiale)](http://wiki.qt.io/PySide) (vedere anche [PySide downloads](https://download.qt.io/official_releases/pyside/.)) e [PyQt](https://wiki.python.org/moin/PyQt). Attualmente il supporto di Python in Visual Studio non include strumenti specifici per lo sviluppo dell'interfaccia utente.

**D. Un progetto Python può produrre un file eseguibile autonomo?**

Un  Python è in genere un linguaggio interpretato, con cui il codice viene eseguito su richiesta in un ambiente in grado di supportare Python, ad esempio Visual Studio e i server Web. Visual Studio attualmente non offre la possibilità di creare un file eseguibile autonomo, ovvero un programma con un interprete Python incorporato. Tuttavia, esistono diversi metodi all'interno della community di Python per creare file eseguibili, come descritto in [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython può anche essere incorporato in un'applicazione nativa, come descritto nel post del blog, [Using CPython's Embeddable Zip File](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/) (Uso del file ZIP incorporabile di CPython).

## <a name="features-matrix"></a>Matrice delle funzionalità

È possibile installare il supporto per Python nelle edizioni seguenti di Visual Studio, come descritto nella [guida all'installazione](installation.md):

- [Visual Studio 2017 (tutte le edizioni)](https://www.visualstudio.com/vs/)
- [Visual Studio 2015 (tutte le edizioni)] (https://www.visualstudio.com/it-it/downloads/visual-studio-2015-downloads-vs)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express per il Web, Update 2 o versione successiva
- Visual Studio 2013 Express per Desktop, Update 2 o versione successiva
- Visual Studio 2013 (Professional Edition o versione successiva)
- Visual Studio 2012 (Professional Edition o versione successiva)
- Visual Studio 2010 SP1 (Professional Edition o versione successiva; richiede .NET 4.5)

Funzionalità supportate in base alla versione e all'edizione di Visual Studio:

| Supporto per Python | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Gestione di più interpreti | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Rilevamento automatico degli interpreti più comuni | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Aggiunta di interpreti personalizzati | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Ambienti virtuali | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Installazione Pip/semplificata | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Sistema del progetto | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Nuovo progetto da codice esistente | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Mostra tutti i file | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Controllo del codice sorgente | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Integrazione con Git | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004;<sup>1</sup> | &#10007; |
<br/>

| Modifica | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Evidenziazione della sintassi | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Completamento automatico | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Supporto per la firma | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Informazioni rapide | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Visualizzatore oggetti/Visualizzazione classi | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Barra di navigazione | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Vai a definizione | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Passa a | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Trova tutti i riferimenti | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Rientro automatico | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Formattazione del codice | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactoring - Ridenominazione | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactoring - Estrazione del metodo | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactoring - Aggiunta/rimozione dell'importazione | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PyLint | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Finestra interattiva | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Finestra interattiva | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IPython con grafici inline | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Desktop | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Applicazione console/Windows | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| WPF IronPython (con finestra di progettazione XAML) | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Windows Form IronPython | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Web | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Progetto Web Django | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Progetto Web Bottle | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Progetto Web Flask | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Progetto Web generico | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Azure | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Distribuzione in sito Web | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| Distribuzione in ruolo Web | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Distribuzione in ruolo di lavoro | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Esecuzione nell'emulatore di Azure | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Debug remoto | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> | &#10007; |
| Collegamento a Esplora server | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
<br/>

| Modelli Django | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Debug | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Completamento automatico | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004; | &#10004; |
| Completamento automatico per CSS e JavaScript | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007; | &#10007; |
<br/>

| Debug | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Debug | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Debug senza progetto | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Debug - Collegamento a modifica | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Debug in modalità mista | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Debug remoto (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Finestra Debug interattivo | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Profilatura | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Profilatura | &#10004; | &#10004; | &#10004; | &#10007; | &#10007; | &#10004; | &#10004; | &#10004; |
<br/>

| Test | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Esplora test | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Esegui test | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Debug di test | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
<br/>

1. Il supporto GIT per Visual Studio 2012 è incluso nell'estensione Visual Studio Tools for Git, disponibile in [Visual Studio Gallery](http://visualstudiogallery.msdn.microsoft.com/abafc7d6-dcaa-40f4-8a5e-d6724bdb980c).

2. Per la distribuzione nel sito Web di Azure è necessario [Azure SDK per .NET 2.1 - Visual Studio 2010 SP1](http://go.microsoft.com/fwlink/?LinkId=313855).  Visual Studio 2010 non è supportato nelle versioni successive.

3. Per il supporto per il ruolo di lavoro e il ruolo Web di Azure è richiesto [Azure SDK per .NET 2.3 - Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=323511) o versione successiva.

4. Per il supporto per il ruolo di lavoro e il ruolo Web di Azure è richiesto [Azure SDK per .NET 2.3 - Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) o versione successiva.

5. L'editor di modelli Django in Visual Studio 2013 presenta alcuni problemi noti che vengono risolti installando l'Update 2.

6. Richiede Windows 8 o versione successiva. La finestra Collega a processo non è disponibile in Visual Studio 2013 Express per il Web, ma è comunque possibile eseguire il debug remoto del sito Web di Azure usando il comando Collega debugger (Python) in Esplora server. Il debug remoto richiede [Azure SDK per .NET 2.3 - Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) o versione successiva.

7. Richiede Windows 8 o versione successiva. Per il comando Collega debugger (Python) in Esplora server è richiesto [Azure SDK per .NET 2.3 - Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) o versione successiva.

8. Richiede Windows 8 o versione successiva.

## <a name="additional-resources"></a>Risorse aggiuntive

- [Writing Kinect games with Python using PyKinect](https://github.com/Microsoft/PTVS/wiki/PyKinect) (Uso di PyKinect per scrivere di giochi Kinect con Python) (wiki GitHub)
- [WFastCGI bridge between IIS and Python](https://pypi.python.org/pypi/wfastcgi) (Ponte WFastCGI tra IIS e Python) (python.org)
- [Corsi gratuiti per Python in Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Top Python Questions (Domande principali su Python) alla Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions)
