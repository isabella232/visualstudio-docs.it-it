---
title: Uso di Git
description: Uso di Git in Visual Studio per Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: 3ce0967d4a0293ca5a0f41998c1e8363a4a91d74d01c05cc0770ea129edabca1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121437566"
---
# <a name="working-with-git"></a>Uso di Git

Git è un sistema di controllo della versione della versione distribuito che consente ai team di lavorare contemporaneamente sugli stessi documenti. Ciò significa che è presente un server centrale che contiene tutti i file ma quando viene estratto un repository da questa origine centrale, l'intero repository viene clonato nel computer locale.

Le sezioni seguenti illustrano come è possibile usare Git per il controllo della versione in Visual Studio per Mac.

## <a name="git-version-control-menu"></a>Menu Controllo della versione di Git

L'immagine seguente illustra le opzioni offerte da Visual Studio per Mac dalla voce di menu Controllo della versione:

![Voce di menu Controllo della versione](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Push e pull

Push e pull sono due delle azioni utilizzate più di frequente in Git. Per sincronizzare le modifiche apportate da altri utenti nel repository remoto, è necessario eseguire il **Pull** da tale posizione. Questa operazione viene eseguita in Visual Studio per Mac selezionando **Controllo della versione > Aggiorna soluzione**.

Dopo aver aggiornato i file, dopo averli rivisti e dopo averne eseguito il commit, è necessario eseguirne il **Push** nel repository remoto per consentire agli altri utenti di accedere alle modifiche apportate. Questa operazione viene eseguita in Visual Studio per Mac selezionando **Controllo della versione > Esegui push delle modifiche**. Verrà visualizzata la finestra di dialogo Push che consente di visualizzare le modifiche di cui si è eseguito il commit e di selezionare il ramo in cui eseguire il push:

![Finestra di dialogo che mostra il ramo in cui eseguire il commit](media/version-control-gitPush.png)

È anche possibile eseguire contemporaneamente il commit e il push delle modifiche, tramite la finestra di dialogo Commit:

![Opzione che mostra come eseguire commit e push contemporaneamente.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Segnala errore, Log e Unisci

Nella parte inferiore della finestra sono visualizzate cinque schede, come illustrato di seguito:

![Schede del controllo della versione](media/version-control-gitTabs.png)

Queste schede consentono le azioni seguenti:

* **Origine**: visualizza il file del codice sorgente.
* **Modifiche**: visualizza le modifiche del codice tra il file locale e il file di base. È anche possibile confrontare diverse versioni del file da hash diversi:

    ![Scheda Modifiche](media/version-control-gitChange.png)

* **Segnala errore**: visualizza il nome dell'utente associato a ogni sezione del codice.
* **Log**: visualizza tutti i commit, le ore, le date, i messaggi e gli utenti responsabili del file:

    ![Scheda Log](media/version-control-gitLog.png)

* **Unisci**: può essere usata in caso di un conflitto di unione quando si esegue il commit del lavoro. Mostra una rappresentazione visiva delle modifiche apportate dall'utente e dall'altro sviluppatore, per consentire di combinare correttamente entrambe le sezioni del codice.

## <a name="switching-branches"></a>Cambio di rami

Per impostazione predefinita, il primo ramo creato in un repository è noto come **ramo** principale. Tecnicamente non c'è nulla di diverso tra il ramo principale e qualsiasi altro, ma il ramo principale è quello che viene più spesso pensato nei team di sviluppo come ramo "live" o "di produzione".

È possibile creare una linea di sviluppo indipendente diramando main (o qualsiasi altro ramo). In questo modo viene fornita una nuova versione del ramo principale in un momento nel tempo, consentendo lo sviluppo indipendentemente da ciò che è "live". Questo uso dei rami è frequente per funzionalità nell'ambiente di sviluppo.

Gli utenti possono creare tutti i rami che desiderano per ogni repository, ma è consigliabile eliminare i rami quando si finisce di usarli per mantenere organizzato il repository.

Per visualizzare i rami in Visual Studio per Mac, spostarsi su **Controllo della versione > Gestisci rami ed origini remote...**:

![Visualizzazione dei rami](media/version-control-gitBranch2.png)

Passare a un altro ramo selezionandolo nell'elenco e premendo il pulsante **Passa al ramo**.

Per creare un nuovo ramo, selezionare il pulsante **Nuovo** nella finestra di dialogo di configurazione del repository Git. Inserire il nome del nuovo ramo:

![Creare un nuovo ruolo](media/version-control-gitBranch.png)

È anche possibile impostare un ramo remoto per il proprio ramo di _verifica_. Per altre informazioni sui rami di verifica, vedere la [documentazione su Git](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Vedere il ramo corrente nella finestra della soluzione, accanto al nome del progetto:

 ![Ramo corrente visualizzato nella finestra della soluzione](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Revisione e commit

Per rivedere le modifiche nei file, usare le schede Modifiche, Segnala errore, Log e Unisci in ogni documento, come illustrato precedentemente in questo argomento.

Rivedere tutte le modifiche del progetto spostandosi sulla voce di menu **Controllo della versione > Review Solution and Commit (Rivedi soluzione ed esegui commit)**:

![Visualizzazione di revisione del codice](media/version-control-gitReviewCommit.png)

Ciò consente di visualizzare tutte le modifiche in ogni file di un progetto con l'opzione di annullarle, creare una patch o eseguire il commit.

Per eseguire il commit di un file nel repository remoto, premere **Commit,** immettere un messaggio di commit e confermare con il pulsante Commit:

![Commit di un file](media/version-control-gitCommit.png)

Dopo aver eseguito il commit delle modifiche, eseguirne il push in un repository remoto per renderle visibili agli altri utenti.

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Vedi anche

* [Share your code with Visual Studio 2017 and Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017) (Condividere il codice con Visual Studio 2017 e Azure Repos Git)
