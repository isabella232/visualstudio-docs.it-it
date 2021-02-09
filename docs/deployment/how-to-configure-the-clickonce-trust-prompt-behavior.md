---
title: Configurare il comportamento della richiesta di attendibilità ClickOnce | Microsoft Docs
description: Informazioni su come configurare la richiesta di attendibilità ClickOnce per controllare se gli utenti finali hanno la possibilità di installare applicazioni ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8cb23eeee53990113d779e241adb8dcf1ab0cf16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890305"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Procedura: Configurare il comportamento di richiesta di attendibilità di ClickOnce
È possibile configurare la richiesta di attendibilità ClickOnce per controllare se gli utenti finali hanno la possibilità di installare applicazioni ClickOnce, ad esempio Windows Form applicazioni, Windows Presentation Foundation applicazioni, applicazioni console, applicazioni browser WPF e soluzioni Office. Per configurare la richiesta di attendibilità, impostare le chiavi del registro di sistema nel computer di ogni utente finale.

 Nella tabella seguente vengono illustrate le opzioni di configurazione che è possibile applicare a ognuna delle cinque zone (Internet, UntrustedSites, computer, LocalIntranet e TrustedSites).

|Opzione|Valore impostazione del registro di sistema|Descrizione|
|------------|----------------------------|-----------------|
|Abilitare la richiesta di attendibilità.|`Enabled`|La richiesta di attendibilità ClickOnce viene visualizzata in modo che gli utenti finali possano concedere l'attendibilità alle applicazioni ClickOnce.|
|Limitare la richiesta di attendibilità.|`AuthenticodeRequired`|La richiesta di attendibilità ClickOnce viene visualizzata solo se le applicazioni ClickOnce sono firmate con un certificato che identifica il server di pubblicazione.|
|Disabilitare la richiesta di attendibilità.|`Disabled`|La richiesta di attendibilità ClickOnce non viene visualizzata per le applicazioni ClickOnce che non sono firmate con un certificato attendibile in modo esplicito.|

 La tabella seguente illustra il comportamento predefinito per ogni zona. La colonna applicazioni si riferisce Windows Form applicazioni, Windows Presentation Foundation applicazioni, applicazioni browser WPF e applicazioni console.

|Zona|Applicazioni|soluzioni Office|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 È possibile eseguire l'override di queste impostazioni abilitando, limitando o disabilitando la richiesta di attendibilità ClickOnce.

## <a name="enable-the-clickonce-trust-prompt"></a>Abilitare la richiesta di attendibilità ClickOnce
 Abilitare la richiesta di attendibilità per una zona quando si desidera che gli utenti finali vengano presentati con la possibilità di installare ed eseguire qualsiasi applicazione ClickOnce che deriva da tale zona.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per abilitare la richiesta di attendibilità ClickOnce mediante l'editor del registro di sistema

1. Aprire l'editor del registro di sistema:

    1. Fare clic sul pulsante **Start** e quindi scegliere **Esegui**.

    2. Nella casella **Apri** Digitare `regedit` , quindi fare clic su **OK**.

2. Trovare la chiave del registro di sistema seguente:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se la chiave non esiste, crearla.

3. Aggiungere le sottochiavi seguenti come **valore di stringa**, se non esistono già, con i valori associati indicati nella tabella seguente.

    |Sottochiave valore stringa|Valore|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Per le soluzioni Office, `Internet` ha il valore predefinito `AuthenticodeRequired` e `UntrustedSites` ha il valore `Disabled` . Per tutti gli altri, `Internet` il valore predefinito è `Enabled` .

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Per abilitare la richiesta di attendibilità ClickOnce a livello di codice

1. Creare un'applicazione console Visual Basic o Visual C# in Visual Studio.

2. Aprire il file *Program. vb* o *Program.cs* per la modifica e aggiungere il codice seguente.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "Enabled")
    key.SetValue("TrustedSites", "Enabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Enabled");
    key.SetValue("LocalIntranet", "Enabled");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "Enabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Compilare ed eseguire l'applicazione.

## <a name="restrict-the-clickonce-trust-prompt"></a>Limita la richiesta di attendibilità ClickOnce
 Limitare la richiesta di attendibilità in modo che le soluzioni debbano essere firmate con certificati Authenticode con identità nota prima che agli utenti venga richiesta una decisione di attendibilità.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per limitare la richiesta di attendibilità ClickOnce mediante l'editor del registro di sistema

1. Aprire l'editor del registro di sistema:

    1. Fare clic sul pulsante **Start** e quindi scegliere **Esegui**.

    2. Nella casella **Apri** Digitare `regedit` , quindi fare clic su **OK**.

2. Trovare la chiave del registro di sistema seguente:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se la chiave non esiste, crearla.

3. Aggiungere le sottochiavi seguenti come **valore di stringa**, se non esistono già, con i valori associati indicati nella tabella seguente.

    |Sottochiave valore stringa|Valore|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Per limitare la richiesta di attendibilità ClickOnce a livello di codice

1. Creare un'applicazione console Visual Basic o Visual C# in Visual Studio.

2. Aprire il file *Program. vb* o *Program.cs* per la modifica e aggiungere il codice seguente.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "AuthenticodeRequired")
    key.SetValue("LocalIntranet", "AuthenticodeRequired")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "AuthenticodeRequired")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "AuthenticodeRequired");
    key.SetValue("LocalIntranet", "AuthenticodeRequired");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "AuthenticodeRequired");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Compilare ed eseguire l'applicazione.

## <a name="disable-the-clickonce-trust-prompt"></a>Disabilitare la richiesta di attendibilità ClickOnce
 È possibile disabilitare la richiesta di attendibilità in modo che gli utenti finali non dispongano dell'opzione per installare soluzioni non ancora considerate attendibili nei criteri di sicurezza.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per disabilitare la richiesta di attendibilità ClickOnce mediante l'editor del registro di sistema

1. Aprire l'editor del registro di sistema:

    1. Fare clic sul pulsante **Start** e quindi scegliere **Esegui**.

    2. Nella casella **Apri** Digitare `regedit` , quindi fare clic su **OK**.

2. Trovare la chiave del registro di sistema seguente:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se la chiave non esiste, crearla.

3. Aggiungere le sottochiavi seguenti come **valore di stringa**, se non esistono già, con i valori associati indicati nella tabella seguente.

    |Sottochiave valore stringa|Valore|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Per disabilitare la richiesta di attendibilità ClickOnce a livello di codice

1. Creare un'applicazione console Visual Basic o Visual C# in Visual Studio.

2. Aprire il file *Program. vb* o *Program.cs* per la modifica e aggiungere il codice seguente.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Disabled")
    key.SetValue("LocalIntranet", "Disabled")
    key.SetValue("Internet", "Disabled")
    key.SetValue("TrustedSites", "Disabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Disabled");
    key.SetValue("LocalIntranet", "Disabled");
    key.SetValue("Internet", "Disabled");
    key.SetValue("TrustedSites", "Disabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();

    ```

3. Compilare ed eseguire l'applicazione.

## <a name="see-also"></a>Vedi anche
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)
- [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)
- [Procedura: Abilitare le impostazioni di sicurezza ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Procedura: Impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Procedura: Impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Procedura: Eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](securing-clickonce-applications.md)
- [Procedura: Aggiungere un autore attendibile a un computer client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Procedura: Firmare nuovamente manifesti di applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
