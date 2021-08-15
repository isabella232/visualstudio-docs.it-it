---
title: Configurare il comportamento ClickOnce richiesta di attendibilità | Microsoft Docs
description: Informazioni su come configurare la richiesta ClickOnce attendibilità per controllare se agli utenti finali viene data la possibilità di installare ClickOnce applicazioni.
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
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 4bb20f403a41ece1096404c3eec9191bc44d461c38d824a2959204fb6fa7df6a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293873"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Procedura: Configurare il comportamento di richiesta di attendibilità di ClickOnce
È possibile configurare la richiesta di attendibilità ClickOnce per controllare se agli utenti finali viene data la possibilità di installare applicazioni ClickOnce, ad esempio applicazioni form Windows, applicazioni Windows Presentation Foundation, applicazioni console, applicazioni browser WPF e soluzioni Office. Per configurare la richiesta di attendibilità, impostare le chiavi del Registro di sistema nel computer di ogni utente finale.

 La tabella seguente illustra le opzioni di configurazione che possono essere applicate a ognuna delle cinque zone (Internet, Siti non attendibili, MyComputer, LocalIntranet e TrustedSites).

|Opzione|Valore dell'impostazione del Registro di sistema|Descrizione|
|------------|----------------------------|-----------------|
|Abilitare la richiesta di attendibilità.|`Enabled`|Viene visualizzata ClickOnce richiesta di attendibilità per consentire agli utenti finali di concedere l'attendibilità ClickOnce applicazioni.|
|Limitare la richiesta di attendibilità.|`AuthenticodeRequired`|La ClickOnce richiesta di attendibilità viene visualizzata solo se ClickOnce applicazioni sono firmate con un certificato che identifica l'autore.|
|Disabilitare la richiesta di attendibilità.|`Disabled`|La ClickOnce di attendibilità non viene visualizzata per le applicazioni ClickOnce firmate con un certificato attendibile in modo esplicito.|

 Nella tabella seguente viene illustrato il comportamento predefinito per ogni zona. La colonna Applicazioni fa riferimento Windows applicazioni Form, Windows Presentation Foundation applicazioni, applicazioni browser WPF e applicazioni console.

|Zona|Applicazioni|soluzioni Office|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 È possibile eseguire l'override di queste impostazioni abilitando, limitando o disabilitando la richiesta ClickOnce trust.

## <a name="enable-the-clickonce-trust-prompt"></a>Abilitare la richiesta ClickOnce trust
 Abilitare la richiesta di attendibilità per una zona quando si vuole che agli utenti finali venga visualizzata la possibilità di installare ed eseguire qualsiasi applicazione ClickOnce che proviene da tale zona.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per abilitare la richiesta di ClickOnce attendibilità tramite l'editor del Registro di sistema

1. Aprire l'editor del Registro di sistema:

    1. Fare clic sul pulsante **Start** e quindi scegliere **Esegui**.

    2. Nella casella **Apri** digitare e quindi `regedit` fare clic su **OK.**

2. Trovare la chiave del Registro di sistema seguente:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se la chiave non esiste, crearla.

3. Aggiungere le sottochiavi seguenti come **Valore** stringa , se non esistono già, con i valori associati illustrati nella tabella seguente.

    |Sottochiave Valore stringa|Valore|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Per Office soluzioni, `Internet` ha il valore predefinito `AuthenticodeRequired` e ha il valore `UntrustedSites` `Disabled` . Per tutti gli altri, `Internet` ha il valore predefinito `Enabled` .

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Per abilitare la richiesta di ClickOnce attendibilità a livello di codice

1. Creare un'Visual Basic console di Visual C# in Visual Studio.

2. Aprire il file *Program.vb o* *Program.cs* per la modifica e aggiungere il codice seguente.

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

## <a name="restrict-the-clickonce-trust-prompt"></a>Limitare la richiesta ClickOnce trust
 Limitare la richiesta di attendibilità in modo che le soluzioni devono essere firmate con certificati Authenticode con identità nota prima che agli utenti venga richiesta una decisione di attendibilità.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per limitare la richiesta ClickOnce attendibilità tramite l'editor del Registro di sistema

1. Aprire l'editor del Registro di sistema:

    1. Fare clic sul pulsante **Start** e quindi scegliere **Esegui**.

    2. Nella casella **Apri** digitare e quindi `regedit` fare clic su **OK.**

2. Trovare la chiave del Registro di sistema seguente:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se la chiave non esiste, crearla.

3. Aggiungere le sottochiavi seguenti come **Valore** stringa , se non esistono già, con i valori associati illustrati nella tabella seguente.

    |Sottochiave Valore stringa|Valore|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Per limitare la richiesta di ClickOnce attendibilità a livello di codice

1. Creare un'Visual Basic console di Visual C# in Visual Studio.

2. Aprire il file *Program.vb o* *Program.cs* per la modifica e aggiungere il codice seguente.

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

## <a name="disable-the-clickonce-trust-prompt"></a>Disabilitare la richiesta ClickOnce trust
 È possibile disabilitare la richiesta di attendibilità in modo che agli utenti finali non venga data la possibilità di installare soluzioni che non sono già attendibili nei criteri di sicurezza.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per disabilitare la richiesta ClickOnce attendibilità tramite l'editor del Registro di sistema

1. Aprire l'editor del Registro di sistema:

    1. Fare clic sul pulsante **Start** e quindi scegliere **Esegui**.

    2. Nella casella **Apri** digitare e quindi `regedit` fare clic su **OK.**

2. Trovare la chiave del Registro di sistema seguente:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se la chiave non esiste, crearla.

3. Aggiungere le sottochiavi seguenti come **Valore** stringa , se non esistono già, con i valori associati illustrati nella tabella seguente.

    |Sottochiave Valore stringa|Valore|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Per disabilitare la richiesta di ClickOnce attendibilità a livello di codice

1. Creare un'Visual Basic console di Visual C# in Visual Studio.

2. Aprire il file *Program.vb o* *Program.cs* per la modifica e aggiungere il codice seguente.

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
