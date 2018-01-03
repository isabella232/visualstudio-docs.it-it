---
title: Visual Studio Tools per Unity - Procedura dettagliata di Azure - Configurazione | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: BAE62C27-CA7A-4466-8738-3DB880221CE1
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 25424ea06c01224bb1b35f783be82a857b991adf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="configure-easy-tables-in-azure"></a>Configurare tabelle semplici in Azure

Le tabelle semplici sono una funzionalità delle [app per dispositivi mobili di Azure](https://azure.microsoft.com/services/app-service/mobile/) che consentono la configurazione e la gestione di tabelle SQL direttamente nell'interfaccia utente grafica del portale di Azure. Le app per dispositivi mobili di Azure supportano molte funzionalità, ma l'ambito di questo esempio è limitato alla lettura e alla scrittura di dati archiviati in un back-end di app per dispositivi mobili di Azure da un progetto Unity.

## <a name="create-a-new-azure-mobile-app"></a>Creare una nuova app per dispositivi mobili di Azure

Accedere al [portale di Azure](https://ms.portal.azure.com). Se non si ha una sottoscrizione di Azure, la [versione di prova gratuita](https://azure.microsoft.com/en-us/free/) o i crediti inclusi in [Visual Studio Dev Essentials](https://www.visualstudio.com/dev-essentials/) sono più che sufficienti per completare questa procedura dettagliata.

**Dopo l'accesso al portale:**

1. Selezionare **Nuovo > Web e dispositivi mobili > App per dispositivi mobili > Crea**.

  ![Creare una nuova app per dispositivi mobili](media/vstu_azure-configure-easy-tables-image1.png)

2. Configurare la nuova app per dispositivi mobili:

  * **Nome app**. Questa impostazione crea l'URL usato per connettersi al back-end dell'app per dispositivi mobili di Azure. È necessario scegliere un nome univoco, indicato dal segno di spunta verde.

  * **Sottoscrizione**. Scegliere la sottoscrizione che la nuova app per dispositivi mobili userà per la fatturazione.

  * **Gruppo di risorse**. Gruppi di risorse consentono una gestione più semplice delle risorse correlate. Per impostazione predefinita, Azure crea un nuovo gruppo di risorse con lo stesso nome della nuova app. Per la procedura dettagliata l'impostazione predefinita è adeguata.

  *  **Piano di servizio app/Località**. Il piano di servizio determina la potenza di calcolo, la posizione e il costo delle risorse che Azure usa per ospitare la nuova app per dispositivi mobili. Per impostazione predefinita, Azure crea un nuovo piano di servizio con alcune impostazioni predefinite. Si tratta dell'opzione più semplice per questa procedura dettagliata. È tuttavia possibile usare questo menu per personalizzare il piano tariffario di un nuovo piano di servizio o di una nuova area geografica. È anche possibile modificare le impostazioni di un piano di servizio dopo la distribuzione di questo.

  ![Creare una nuova app per dispositivi mobili](media/vstu_azure-configure-easy-tables-image2.png)

3. Selezionare **Crea** e concedere ad Azure alcuni minuti per distribuire la nuova risorsa. Quando la distribuzione è completata, nel portale di Azure viene visualizzata una notifica.

## <a name="add-a-new-data-connection"></a>Aggiungere una nuova connessione dati

4. Dopo il completamento della distribuzione, fare clic sul pulsante **Tutte le risorse** e quindi selezionare l'app per dispositivi mobili appena creata.

  ![Selezionare la nuova app per dispositivi mobili](media/vstu_azure-configure-easy-tables-image3.png)

5. Nel pannello appena aperto, far scorrere verso il basso il menu a sinistra e fare clic sul pulsante **Tabelle semplici** sotto l'intestazione **MOBILE**.

  ![Selezionare tabelle semplici](media/vstu_azure-configure-easy-tables-image4.png)

6. Fare clic sul messaggio **È necessario configurare tabelle semplici/API semplici** azzurro visualizzato lungo la parte superiore del pannello Tabelle semplici.

  ![Fare clic sul messaggio Tabelle semplici](media/vstu_azure-configure-easy-tables-image5.png)

7. Fare clic sul messaggio **Per usare tabelle semplici, è necessario un database. Per crearne uno, fare clic qui**.

  ![Fare clic sul messaggio sulla creazione del database](media/vstu_azure-configure-easy-tables-image6.png)

8. Nel pannello Connessioni dati, fare clic sul pulsante **Aggiungi**.

  ![Fare clic sul pulsante Aggiungi](media/vstu_azure-configure-easy-tables-image7.png)

9. Nel pannello Aggiungi connessione dati selezionare **Database SQL**.

  ![Selezionare un database SQL](media/vstu_azure-configure-easy-tables-image8.png)

10. Verrà aperto un pannello per la configurazione di un nuovo database SQL e di un nuovo server SQL:

  * **Nome**. Immettere un nome per il database.

  * **Server di destinazione**. Fare clic su **Server di destinazione** per aprire il pannello Nuovo server.

      * **Nome server**. Immettere un nome per il server.

      * **Accesso amministratore server e Password**. Creare un nome utente e una password per l'amministratore del server.

      * **Posizione**. Scegliere una posizione nelle vicinanze per il server.

      * Verificare che la casella di controllo **Consenti ai servizi di Azure di accedere al server** rimanga selezionata.

      * Fare clic su **Seleziona** per completare la configurazione del server.

    * **Piano tariffario**. Per la procedura dettagliata lasciare invariata l'impostazione predefinita. Sarà possibile modificarla in seguito.

    * **Regole di confronto**. Lasciare invariata l'impostazione predefinita.

    * Fare clic su **Seleziona** per completare la configurazione del database.

    ![Configurare il server SQL e il database](media/vstu_azure-configure-easy-tables-image9.png)

11. Tornando al pannello Aggiungi dati connessione, fare clic su **Stringa di connessione**. Quando viene visualizzato il pannello Stringa di connessione, lasciare invariate le impostazioni predefinite e fare clic su **OK**.

  ![Fare clic su Stringa di connessione](media/vstu_azure-configure-easy-tables-image9.1.png)

12. Tornando al pannello Aggiungi dati connessione, il testo "MS_TableConnectionString" non è più in corsivo. Fare clic su **OK** e concedere ad Azure alcuni minuti per creare la nuova connessione dati. Quando il processo è completato, si riceve una notifica.

  ![Fare clic su OK.](media/vstu_azure-configure-easy-tables-image9.2.png)

## <a name="complete-the-easy-table-initialization"></a>Completare l'inizializzazione delle tabelle semplici

13. Dopo la creazione della nuova connessione dati, fare clic sul pulsante **Tutte le risorse** e tornare nuovamente all'app per dispositivi mobili. È importante eseguire questo passaggio per aggiornare il messaggio sulla configurazione delle tabelle semplici.

14. Scorrere verso il basso e selezionare **Tabelle semplici** e selezionare di nuovo il messaggio **È necessario configurare Tabelle semplici/API semplici** azzurro.

  ![Fare clic sul messaggio sulle tabelle semplici](media/vstu_azure-configure-easy-tables-image5.png)

15. Questa volta il messaggio nel pannello visualizzato sotto l'intestazione **1** segnala "Esiste già una connessione dati". Sotto l'intestazione **2** selezionare la casella di controllo **Sono consapevole che questa operazione comporterà la sovrascrittura di tutti i contenuti del sito**. Ora fare clic su **Inizializza app** e attendere qualche minuto che Azure completi il processo di inizializzazione. Una nuova notifica informerà del completamento del processo.

  ![Fare clic su Inizializza app](media/vstu_azure-configure-easy-tables-image10.png)

## <a name="next-step"></a>Passaggio successivo

* [Creare tabelle semplici](visual-studio-tools-for-unity-azure-setup.md)
