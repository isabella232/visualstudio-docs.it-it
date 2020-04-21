---
title: 'Procedura: configurare il comportamento del prompt di attendibilità ClickOnce Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5f1cca49f1b799b39969849e0a73bf1e6e296d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649166"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Procedura: Configurare il comportamento di richiesta di attendibilità di ClickOnce
È possibile configurare la richiesta di attendibilità ClickOnce per controllare se agli utenti finali viene data la possibilità di installare applicazioni ClickOnce, ad esempio applicazioni Windows Form, applicazioni Windows Presentation Foundation, applicazioni console, applicazioni browser WPF e soluzioni Office. Configurare la richiesta di attendibilità impostando le chiavi del Registro di sistema nel computer di ogni utente finale.

 Nella tabella seguente vengono illustrate le opzioni di configurazione che possono essere applicate a ognuna delle cinque aree (Internet, UntrustedSites, MyComputer, LocalIntranet e TrustedSites).

|Opzione|Valore dell'impostazione del Registro di sistema|Descrizione|
|------------|----------------------------|-----------------|
|Abilitare la richiesta di attendibilità.|`Enabled`|Il prompt di attendibilità ClickOnce viene visualizzato in modo che gli utenti finali possano concedere l'attendibilità alle applicazioni ClickOnce.The ClickOnce trust prompt is display so that end users can grant trust to ClickOnce applications.|
|Limitare la richiesta di attendibilità.|`AuthenticodeRequired`|Il prompt di attendibilità ClickOnce viene visualizzato solo se le applicazioni ClickOnce sono firmate con un certificato che identifica l'autore.|
|Disabilitare la richiesta di attendibilità.|`Disabled`|Il prompt di attendibilità ClickOnce non viene visualizzato per le applicazioni ClickOnce che non sono firmate con un certificato esplicitamente attendibile.|

 Nella tabella seguente viene illustrato il comportamento predefinito per ogni zona. La colonna Applicazioni fa riferimento alle applicazioni Windows Form, alle applicazioni Windows Presentation Foundation, alle applicazioni browser WPF e alle applicazioni console.

|Zona|APPLICAZIONI|soluzioni Office|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 È possibile ignorare queste impostazioni abilitando, limitando o disabilitando il prompt di attendibilità ClickOnce.You can override these settings by enabling, restricting, or disabling the ClickOnce trust prompt.

## <a name="enable-the-clickonce-trust-prompt"></a>Abilitare la richiesta di attendibilità ClickOnceEnable the ClickOnce trust prompt
 Abilitare la richiesta di attendibilità per un'area quando si desidera che agli utenti finali venga visualizzata l'opzione di installazione ed esecuzione di qualsiasi applicazione ClickOnce proveniente da tale area.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per attivare la richiesta di attendibilità ClickOnce utilizzando l'editor del Registro di sistema

1. Aprire l'editor del Registro di sistema:

    1. Fare clic su **Start**, quindi scegliere **Esegui**.

    2. Nella casella **Apri** `regedit`digitare e quindi fare clic su **OK**.

2. Individuare la seguente chiave del Registro di sistema:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se la chiave non esiste, crearla.

3. Aggiungere le seguenti sottochiavi come **Valore stringa**, se non esistono già, con i valori associati illustrati nella tabella seguente.

    |Sottochiave Valore stringa|valore|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Per le `Internet` soluzioni Office, `UntrustedSites` ha `Disabled`il valore `AuthenticodeRequired` predefinito e il valore . Per tutti `Internet` gli altri, `Enabled`ha il valore predefinito .

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Per abilitare il prompt di attendibilità ClickOnce a livello di codiceTo enable the ClickOnce trust prompt programmatically

1. Creare un'applicazione console di Visual Basic o Visual C, in Visual Studio.

2. Aprire il file *Program.vb* o *Program.cs* per la modifica e aggiungere il codice seguente.

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

## <a name="restrict-the-clickonce-trust-prompt"></a>Limitare la richiesta di attendibilità ClickOnce
 Limitare il prompt di attendibilità in modo che le soluzioni devono essere firmate con certificati Authenticode con identità nota prima che agli utenti venga richiesta una decisione di attendibilità.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per limitare la richiesta di attendibilità ClickOnce utilizzando l'editor del Registro di sistema

1. Aprire l'editor del Registro di sistema:

    1. Fare clic su **Start**, quindi scegliere **Esegui**.

    2. Nella casella **Apri** `regedit`digitare e quindi fare clic su **OK**.

2. Individuare la seguente chiave del Registro di sistema:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se la chiave non esiste, crearla.

3. Aggiungere le seguenti sottochiavi come **Valore stringa**, se non esistono già, con i valori associati illustrati nella tabella seguente.

    |Sottochiave Valore stringa|valore|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Per limitare la richiesta di attendibilità ClickOnce a livello di codiceTo restrict the ClickOnce trust prompt programmatically

1. Creare un'applicazione console di Visual Basic o Visual C, in Visual Studio.

2. Aprire il file *Program.vb* o *Program.cs* per la modifica e aggiungere il codice seguente.

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

## <a name="disable-the-clickonce-trust-prompt"></a>Disabilitare la richiesta di attendibilità ClickOnceDisable the ClickOnce trust prompt
 È possibile disabilitare la richiesta di attendibilità in modo che agli utenti finali non venga data la possibilità di installare soluzioni che non sono già attendibili nei criteri di sicurezza.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per disabilitare la richiesta di attendibilità ClickOnce utilizzando l'editor del Registro di sistema

1. Aprire l'editor del Registro di sistema:

    1. Fare clic su **Start**, quindi scegliere **Esegui**.

    2. Nella casella **Apri** `regedit`digitare e quindi fare clic su **OK**.

2. Individuare la seguente chiave del Registro di sistema:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se la chiave non esiste, crearla.

3. Aggiungere le seguenti sottochiavi come **Valore stringa**, se non esistono già, con i valori associati illustrati nella tabella seguente.

    |Sottochiave Valore stringa|valore|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Per disabilitare la richiesta di attendibilità ClickOnce a livello di codiceTo disable the ClickOnce trust prompt programmatically

1. Creare un'applicazione console di Visual Basic o Visual C, in Visual Studio.

2. Aprire il file *Program.vb* o *Program.cs* per la modifica e aggiungere il codice seguente.

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
- [Procedura: Firmare nuovamente manifesti di applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
