---
title: Gestire le dipendenze di pacchetto con un file requirements.txt
description: Un file requirements.txt descrive le dipendenze di un progetto. Se si riceve un progetto che contiene un file requirements.txt, è possibile installare facilmente tali dipendenze in un unico passaggio.
ms.date: 01/28/2019
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 2026c80141c29e14ca1d7c8f1f7e1bc5cecd2e32
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924344"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Gestire i pacchetti necessari con requirements.txt

Se si condivide un progetto con altri utenti usando un sistema di compilazione oppure si prevede di copiare il progetto in un'altra posizione dove deve essere ripristinato un ambiente, è necessario specificare i pacchetti esterni richiesti dal progetto. L'approccio consigliato prevede l'uso di un [file requirements.txt](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org), che contiene un elenco dei comandi per pip e che consente di installare le versioni richieste di pacchetti dipendenti. Il comando più comune è `pip freeze > requirements.txt`, che registra l'elenco dei pacchetti correnti di un ambiente in *requirements.txt*.

Dal punto di vista tecnico, per tenere traccia dei requisiti è possibile usare un qualsiasi nome file, usando `-r <full path to file>` quando si installa un pacchetto, ma Visual Studio fornisce supporto specifico per *requirements.txt*:

- Se è stato caricato un progetto che contiene *requirements.txt* e si vogliono installare tutti i pacchetti elencati nel file, espandere il nodo **Ambienti Python** in **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul progetto e scegliere **Installa da requirements.txt**:

    ![Installa da requirements.txt](media/environments-requirements-txt-install.png)

- Se tutti i pacchetti necessari sono già installati in un ambiente, è possibile fare clic con il pulsante destro del mouse su tale ambiente in **Esplora soluzioni** e scegliere **Genera requirements.txt** per creare il file necessario. Se il file esiste già, viene visualizzato un prompt che chiede come aggiornarlo:

    ![Opzioni per l'aggiornamento di requirements.txt](media/environments-requirements-txt-replace.png)

  - **Sostituisci intero file**: rimuove tutti gli elementi, i commenti e le opzioni esistenti.
  - **Aggiorna voci esistenti**: rileva i requisiti del pacchetto e aggiorna gli identificatori di versione in base alla versione attualmente installata.
  - **Aggiorna e aggiungi voci**: aggiorna eventuali requisiti trovati e aggiunge tutti gli altri pacchetti alla fine del file.

Poiché i file *requirements.txt* servono a bloccare i requisiti di un ambiente, vengono indicate le versioni precise per tutti i pacchetti installati. L'uso di versioni precise garantisce di poter riprodurre facilmente l'ambiente in un altro computer. I pacchetti vengono inclusi anche se sono stati installati con un intervallo di versioni, come dipendenza di un altro pacchetto o con un programma di installazione diverso da pip.

Se pip non riesce a installare un pacchetto e questo è presente in un file *requirements.txt*, l'intera installazione non riesce. In questo caso, modificare manualmente il file in modo da escludere questo pacchetto oppure usare le [opzioni di pip](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) in modo che facciano riferimento a una versione installabile del pacchetto. È ad esempio possibile che si preferisca usare [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) per compilare una dipendenza e aggiungere l'opzione `--find-links <path>` al file *requirements.txt*:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="see-also"></a>Vedere anche

- [Gestire ambienti Python in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selezionare un interprete per un progetto](selecting-a-python-environment-for-a-project.md)
- [Percorsi di ricerca](search-paths.md)
- [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)
