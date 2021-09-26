---
title: Eseguire Visual Studio sottoscrizioni a un nuovo contratto | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 80e3b300-f2fc-40d4-bbb2-c831a2fa5d34
ms.date: 09/09/2021
ms.topic: how-to
description: Questo articolo descrive come gli amministratori possono eseguire la migrazione delle sottoscrizioni assegnate da un contratto a un altro.
ms.openlocfilehash: c92cf112607211c5ad998a26ca5722e8207aea49
ms.sourcegitcommit: 364e106fcbf4fb6af534e81d8b700901f79f4ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/26/2021
ms.locfileid: "129013184"
---
# <a name="migrate-subscriptions-from-one-agreement-to-another"></a>Eseguire la migrazione delle sottoscrizioni da un contratto a un altro
Se sono state Visual Studio ai sottoscrittori come parte di un contratto e la società acquista un nuovo contratto, potrebbe essere necessario eseguire la migrazione dei sottoscrittori dal contratto corrente a quello nuovo. Questo articolo illustra come spostare le sottoscrizioni assegnate nel nuovo contratto.  

Quando si spostano i sottoscrittori nel nuovo contratto, ecco cosa accade:
- Ottiene un nuovo GUID della sottoscrizione.
- I vantaggi vengono reimpostati. Ad esempio, se in precedenza hanno usato un vantaggio di training, riceveranno una nuova istanza di tale vantaggio. 
- Se usavano crediti singoli di Azure nella sottoscrizione precedente, dovranno attivare una nuova sottoscrizione e trasferirne gli asset di Azure. 

Il processo per lo spostamento dei sottoscrittori nel nuovo contratto è costituito da tre passaggi:
1. Esportare le assegnazioni di sottoscrizione correnti dal contratto precedente. 
2. Preparare un elenco di sottoscrizioni per il caricamento nel nuovo contratto. 
3. Upload'elenco delle sottoscrizioni al nuovo contratto.

> [!IMPORTANT]
> Prima di avviare questo processo, tenere presente le considerazioni seguenti:
> - Se il rivenditore ha selezionato l'opzione per trasferire automaticamente i sottoscrittori al nuovo contratto al momento dell'acquisto, è possibile che le modifiche non verranno visualizzati fino a 48-72 ore dopo l'invio del contratto. Prima di procedere con il processo di spostamento manuale dei sottoscrittori, rivolgersi al rivenditore.  
> - È possibile usare Azure Active Directory (Azure AD) per semplificare il processo di spostamento dei sottoscrittori nel nuovo contratto. Per altre informazioni, vedere [Assegnazione di sottoscrizioni tramite Azure AD gruppi.](assign-azure-ad.md)

## <a name="export-your-current-subscription-assignments"></a>Esportare le assegnazioni di sottoscrizione correnti
Il primo passaggio per eseguire la migrazione delle sottoscrizioni assegnate da un contratto a un altro consiste nell'esportare le assegnazioni di sottoscrizione correnti come file CSV. Nel portale Sottoscrizioni di Visual Studio di amministrazione è possibile esportare un elenco dei sottoscrittori e informazioni dettagliate sulle relative assegnazioni. 

Sono incluse le informazioni seguenti: 
- Nome del Sottoscrittore.
- Indirizzo di posta elettronica. 
- Indirizzo di posta elettronica di notifica. 
- Livello di sottoscrizione.
- Data assegnata.
- Data di scadenza.
- Campo di riferimento.
- Indica se i download sono abilitati.
- Paese. 
- Lingua.
- Stato della sottoscrizione.
- GUID della sottoscrizione.

L'elenco viene esportato come file CSV che è possibile aprire facilmente in Microsoft Excel in modo da poterlo preparare per il caricamento nel nuovo contratto.

