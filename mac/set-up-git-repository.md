---
title: Impostazione di un repository Git
description: Utilizzo di Git e Subversion in Visual Studio per Mac.
author: therealjohn
ms.author: johmil
ms.date: 05/13/2020
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: 7e9dc8728a3115368f1772287362b2a9f21a4309
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173359"
---
# <a name="set-up-a-git-repository"></a>Impostare un repository Git

Git è un sistema di controllo della versione della versione distribuito che consente ai team di lavorare contemporaneamente sugli stessi documenti. Ciò significa che è presente un unico server che contiene tutti i file ma ogni volta che viene estratto un repository da questa origine centrale, l'intero repository viene clonato localmente nel computer in uso.

Vi sono molti host remoti che consentono di lavorare con Git per il controllo della versione, tuttavia il più comune di questi è GitHub. Nell'esempio seguente viene usato un host GitHub, ma è possibile usare qualsiasi host Git per il controllo della versione in Visual Studio per Mac.

Se si desidera usare GitHub, assicurarsi che sia stato creato e configurato un account prima di eseguire i passaggi in questo articolo.

## <a name="creating-a-remote-repo-on-github"></a>Creazione di un repository remoto su GitHub

Nell'esempio seguente viene usato un host GitHub, ma è possibile usare qualsiasi host Git per il controllo della versione in Visual Studio per Mac.

Per impostare un repository Git, seguire questa procedura:

1. Creare un nuovo repository Git in github.com:

    ![Creare nuovo repository Git](media/version-control-git1-sml.png)

2. Impostare il nome, la descrizione e la privacy del repository. **Non** inizializzare il repository. Impostare .gitignore e licenza su None (Nessuno):

    ![Impostare i dettagli del repository Git](media/version-control-git2.png)

