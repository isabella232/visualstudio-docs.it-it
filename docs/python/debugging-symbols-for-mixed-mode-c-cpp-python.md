---
title: Simboli per il debug in modalità mista con Python/C++
description: Come Visual Studio offre la possibilità di caricare i simboli per il debug completo in modalità mista con C++ e Python.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: aaf6fd34544714444afef5d4a9bea8d4aa827afd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038565"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Installare i simboli di debug per interpreti Python

Per offrire un'esperienza di debug completa, il [debugger in modalità mista di Python](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) in Visual Studio ha bisogno dei simboli di debug per l'interprete Python in uso per analizzare numerose strutture dei dati interne. Ad *python27.dll*, ad esempio, il file di simboli corrispondente *è python27.pdb*; per *python36.dll*, il file di simboli *è python36.pdb.* Per ogni versione dell'interprete sono disponibili anche i file di simboli per un'ampia gamma di moduli.

Con Visual Studio 2017 e versioni successive gli interpreti Python 3 e Anaconda 3 installano automaticamente i rispettivi simboli, che Visual Studio trova automaticamente. Per Visual Studio 2015 e versioni precedenti o quando si usano altri interpreti, è necessario scaricare i simboli separatamente e quindi puntare Visual Studio tramite la finestra di dialogo Opzioni degli strumenti nella scheda Simboli di  >     >   debug. Questi passaggi sono descritti in dettaglio nelle sezioni seguenti.

È possibile che Visual Studio richieda i simboli se sono necessari, di solito quando avvia una sessione di debug in modalità mista. In questo caso, viene visualizzata una finestra di dialogo con due opzioni:

- **Apri finestra di dialogo per le impostazioni dei simboli** apre la finestra di dialogo **Opzioni** che consente di passare alla scheda **Debug** > **Simboli**.
- **Scarica i simboli per l'interprete personale** apre questa pagina della documentazione e in questo caso consente di selezionare **Strumenti** > **Opzioni** e passare alla scheda **Debug** > **Simboli** per continuare.

    ![Prompt per i simboli del debugger in modalità mista](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Scaricare i simboli

- Python 3.5 e versioni successive: acquisire i simboli di debug usando il programma di installazione di Python. Selezionare **Custom installation** (Installazione personalizzata), selezionare **Next** (Avanti) per passare ad **Advanced Options** (Opzioni avanzate) e quindi selezionare le caselle delle opzioni **Download debugging symbols** (Scarica simboli di debug) e **Download debug binaries** (Scarica file binari di debug):

    ![Programma di installazione di Python 3.x con l'opzione per includere i simboli di debug](media/mixed-mode-debugging-symbols-installer35.png)

    I file di simboli (con estensione *pdb*) sono nella cartella radice di installazione. Anche i file di simboli per i singoli moduli sono nella cartella *DLLs*. Per questo motivo, Visual Studio li trova automaticamente e non sono necessari altri passaggi.

- Python 3.4.x e versioni precedenti:  i simboli sono [](#official-distributions) disponibili come file.zipscaricabili dalle distribuzioni ufficiali o [da Enthought Canopy](#enthought-canopy). Dopo il download, estrarre i file in una cartella locale per continuare, ad esempio una cartella *Symbols* nella cartella di Python.

    > [!Important]
    > I simboli sono diversi tra le diverse build secondarie di Python, nonché tra la build a 32 bit e quella a 64 bit, quindi è importante che le versioni corrispondano esattamente. Per controllare l'interprete in uso, espandere il **nodo Ambienti Python**  nel progetto **in** Esplora soluzioni prendere nota del nome dell'ambiente. Passare quindi alla finestra **Ambienti Python** *e* prendere nota del percorso di installazione. Aprire quindi una finestra di comando nel percorso e avviare *python.exe* che visualizza la versione esatta e indica se è una versione a 32 o a 64 bit.

- Per qualsiasi altra distribuzione Python di terze parti, ad esempio ActiveState Python: contattare gli autori della distribuzione e richiedere loro i relativi simboli. WinPython tuttavia incorpora l'interprete Python standard senza modifiche, quindi usare i simboli della distribuzione ufficiale per il numero di versione corrispondente.

## <a name="point-visual-studio-to-the-symbols"></a>Impostare Visual Studio in modo che punti ai simboli

Se i simboli sono stati scaricati separatamente, eseguire i passaggi riportati di seguito per indicarlo a Visual Studio. Se i simboli sono stati installati con il programma di installazione di Python 3.5 o versione successiva, Visual Studio li trova automaticamente.

1. Selezionare il menu  >  **Opzioni strumenti** e passare a Simboli **di**  >  **debug**.

1. Selezionare il pulsante **Aggiungi** sulla barra degli strumenti (evidenziata nell'immagine), immettere la cartella in cui sono stati espansi i simboli scaricati, ovvero dove si trova *python.pdb*, ad esempio *c:\python34\Symbols* nell'immagine, e selezionare **OK**.

    ![Opzioni per i simboli del debugger in modalità mista](media/mixed-mode-debugging-symbols.png)

1. Durante una sessione di debug Visual Studio potrebbero anche richiedere il percorso di un file di origine per l'interprete Python. Se sono stati scaricati file di origine, ad esempio da [python.org/downloads/](https://www.python.org/downloads/), è ovviamente possibile fare riferimento anche a questi.

> [!Note]
> Le funzionalità di memorizzazione nella cache dei simboli presenti nella finestra di dialogo consentono di creare una cache locale dei simboli ottenuti da un'origine online. Queste funzionalità non sono necessarie con i simboli dell'interprete Python, poiché questi sono già disponibili in locale. Per informazioni dettagliate, vedere Specificare simboli e file di origine [Visual Studio debugger.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="official-distributions"></a>Distribuzioni ufficiali

| Versione Python | Download |
| --- | --- |
| 3.5 e versioni successive | Installare i simboli usando il programma di installazione di Python. |
| 3.4.4 | [32 bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.18 | [32 bit](https://www.python.org/ftp/python/2.7.18/python-2.7.18-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.18/python-2.7.18.amd64-pdb.zip) |
| 2.7.17 | [32 bit](https://www.python.org/ftp/python/2.7.17/python-2.7.17-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.17/python-2.7.17.amd64-pdb.zip) |
| 2.7.16 | [32 bit](https://www.python.org/ftp/python/2.7.16/python-2.7.16-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.16/python-2.7.16.amd64-pdb.zip) |
| 2.7.15 | [32 bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32 bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32 bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32 bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32 bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip)  -  [64 bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Enthought Canopy

Enthought Canopy fornisce i simboli per i relativi file binari a partire dalla versione 1.2. I simboli vengono installati automaticamente insieme alla distribuzione, ma è comunque necessario aggiungere manualmente la cartella che li contiene al percorso dei simboli come descritto in precedenza. In un'installazione tipica di Canopy per utente i simboli si trovano in *%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts* per la versione a 64 bit e in *%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts* per la versione a 32 bit.

Enthought Canopy 1.1 e versioni precedenti, così come Enthought Python Distribution (EPD), non forniscono simboli per l'interprete e pertanto non sono compatibili con il debug in modalità mista.
