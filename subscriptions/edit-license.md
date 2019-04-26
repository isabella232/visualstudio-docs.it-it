---
title: Modificare le sottoscrizioni nel portale di amministrazione | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: conceptual
description: Informazioni su come gli amministratori possono modificare le assegnazioni di sottoscrizione.
searchscope: VS Subscription
ms.openlocfilehash: d3dbc2e05d85ed8277d7a7c0f530dfa92da7dba6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946246"
---
# <a name="editing-visual-studio-subscription-assignments"></a>Modifica delle assegnazioni di sottoscrizione di Visual Studio

L'amministratore delle sottoscrizioni può modificare le sottoscrizioni assegnate a utenti all'interno dell'organizzazione.  Questo articolo presenta il tipo di modifiche che è possibile apportare, insieme ai passaggi necessari.

## <a name="making-changes-to-subscriber-information"></a>Apportare modifiche alle informazioni relative al sottoscrittore
È possibile modificare le informazioni di un sottoscrittore per correggere gli errori o aggiornare le informazioni.

Per modificare un sottoscrittore, selezionare i puntini di sospensione (…) che vengono visualizzati accanto all'indirizzo di posta elettronica del sottoscrittore quando vi si passa sopra il mouse. Verrà visualizzato un elenco a discesa.  Selezionare **Modifica** per modificare i dati del sottoscrittore. È anche possibile fare doppio clic sulla riga del sottoscrittore nella griglia per aprire la finestra di modifica.
> [!div class="mx-imgBorder"]
> ![Selezionare un sottoscrittore da modificare](_img/edit-license/select-subscriber.png)

È possibile aggiornare nome, cognome, paese, lingua e i download effettuati dal sottoscrittore. Modificare le informazioni del sottoscrittore, quindi fare clic su **Salva**.

   > [!NOTE]
   > Se è necessario modificare il livello di sottoscrizione per un sottoscrittore, sarà necessario eliminare l'utente dal portale e aggiungerlo nuovamente. I livelli di sottoscrizione non sono modificabili.

## <a name="editing-multiple-subscribers-using-bulk-edit"></a>Modifica di più sottoscrittori tramite modifiche di massa

È possibile modificare più sottoscrittori contemporaneamente utilizzando il processo di modifiche di massa. Questa funzionalità viene utilizzata principalmente per le organizzazioni che devono effettuare modifiche dell'indirizzo di posta elettronica aziendale o se un'organizzazione ha deciso di limitare l'accesso ai download.

   > [!IMPORTANT]
   > I livelli di sottoscrizione (ad esempio Enterprise, Professional e così via) e gli identificatori univoci globali della sottoscrizione non possono essere modificati.  Se si tenta di eseguire il caricamento con questi elementi modificati, il caricamento avrà esito negativo.

1. Per modificare contemporaneamente più sottoscrittori, passare alla scheda Sottoscrittori. Nella barra multifunzione in alto, fare clic su **Modifiche di massa**.

2. La procedura di Modifiche di massa usa un modello di Excel per apportare modifiche a informazioni relative al sottoscrittore. Nella casella Modifiche di massa, fare clic su **Esporta in Excel** per scaricare l'elenco corrente di sottoscrittori, incluse tutte le relative informazioni.
   > [!div class="mx-imgBorder"]
   > ![Modifica di una licenza - Esportazione di un elenco di modifiche in blocco](_img/edit-license/edit-license-bulk-edit-export.png)

3. Successivamente, salvare il file in locale in modo che sia più facile trovarlo e apportare le modifiche necessarie prima di caricarlo. Per garantire una corretta esecuzione del caricamento, **non modificare il livello di sottoscrizione o l'identificatore univoco globale di sottoscrizione** perché altrimenti il caricamento avrebbe esito negativo.

4. Tornare al portale di amministrazione delle sottoscrizioni di Visual Studio e nella finestra di dialogo Modifiche in blocco, fare clic su **Sfoglia**. Selezionare il file di Excel salvato e fare clic su **OK**. Lo stato di avanzamento del caricamento verrà visualizzato sullo schermo.
   > [!div class="mx-imgBorder"]
   > ![Modifica di una licenza - Caricamento file delle modifiche di massa](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Dopo aver caricato il file, verrà visualizzata una notifica per comunicare l'esito positivo. A questo punto, tutte le modifiche si rifletteranno nelle informazioni relative al sottoscrittore.
