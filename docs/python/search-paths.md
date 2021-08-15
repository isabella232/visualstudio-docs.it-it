---
title: Come vengono applicati i percorsi di ricerca di Python
description: Visual Studio offre un modo più preciso per specificare i percorsi di ricerca per ambienti e progetti al fine di evitare di usare variabili a livello di sistema.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 613dd8d47d4b566f2f02256a4fd981575cf10fb1acb9e117d948695edac6f2c4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121244875"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Come vengono usati i percorsi di ricerca di Python Visual Studio

Quando Python viene usato normalmente, il percorso di ricerca predefinito per i file di modulo viene fornito dalla variabile di ambiente `PYTHONPATH` (o `IRONPYTHONPATH` e così via). Quando si usa un'istruzione `from <name> import...` o `import <name>`, Python esegue la ricerca di un nome corrispondente nelle posizioni seguenti nell'ordine indicato:

1. I moduli predefiniti di Python.
1. La cartella contenente il codice Python in esecuzione.
1. Il "percorso di ricerca del modulo" come definito dalla variabile di ambiente applicabile. Vedere [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Percorso di ricerca del modulo) e [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Variabili di ambiente) nella documentazione principale di Python.

Visual Studio ignora tuttavia la variabile di ambiente del percorso di ricerca, anche se è stata impostata per l'intero sistema. In realtà, viene ignorata proprio *perché* è impostata per l'intero sistema e genera determinate domande a cui non è possibile rispondere automaticamente: i moduli di riferimento sono validi per Python 2.7 o per Python 3.6+? Sostituiranno i moduli di libreria standard? Lo sviluppatore è a conoscenza di questo comportamento o si tratta di un tentativo di hijack effettuato da utenti malintenzionati?

Visual Studio consente quindi di specificare direttamente i percorsi di ricerca sia negli ambienti che nei progetti. Il codice eseguito o sottoposto a debug in Visual Studio riceve i percorsi di ricerca nel valore di `PYTHONPATH` (e altre variabili equivalenti). Quando si aggiungono percorsi di ricerca, Visual Studio controlla le librerie in questi percorsi e crea i database di IntelliSense corrispondenti all'occorrenza (Visual Studio 2017 versione 15.5 e precedenti; la creazione dei database potrebbe richiedere tempo a seconda del numero di librerie).

Per aggiungere un percorso di ricerca, passare a **Esplora soluzioni, espandere** il nodo del progetto, fare clic con il pulsante destro del mouse su Percorsi **di** ricerca e scegliere Aggiungi cartella al percorso **di ricerca**:

::: moniker range="vs-2017"
![Comando Aggiungi cartella al percorso di ricerca in Percorsi di ricerca di Esplora soluzioni](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Comando Aggiungi cartella al percorso di ricerca in Percorsi di ricerca di Esplora soluzioni](media/search-paths-command-2019.png)
::: moniker-end

Questo comando visualizza un browser in cui è possibile selezionare la cartella da includere.

Se la variabile di ambiente `PYTHONPATH` include già la cartella necessaria, usare il collegamento **Aggiungi PYTHONPATH al percorso di ricerca**.

Dopo aver aggiunto le cartelle ai percorsi di ricerca, Visual Studio usa tali percorsi per tutti gli ambienti associati al progetto. (È possibile riscontrare errori se l'ambiente è basato su Python 3 e si tenta di aggiungere un percorso di ricerca per i moduli Python 2.7.)

È possibile aggiungere come percorsi di ricerca i file con estensione *zip* o *egg*, selezionando il comando **Aggiungi archivio ZIP al percorso di ricerca**. Come con le cartelle, il contenuto di questi file viene analizzato e reso disponibile per IntelliSense.

## <a name="see-also"></a>Vedi anche

- [Gestire ambienti Python in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selezionare un interprete per un progetto](selecting-a-python-environment-for-a-project.md)
- [Usare requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)
