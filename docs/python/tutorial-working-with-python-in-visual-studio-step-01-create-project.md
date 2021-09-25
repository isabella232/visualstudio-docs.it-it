---
title: Esercitazione sull'uso di Python in Visual Studio, passaggio 1, creare un progetto
titleSuffix: ''
description: Panoramica e passaggio 1 della procedura dettagliata di base delle funzionalità di Python in Visual Studio, inclusi i prerequisiti e la creazione di un nuovo progetto Python.
ms.date: 09/14/2021
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: vs-acquisition
ms.workload:
- python
- data-science
ms.openlocfilehash: 50894927535010efcee70a079f935176590ba653
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429312"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Esercitazione: Uso di Python in Visual Studio

Python è un linguaggio di programmazione diffuso, affidabile, flessibile, facile da apprendere e gratuito da usare in tutti i sistemi operativi. Python è supportato sia da una solida community di sviluppatori che da molte librerie gratuite. Il linguaggio supporta tutti i tipi di sviluppo, tra cui applicazioni Web, servizi Web, app desktop, scripting e scientific computing. Molte università, scienziati, sviluppatori occasionali e sviluppatori professionisti usano Python.

Visual Studio offre un supporto dei linguaggi di prima classe per Python. Completare le fasi dell'esercitazione indicate di seguito:

