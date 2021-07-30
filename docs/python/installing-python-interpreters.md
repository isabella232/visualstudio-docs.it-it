---
title: Selezionare e installare interpreti Python
description: Elenco completo degli interpreti Python supportati in Visual Studio con brevi istruzioni su dove trovare i relativi programmi di installazione.
ms.date: 07/28/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 239a8f40aa669aa60853405621a0b335aabdcb3c
ms.sourcegitcommit: 879ba768364f3bfdaeb9004f740478489ab15c3a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2021
ms.locfileid: "114796164"
---
# <a name="install-python-interpreters"></a>Installare interpreti Python

Per impostazione predefinita, l'installazione del carico di lavoro di sviluppo Python in Visual Studio 2017 e versioni successive installa anche Python 3 (a 64 bit). È facoltativamente possibile scegliere di installare le versioni a 32 e 64 bit di Python 2 e Python 3, insieme a Miniconda (Visual Studio 2019) o Anaconda 2/Anaconda 3 (Visual Studio 2017), come descritto in [Installazione](installing-python-support-in-visual-studio.md).

::: moniker range=">=vs-2019"
In alternativa, è possibile installare gli interpreti Python standard dalla finestra di dialogo **Aggiungi ambiente**. Selezionare il comando **Aggiungi ambiente** nella finestra **Ambienti Python** o sulla barra degli strumenti Python, selezionare la scheda **Installazione di Python**, indicare quali interpreti installare e selezionare **Installa**.
::: moniker-end

È anche possibile installare manualmente uno qualsiasi degli interpreti elencati nella tabella riportata di seguito al di fuori del programma di installazione di Visual Studio. Ad esempio, se Anaconda 3 è stato installato prima di installare Visual Studio, non è necessario eseguire nuovamente l'installazione tramite il programma di installazione di Visual Studio. È anche possibile installare un interprete manualmente se, ad esempio, è disponibile una versione più recente che ancora non è visualizzata nel programma di installazione di Visual Studio.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio supporta Python versione 2.7, nonché dalla versione 3.5 alla 3.7. Sebbene sia possibile usare Visual Studio per modificare anche il codice scritto in altre versioni di Python, queste non sono ufficialmente supportate e alcune funzionalità, tra cui IntelliSense e il debug, potrebbero non funzionare.
::: moniker-end

Per **Visual Studio 2015 e versioni precedenti** è necessario installare manualmente uno degli interpreti.

> [!Note]
> Anche Visual Studio offre di installare la distribuzione Anaconda, l'uso della distribuzione e dei pacchetti aggiuntivi dal repository Anaconda è vincolato dalle Condizioni per l'utilizzo [del servizio Anaconda.](https://www.anaconda.com/terms-of-service) Queste condizioni possono richiedere ad alcune organizzazioni di pagare Anaconda per una licenza commerciale oppure configurare gli strumenti per accedere a un repository alternativo. Per altre informazioni, vedere la documentazione sui canali [Conda.](https://docs.conda.io/projects/conda/en/latest/user-guide/concepts/channels.html)

Visual Studio, in tutte le versioni, rileva automaticamente ogni interprete Python installato e il relativo ambiente controllando il Registro di sistema secondo quanto descritto in [PEP 514 - Python registration in the Windows registry](https://www.python.org/dev/peps/pep-0514/) (PEP 514 - Registrazione di Python nel Registro di sistema di Windows). Le installazioni di Python in genere si trovano in **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32 bit) e **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64 bit) e quindi all'interno di nodi per la distribuzione, ad esempio **PythonCore** (CPython) e **ContinuumAnalytics** (Anaconda).

Se Visual Studio non rileva un ambiente installato, vedere [Identificare manualmente un ambiente esistente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Visual Studio visualizza tutti gli ambienti noti nella finestra [**Ambienti Python**](managing-python-environments-in-visual-studio.md#the-python-environments-window) e rileva automaticamente gli aggiornamenti per gli interpreti esistenti.

| Interprete | Descrizione |
| --- | --- |
| [CPython](https://www.python.org/) | Interprete "nativo" più comunemente usato, disponibile nelle versioni a 32 bit e a 64 bit (consigliata la versione a 32 bit). Include le funzionalità più recenti del linguaggio e offre la massima compatibilità con i pacchetti Python, nonché il supporto completo per il debug e l'interoperabilità con [IPython](https://ipython.org/). Vedere anche: [Should I use Python 2 or Python 3?](https://wiki.python.org/moin/Python2orPython3) (Differenze tra Python 2 e Python 3). Si noti che Visual Studio 2015 e versioni precedenti non supportano Python 3.6+ e possono segnalare errori come **Unsupported python version 3.6** (Versione 3.6 di Python non supportata). Usare Python 3.5 o versioni precedenti. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Implementazione .NET di Python, disponibile nelle versioni a 32 bit e a 64 bit, che offre interoperabilità con C#/F# e Visual Basic, accesso alle API .NET, debug Python standard (ma non debug C++ in modalità mista) e debug IronPython/C# in modalità mista. IronPython non supporta però gli ambienti virtuali. |
| [Anaconda](https://anaconda.com) | Piattaforma Open Data Science basata su Python che include la versione più recente di CPython e la maggior parte dei pacchetti difficili da installare. È la piattaforma consigliata se non è possibile sceglierne una diversa. |
| [PyPy](https://www.pypy.org/) | Implementazione JIT di traccia ad alte prestazioni di Python, ideale per applicazioni a esecuzione prolungata e situazioni in cui si verificano problemi di prestazioni, ma non si riesce a trovare altre soluzioni. Funziona con Visual Studio, ma offre supporto limitato per le funzionalità avanzate di debug. |
| [Jython](https://www.jython.org/) | Implementazione di Python in Java Virtual Machine (JVM). Analogamente a IronPython, il codice in esecuzione in Jython può interagire con librerie e classi Java, ma potrebbe non essere in grado di usare molte librerie destinate a CPython. Funziona con Visual Studio, ma offre supporto limitato per le funzionalità avanzate di debug. |

Se si intende offrire nuove forme di rilevamento per gli ambienti Python, vedere [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (Rilevamento degli ambienti PTVS) su github.com.

## <a name="move-an-interpreter"></a>Spostare un interprete

Se si sposta un interprete esistente in una nuova posizione nel file system, Visual Studio non rileva automaticamente la modifica.

- Se il percorso dell'interprete è stato specificato in origine tramite la finestra **Ambienti Python**, modificarne l'ambiente tramite la scheda **Configura** in tale finestra per identificare il nuovo percorso. Vedere [Identificare manualmente un ambiente esistente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- Se l'interprete è stato installato usando un programma di installazione, seguire questa procedura per reinstallare l'interprete nel nuovo percorso:

  1. Ripristinare l'interprete Python nel percorso originale.
  2. Disinstallare l'interprete usando il relativo programma di installazione, in modo da cancellare le voci del Registro di sistema.
  3. Reinstallare l'interprete nel percorso desiderato.
  4. Riavviare Visual Studio, in modo che rilevi automaticamente il nuovo percorso, al posto del precedente.

Seguendo questa procedura si assicura il corretto aggiornamento delle voci del Registro di sistema che identificano il percorso dell'interprete, usato da Visual Studio. L'uso di un programma di installazione consente anche di gestire eventuali altri effetti collaterali.

## <a name="see-also"></a>Vedere anche

- [Gestire gli ambienti Python](managing-python-environments-in-visual-studio.md)
- [Selezionare un interprete per un progetto](selecting-a-python-environment-for-a-project.md)
- [Usare requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Percorsi di ricerca](search-paths.md)
- [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)
