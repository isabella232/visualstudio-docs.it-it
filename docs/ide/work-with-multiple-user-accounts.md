---
title: Gestire più account utente
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0eaba2b81467c60e900aa70b633e15b81175ffc7
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283470"
---
# <a name="work-with-multiple-user-accounts"></a>Gestire più account utente

Se si dispone di più account Microsoft e/o di account aziendali o dell’istituto di istruzione è possibile aggiungerli tutti a Visual Studio in modo che le risorse di tutti gli account siano accessibili Da tutti gli account senza dover autenticarsi separatamente. I servizi di Azure, Application Insights, Team Foundation Server e Office 365 attualmente supportano l'esperienza di accesso semplificato. Servizi aggiuntivi possono diventare disponibili come passare del tempo.

Dopo l'aggiunta di più account in un computer, tale set di account comune con l'utente se si accede a Visual Studio in un altro computer. È importante notare che, anche se si spostano i nomi di account, le credenziali non. Pertanto, verrà richiesto di immettere le credenziali per gli altri account la prima volta che si tenta di utilizzare le risorse nel nuovo computer.

Questa procedura dettagliata illustra come aggiungere più account a Visual Studio e come visualizzare le risorse accessibili da tali account in posizioni quali la finestra di dialogo **Aggiungi servizio connesso** , **Esplora server**, e **Team Explorer**.

## <a name="sign-in-to-visual-studio"></a>Accedi a Visual Studio

