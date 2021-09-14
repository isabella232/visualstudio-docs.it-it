---
title: 'Guida introduttiva: creare un progetto Python da un modello'
description: In questa guida introduttiva viene creato un progetto Visual Studio per Python usando il modello predefinito per un'app Flask di base.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c77f8c52e62772cbef61f7ae07f29a2594e608c0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711482"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Guida introduttiva: Creare un progetto Python da un modello in Visual Studio

Dopo aver [installato il supporto di Python in Visual Studio](installing-python-support-in-visual-studio.md), è facile creare un nuovo progetto Python con una varietà di modelli. In questa guida introduttiva viene creata un'app Flask semplice tramite un modello. Il progetto risultante è simile al progetto creato manualmente in [Guida introduttiva: creare un'app Web con Flask](../ide/quickstart-python.md).

1. Avviare Visual Studio.

1. Nella barra dei menu superiore scegliere **File** Nuovo Project , quindi nella finestra di dialogo Nuovo Project cercare  >    >  "flask  vuota", selezionare il modello Blank **Flask Web Project** nell'elenco centrale, assegnare un nome al progetto e selezionare **OK:**

    ![Creazione di un nuovo progetto con il modello Blank Flask Web Project](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio visualizza la finestra di dialogo con il messaggio **Questo progetto richiede pacchetti esterni.** Questa finestra di dialogo viene visualizzata perché il modello include un file *requirements.txt* che specifica una dipendenza da Flask. Visual Studio può installare i pacchetti automaticamente e offre la possibilità di installarli in un *ambiente virtuale*. L'uso di un ambiente virtuale è consigliato rispetto all'installazione in un ambiente globale. Selezionare quindi **Installa in un ambiente virtuale**.

    ![Installazione di Flask in un ambiente virtuale](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio visualizza la finestra di dialogo **Aggiungi ambiente virtuale**. Accettare l'impostazione predefinita, selezionare **Crea** e quindi fornire il consenso a eventuali richieste di elevazione dei privilegi.

    > [!Tip]
    > Quando si inizia un progetto, è consigliabile creare subito un ambiente virtuale, come invita a fare la maggior parte dei modelli di Visual Studio. Gli ambienti virtuali mantengono nel tempo i requisiti del progetto man mano che si aggiungono e rimuovono librerie. È quindi possibile generare facilmente un file *requirements.txt* con cui reinstallare le dipendenze in altri computer di sviluppo, ad esempio quando si usa il controllo del codice sorgente, e quando si distribuisce il progetto in un server di produzione. Per altre informazioni sugli ambienti virtuali e i vantaggi che offrono, vedere [Usare gli ambienti virtuali](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) e [Gestire i pacchetti necessari con requirements.txt](../python/managing-required-packages-with-requirements-txt.md).

1. Dopo che Visual Studio ha creato tale ambiente, verificare che in **Esplora soluzioni** sia presente un file *app.py*, oltre al file *requirements.txt*. Aprire *app.py* per verificare che il modello contenga codice simile a quello presente in [Guida introduttiva: Creare un'app Web con Flask](../ide/quickstart-python.md), con alcune sezioni in più. Tutto il codice illustrato di seguito viene creato dal modello, pertanto non è necessario incollare manualmente nessun elemento in *app.py*.

    Il codice inizia con le importazioni necessarie:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    In seguito si ha la riga seguente, che può essere utile quando si distribuisce un'app in un host Web:

    ```python
    wsgi_app = app.wsgi_app
    ```

    Si arriva quindi all'elemento Decorator in una funzione semplice che definisce una vista:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Infine, il codice di avvio riportato di seguito consente di impostare l'host e la porta tramite variabili di ambiente anziché a livello di codice. Tale codice consente di controllare facilmente la configurazione sia nei computer di sviluppo che in quelli di produzione senza modificare il codice:

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Selezionare **Debug**  >  **Avvia senza eseguire debug** per eseguire l'app e aprire un browser in `localhost:5555` .

**Domanda: quali altri modelli Python offre Visual Studio?**

**Risposta**: con il carico di lavoro Python installato, Visual Studio offre diversi modelli di progetto, inclusi quelli per i framework Web [Flask, Bottle e Django](../python/python-web-application-project-templates.md), per i servizi cloud di Azure e per diversi scenari di apprendimento automatico, nonché un modello per creare un progetto da una struttura di cartelle esistente contenente un'app Python. È possibile accedervi tramite **la finestra di** dialogo Project file selezionando il nodo del linguaggio  >    >   **Python** e i relativi nodi figlio.

Visual Studio offre anche diversi file o *modelli di elemento* per creare rapidamente una classe Python, un pacchetto Python, uno unit test Python, un file *web.config* e altro ancora. Quando è aperto un progetto Python, è possibile accedere ai modelli di elemento **Project** comando di menu Aggiungi  >  **nuovo** elemento. Vedere il riferimento ai [modelli di elemento](python-item-templates.md).

L'uso di modelli consente di risparmiare una quantità di tempo significativa quando si inizia un progetto o si crea un file. I modelli sono anche un ottimo modo per ottenere informazioni sui diversi tipi di app e strutture di codice. È utile dedicare alcuni minuti alla creazione di progetti ed elementi dai diversi modelli per acquisire familiarità con ciò che questi ultimi hanno da offrire.

**Domanda: si possono usare anche modelli Cookiecutter?**

**Risposta:** Sì. Visual Studio infatti garantisce l'integrazione diretta con Cookiecutter, su cui è possibile acquisire informazioni tramite [Guida introduttiva: Creare un progetto da un modello Cookiecutter](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione: Usare Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vedi anche

- [Identificare manualmente un interprete Python esistente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Installare il supporto di Python in Visual Studio 2015 e versioni precedenti](installing-python-support-in-visual-studio.md)
- [Percorsi di installazione](installing-python-support-in-visual-studio.md#install-locations)
