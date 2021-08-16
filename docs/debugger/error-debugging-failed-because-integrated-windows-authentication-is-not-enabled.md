---
description: L'autenticazione dell'utente che ha richiesto il debug non è stata possibile a causa di un errore di autenticazione.
title: Debug non riuscito perché l'autenticazione Windows integrata non è abilitata | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ac1922c66702ba5b0e5e3d10d7057c31239dffd492243f6d2dda37eddaaa33c6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379409"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Errore: debug non riuscito. Non è attivata l'autenticazione di Windows integrata
L'autenticazione dell'utente che ha richiesto il debug non è stata possibile a causa di un errore di autenticazione. Questo errore può verificarsi quando si tenta di eseguire un'applicazione Web o un servizio Web XML. Una causa di questo errore è la mancata attivazione dell'autenticazione di Windows integrata. Per attivarla, seguire i passaggi della procedura relativa all'attivazione dell'autenticazione integrata di Windows.

 Se l'autenticazione integrata di Windows è stata attivata e l'errore si ripete, è possibile che sia dovuto all'attivazione dell'**autenticazione del digest per i server di dominio Windows**. In questa situazione è necessario consultare l'amministratore di rete.

### <a name="to-enable-integrated-windows-authentication"></a>Per attivare l'autenticazione di Windows integrata

1. Accedere al server Web mediante un account amministratore.

2. Fare clic sul pulsante **Start** e scegliere **Pannello di controllo**.

3. In **Pannello di controllo** fare doppio clic su **Strumenti di amministrazione**.

4. Fare doppio clic su **Internet Information Services**.

5. Fare clic sul nodo del server Web.

     Verrà aperta una cartella **Siti Web** sotto il nome del server.

6. È possibile configurare l'autenticazione per tutti i siti Web complessivamente o singolarmente. Per configurare l'autenticazione per tutti i siti Web, fare clic con il pulsante destro del mouse sulla cartella **Siti Web**, quindi scegliere **Proprietà**. Per configurare l'autenticazione per un singolo sito Web, aprire la cartella **Siti Web**, fare clic con il pulsante destro del mouse sul singolo sito Web, quindi scegliere **Proprietà**.

     Verrà visualizzata la finestra di dialogo **Proprietà**.

7. Fare clic sulla scheda **Sicurezza directory**.

8. Nella sezione **Controllo autenticazione e accesso anonimo** fare clic su **Modifica**.

     Verrà visualizzata la finestra di dialogo **Metodi di autenticazione**.

9. In **Accesso con autenticazione** selezionare **Autenticazione integrata di Windows**.

10. Scegliere **OK** per chiudere la finestra di dialogo **Metodi di autenticazione**.

11. Scegliere **OK** per chiudere la finestra di dialogo **Proprietà**.

12. Chiudere la finestra **Internet Information Services**.

### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Per attivare l'autenticazione integrata di Windows in Windows Vista/IIS 7

1. Accedere al server Web mediante un account amministratore.

2. Attivare Autenticazione di Windows e Compatibilità di gestione con IIS 6, se tale operazione non è stata già effettuata, seguendo questi passaggi:

    1. Fare **clic sul pulsante Start**, **Pannello di controllo** e quindi su **Programmi**.

    2. In **Programmi e funzionalità** fare clic su **Attivazione o disattivazione delle funzionalità Windows**.

         Verrà visualizzata la finestra di dialogo Controllo di accesso utente e verrà richiesto di immettere l'autorizzazione per continuare.

    3. Fare clic su **Continue**.

         Verrà visualizzata la finestra di dialogo Funzionalità Windows.

    4. Nell'elenco delle funzionalità espandere il nodo **Internet Information Services**.

    5. In **Internet Information Services** espandere il nodo **Servizi Web**.

    6. In **Servizi World Wide Web** fare clic su **Sicurezza**.

    7. Scegliere **Autenticazione di Windows**.

    8. In **Internet Information Services** espandere il nodo **Strumenti di gestione Web**.

    9. In **Strumenti di gestione Web** espandere il nodo **Compatibilità di gestione con IIS 6**, quindi selezionare la casella di controllo **IIS 6 Metabase and IIS 6 Configuration Compatibility**.

    10. In **Strumenti di gestione Web** selezionare **Console di gestione IIS**, quindi scegliere **OK**.

    11. Per rendere effettive queste modifiche, riavviare il computer.

3. Fare **clic su Start** e quindi su **Pannello di controllo**.

4. Selezionare **Visualizzazione classica**, quindi fare doppio clic su **Strumenti di amministrazione**.

5. Nella colonna **Nome** fare doppio clic su **Gestione Internet Information Services (IIS)**.

6. Nella colonna **Connessioni** espandere il nodo del server.

     Verrà aperta una cartella **Siti Web** sotto il nome del server.

7. Espandere il nodo **Siti Web**, quindi fare clic sul sito Web per il quale si desidera attivare l'autenticazione integrata di Windows.

8. Il titolo del riquadro centrale viene sostituito con il nome del sito Web selezionato. Sotto l'intestazione **IIS** di questo riquadro fare doppio clic su **Autenticazione**.

     Il titolo del riquadro viene sostituito con **Autenticazione**.

9. Nella colonna **Nome** del riquadro **Autenticazione** fare clic con il pulsante destro del mouse su **Autenticazione di Windows**, quindi scegliere **Attiva**.

10. Chiudere la finestra **Gestione Internet Information Services (IIS)**.

## <a name="see-also"></a>Vedi anche
- [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Autenticazione digest Microsoft](/windows/win32/secauthn/microsoft-digest-authentication)
- [Esecuzione di applicazioni Web Windows Vista con IIS 7.0 e Visual Studio](/previous-versions/aa964620(v=vs.140))
