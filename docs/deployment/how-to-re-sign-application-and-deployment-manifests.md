---
title: "Procedura: firmare nuovamente i manifesti dell'applicazione e della distribuzione Documenti Microsoft"
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc69ce1f79644d7f4b35fbb1c1e3a41691761390
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649157"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Procedura: Firmare nuovamente manifesti di applicazione e distribuzione
Dopo aver apportato modifiche alle proprietà di distribuzione nel manifesto dell'applicazione per le applicazioni Windows Form, le applicazioni Windows Presentation Foundation (xbap) o le soluzioni Office, è necessario firmare nuovamente i manifesti dell'applicazione e di distribuzione con un certificato. Questo processo aiuta ad assicurare che nei computer degli utenti finali non siano installati file alterati.

 Un altro scenario in cui è possibile firmare nuovamente i manifesti è quando i clienti desiderano firmare i manifesti dell'applicazione e di distribuzione con il proprio certificato.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Firmare nuovamente i manifesti dell'applicazione e di distribuzione
 In questa procedura si presuppone che siano già state apportate modifiche al file manifesto dell'applicazione (*.manifest*). Per ulteriori informazioni, vedere [Procedura: modificare le proprietà](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472)di distribuzione .

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Per firmare nuovamente i manifesti dell'applicazione e di distribuzione con Mage.exe

1. Aprire una finestra del prompt dei comandi di Visual Studio.Open a **Visual Studio Command Prompt** window.

2. Passare alla cartella che contiene i file manifesto che si desidera firmare.

3. Digitare il comando seguente per firmare il file manifesto dell'applicazione. Sostituire *ManifestFileName* con il nome del file manifesto più l'estensione. Sostituire *Certificate* con il percorso relativo o completo del file del certificato e sostituire *Password* con la password per il certificato.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Ad esempio, è possibile eseguire il comando seguente per firmare un manifesto dell'applicazione per un componente aggiuntivo, un'applicazione Windows Form o un'applicazione browser Windows Presentation Foundation.For example, you could run the following command to sign an application manifest for an add-in, a Windows Form application, or a Windows Presentation Foundation browser application. I certificati temporanei creati da Visual Studio non sono consigliati per la distribuzione in ambienti di produzione.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. Digitare il comando seguente per aggiornare e firmare il file manifesto di distribuzione, sostituendo i nomi segnaposto come nel passaggio precedente.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Ad esempio, è possibile eseguire il comando seguente per aggiornare e firmare un manifesto di distribuzione per un componente aggiuntivo di Excel, un'applicazione Windows Form o un'applicazione browser Windows Presentation Foundation.For example, you could run the following command to update and sign a deployment manifest for an Excel add-in, a Windows Forms application, or a Windows Presentation Foundation browser application.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Facoltativamente, copiare il manifesto di distribuzione master (*\\\<publish appname>.application*) nella directory di distribuzione della versione (*publish, Application Files\\\<appname\<>_ version>*).

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Aggiornare e firmare nuovamente i manifesti dell'applicazione e di distribuzioneUpdate and re-sign the application and deployment manifests
 In questa procedura si presuppone che siano già state apportate modifiche al file manifesto dell'applicazione (*.manifest*), ma che siano presenti altri file aggiornati. Quando i file vengono aggiornati, deve essere aggiornato anche l'hash che rappresenta il file.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Per aggiornare e firmare nuovamente i manifesti dell'applicazione e di distribuzione con Mage.exe

1. Aprire una finestra del prompt dei comandi di Visual Studio.Open a **Visual Studio Command Prompt** window.

2. Passare alla cartella che contiene i file manifesto che si desidera firmare.

3. Rimuovere l'estensione *.deploy* dai file nella cartella di output di pubblicazione.

4. Digitare il comando seguente per aggiornare il manifesto dell'applicazione con i nuovi eventi per i file aggiornati e firmare il file manifesto dell'applicazione. Sostituire *ManifestFileName* con il nome del file manifesto più l'estensione. Sostituire *Certificate* con il percorso relativo o completo del file del certificato e sostituire *Password* con la password per il certificato.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Ad esempio, è possibile eseguire il comando seguente per firmare un manifesto dell'applicazione per un componente aggiuntivo, un'applicazione Windows Form o un'applicazione browser Windows Presentation Foundation.For example, you could run the following command to sign an application manifest for an add-in, a Windows Form application, or a Windows Presentation Foundation browser application. I certificati temporanei creati da Visual Studio non sono consigliati per la distribuzione in ambienti di produzione.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Digitare il comando seguente per aggiornare e firmare il file manifesto di distribuzione, sostituendo i nomi segnaposto come nel passaggio precedente.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Ad esempio, è possibile eseguire il comando seguente per aggiornare e firmare un manifesto di distribuzione per un componente aggiuntivo di Excel, un'applicazione Windows Form o un'applicazione browser Windows Presentation Foundation.For example, you could run the following command to update and sign a deployment manifest for an Excel add-in, a Windows Forms application, or a Windows Presentation Foundation browser application.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. Aggiungere di nuovo l'estensione del file *.deploy* ai file, ad eccezione dei file del manifesto dell'applicazione e della distribuzione.

7. Facoltativamente, copiare il manifesto di distribuzione master (*\\\<publish appname>.application*) nella directory di distribuzione della versione (*publish, Application Files\\\<appname\<>_ version>*).

## <a name="see-also"></a>Vedere anche
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)
- [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)
- [Procedura: Abilitare le impostazioni di sicurezza ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Procedura: Impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Procedura: Impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Procedura: Eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](securing-clickonce-applications.md)
- [Procedura: Aggiungere un autore attendibile a un computer client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Procedura: Configurare il comportamento di richiesta di attendibilità di ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)