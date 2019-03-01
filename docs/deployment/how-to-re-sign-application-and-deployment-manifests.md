---
title: "Procedura: firmare manifesti dell'applicazione e distribuzione | Microsoft Docs"
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
ms.openlocfilehash: 03606c1844ba058c5129affb5776cdc0a89849be
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610645"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Procedura: Firmare nuovamente manifesti di applicazione e distribuzione
Dopo aver apportato le modifiche apportate alle proprietà di distribuzione nel manifesto dell'applicazione per applicazioni Windows Forms, le applicazioni Windows Presentation Foundation (xbap) o soluzioni Office, è necessario firmare nuovamente l'applicazione e distribuzione dei manifesti con un certificato. Questo processo aiuta ad assicurare che nei computer degli utenti finali non siano installati file alterati.

 Un altro scenario in cui si potrebbero accedere nuovamente i manifesti è quando i clienti vogliono firmare l'applicazione e manifesti della distribuzione con il proprio certificato.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Firmare nuovamente i manifesti dell'applicazione e di distribuzione
 Questa procedura presuppone che sono già state apportate modifiche al file manifesto dell'applicazione (*manifest*). Per altre informazioni, vedere [procedura: modificare le proprietà di distribuzione](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Per firmare nuovamente l'applicazione e distribuzione dei manifesti con Mage.exe

1.  Aprire una **Prompt dei comandi di Visual Studio** finestra.

2.  Passare alla cartella che contiene i file manifesto che si desidera accedere.

3.  Digitare il comando seguente per firmare il file manifesto dell'applicazione. Sostituire *ManifestFileName* con il nome del file manifesto e l'estensione. Sostituire *certificato* con il percorso relativo o completo del file di certificato e sostituire *Password* con la password per il certificato.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Ad esempio, è possibile eseguire il comando seguente per firmare un manifesto dell'applicazione per un componente aggiuntivo, un'applicazione Windows Form o un'applicazione browser di Windows Presentation Foundation. Certificati temporanei creati da Visual Studio non sono consigliati per la distribuzione in ambienti di produzione.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4.  Digitare il comando seguente per aggiornare e firmare il file manifesto di distribuzione, sostituendo i nomi di segnaposto come nel passaggio precedente.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Ad esempio, è possibile eseguire il comando seguente per aggiornare e firmare un manifesto di distribuzione per un componente aggiuntivo di Excel, un'applicazione Windows Forms o un'applicazione browser di Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5.  Facoltativamente, copiare il manifesto di distribuzione master (*pubblicare\\\<NomeApp > Application*) nella directory di distribuzione della versione (*publish\Application file\\ \<appname > _\<versione >*).

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Aggiornare e firmare nuovamente i manifesti dell'applicazione e distribuzione
 Questa procedura presuppone che sono già state apportate modifiche al file manifesto dell'applicazione (*manifest*), ma che sono presenti altri file che sono stati aggiornati. Quando i file vengono aggiornati, è necessario aggiornare anche l'hash che rappresenta il file.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Per aggiornare e firmare nuovamente l'applicazione e distribuzione dei manifesti con Mage.exe

1.  Aprire una **Prompt dei comandi di Visual Studio** finestra.

2.  Passare alla cartella che contiene i file manifesto che si desidera accedere.

3.  Rimuovere il *deploy* cartella di output del file con estensione di file nella finestra pubblica.

4.  Digitare il comando seguente per aggiornare il manifesto dell'applicazione con i nuovi hash per i file aggiornati e firmare il file manifesto dell'applicazione. Sostituire *ManifestFileName* con il nome del file manifesto e l'estensione. Sostituire *certificato* con il percorso relativo o completo del file di certificato e sostituire *Password* con la password per il certificato.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Ad esempio, è possibile eseguire il comando seguente per firmare un manifesto dell'applicazione per un componente aggiuntivo, un'applicazione Windows Form o un'applicazione browser di Windows Presentation Foundation. Certificati temporanei creati da Visual Studio non sono consigliati per la distribuzione in ambienti di produzione.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5.  Digitare il comando seguente per aggiornare e firmare il file manifesto di distribuzione, sostituendo i nomi di segnaposto come nel passaggio precedente.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Ad esempio, è possibile eseguire il comando seguente per aggiornare e firmare un manifesto di distribuzione per un componente aggiuntivo di Excel, un'applicazione Windows Forms o un'applicazione browser di Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6.  Aggiungere il *deploy* estensione file al file, ad eccezione del fatto file manifesto dell'applicazione e distribuzione.

7.  Facoltativamente, copiare il manifesto di distribuzione master (*pubblicare\\\<NomeApp > Application*) nella directory di distribuzione della versione (*publish\Application file\\ \<appname > _\<versione >*).

## <a name="see-also"></a>Vedere anche
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)
- [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)
- [Procedura: Abilitare le impostazioni di sicurezza ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Procedura: Impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Procedura: Impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Procedura: Eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Procedura: Aggiungere un autore attendibile a un computer client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Procedura: Configurare il comportamento di richiesta di attendibilità di ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)