Per esportare le sottoscrizioni assegnate:
1. Accedere al portale [di amministrazione.](https://manage.visualstudio.com)
2. Selezionare la **scheda** Esporta.
3. Un file CSV verrà scaricato nel computer. Il nome del file rifletterà il nome e il tipo del contratto corrente e la data di creazione del file.  

   > [!div class="mx-imgBorder"]
   > ![Esportare sottoscrittori](_img/exporting-subscriptions/exporting-subscriptions.png "Screenshot che mostra il pulsante Esporta per scaricare l'elenco delle sottoscrizioni assegnate.")

## <a name="prepare-your-subscription-list-for-upload-to-the-new-agreement"></a>Preparare l'elenco delle sottoscrizioni per il caricamento nel nuovo contratto
Seguire questa procedura per aprire l'elenco delle sottoscrizioni esportate e spostare i dati rilevanti in un modello per il caricamento nel nuovo contratto:
1. Individuare e aprire il file creato durante l'esportazione dell'elenco delle sottoscrizioni. Dovrebbero essere visualizzati i nomi di colonna seguenti e i relativi dati associati:
   - **Nome sottoscrittore**
   - **Posta elettronica**
   - **Indirizzo di posta elettronica di notifica**
   - Gruppo AAD 
   - **Livello di sottoscrizione**
   - Assegnato
   - Attivato 
   - Data di scadenza (UTC)
   - **Riferimento**
   - **Download**
   - **Paese**
   - **Lingua**
   - Stato sottoscrizione
   - **GUID della sottoscrizione**
   - Stato utilizzo
 
   Non tutti i campi nel file CSV esportato sono necessari nel file usato per caricare le sottoscrizioni nel nuovo contratto. I campi visualizzati in **grassetto nell'elenco** precedente verranno visualizzati nel modello usato per caricare l'elenco. 

2. Scaricare il Excel modello che verrà utilizzato per caricare le sottoscrizioni.  
   1. Accedere al portale [di amministrazione.](https://manage.visualstudio.com)
   1. Nella scheda **Gestisci sottoscrittori** selezionare il nuovo contratto nell'elenco a discesa:
      > [!div class="mx-imgBorder"]
      > ![Scegliere l'accordo](_img/migrate-subscriptions/choose-agreement.png "Screenshot che mostra l'elenco a discesa per la selezione del nuovo contratto.")
   1. Selezionare **Aggiungi** e quindi **Aggiungi in blocco.**
   1. Verrà **Upload finestra di dialogo** più sottoscrittori.  
   1. Nel passaggio 2 selezionare il **collegamento Scarica** per scaricare il modello. 
      > [!div class="mx-imgBorder"]
      > ![Scaricare il modello di aggiunta in blocco](_img/migrate-subscriptions/download-template.png "Screenshot che mostra il pulsante Scarica.")
   
      Il modello verrà visualizzato nella cartella Download.  
   1. Aprire il modello.

3. Aprire sia l'elenco dei sottoscrittori esportati che il modello di aggiunta in blocco vuoto. Copiare manualmente i dati della sottoscrizione dall'elenco esportato e incollarli nel modello. 

    Si noti che l'ordine delle colonne nell'elenco dei sottoscrittori esportati è diverso dall'ordine nel modello. Anche i nomi delle colonne sono leggermente diversi. La tabella seguente mostra i nomi dei campi comuni a entrambi i fogli di calcolo:

   | Esporta elenco                | Aggiungere in blocco un modello  |
   |----------------------------|--------------------|
   | Nome sottoscrittore            | Nome               |
   | Email                      | Messaggio di posta elettronica di accesso      |
   | Indirizzo di posta elettronica di notifica | Messaggio di posta elettronica di notifica |
   | Livello di sottoscrizione         | Livello di sottoscrizione |
   | Riferimento                  | Riferimento          |
   | Download                  | Download          |
   | Paese                    | Paese            |
   | Linguaggio                   | Linguaggio           |
   | GUID della sottoscrizione          | GUID della sottoscrizione  |

   > [!TIP]
   > Se si hanno molti sottoscrittori, può essere utile usare i tasti di scelta rapida quando si copiano e incollano i dati. Per selezionare tutte le voci in una colonna come Nome Sottoscrittore, selezionare la prima voce nella colonna (non l'intestazione di colonna), premere **CTRL+MAIUSC** e quindi premere freccia GIÙ. Verranno selezionati tutti i dati nella colonna.  

4. Quando tutti i dati vengono spostati nel modello di aggiunta in blocco, salvare il modello e chiuderlo. Questo elenco è l'elenco di sottoscrizioni che verrà caricato nel nuovo contratto.

## <a name="upload-your-subscription-list-to-the-new-agreement"></a>Upload l'elenco delle sottoscrizioni al nuovo contratto
1.  Nel portale [di amministrazione,](https://manage.visualstudio.com)se la **finestra Upload più** sottoscrittori è ancora aperta, selezionare il **pulsante** Sfoglia. Passare al percorso in cui è stato salvato l'elenco delle sottoscrizioni, selezionarlo e quindi selezionare **Apri.**  
    > [!div class="mx-imgBorder"]
    > ![Sfogliare il modello](_img/migrate-subscriptions/browse-template.png "Screenshot che mostra il pulsante Sfoglia nella finestra Upload più sottoscrittori.")
1. Il nome dell'elenco delle sottoscrizioni verrà visualizzato nella finestra **Upload più sottoscrittori.** Selezionare **OK** per caricare il file. 
 
   Nel portale di amministrazione potrebbe essere visualizzato brevemente un messaggio di stato che informa che è in corso il caricamento di un file. Al termine del caricamento, verrà visualizzato il messaggio Sottoscrittori **aggiornati correttamente.**
La migrazione dei sottoscrittori dal contratto precedente a quello nuovo è stata completata.  
> [!NOTE]
> Dopo aver aggiunto i sottoscrittori al nuovo contratto, è necessario rimuoverli dal contratto precedente. La loro rimozione impedirà loro di ricevere notifiche relative alle sottoscrizioni precedente.

## <a name="resources"></a>Risorse
- Per informazioni sulla gestione delle Visual Studio, vedere Supporto [Visual Studio sottoscrizioni](https://aka.ms/vsadminhelp).

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- [Usare Azure Active Directory gruppi per assegnare altre sottoscrizioni](assign-azure-ad.md)
- [Modificare le sottoscrizioni esistenti](edit-license.md)
