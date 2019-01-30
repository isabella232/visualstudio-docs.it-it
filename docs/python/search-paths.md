---
title: Come vengono applicati i percorsi di ricerca di Python
description: Visual Studio offre un modo più preciso per specificare i percorsi di ricerca per ambienti e progetti al fine di evitare di usare variabili a livello di sistema.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: eca8ce0a2b791cba5513c2d3936a429dd4ad4eaa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010194"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Come vengono usati i percorsi di ricerca di Python Visual Studio

Quando Python viene usato normalmente, il percorso di ricerca predefinito per i file di modulo viene fornito dalla variabile di ambiente `PYTHONPATH` (o `IRONPYTHONPATH` e così via). Quando si usa un'istruzione `from <name> import...` o `import <name>`, Python esegue la ricerca di un nome corrispondente nelle posizioni seguenti nell'ordine indicato:

1. I moduli predefiniti di Python.
1. La cartella contenente il codice Python in esecuzione.
1. Il "percorso di ricerca del modulo" come definito dalla variabile di ambiente applicabile. Vedere [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Percorso di ricerca del modulo) e [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Variabili di ambiente) nella documentazione principale di Python.

Visual Studio ignora tuttavia la variabile di ambiente del percorso di ricerca, anche se è stata impostata per l'intero sistema. La variabile viene in realtà ignorata proprio *perché* è impostata per l'intero sistema e genera quindi alcune domande a cui non è possibile rispondere automaticamente: i moduli di riferimento sono validi per Python 2.7 o Python 3.6+? Sostituiranno i moduli di libreria standard? Lo sviluppatore è a conoscenza di questo comportamento o si tratta di un tentativo di hijack effettuato da utenti malintenzionati?

Visual Studio consente quindi di specificare direttamente i percorsi di ricerca sia negli ambienti che nei progetti. Il codice eseguito o sottoposto a debug in Visual Studio riceve i percorsi di ricerca nel valore di `PYTHONPATH` (e altre variabili equivalenti). Quando si aggiungono percorsi di ricerca, Visual Studio controlla le librerie in questi percorsi e crea i database di IntelliSense corrispondenti all'occorrenza (Visual Studio 2017 versione 15.5 e precedenti; la creazione dei database potrebbe richiedere tempo a seconda del numero di librerie).

Per aggiungere un percorso di ricerca, passare a **Esplora soluzioni**, espandere il nodo del progetto, fare clic con il pulsante destro del mouse su **Percorsi di ricerca** e selezionare **Aggiungi cartella al percorso di ricerca**:

![Comando Aggiungi cartella al percorso di ricerca in Percorsi di ricerca di Esplora soluzioni](media/search-paths-command.png)

Questo comando visualizza un browser in cui è possibile selezionare la cartella da includere.

Se la variabile di ambiente `PYTHONPATH` include già la cartella necessaria, usare il collegamento **Aggiungi PYTHONPATH al percorso di ricerca**.

Dopo aver aggiunto le cartelle ai percorsi di ricerca, Visual Studio usa tali percorsi per tutti gli ambienti associati al progetto. (È possibile riscontrare errori se l'ambiente è basato su Python 3 e si tenta di aggiungere un percorso di ricerca per i moduli Python 2.7.)

È possibile aggiungere come percorsi di ricerca i file con estensione *zip* o *egg*, selezionando il comando **Aggiungi archivio ZIP al percorso di ricerca**. Come con le cartelle, il contenuto di questi file viene analizzato e reso disponibile per IntelliSense.

## <a name="see-also"></a>Vedere anche

- [Gestire ambienti Python in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selezionare un interprete per un progetto](selecting-a-python-environment-for-a-project.md)
- [Usare requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)
