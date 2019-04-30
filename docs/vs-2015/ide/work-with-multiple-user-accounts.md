---
title: Usare più account utente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: b73c865c-74e0-420e-89cc-43524f4aafd0
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a60a44a20c06c24645583db4e16ce60cef166554
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441640"
---
# <a name="work-with-multiple-user-accounts"></a>Gestire più account utente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si dispone di più account Microsoft e/o di account aziendali o dell’istituto di istruzione è possibile aggiungerli tutti a Visual Studio in modo che le risorse di tutti gli account siano accessibili Da tutti gli account senza dover autenticarsi separatamente. Alla data in Visual Studio 2015 RTM, servizi di Azure, Application Insights, Team Foundation Server e Office 365 supportano l'esperienza di accesso semplificato. Servizi aggiuntivi possono diventare disponibili come passare del tempo.  
  
 Dopo l'aggiunta di più account in un computer, tale set di account comune con l'utente se si accede a Visual Studio in un altro computer. È importante notare che, anche se si spostano i nomi di account, le credenziali non. Pertanto, verrà richiesto di immettere le credenziali per gli altri account la prima volta che si tenta di utilizzare le risorse nel nuovo computer.  
  
 Questa procedura dettagliata illustra come aggiungere più account a Visual Studio e come visualizzare le risorse accessibili da tali account in posizioni quali la finestra di dialogo **Aggiungi servizio connesso** , **Esplora server**, e **Team Explorer**.  
  
#### <a name="sign-in-to-visual-studio"></a>Accedi a Visual Studio  
  
1. Accedere a Visual Studio 2015 con un account Microsoft o un account aziendale. Il nome utente dovrebbe essere visualizzato nell’angolo in alto a destra nella finestra, come illustrato nella figura seguente:  
  
     ![Utente attualmente connesso](../ide/media/vs2015-username.png "VS2015_UserName")  
  
### <a name="access-your-azure-account-in-server-explorer"></a>Accedere all'account Azure in Esplora server  
 Premere **CTRL+ALT+S** per aprire **Esplora server**. Fare clic sull'icona di Azure per espanderla e visualizzare le risorse disponibili nell'account Azure associato all'ID da usare per accedere a Visual Studio 2015. L'aspetto della finestra visualizzata è simile al seguente, ma le risorse visualizzate saranno quelle personali e non quelle dell'utente specificato:  
  
 ![Esplora server con nodo Strumenti di Azure espanso](../ide/media/vs2015-serverexplorer.png "VS2015_ServerExplorer")  
  
 La prima volta che si usa Visual Studio su qualsiasi dispositivo specifico, la finestra di dialogo visualizzerà solo le sottoscrizioni registrate con l'ID di accesso all'IDE. È possibile accedere alle risorse per tutti gli altri account direttamente da **Esplora Server** facendo clic sul nodo di Azure e scegliendo **Gestisci e filtra sottoscrizioni** e aggiungendo gli account dal controllo selezione account. È possibile scegliere un altro account, se necessario, facendo clic sulla freccia giù, sceglierlo dall'elenco di account collegati. Dopo aver scelto l'account, è possibile scegliere le sottoscrizioni con tale account che si desidera visualizzare in Esplora Server.  
  
 ![Finestra di dialogo Gestisci sottoscrizioni Microsoft Azure](../ide/media/vs2015-manage-subs.png "vs2015_manage_subs")  
  
 Alla successiva apertura di Esplora Server, vengono visualizzate le risorse per tale sottoscrizioni.  
  
### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Accedere all'account Azure tramite la finestra di dialogo Aggiungi servizio connesso  
  
1. Creare un progetto di app universale in C#.  
  
