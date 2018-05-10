---
title: Modello di progetto Web Django per Python
description: Panoramica dei modelli di Visual Studio per le applicazioni Web scritte in Python con il framework Django.
ms.date: 04/17/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 077619b7d47441bb4a02dbe87e7cf714b634beff
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
# <a name="django-web-project-template"></a>Modello di progetto Web Django

[Django](https://www.djangoproject.com/) è un framework Python di alto livello progettato per lo sviluppo rapido, sicuro e scalabile di applicazioni Web. Il supporto di Python in Visual Studio include vari modelli di progetto per configurare la struttura di un'applicazione Web basata su Django. Per utilizzare un modello in Visual Studio, selezionare **File** > **Nuovo** > **Progetto**, cercare "Django" e scegliere tra i modelli "Progetto Web Django vuoto", "Progetto Web Django" e "Progetto Web Django di sondaggi". Vedere l'[Esercitazione su Django](learn-django-in-visual-studio-step-01-project-and-solution.md) per una guida su tutti i modelli.

Visual Studio offre il supporto IntelliSense completo per i progetti Django:

- Variabili di contesto passate nel modello:

    ![IntelliSense per le variabili di contesto](media/template-django-intellisense.png)

- Assegnazione di tag e filtro sia per variabili incorporate che per quelle definite dall'utente:

    ![IntelliSense per tag e filtri](media/template-django-intellisense-filter.png)

- Colorazione della sintassi per codice CSS e JavaScript incorporato:

    ![IntelliSense per CSS](media/template-django-intellisense-css.png)

    ![IntelliSense per JavaScript](media/template-django-intellisense-js.png)

Visual Studio offre anche [supporto completo per il debug](debugging-python-in-visual-studio.md) di progetti Django: 

![Punti di interruzione](media/template-django-debugging.png)

È normale che i progetti Django vengano gestiti usando il relativo file `manage.py` e questo è un presupposto a cui Visual Studio si attiene. Se si smette di usare tale file come punto di ingresso, praticamente si interrompe il file di progetto. In questo caso è necessario [ricreare il progetto da file esistenti](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files) senza contrassegnarlo come progetto Django.

## <a name="django-management-console"></a>Console di gestione Django

È possibile accedere alla console di gestione Django da vari comandi del menu **Progetto** oppure facendo clic con il pulsante destro del mouse sul progetto in Esplora soluzioni.

- **Apri shell Django**: apre una shell nel contesto dell'applicazione che consente di modificare i modelli.

    ![Console](media/template-django-console-shell.png)

- **DB sincronizzazione Django**: esegue `manage.py syncdb` in una finestra interattiva.

    ![Console](media/template-django-console-sync-db.png)

- **Raccogli file statici**: esegue `manage.py collectstatic --noinput` per copiare tutti i file statici nel percorso specificato da `STATIC_ROOT` nel file `settings.py`. Durante la [pubblicazione in Servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md) l'operazione di pubblicazione include anche la raccolta automatica dei file statici.

    ![Console](media/template-django-console-collect-static.png)

- **Convalida**: esegue `manage.py validate`, che restituisce tutti gli errori di convalida presenti nei modelli installati specificati da `INSTALLED_APPS` nel file `settings.py`:

    ![Console](media/template-django-console-validate.png)

## <a name="see-also"></a>Vedere anche

- [Esercitazione su Django](learn-django-in-visual-studio-step-01-project-and-solution.md)