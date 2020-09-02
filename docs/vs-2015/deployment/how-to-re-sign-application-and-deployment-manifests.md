---
title: "Procedura: ripetere la firma dei manifesti dell'applicazione e della distribuzione | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5956ad23fe22c7c36b712fac61df268586142df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697551"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Procedura: ripetere la firma dei manifesti dell'applicazione e di distribuzione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dopo aver apportato le modifiche alle proprietà di distribuzione nel manifesto dell'applicazione per Windows Forms applicazioni, applicazioni Windows Presentation Foundation (XBAP) o soluzioni Office, è necessario firmare di nuovo entrambi i manifesti dell'applicazione e della distribuzione con un certificato. Questo processo aiuta ad assicurare che nei computer degli utenti finali non siano installati file alterati.  
  
 Un altro scenario in cui è possibile firmare di nuovo i manifesti è quando i clienti vogliono firmare i manifesti dell'applicazione e della distribuzione con il proprio certificato.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Firma di nuovo i manifesti dell'applicazione e della distribuzione  
 Questa procedura presuppone che siano già state apportate modifiche al file manifesto dell'applicazione (. manifest). Per altre informazioni, vedere [procedura: modificare le proprietà di distribuzione](https://msdn.microsoft.com/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Per firmare nuovamente i manifesti dell'applicazione e della distribuzione con Mage.exe  
  
1. Aprire una finestra del **prompt dei comandi di Visual Studio** .  
  
2. Passare alla cartella che contiene i file manifesto che si desidera firmare.  
  
3. Digitare il comando seguente per firmare il file manifesto dell'applicazione. Sostituire ManifestFileName con il nome del file manifesto più l'estensione. Sostituire il certificato con il percorso relativo o il percorso completo del file di certificato e sostituire password con la password per il certificato.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Ad esempio, è possibile eseguire il comando seguente per firmare un manifesto dell'applicazione per un componente aggiuntivo, un'applicazione Windows Form o un'applicazione Windows Presentation Foundation browser. I certificati temporanei creati da Visual Studio non sono consigliati per la distribuzione in ambienti di produzione.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4. Digitare il comando seguente per aggiornare e firmare il file manifesto di distribuzione, sostituendo i nomi di segnaposto come nel passaggio precedente.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Ad esempio, è possibile eseguire il comando seguente per aggiornare e firmare un manifesto di distribuzione per un componente aggiuntivo di Excel, un Windows Forms Application o un'applicazione Windows Presentation Foundation browser.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. Facoltativamente, copiare il manifesto della distribuzione master (Publish \\ *appname*. Application) nella directory di distribuzione della versione (file publish\Application \\ *appname*_*Version*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Aggiornamento e ripetizione della firma dei manifesti dell'applicazione e della distribuzione  
 Questa procedura presuppone che siano già state apportate modifiche al file manifesto dell'applicazione (. manifest), ma che siano presenti altri file aggiornati. Quando i file vengono aggiornati, è necessario aggiornare anche l'hash che rappresenta il file.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Per aggiornare e firmare nuovamente i manifesti dell'applicazione e della distribuzione con Mage.exe  
  
1. Aprire una finestra del **prompt dei comandi di Visual Studio** .  
  
2. Passare alla cartella che contiene i file manifesto che si desidera firmare.  
  
3. Rimuovere l'estensione di file. deploy dai file nella cartella publish output.  
  
4. Digitare il comando seguente per aggiornare il manifesto dell'applicazione con i nuovi hash per i file aggiornati e firmare il file manifesto dell'applicazione. Sostituire ManifestFileName con il nome del file manifesto più l'estensione. Sostituire il certificato con il percorso relativo o il percorso completo del file di certificato e sostituire password con la password per il certificato.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Ad esempio, è possibile eseguire il comando seguente per firmare un manifesto dell'applicazione per un componente aggiuntivo, un'applicazione Windows Form o un'applicazione Windows Presentation Foundation browser. I certificati temporanei creati da Visual Studio non sono consigliati per la distribuzione in ambienti di produzione.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. Digitare il comando seguente per aggiornare e firmare il file manifesto di distribuzione, sostituendo i nomi di segnaposto come nel passaggio precedente.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Ad esempio, è possibile eseguire il comando seguente per aggiornare e firmare un manifesto di distribuzione per un componente aggiuntivo di Excel, un Windows Forms Application o un'applicazione Windows Presentation Foundation browser.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6. Aggiungere di nuovo l'estensione di file. deploy ai file, ad eccezione dei file manifesto dell'applicazione e della distribuzione.  
  
7. Facoltativamente, copiare il manifesto della distribuzione master (Publish \\ *appname*. Application) nella directory di distribuzione della versione (file publish\Application \\ *appname*_*Version*).  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione delle applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Panoramica della distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)   
 [Procedura: abilitare le impostazioni di sicurezza ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Procedura: impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Procedura: impostare autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Procedura: eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Procedura: aggiungere un autore attendibile a un computer client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Procedura: configurare il comportamento della richiesta di attendibilità ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
