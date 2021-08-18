---
title: Debug del codice Python in computer Linux remoti
description: Usare Visual Studio per eseguire il debug del codice Python in esecuzione in computer Linux remoti, inclusi i passaggi di configurazione necessari, la sicurezza e la risoluzione dei problemi.
ms.date: 05/12/2020
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 74b4e25bccf52893302adf4bca6bb81a5e7e3794
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140530"
---
Visual Studio avviare ed eseguire il debug di applicazioni Python in locale e in remoto in un computer Windows remoto (vedere [Debug remoto](../../../debugger/remote-debugging.md)). Può anche eseguire il debug in modalità remota in un sistema operativo, un dispositivo o un'implementazione Python diversa da CPython usando la [libreria debugpy](https://pypi.org/project/debugpy/).

Quando si usa debugpy, il codice Python in fase di debug ospita il server di debug a cui Visual Studio collegarsi. L'hosting richiede una piccola modifica del codice per importare e abilitare il server e potrebbe richiedere configurazioni della rete o del firewall nel computer remoto per consentire le connessioni TCP.

> [!NOTE]
> Per Visual Studio 2019 versione 16.4 e precedenti, è stata usata la [libreria ptvsd.](https://pypi.python.org/pypi/ptvsd) La libreria debugpy ha sostituito ptvsd 4 in Visual Studio 2019 versione 16.5.

## <a name="set-up-a-linux-computer"></a>Impostare un computer Linux

Per eseguire questa procedura dettagliata sono necessari gli elementi seguenti:

- Un computer remoto che esegue Python in un sistema operativo come Mac OSX o Linux.
- La porta 5678 (in ingresso) deve essere aperta nel firewall di tale computer, in base all'impostazione predefinita per il debug remoto.

> [!NOTE]
> Questa procedura dettagliata è basata Visual Studio 2019 versione 16.6.

È possibile creare facilmente [macchine virtuali Linux in Azure](/azure/virtual-machines/linux/creation-choices) e [accedervi usando Desktop remoto](/azure/virtual-machines/linux/use-remote-desktop) da Windows. L'uso di Ubuntu per la macchina virtuale è comodo perché Python è installato per impostazione predefinita. Se si preferisce scegliere un altro percorso di download per Python, vedere l'elenco di opzioni in [Installazione degli interpreti Python](../../installing-python-interpreters.md).

Per informazioni dettagliate sulla creazione di una regola del firewall per una macchina virtuale di Azure, vedere [Aprire porte su una VM tramite il portale di Azure](/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="prepare-the-script-for-debugging"></a>Preparare lo script per il debug

1. Nel computer remoto creare un file Python denominato *guessing-game.py* con il codice seguente:

    ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
        guess = int(input('Take a guess: '))
        guesses_made += 1
        if guess < number:
            print('Your guess is too low.')
        if guess > number:
            print('Your guess is too high.')
        if guess == number:
            break
    if guess == number:
        print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
        print('Nope. The number I was thinking of was {0}'.format(number))
    ```

1. Installare il pacchetto `debugpy` nell'ambiente usando `pip3 install debugpy`.
   >[!NOTE]
   >È buona idea registrare la versione di debugpy installata nel caso in cui sia necessaria per la risoluzione dei problemi. [L'elenco debugpy](https://pypi.org/project/debugpy/) mostra anche le versioni disponibili.

1. Abilitare il debug remoto aggiungendo il codice seguente nel primo punto possibile in *guessing-game.py* prima di altro codice. Anche se non è un requisito vincolante, non è possibile eseguire il debug di qualsiasi thread in background generato prima della chiamata della funzione `listen`.

   ```python
   import debugpy
   debugpy.listen(5678)
   ```

1. Salvare il file ed eseguire `python3 guessing-game.py`. La chiamata a `listen` viene eseguita in background e attende connessioni in ingresso quando si interagisce in altro modo con il programma. Se richiesto, è possibile chiamare la funzione `wait_for_client` dopo `listen` per bloccare il programma fino al collegamento del debugger.

> [!Tip]
> Oltre a e , debugpy fornisce anche una funzione helper , che funge da punto di interruzione a livello di codice `listen` se il debugger è `wait_for_client` `breakpoint` collegato. È anche disponibile una funzione `is_client_connected` che restituisce `True` se il debugger è collegato (si noti che non è necessario verificare questo risultato prima di chiamare qualsiasi altra funzione `debugpy`).

## <a name="attach-remotely-from-python-tools"></a>Collegarsi in remoto da Python Tools

In questa procedura viene impostato un semplice punto di interruzione per arrestare il processo remoto.

1. Creare una copia del file remoto nel computer locale e aprirlo in Visual Studio. La posizione del file non è importante, ma il relativo nome deve corrispondere al nome dello script nel computer remoto.

1. (Facoltativo) Per avere IntelliSense per il debugpy nel computer locale, installare il pacchetto debugpy nell'ambiente Python.

1. Selezionare **Debug**  >  **collegamento a processo**.

1. Nella finestra **di dialogo Collega a** processo visualizzata impostare Tipo **di** connessione su Python **remoto (debugpy).**

1. Nel campo **Destinazione connessione** immettere dove è quello del computer remoto (che può essere un indirizzo esplicito o un nome come myvm.cloudapp.net) e è il numero di porta del debug `tcp://<ip_address>:5678` `<ip_address>` `:5678` remoto.

1. Premere **INVIO** per popolare l'elenco dei processi di debug disponibili nel computer:

    ![Immissione della destinazione di connessione e indicazione dei processi](../../media/remote-debugging-attach.png)

    Se si avvia un altro programma nel computer remoto dopo la compilazione di questo elenco, selezionare il pulsante **Aggiorna**.

1. Selezionare il processo per cui eseguire il debug e quindi **Allega** oppure fare doppio clic sul processo.

1. Visual Studio passa quindi in modalità di debug mentre lo script continua l'esecuzione nel computer remoto, rendendo disponibili tutte le consuete funzionalità di [debug](../../debugging-python-in-visual-studio.md). Ad esempio, impostare un punto di interruzione sulla riga `if guess < number:`, quindi passare al computer remoto e immettere un'altra proposta. Al termine dell'operazione, Visual Studio si arresta nel computer locale in corrispondenza di tale punto di interruzione, indica le variabili locali e così via:

    ![Visual Studio sospende il debug quando viene raggiunto il punto di interruzione](../../media/remote-debugging-breakpoint-hit.png)

1. Quando si arresta il debug, Visual Studio si disconnette dal programma, che rimane in esecuzione nel computer remoto. debugpy continua anche a essere in ascolto del collegamento dei debugger, quindi è possibile ricollegare il processo in qualsiasi momento.

### <a name="connection-troubleshooting"></a>Risoluzione dei problemi di connessione

1. Assicurarsi di aver selezionato **Python remoto (debugpy)** per Tipo **di connessione**
1. Verificare che il segreto in **Destinazione connessione corrisponda** esattamente al segreto nel codice remoto.
1. Verificare che l'indirizzo IP in **Destinazione connessione** corrisponda a quello del computer remoto.
1. Verificare di aver aperto la porta di debug remoto nel computer remoto e di aver incluso il suffisso di porta nella destinazione della connessione, ad esempio `:5678` .
    - Se è necessario usare una porta diversa, è possibile specificarla in `listen` , come in `debugpy.listen((host, port))` . In questo caso, aprire quella porta specifica nel firewall.
1. Verificare che la versione di debugpy installata nel computer remoto restituita dalle corrispondenze usate dalla versione degli strumenti Python in uso in Visual Studio nella tabella `pip3 list` seguente. Se necessario, aggiornare debugpy nel computer remoto.

    | Versione di Visual Studio | Strumenti Python/versione di debugpy |
    | --- | --- |
    | 2019 16.6 | 1.0.0b5 |
    | 2019 16.5 | 1.0.0b1 |

> [!NOTE]
> Visual Studio 2019 versione 16.0-16.4 ha utilizzato ptvsd, non debugpy. Il processo di questa procedura dettagliata per queste versioni è simile, ma i nomi delle funzioni sono diversi. Visual Studio 2019 versione 16.5 usa debugpy, ma i nomi delle funzioni sono gli stessi di quelli in ptvsd. Invece di `listen` , si userebbe `enable_attach` . Invece di `wait_for_client` , si userebbe `wait_for_attach` . Invece di `breakpoint` , si userebbe `break_into_debugger` .

## <a name="using-ptvsd-3x-for-legacy-debugging"></a>Uso di ptvsd 3.x per il debug legacy
La versione 15.8 e successive di Visual Studio 2017 usano un debugger basato sulla versione ptvsd 4.1 +. Visual Studio 2019 versione 16.5 e successive usa un debugger basato su debugpy. Queste versioni del debugger sono compatibili con Python 2.7 e Python 3.5+. Se si usa Python 2.6, da 3.1 a 3.4 o IronPython, Visual Studio visualizza l'errore, debugger non supporta questo ambiente **Python.** Le informazioni seguenti si applicano solo al debug remoto con ptvsd 3.x.

1. Con ptvsd 3.x, la funzione `enable_attach` richiede il passaggio di un "segreto" come primo argomento, che limita l'accesso allo script in esecuzione. Si immette questo segreto quando si collega il debugger remoto. Sebbene non sia consigliabile, è possibile consentire a chiunque di eseguire la connessione usando `enable_attach(secret=None)`.

1. L'URL di destinazione della connessione è `tcp://<secret>@<ip_address>:5678`, dove `<secret>` è la stringa passata a `enable_attach` nel codice Python.

Per impostazione predefinita, la connessione al server di debug remoto di ptvsd 3.x è protetta solo dal segreto e tutti i dati vengono passati come testo normale. Per una connessione più sicura, ptvsd 3.x supporta SSL con il protocollo `tcsp`, che deve essere configurato come indicato di seguito:

1. Nel computer remoto generare un certificato autofirmato separato e i file di chiave usando il comando openssl:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    Quando openssl richiede il **nome comune** usare il nome host o l'indirizzo IP, a seconda dell'opzione scelta per la connessione.

    Per maggiori dettagli, vedere la sezione relativa ai [certificati autofirmati](https://docs.python.org/3/library/ssl.html#self-signed-certificates) nei documenti del modulo `ssl` di Python. Si noti che il comando in tali documenti genera solo un singolo file combinato.

1. Nel codice modificare la chiamata a `enable_attach` per includere gli argomenti `certfile` e `keyfile` usando i nomi di file come valori. Questi argomenti hanno lo stesso significato per la funzione `ssl.wrap_socket` standard di Python:

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    È anche possibile apportare la stessa modifica nel file di codice nel computer locale, ma poiché il codice non viene effettivamente eseguito, non è strettamente necessario.

1. Riavviare il programma Python nel computer remoto, in modo che sia pronto per il debug.

1. Proteggere il canale aggiungendo il certificato alla CA radice attendibile nel computer Windows con Visual Studio:

    1. Copiare il file del certificato dal computer remoto al computer locale.
    1. Aprire il **Pannello di controllo** e passare a **Strumenti di amministrazione** > **Gestisci i certificati computer**.
    1. Nella finestra visualizzata espandere **Autorità di certificazione radice attendibili** sul lato sinistro, fare clic con il pulsante destro del mouse su **Certificati** e selezionare **Tutte le attività** > **Importa**.
    1. Individuare e selezionare il file con estensione *cer* copiato dal computer remoto, quindi fare clic nelle finestre di dialogo per completare l'importazione.

1. Ripetere il processo di associazione in Visual Studio come descritto in precedenza, usando ora `tcps://` come protocollo per **Destinazione della connessione** (o **Qualificatore**).

    ![Scelta del trasporto di debug remoto con SSL](../../media/remote-debugging-qualifier-ssl.png)

1. Visual Studio segnala i potenziali problemi di certificato quando si esegue la connessione con SSL. È possibile ignorare gli avvisi e continuare, ma anche se il canale rimane crittografato per evitare intercettazioni, può comunque essere vulnerabile agli attacchi di tipo man-in-the-middle.

    1. Se viene visualizzato **l'avviso seguente il** certificato remoto non è attendibile, significa che il certificato non è stato aggiunto correttamente alla CA radice attendibile. Verificare questi passaggi e riprovare.

        ![Avviso su attendibilità del certificato SSL](../../media/remote-debugging-ssl-warning.png)

    1. Se appare l'avviso **il nome del certificato remoto non corrisponde al nome host**, significa che non è stato usato il nome host o l'indirizzo IP corretto come **nome comune** durante la creazione del certificato.

        ![Avviso sul nome host del certificato SSL](../../media/remote-debugging-ssl-warning2.png)
