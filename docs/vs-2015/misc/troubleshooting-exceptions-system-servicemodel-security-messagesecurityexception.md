---
title: 'Risoluzione dei problemi relativi ad eccezioni: MessageSecurityException | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- System.ServiceModel.Security.MessageSecurityException exception
- MessageSecurityException exception
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: douge
ms.openlocfilehash: 9d886b8eeddc84c8b6597bca77e2d7b63ca21875
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532812"
---
# <a name="troubleshooting-exceptions-systemservicemodelsecuritymessagesecurityexception"></a>Risoluzione dei problemi relativi alle eccezioni: System.ServiceModel.Security.MessageSecurityException
Oggetto <xref:System.ServiceModel.Security.MessageSecurityException> eccezione viene generata quando [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] determina che un messaggio non è protetto correttamente oppure è stato manomesso. Questo errore si verifica il più delle volte quando le condizioni indicate di seguito si verificano contemporaneamente:  
  
-   Si utilizza un riferimento al servizio WCF su una connessione remota, ad esempio Connessione desktop remoto o Servizi terminal, per comunicare con un servizio WCF (con estensione svc) in un sito Web o in un progetto di applicazione Web.  
  
-   Non si dispone di autorizzazioni di amministrazione per il sito remoto.  
  
-   Le richieste a localhost sul sito remoto vengono gestite dal server di sviluppo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
## <a name="associated-tips"></a>Suggerimenti associati  
 **Risolvere i problemi di autenticazione NTLM quando si usa il Server di sviluppo ASP.Net.**  
 Nel server di sviluppo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] di solito la sicurezza NTLM (Windows NT Challenge/Response) è disattivata e ciò consente l'accesso anonimo. Per impostazione predefinita, quando si esegue una sessione di Servizi terminal o si utilizza una connessione remota, la sicurezza NTLM è attivata. Quando la sicurezza NTLM è attivata, tutte le richieste a localhost vengono convalidate in base alle credenziali dell'utente o al processo che ha avviato il server di sviluppo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. In questo modo è possibile ridurre le minacce per la sicurezza. L'autenticazione WCF viene eseguita comunque e l'utilizzo dei servizi WCF viene limitato esclusivamente agli account di amministratore.  
  
 Se un utente remoto può eseguire il sito Web utilizzando il [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server e utilizzare con un servizio WCF o un servizio Web, è possibile creare un'associazione al servizio personalizzata o disattivare la sicurezza NTLM.  
  
> [!IMPORTANT]
>  La disattivazione della sicurezza NTLM non è un'operazione consigliata e può costituire una minaccia per la sicurezza.  
  
 Se si crea un'associazione al servizio personalizzata è possibile mantenere la sicurezza dell'autenticazione NTLM.  
  
 Utilizzare i passaggi indicati di seguito per creare un'associazione al servizio personalizzata per il servizio WCF.  
  
#### <a name="to-create-a-custom-service-binding-for-the-wcf-service-hosted-inside-the-aspnet-development-server"></a>Per creare un'associazione al servizio personalizzata per il servizio WCF ospitato all'interno del server di sviluppo ASP.NET  
  
1.  Aprire il file Web.config del servizio WCF che genera l'eccezione.  
  
2.  Immettere le informazioni riportate di seguito nel file Web.config.  
  
    ```  
    <bindings>  
      <customBinding>  
        <binding name="Service1Binding">  
          <transactionFlow />  
          <textMessageEncoding />  
          <httpTransport authenticationScheme="Ntlm" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
3.  Salvare e chiudere il file Web.config.  
  
4.  Nel codice del servizio WCF o del servizio Web, sostituire il valore dell'endpoint con quanto segue:  
  
    ```  
    <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />  
    ```  
  
     Ciò garantisce l'utilizzo dell'associazione personalizzata da parte del servizio.  
  
5.  Aggiungere un riferimento al servizio nell'applicazione Web che vi ha accesso. Nella finestra di dialogo **Aggiungi riferimento al servizio** , aggiungere un riferimento al servizio come già fatto per il servizio originario che generava l'eccezione.  
  
 Utilizzare la procedura indicata di seguito per disabilitare la sicurezza NTLM quando si utilizza un riferimento a un servizio WCF.  
  
> [!IMPORTANT]
>  La disattivazione della sicurezza NTLM non è un'operazione consigliata e può costituire una minaccia per la sicurezza.  
  
#### <a name="to-turn-off-ntlm-security"></a>Per disattivare la sicurezza NTLM  
  
1.  In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nome del sito Web e scegliere **Pagine delle proprietà**.  
  
2.  Scegliere **Opzioni di avvio**, quindi deselezionare la casella di controllo **Autenticazione NTLM** .  
  
3.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.ServiceModel.Security.MessageSecurityException>   
 [Usare le informazioni sulle eccezioni](http://msdn.microsoft.com/library/e0a78c50-7318-4d54-af51-40c00aea8711)