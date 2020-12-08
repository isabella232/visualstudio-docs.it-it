---
title: "Procedura: configurare la sicurezza dell'elenco di inclusione"
description: Configurare la richiesta di attendibilità ClickOnce per controllare se gli utenti finali hanno la possibilità di installare soluzioni Office salvando una decisione di attendibilità nell'elenco di inclusione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1f9eca5150e019906805adf40e5c9b6af8a3c14e
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846727"
---
# <a name="how-to-configure-inclusion-list-security"></a>Procedura: configurare la sicurezza dell'elenco di inclusione
  Se si dispone delle autorizzazioni di amministratore, è possibile configurare la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] richiesta di attendibilità per controllare se gli utenti finali hanno la possibilità di installare soluzioni Office salvando una decisione di attendibilità nell'elenco di inclusione. Per informazioni sugli elenchi di inclusione, vedere [considerare attendibili le soluzioni Office usando gli elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Per le soluzioni che si trovano in ognuna delle cinque zone, è possibile impostare le opzioni seguenti:

- Abilitare la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave della richiesta di attendibilità e l'elenco di inclusione. È possibile consentire agli utenti finali di concedere l'attendibilità alle soluzioni Office firmate con un certificato.

- Limitare la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave della richiesta di attendibilità e l'elenco di inclusione. È possibile consentire agli utenti finali di installare soluzioni Office firmate con un certificato che identifica il server di pubblicazione, ma ciò non è già attendibile.

- Disabilitare la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave della richiesta di attendibilità e l'elenco di inclusione. È possibile impedire agli utenti finali di installare qualsiasi soluzione Office non firmata con un certificato attendibile in modo esplicito.

## <a name="enable-the-inclusion-list"></a>Abilita l'elenco di inclusione
 Abilitare l'elenco di inclusione per una zona quando si desidera che gli utenti finali vengano presentati con l'opzione di installare ed eseguire qualsiasi soluzione Office che deriva da tale area.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Per abilitare l'elenco di inclusione mediante l'editor del registro di sistema

1. Aprire l'editor del registro di sistema:

    1. Fare clic sul pulsante **Start** e quindi scegliere **Esegui**.

    2. Nella casella **Apri** Digitare **regedt32.exe**, quindi fare clic su **OK**.

2. Trovare la chiave del registro di sistema seguente:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se la chiave non esiste, crearla.

3. Aggiungere le sottochiavi seguenti come **valore di stringa**, se non esistono già, con i valori associati.

    |Sottochiave valore stringa|Valore|
    |-------------------------|-----------|
    |**Internet**|**AuthenticodeRequired**|
    |**UntrustedSites**|**Disabilitato**|
    |**MyComputer**|**Abilitato**|
    |**LocalIntranet**|**Abilitato**|
    |**TrustedSites**|**Abilitato**|

     Per impostazione predefinita, il valore di **Internet** è **AuthenticodeRequired** e il valore di **UntrustedSites** è **disabilitato**.

### <a name="to-enable-the-inclusion-list-programmatically"></a>Per abilitare l'elenco di inclusione a livello di codice

1. Creare un'applicazione console Visual Basic o Visual C#.

2. Aprire il file *Program. vb* o *Program.cs* per la modifica e aggiungere il codice seguente.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "AuthenticodeRequired")
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

## <a name="restrict-the-inclusion-list"></a>Limitare l'elenco di inclusione
 Limitare l'elenco di inclusione in modo che le soluzioni debbano essere firmate con certificati Authenticode con identità nota prima che agli utenti venga richiesta una decisione di attendibilità.

### <a name="to-restrict-the-inclusion-list"></a>Per limitare l'elenco di inclusione

1. Aprire l'editor del registro di sistema:

    1. Fare clic sul pulsante **Start** e quindi scegliere **Esegui**.

    2. Nella casella **Apri** Digitare **regedt32.exe**, quindi fare clic su **OK**.

2. Trovare la chiave del registro di sistema seguente:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se la chiave non esiste, crearla.

3. Aggiungere le sottochiavi seguenti come **valore di stringa**, se non esistono già, con i valori associati.

    |Sottochiave valore stringa|Valore|
    |-------------------------|-----------|
    |**UntrustedSites**|**Disabilitato**|
    |**Internet**|**AuthenticodeRequired**|
    |**MyComputer**|**AuthenticodeRequired**|
    |**LocalIntranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     Per impostazione predefinita, il valore di **Internet** è **AuthenticodeRequired** e il valore di **UntrustedSites** è **disabilitato**.

### <a name="to-restrict-the-inclusion-list-programmatically"></a>Per limitare l'elenco di inclusione a livello di codice

1. Creare un'applicazione console Visual Basic o Visual C#.

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

## <a name="disable-the-inclusion-list"></a>Disabilitare l'elenco di inclusione
 È possibile disabilitare l'elenco di inclusione in modo che gli utenti finali possano installare solo le soluzioni firmate con un certificato attendibile e noto.

### <a name="to-disable-the-inclusion-list"></a>Per disabilitare l'elenco di inclusione

1. Aprire l'editor del registro di sistema:

    1. Fare clic sul pulsante **Start** e quindi scegliere **Esegui**.

    2. Nella casella **Apri** Digitare **regedt32.exe**, quindi fare clic su **OK**.

2. Se non esiste già, creare la seguente chiave del registro di sistema:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

3. Aggiungere le sottochiavi seguenti come **valore di stringa**, se non esistono già, con i valori associati.

    |Sottochiave valore stringa|Valore|
    |-------------------------|-----------|
    |**UntrustedSites**|**Disabilitato**|
    |**Internet**|**Disabilitato**|
    |**MyComputer**|**Disabilitato**|
    |**LocalIntranet**|**Disabilitato**|
    |**TrustedSites**|**Disabilitato**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>Per disabilitare l'elenco di inclusione a livello di codice

1. Creare un'applicazione console Visual Basic o Visual C#.

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
- [Considerare attendibili le soluzioni Office usando gli elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