- [Passaggio 0: Installazione](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Passaggio 1: Creare un progetto di Python (questo articolo)](#step-1-create-a-new-python-project)
- [Passaggio 2: Scrivere ed eseguire codice per visualizzare Visual Studio IntelliSense al lavoro](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Passaggio 3: Creare altro codice nella finestra INTERACTIVE REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Passaggio4: Eseguire un programma nel debugger di Visual Studio.](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Passaggio 5: Installare pacchetti e gestire gli ambienti Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Passaggio 6: Utilizzo di Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>Passaggio 1: Creare un nuovo progetto Python

Un *progetto* è il Visual Studio gestisce tutti i file che si uniscono per produrre una singola applicazione. I file dell'applicazione includono codice sorgente, risorse e configurazioni. Un progetto formalizza e mantiene le relazioni tra tutti i file del progetto. Il progetto gestisce anche le risorse esterne condivise tra più progetti. Un progetto consente all'applicazione di espandersi e crescere senza sforzo. L'uso dei progetti è molto più semplice rispetto alla gestione manuale delle relazioni in cartelle, script, file di testo e memoria ad hoc.

Questa esercitazione inizia con un semplice progetto contenente un singolo file di codice vuoto.

::: moniker range="<=vs-2019"
1. In Visual Studio selezionare **File** Nuovo Project ( CTRL MAIUSC N ), che apre la finestra di  >    >    +  +  **dialogo Project** nuovo file. Qui è possibile esplorare i modelli tra i diversi linguaggi, quindi selezionarne uno per il progetto e specificare dove inserire i file Visual Studio.

1. Per visualizzare i modelli Python, selezionare  >  **Python** installato a sinistra o cercare "Python". La ricerca è un ottimo modo per trovare un modello quando non si ricorda la posizione nell'albero dei linguaggi.

    ![Screenshot che mostra la finestra di dialogo Crea un nuovo progetto con modelli di progetto Python.](media/vs-getting-started-python-01-new-project.png)

    Il supporto di Python Visual Studio diversi modelli di progetto, tra cui applicazioni Web che usano i framework Bottle, Flask e Django. Per gli scopi di questa procedura dettagliata, tuttavia, si inizierà con un progetto vuoto.

1. Selezionare il modello **Applicazione Python**, specificare un nome per il progetto e selezionare **OK**.

1. Dopo qualche secondo, Visual Studio visualizza la struttura del progetto nella finestra **Esplora soluzioni** (1). Il file di codice predefinito è aperto nell'editor (2). Viene **visualizzata** anche la finestra Proprietà (3) per visualizzare informazioni aggiuntive per qualsiasi elemento selezionato **in** Esplora soluzioni , inclusa la posizione esatta su disco.

    ![Screenshot che mostra il nuovo progetto aperto in Visual Studio.](media/vs-getting-started-python-02-windows.png)

1. È necessario acquisire familiarità con Esplora soluzioni **,** che è la posizione in cui si esplorano file e cartelle nel progetto.

    ![Screenshot della Esplora soluzioni espansa per visualizzare le funzionalità.](media/vs-getting-started-python-03-solution-explorer.png)

    (1) Il progetto è evidenziato in grassetto, usando il nome specificato nella finestra **di dialogo Project** nuova pagina. Sul disco questo progetto è rappresentato nella cartella del progetto da un file con estensione *.pyproj*.

    (2) Al primo livello è presente una *soluzione* che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata da un file *sln* su disco, è un contenitore per uno o più progetti correlati. Ad esempio, se si scrive un'estensione C++ per l'applicazione Python, tale progetto C++ potrebbe essere nella stessa soluzione. La soluzione può contenere anche un progetto per un servizio web, insieme ai progetti per i programmi di test dedicati.

    (3) Nel progetto si possono vedere i file di origine, in questo caso un solo file con estensione *py*. La selezione di un file ne visualizza le proprietà nella **finestra** Proprietà. Facendo doppio clic su un file, questo verrà aperto nel modo più appropriato.

    (4) Il nodo **Ambienti Python** è visualizzabile anche dal progetto. Attraverso l'espansione è possibile visualizzare gli interpreti Python disponibili. Espandere un nodo dell'interprete per visualizzare le librerie installate in tale ambiente (5).

    Fare clic con il pulsante destro del mouse su qualsiasi **nodo o elemento Esplora soluzioni** per accedere a un menu di comandi applicabili. Ad esempio, il comando **Rinomina** consente di modificare il nome di un nodo o di un elemento, inclusi il progetto e la soluzione.

::: moniker-end

::: moniker range=">=vs-2022"
1. In Visual Studio selezionare **File**  >  **nuovo**  >  **Project** o premere CTRL  + **MAIUSC** + **N**. Viene **visualizzata la schermata Crea un nuovo** progetto, in cui è possibile cercare ed esplorare i modelli in lingue diverse.
   
1. Per visualizzare i modelli Python, cercare *python*. La ricerca è un ottimo modo per trovare un modello quando non è possibile ricordarne la posizione nell'albero delle lingue.
   
   ![Screenshot che mostra la finestra di dialogo Crea un nuovo progetto con modelli di progetto Python.](media/vs-2022/getting-started-python-new-project.png)
   
   Il supporto di Python Visual Studio diversi modelli di progetto, ad esempio applicazioni Web nei framework Bottle, Flask e Django. Per questa esercitazione, iniziare con un progetto vuoto.
   
1. Selezionare il **modello PythonConsoleApp** e selezionare **Avanti.**
   
1. Nella schermata **Configura il nuovo progetto** specificare un nome e un percorso di file per il progetto e quindi selezionare **Crea**.
   
   Il nuovo progetto viene aperto in Visual Studio.
   
   - La Visual Studio **Esplora soluzioni** mostra la struttura del progetto **(1).**
   - Il file di codice predefinito viene aperto nell'editor **(2)**.
   - Nella **finestra** Proprietà vengono visualizzate altre informazioni per l'elemento selezionato in **Esplora soluzioni**, inclusa la posizione esatta su disco **(3).**
   
   ![Screenshot che mostra il nuovo progetto aperto in Visual Studio.](media/vs-2022/getting-started-python-windows.png)
   
1. Acquisire familiarità con **Esplora soluzioni**, in cui è possibile esplorare file e cartelle nel progetto.
   
   ![Screenshot della Esplora soluzioni espansa per visualizzare le funzionalità.](media/vs-2022/getting-started-python-solution-explorer.png)
   
   - Al livello superiore è la *soluzione*, che per impostazione predefinita ha lo stesso nome del progetto **(1).**
     
     Una soluzione, che viene visualizzata come file con estensione *sln* su disco, è un contenitore per uno o più progetti correlati. Ad esempio, se si scrive un'estensione C++ per l'applicazione Python, tale progetto C++ può essere nella stessa soluzione. La soluzione può contenere anche un progetto per un servizio Web e progetti per programmi di test dedicati.
   
   - Il progetto, con il nome specificato nella finestra **di** dialogo Crea un nuovo progetto, viene visualizzato in grassetto **(2)**. Su disco, il progetto è un file *con estensione pyproj* nella cartella del progetto.
   
   - Nel progetto sono presenti file di origine, in questo caso solo un singolo file con estensione *py* **(3)**. La selezione di un file ne visualizza le proprietà nella **finestra** Proprietà. Facendo doppio clic su un file, questo verrà aperto nel modo più appropriato.
   
   - Nel progetto è anche in corso **il nodo Ambienti Python** **(4).** Espandere il nodo per visualizzare gli interpreti Python disponibili.
   
   - Espandere un nodo interprete per visualizzare le librerie installate in tale ambiente **(5).**
   
   Fare clic con il pulsante destro del mouse su un **nodo o un** elemento Esplora soluzioni per visualizzare un menu di scelta rapida dei comandi applicabili. Ad esempio, **Rinomina** consente di modificare il nome di un nodo o di un elemento, inclusi il progetto e la soluzione.
::: moniker-end

## <a name="next-step"></a>Passaggio successivo

> [!div class="nextstepaction"]
> [scrivere ed eseguire codice](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Approfondimento

- [Progetti Python in Visual Studio](managing-python-projects-in-visual-studio.md).
- [Informazioni sul linguaggio Python in python.org](https://www.python.org)
- [Python per utenti meno esperti](https://www.python.org/about/gettingstarted/) (python.org)
