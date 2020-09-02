---
title: 'Procedura: aggiungere un autore attendibile a un computer client per applicazioni ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 296aec3b2b5cd307400b230375a7171f158fee60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847700"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Procedura: aggiungere un autore attendibile a un computer client per applicazioni ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con la distribuzione di applicazioni attendibili, è possibile configurare i computer client in modo che le applicazioni [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] siano eseguite con un livello di attendibilità superiore senza chiedere conferma all'utente. Le procedure seguenti illustrano come usare lo strumento da riga di comando CertMgr.exe per aggiungere un certificato dell'autore all'archivio editori attendibili in un computer client.  
  
 I comandi utilizzati variano leggermente a seconda che l'autorità di certificazione (CA) che ha emesso il certificato sia parte della radice attendibile del client. Se un computer client Windows fa parte di un dominio conterrà, in un elenco, le autorità di certificazione considerate attendibili. Questo elenco è in genere configurato dall'amministratore di sistema. Se il certificato è stato rilasciato da una di queste fonti attendibili o da un'autorità di certificazione legata a una di queste fonti attendibili, è possibile aggiungere il certificato all'archivio radice attendibile del client. Se invece il certificato non è stato rilasciato da una di queste fonti attendibili, è necessario aggiungere il certificato sia all'archivio radice attendibile del client sia all'archivio autori attendibili.  
  
> [!NOTE]
> È necessario aggiungere i certificati in questo modo su ogni computer client in cui si intende distribuire un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] che richiede autorizzazioni elevate. I certificati possono essere aggiunti manualmente o mediante un'applicazione distribuita nei client. È sufficiente configurare questi computer una volta, dopo di che è possibile distribuire un numero qualsiasi di applicazioni [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] firmate con lo stesso certificato.  
  
 È anche possibile aggiungere un certificato a un archivio a livello di codice tramite la classe <xref:System.Security.Cryptography.X509Certificates.X509Store> .  
  
 Per una panoramica della distribuzione di applicazioni attendibili, vedere [Panoramica della distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Per aggiungere un certificato nell'archivio autori attendibili sotto la radice attendibile  
  
1. Ottenere un certificato digitale da un'autorità di certificazione.  
  
2. Esportare il certificato nel formato Base64 X.509 (.cer). Per ulteriori informazioni sui formati di certificato, vedere [esportare un certificato](https://technet.microsoft.com/library/cc730988(WS.10).aspx).  
  
3. Dal prompt dei comandi nei computer client eseguire il comando seguente:  
  
     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Per aggiungere un certificato nell'archivio autori attendibili sotto un'altra radice  
  
1. Ottenere un certificato digitale da un'autorità di certificazione.  
  
2. Esportare il certificato nel formato Base64 X.509 (.cer). Per ulteriori informazioni sui formati di certificato, vedere [esportare un certificato](https://technet.microsoft.com/library/cc730988(WS.10).aspx).  
  
3. Dal prompt dei comandi nei computer client eseguire il comando seguente:  
  
     **certmgr.exe -add good.cer -c -s -r localMachine Root**  
  
     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Protezione delle applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Panoramica della distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)   
 [Procedura: abilitare le impostazioni di sicurezza ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Procedura: impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Procedura: impostare autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Procedura: eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Procedura: aggiungere un autore attendibile a un computer client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Procedura: ripetere la firma dei manifesti dell'applicazione e della distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [Procedura: configurare il comportamento della richiesta di attendibilità ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