3. Nella pagina successiva viene offerta la possibilità di visualizzare e copiare l'indirizzo HTTPS o SSH nel repository appena creato:

    ![visualizzare e copiare l'indirizzo](media/version-control-git3.png)

   L'indirizzo HTTPS sarà necessario perché Visual Studio per Mac punti a questo repository.

## <a name="publishing-an-existing-project"></a>Pubblicazione di un progetto esistente

Per un progetto esistente che _non_ sia stato ancora inserito nel sistema di controllo della versione, usare i passaggi seguenti per impostarlo in Git:

1. Selezionare il nome della soluzione nel riquadro della soluzione in Visual Studio per Mac.

2. Nella barra dei menu selezionare **controllo della versione > pubblica nel controllo della versione** per visualizzare la finestra di dialogo **clona repository** :

    ![Avviare l'estrazione in Visual Studio per Mac](media/version-control-git4.png)

    Se questa voce di menu risulta disattivata, verificare di aver selezionato il nome della soluzione.

3. Scegliere la scheda **Seleziona da registrato** e premere il pulsante **Aggiungi** :

    ![](media/version-control-git5.png)

4. Inserire il nome del repository che si desidera visualizzare localmente e incollare l'URL del passaggio 3. La finestra di dialogo Configurazione repository sarà analoga alla seguente. Premere OK:

    ![Finestra di dialogo di inserimento dettagli Git](media/version-control-git6.png)

    È anche possibile usare SSH per la connessione a Git.

5. Per tentare di pubblicare l'app in Git, selezionare il repository e assicurarsi che i campi di testo **Nome modulo** e **Messaggio** siano compilati:

    ![Tentativo di pubblicazione del progetto in Git](media/version-control-git7.png)

6. Fare clic su **OK** e quindi su **Pubblica** dalla finestra di dialogo di avviso.

7. Nella finestra **Credenziali GIT** immettere il nome utente e la password GitHub. 

> [!NOTE]
> Se per l'account è abilitata l'autenticazione a due fattori, è necessario creare un token di accesso, che verrà usato al posto della password. Se non è stato creato un token di accesso, seguire i passaggi descritti nella documentazione relativa ai [token di accesso](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) Git.

8. Inserire il nome utente e il token di accesso personale, quindi premere **OK**:

    ![Inserire nome utente e password per Git](media/version-control-git9-sml.png)

9. Dopo alcuni secondi, la soluzione verrà pubblicata con il commit iniziale. Per verificare l'avvenuta pubblicazione, aprire la voce del menu Version Control (Controllo della versione), che dovrebbe ora includere molte opzioni:

    ![Menu Controllo della versione](media/version-control-git10.png)

10. Una volta avviate le modifiche aggiuntive, usare prima il **controllo della versione > esaminare e confermare** il menu per aprire la visualizzazione dello stato. Dopo aver selezionato e sottoposta a commit le modifiche, selezionare **push** per eseguire il push delle modifiche nel repository remoto. Ciò consentirà a tutti gli utenti appropriati di visualizzarlo in github.com:

    ![Eseguire il push delle modifiche nel repository remoto](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Pubblicazione di un nuovo progetto

È possibile usare la finestra di dialogo Nuovo progetto per creare un nuovo progetto con un repository Git locale. Per abilitarlo, selezionare la casella di controllo **Usa GIT per il controllo della versione**, come illustrato nello screenshot seguente. Verrà inizializzato il repository e verrà aggiunto un file con estensione gitignore facoltativo:

![Creare un nuovo progetto con il supporto Git](media/version-control-git-publish-new1.png)

Seguire questa procedura per eseguire il push del nuovo repository locale in un nuovo repository GitHub:

> [!NOTE]
> Se non è ancora stato creato un repository GitHub, vedere la sezione [Creazione di un repository remoto su GitHub](#creating-a-remote-repo-on-github).

1. Per creare il primo commit, passare a **controllo della versione > verifica e commit** nella barra dei menu.

2. Nella scheda Stato scegliere **Commit** nella parte superiore sinistra.

3. Scrivere un messaggio di commit, ad esempio "First Commit", quindi fare clic su **Commit**:

    ![Eseguire il commit delle modifiche iniziali nel repository Git](media/version-control-git-publish-new2.png)

4. Nella barra dei menu passare quindi a **Controllo della versione > Gestisci rami ed origini remote**.

5. Passare alla scheda **Origini remote**, quindi fare clic su **Aggiungi**.

6. Nella finestra **Origine remota** aggiungere i dettagli del repository GitHub precedentemente creato e fare clic su **OK**:

    ![Configurare le origini remote per il repository Git](media/version-control-git-publish-new3.png)

7. Chiudere la finestra **Configurazione del repository GIT**, quindi nella barra dei menu passare a **Controllo della versione > Esegui push delle modifiche**.

8. Nella finestra **Esegui push nel repository** fare clic sul pulsante **Esegui push delle modifiche**:

    ![Eseguire il push delle modifiche nel repository remoto](media/version-control-git-publish-new4.png)

9. Quando richiesto, immettere il nome utente e la password di GitHub.

> [!NOTE]
> Se per l'account è abilitata l'autenticazione a due fattori, è necessario creare un token di accesso, che verrà usato al posto della password. Se non è stato creato un token di accesso, seguire i passaggi descritti nella documentazione relativa ai [token di accesso](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) Git.

Visual Studio per Mac eseguirà ora il push delle modifiche nel repository GitHub remoto:

![Conferma di operazione push completata](media/version-control-git11.png)

## <a name="clone-an-existing-repository"></a>Clonare un repository esistente

È probabile che sarà necessario usare un repository di GitHub che esiste solo in remoto e non nel computer locale. Visual Studio per Mac consente di clonare rapidamente questo repository. Seguire questa procedura per clonarlo nel computer in uso:

1. Nella barra dei menu selezionare **controllo della versione > repository clone**:

2. Verrà visualizzata la scheda **Connetti con URL** :

    ![Scheda Connetti con URL con i dettagli immessi](media/version-control-git13.png)

3. Nella pagina di GitHub del repository remoto, scegliere il pulsante **Clone or Download** (Clona o scarica) e copiare l'URL fornito:

    ![URL di GitHub visualizzato](media/version-control-git14.png)

4. Sostituire tutto il testo nel campo immissione **URL** nella scheda **Connetti con URL** . In questo modo, la maggior parte degli altri campi in questa scheda viene popolata, come illustrato nell'immagine nel passaggio #2.

5. Immettere la directory in cui si vuole clonare il repository e premere **Clone**.

> [!NOTE]
> Se il repository ha dimensioni maggiori di 4 GB, potrebbero verificarsi problemi.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si verificano problemi con l'inizializzazione del progetto con un repository remoto vuoto, provare a seguire questa procedura:

1. Andare alla cartella della soluzione.
1. Premere **Comando + MAIUSC + .** per visualizzare i file e le cartelle nascosti.
1. Se è presente una cartella **.git**, eliminarla.
1. Se è presente un file **gitignore**, eliminarlo.
1. Premere **Comando + MAIUSC + .** per nascondere i file e le cartelle.
1. Aprire la soluzione in Visual Studio per Mac.
1. Nel riquadro della soluzione selezionare il nodo della soluzione.
1. Andare al menu Controllo della versione e scegliere **Pubblica nel Controllo della versione**.
1. Seguire la procedura dell'esercitazione precedente partendo dal passaggio 6.

## <a name="see-also"></a>Vedere anche

- [Controllo della versione in Visual Studio (in Windows)](/visualstudio/version-control/)
