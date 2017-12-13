---
title: Modificare le sottoscrizioni nel portale di amministrazione | Visual Studio Marketplace
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Informazioni su come gli amministratori possono modificare le assegnazioni di sottoscrizione.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 985dea7a301130d4641ef9ba3ca2c5ae67218ad4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="editing-visual-studio-subscription-assignments"></a>Modifica delle assegnazioni di sottoscrizione in Visual Studio

## <a name="making-changes-to-subscriber-information"></a>Apportare modifiche alle informazioni relative al sottoscrittore
È possibile modificare le informazioni di un sottoscrittore per correggere gli errori o aggiornare le informazioni. 
**Si noti che la modifica dell'indirizzo di posta elettronica di un sottoscrittore comporta la reimpostazione degli eventuali vantaggi esistenti.**

Per modificare un sottoscrittore, selezionare i puntini di sospensione (…) che vengono visualizzati accanto all'indirizzo di posta elettronica del sottoscrittore quando vi si passa sopra il mouse. Verrà visualizzato un elenco a discesa.  Selezionare **Modifica** per modificare i dati del sottoscrittore. È possibile anche fare doppio clic sulla riga del sottoscrittore nella griglia per aprire la finestra di modifica.

![Selezionare un sottoscrittore da modificare](_img\edit-license\select-subscriber.png)

È possibile aggiornare nome, cognome, paese, lingua e i download effettuati dal sottoscrittore. Modificare le informazioni del sottoscrittore, quindi fare clic su **Salva**.

![Modifica dettagli del sottoscrittore](_img\edit-license\edit-subscriber.png)

Nota: se è necessario modificare il livello di sottoscrizione di un sottoscrittore, sarà necessario eliminare l'utente dal portale e aggiungerlo nuovamente. I livelli di sottoscrizione non sono modificabili.

## <a name="editing-multiple-subscribers-by-using-bulk-edit"></a>Modifica di più sottoscrittori tramite modifiche di massa

È possibile modificare più sottoscrittori contemporaneamente utilizzando il processo di modifiche di massa. Questa funzionalità viene utilizzata principalmente per le organizzazioni che devono effettuare modifiche dell'indirizzo di posta elettronica aziendale o se un'organizzazione ha deciso di limitare l'accesso ai download. **IMPORTANTE:** i livelli di sottoscrizione (ad esempio Enterprise, Professional, ecc.) e gli identificatori univoci globali della sottoscrizione non possono essere modificati.  Se si tenta di eseguire il caricamento con questi elementi modificati, il caricamento avrà esito negativo.  

1.  Per modificare contemporaneamente più sottoscrittori, passare alla scheda Sottoscrittori. Nella barra multifunzione in alto, fare clic su **Modifiche di massa**. 

![Modifica di una licenza - Modifiche di massa](_img\edit-license\edit-license-bulk-edit.png)

2.  La procedura di Modifiche di massa usa un modello di Excel per apportare modifiche a informazioni relative al sottoscrittore. Nella casella Modifiche di massa, fare clic su **Esporta in Excel** per scaricare l'elenco corrente di sottoscrittori, incluse tutte le relative informazioni. 

![Modifica di una licenza - Esportazione di un elenco di modifiche in blocco](_img\edit-license\edit-license-bulk-edit-export.png)

3.  Successivamente, salvare il file in locale in modo che sia più facile trovarlo e apportare le modifiche necessarie prima di caricarlo. Per garantire una corretta esecuzione del caricamento, **non modificare il livello di sottoscrizione o l'identificatore univoco globale di sottoscrizione** perché altrimenti il caricamento avrebbe esito negativo. 

4.  Tornare al portale di amministrazione delle sottoscrizioni di Visual Studio e nella finestra di dialogo Modifiche in blocco, fare clic su **Sfoglia**. Selezionare il file di Excel salvato e fare clic su **OK**. Lo stato di avanzamento del caricamento verrà visualizzato sullo schermo.

![Modifica di una licenza - Caricamento file delle modifiche di massa](_img\edit-license\edit-license-bulk-file-upload.png)

5.  Dopo aver caricato il file, verrà visualizzata una notifica per comunicare l'esito positivo. 

![Modifica di una licenza - Caricamento modifiche di massa completato](_img\edit-license\edit-license-bulk-upload-complete.png)