- Accedere a Visual Studio con un account Microsoft o un account aziendale. Il nome utente dovrebbe essere visualizzato nell'angolo superiore della finestra, come illustrato nella figura seguente:

     ![Utente attualmente connesso](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Accedere all'account Azure in Esplora server

Premere **CTRL**+**ALT**+**S** per aprire **Esplora server**. Scegliere l'icona di **Azure** per espanderla e visualizzare le risorse disponibili nell'account Azure associato all'ID usato per accedere a Visual Studio. Dovrebbe apparire una struttura simile a quella seguente, che però contiene le risorse dell'utente.

![Esplora server con nodo Strumenti di Azure espanso](../ide/media/vs2015_serverexplorer.png)

La prima volta che si usa Visual Studio su qualsiasi dispositivo specifico, la finestra di dialogo visualizzerà solo le sottoscrizioni registrate con l'ID di accesso all'IDE. Per accedere alle risorse di altri account direttamente da **Esplora server**, fare clic con il pulsante destro del mouse sul nodo **Azure**, scegliere **Gestisci e filtra sottoscrizioni** e aggiungere gli account dal controllo di selezione account. È possibile scegliere un altro account, se necessario, facendo clic sulla freccia giù, sceglierlo dall'elenco di account collegati. Dopo aver scelto l'account, è possibile scegliere le sottoscrizioni da visualizzare in **Esplora server**.

![Finestra di dialogo Gestisci sottoscrizioni Microsoft Azure](../ide/media/vs2015_manage_subs.png)

Alla successiva apertura di **Esplora server** verranno visualizzate le risorse per la sottoscrizione.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Accedere all'account Azure tramite la finestra di dialogo Aggiungi servizio connesso

1. Creare un progetto di app UWP in C#.

1. Scegliere il nodo del progetto in **Esplora soluzioni** e quindi **Aggiungi** > **Servizio connesso**. Viene visualizzata la procedura guidata **Aggiungi servizio connesso** con l'elenco dei servizi dell'account Azure associato all'ID di accesso di Visual Studio. Notare che non è necessario effettuare separatamente l'accesso ad Azure. Tuttavia, è necessario accedere ad altri account la prima volta che si tenta di accedere alle risorse da un determinato computer.

    > [!WARNING]
    > Se è la prima volta che si crea un'app UWP in Visual Studio in un computer specifico, verrà richiesto di abilitare il dispositivo per la modalità di sviluppo passando a **Impostazioni** > **Aggiornamento e sicurezza** > **Per sviluppatori** nel computer. Per altre informazioni, vedere [Abilitare il dispositivo per lo sviluppo](/windows/uwp/get-started/enable-your-device-for-development).

### <a name="access_azure"></a> Accedere ad Azure Active Directory in un progetto Web

Con Azure AD viene abilitato il supporto di Single Sign-On per utenti finali in applicazioni Web ASP.NET MVC o per Autenticazione di AD in servizi API Web. L'autenticazione di dominio è diverso da autenticazione degli account utente singoli; gli utenti che dispongono dell'accesso al dominio Active Directory è possono utilizzare gli account di Windows Azure esistenti per connettersi alle applicazioni web. Le applicazioni di Office 365 inoltre possono utilizzare l'autenticazione di dominio. Per un esempio pratico, creare un'applicazione Web (**File** > **Nuovo progetto** > **C#** > **Cloud** > **Applicazione Web ASP.NET**). Nella finestra di dialogo **Nuovo progetto ASP.NET** scegliere **Modifica autenticazione**. Autenticazione guidata viene visualizzata e consente di scegliere il tipo di autenticazione da utilizzare nell'applicazione.

![Finestra di dialogo Modifica autenticazione per ASP.NET](../ide/media/vs2015_change_authentication.png)

Per altre informazioni sui diversi tipi di autenticazione in ASP.NET, vedere [Creare progetti Web ASP.NET in Visual Studio 2013](http://www.asp.net/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) (le informazioni sull'autenticazione sono ancora pertinenti per le versioni attuali di Visual Studio).

### <a name="access-your-team-foundation-server-tfs-organization"></a>Accedere all'organizzazione di Team Foundation Server (TFS)

Nel menu principale scegliere **Team** > **Connetti a Team Foundation Server** per visualizzare la finestra di **Team Explorer**. Fare clic su **Seleziona progetti**. A questo punto nella casella di riepilogo sotto **Seleziona Team Foundation Server** verrà visualizzato l'URL dell'organizzazione TFS. Quando si seleziona l'URL verrà registrato senza dover immettere nuovamente le credenziali.

## <a name="add-a-second-user-account-to-visual-studio"></a>Aggiungere un secondo account utente a Visual Studio

Fare clic sulla freccia GIÙ accanto al nome utente nell'angolo superiore di Visual Studio. Quindi scegliere la voce di menu **Impostazioni account**. Verrà visualizzata la finestra **Gestione account** con l'account usato per accedere. Scegliere il collegamento **Aggiungi nuovo account** in basso nella finestra di dialogo per aggiungere un nuovo account Microsoft oppure un nuovo account aziendale o dell'istituto di istruzione.

![Selezione di account di Visual Studio](../ide/media/vs2015_acct_picker.png)

Seguire i prompt visualizzati per immettere le credenziali del nuovo account. La figura seguente illustra **Gestione account** dopo che un utente ha aggiunto il proprio account aziendale *Contoso.com*.

![Gestione account](../ide/media/vs2015_accountmanager.gif)

## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Tornare alla procedura guidata Aggiungi servizio connesso e a Esplora server

Passare ora di nuovo a **Esplora server**, fare clic con il pulsante destro del mouse sul nodo **Azure** e scegliere **Gestisci e filtra sottoscrizioni**. Scegliere il nuovo account facendo clic sulla freccia a discesa vicino all'account corrente, quindi scegliere le sottoscrizioni da visualizzare in **Esplora server**. Verranno visualizzati tutti i servizi associati alla sottoscrizione specificata. Anche se non si è connessi all'IDE di Visual Studio con il secondo account, si è connessi ai servizi e alle risorse di questo account. Lo stesso vale per **Progetto** > **Aggiungi servizio connesso** e **Team** > **Connetti a Team Foundation Server**.

## <a name="see-also"></a>Vedere anche

- [Accedere a Visual Studio](signing-in-to-visual-studio.md)
