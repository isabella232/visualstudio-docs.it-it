---
ms.topic: include
ms.openlocfilehash: 0ee0234e91cdf07c2b52c39d065d527a776dc4ce
ms.sourcegitcommit: 64bf371ffe294e9b3cf769db03cf0f5c1a9b680c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666978"
---
### <a name="create-a-project-using-django-20"></a>Creare un progetto usando Django 2.0

Al momento, il modello Progetto Web Django vuoto usa la versione 1.x più recente di Django. Per usare Django 2.x, il modo più rapido consiste nell'importare file Django 2.x in un progetto Django 1.x. Seguendo questo processo, è possibile sfruttare altri dettagli gestiti dal modello di progetto di Visual Studio.

1. Creare un progetto Django 1.x usando il modello "Progetto Web Django vuoto", come descritto nella sezione precedente. Tuttavia, nella richiesta "Questo progetto richiede pacchetti esterni" selezionare **Installazione manuale**. Scegliendo questa opzione, si evita di installare dipendenze che verranno disinstallate in un passaggio successivo.

1. Aprire un prompt dei comandi e passare a una cartella temporanea.

1. Eseguire `pip install django` per installare il pacchetto Django più recente nell'ambiente Python globale.

1. Eseguire `django-admin startproject <project_name>` sostituendo `<project_name>` con lo stesso nome di progetto usato nel passaggio 1, ad esempio "HelloDjango". Il comando `startproject` crea un file `manage.py` insieme a una cartella corrispondente a `<project_name>`, che contiene i file `__init__.py`, `settings.py`, `urls.py` e `wsgi.py`.

1. In Visual Studio sostituire i file Django 1.x nel progetto con i file Django 2.x, in questo modo:

  a. In **Esplora soluzioni** eliminare `manage.py` e la cartella dell'app Django.
  b. Fare clic con il pulsante destro del mouse sul progetto, scegliere il comando **Aggiungi > Elemento esistente**, individuare e selezionare il file `manage.py` creato nel passaggio 4 e quindi selezionare **OK**. Visual Studio copia il file nel progetto.
  c. Fare clic con il pulsante destro del mouse sul progetto, scegliere il comando **Aggiungi > Elemento esistente**, individuare e selezionare la cartella dell'app creata nel passaggio 4 e quindi selezionare **OK**. Visual Studio copia l'intera cartella e i quattro file nel progetto.
  d. Fare clic con il pulsante destro del mouse su `manage.py` e scegliere **Imposta come file di avvio**.

  > [!Important]
  > Il nome dell'app indicato nel progetto di Visual Studio deve corrispondere al valore di `<project_name>` usato con l'utilità `django-admin` perché l'utilità usa il nome come spazio dei nomi all'interno dei file di codice Python.

1. Aprire `requirements.txt`, modificarne il contenuto in `django >=2.0, <3` e salvare il file.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** e scegliere **Aggiungi ambiente virtuale**. Accettare le impostazioni predefinite nella finestra di dialogo visualizzata e selezionare **Crea**. Accettare tutte le indicazioni per i privilegi di amministratore.