2. Fare clic con il pulsante destro del mouse sul nodo del progetto in Esplora soluzioni e scegliere **Aggiungi > Servizio connesso**. Verrà visualizzata la procedura guidata Aggiungi servizio connesso in cui viene presentato l'elenco dei servizi dell'account Azure associato all'ID di accesso di Visual Studio. Notare che non è necessario effettuare separatamente l'accesso ad Azure. Tuttavia, è necessario accedere ad altri account la prima volta che si tenta di accedere alle risorse da un determinato computer.  
  
    > [!WARNING]
    > Se questa è la prima volta che si sta creando un'app di Store in Visual Studio 2015 in un computer specifico, verrà richiesto di abilitare il dispositivo per la modalità di sviluppo passando a **impostazioni &#124; . Sicurezza e aggiornamenti &#124; per gli sviluppatori** nel computer. Per altre informazioni, vedere [Abilitare il dispositivo per lo sviluppo](https://msdn.microsoft.com/library/windows/apps/dn706236.aspx).  
  
### <a name="access_azure"></a> Accedere ad Azure Active Directory in un progetto Web  
 Con Azure AD viene abilitato il supporto per end-user Single Sign-On in applicazioni Web ASP.NET o per Autenticazione di AD in servizi API Web. L'autenticazione di dominio è diverso da autenticazione degli account utente singoli; gli utenti che dispongono dell'accesso al dominio Active Directory è possono utilizzare gli account di Windows Azure esistenti per connettersi alle applicazioni web. Le applicazioni di Office 365 inoltre possono utilizzare l'autenticazione di dominio. Per un esempio, creare un'applicazione Web (**File > Nuovo progetto > C# > Cloud > Applicazione Web ASP.NET**). Nella finestra di dialogo Nuovo progetto ASP.NET scegliere **Modifica autenticazione**. Autenticazione guidata viene visualizzata e consente di scegliere il tipo di autenticazione da utilizzare nell'applicazione.  
  
 ![Finestra di dialogo Modifica autenticazione per ASP.NET](../ide/media/vs2015-change-authentication.png "VS2015_change_authentication")  
  
 Per altre informazioni sui diversi tipi di autenticazione in ASP.NET, vedere [Creazione di progetti Web ASP.NET in Visual Studio 2013](http://www.asp.net/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) (le informazioni sull'autenticazione sono ancora rilevanti per Visual Studio 2015).  
  
### <a name="access-your-visual-studio-team-services-account"></a>Accedere all'account di Visual Studio Team Services  
 Nel menu principale scegliere **Team> Connetti a Team Foundation Server** per visualizzare la finestra **Team Explorer**. Fare clic su **Seleziona progetti team**. A questo punto nella casella di riepilogo sotto **Seleziona Team Foundation Server**verrà visualizzato l'URL dell'account di Visual Studio Team Services. Quando si seleziona l'URL verrà registrato senza dover immettere nuovamente le credenziali.  
  
## <a name="add-a-second-user-account-to-visual-studio"></a>Aggiungere un secondo account utente a Visual Studio  
 Fare clic sulla freccia GIÙ accanto al nome utente nell'angolo in alto a destra della finestra di Visual Studio. Fare clic sulla voce di menu **Impostazioni account** . Verrà visualizzata la finestra **Gestione account** con l'account usato per accedere. Fare clic sul collegamento **Aggiungi nuovo account** in basso a sinistra nella finestra di dialogo per aggiungere un nuovo account Microsoft oppure un nuovo account aziendale o dell'istituto di istruzione.  
  
 ![Selezione account di Visual Studio](../ide/media/vs2015-acct-picker.png "VS2015_acct_picker")  
  
 Seguire i prompt visualizzati per immettere le credenziali del nuovo account. La figura seguente mostra Gestione account dopo che un utente ha aggiunto il proprio account aziendale Contoso.com.  
  
 ![Gestione account](../ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")  
  
## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Accedere nuovamente alla procedura guidata Aggiungi servizio connesso e a Esplora server  
 Passare a **Esplora Server** destro del mouse sul nodo di Azure e scegliere Nuovo, **sottoscrizioni Gestisci e filtro**. Scegliere il nuovo account facendo clic sulla freccia accanto al conto corrente a discesa e quindi scegliere le sottoscrizioni che si desidera visualizzare in Esplora Server. Si noterà che tutti i servizi associati alla sottoscrizione specificata. Anche se non attualmente connessi all'IDE di Visual Studio con il secondo account, connesso a tale account servizi e risorse. Lo stesso vale per **Progetto> Aggiungi servizio connesso** e per **Team> Connetti a Team Foundation Server**.
