---
title: Modificare Visual Studio sottoscrizioni nel portale di amministrazione | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 03/21/2021
ms.topic: how-to
description: Informazioni su come gli amministratori possono modificare le assegnazioni delle sottoscrizioni.
ms.openlocfilehash: a545a276714c7fb21d9adc966b2ef0c9e250250c
ms.sourcegitcommit: da19ed1e48259b219c61c4cb9e98b006004a5766
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/21/2021
ms.locfileid: "128052834"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Modificare assegnazioni di sottoscrizioni di Visual Studio
L'amministratore della sottoscrizione può apportare modifiche alle sottoscrizioni assegnate a singoli utenti all'interno dell'organizzazione.  Questo articolo presenta il tipo di modifiche che è possibile apportare, insieme ai passaggi necessari.

   > [!NOTE]
   > Se è necessario modificare i dettagli della sottoscrizione per un sottoscrittore assegnato tramite un gruppo Azure Active Directory, è necessario rimuoverli dal gruppo e aggiungerli singolarmente nel portale di amministrazione.  

## <a name="change-subscriber-information"></a>Modificare le informazioni sul sottoscrittore
È possibile modificare le informazioni di un sottoscrittore per correggere gli errori o aggiornare le informazioni.

Per modificare un sottoscrittore, selezionare i puntini di sospensione (…) che vengono visualizzati accanto all'indirizzo di posta elettronica del sottoscrittore quando vi si passa sopra il mouse. Verrà visualizzato un elenco a discesa.  Selezionare **Modifica** per modificare i dati del sottoscrittore. 
> [!div class="mx-imgBorder"]
> ![Selezionare un sottoscrittore da modificare](_img/edit-license/select-subscriber.png "Fare clic sui puntini di sospensione e scegliere Modifica.")

È possibile aggiornare il nome, il cognome, il livello di sottoscrizione, l'indirizzo di posta elettronica, il paese, la lingua, i download e il campo di riferimento del sottoscrittore. Modificare le informazioni del sottoscrittore e fare clic su **Salva**.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Modificare più sottoscrittori usando la modifica di massa

È possibile modificare più sottoscrittori contemporaneamente utilizzando il processo di modifiche di massa. Questa funzionalità viene utilizzata principalmente per le organizzazioni che devono effettuare modifiche dell'indirizzo di posta elettronica aziendale o se un'organizzazione ha deciso di limitare l'accesso ai download.

Guardare questo video o leggere per informazioni su come modificare più sottoscrittori usando la modifica in blocco. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vkAF]

> [!NOTE]
> Non modificare i GUID della sottoscrizione nel modello. Vedere l'articolo [sull'assegnazione di GUID di sottoscrizione specifici.](assign-guid.md)

1. Per modificare più sottoscrittori contemporaneamente, passare alla scheda Sottoscrittori . Nella barra multifunzione in alto fare clic su **Modifica in blocco.**

2. La procedura di Modifiche di massa usa un modello di Excel per apportare modifiche a informazioni relative al sottoscrittore. Nella casella Modifiche di massa, fare clic su **Esporta in Excel** per scaricare l'elenco corrente di sottoscrittori, incluse tutte le relative informazioni.
   > [!div class="mx-imgBorder"]
   > ![Modifica di una licenza - Esportazione di un elenco di modifiche in blocco](_img/edit-license/edit-license-bulk-edit-export.png "Fare clic su Esporta questo excel per creare un elenco delle sottoscrizioni correnti.")

3. Successivamente, salvare il file in locale in modo che sia più facile trovarlo e apportare le modifiche necessarie prima di caricarlo. 

4. Tornare al portale di amministrazione delle sottoscrizioni di Visual Studio e nella finestra di dialogo Modifiche in blocco, fare clic su **Sfoglia**. Selezionare il file di Excel salvato e fare clic su **OK**. Lo stato di avanzamento del caricamento verrà visualizzato sullo schermo.
   > [!div class="mx-imgBorder"]
   > ![Modifica di una licenza - Caricamento file delle modifiche di massa](_img/edit-license/edit-license-bulk-file-upload1.png "Passare al percorso del file di Excel completato, selezionarlo e fare clic su OK.")

5. Dopo aver caricato il file, verrà visualizzata una notifica per comunicare l'esito positivo. A questo punto, tutte le modifiche si rifletteranno nelle informazioni relative al sottoscrittore.

## <a name="resources"></a>Risorse
- [Supporto delle sottoscrizioni](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- È necessario assegnare un ID sottoscrizione specifico? Vedere Assegnazione di un ID sottoscrizione. 
- Per informazioni sull'individuazione di una sottoscrizione specifica, vedere [Cercare una sottoscrizione](search-license.md).
- Per creare un elenco di tutte le sottoscrizioni,  vedere [Esportare sottoscrizioni](exporting-subscriptions.md).