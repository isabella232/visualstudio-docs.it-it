---
title: "Procedura: Configurare la sicurezza dell'elenco di inclusione"
description: Configurare la richiesta ClickOnce attendibilità per controllare se agli utenti finali viene data la possibilità di installare soluzioni Office salvando una decisione di attendibilità nell'elenco di inclusione.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: adde40770aad2d665ad482b72189abda2d6d4176
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148181"
---
# <a name="how-to-configure-inclusion-list-security"></a>Procedura: Configurare la sicurezza dell'elenco di inclusione
  Se si dispone delle autorizzazioni di amministratore, è possibile configurare la richiesta di attendibilità per controllare se agli utenti finali viene data la possibilità di installare soluzioni Office salvando una decisione di attendibilità nell'elenco [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] di inclusione. Per informazioni sugli elenchi di inclusione, vedere [Trust Office solutions by using inclusion lists](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Per le soluzioni in ognuna delle cinque zone, è possibile impostare le opzioni seguenti:

- Abilitare la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave di richiesta di attendibilità e l'elenco di inclusione. È possibile consentire agli utenti finali di concedere l'attendibilità Office soluzioni firmate con qualsiasi certificato.

- Limitare la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave di richiesta di attendibilità e l'elenco di inclusione. È possibile consentire agli utenti finali di Office soluzioni firmate con un certificato che identifica l'autore, ma che non è già attendibile.

- Disabilitare la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave di richiesta di attendibilità e l'elenco di inclusione. È possibile impedire agli utenti finali di installare Office soluzione non firmata con un certificato attendibile in modo esplicito.

## <a name="enable-the-inclusion-list"></a>Abilitare l'elenco di inclusione
 Abilitare l'elenco di inclusione per una zona quando si vuole che agli utenti finali venga visualizzata la possibilità di installare ed eseguire qualsiasi soluzione Office che proviene da tale zona.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Per abilitare l'elenco di inclusione tramite l'editor del Registro di sistema

1. Aprire l'editor del Registro di sistema:

    1. Fare clic sul pulsante **Start** e quindi scegliere **Esegui**.

    2. Nella casella **Apri** digitare **regedt32.exe** e quindi fare clic su **OK.**

2. Trovare la chiave del Registro di sistema seguente:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se la chiave non esiste, crearla.

3. Aggiungere le sottochiavi seguenti come **Valore** stringa , se non esistono già, con i valori associati.

    |Sottochiave Valore stringa|Valore|
    |-------------------------|-----------|
    |**Internet**|**AuthenticodeRequired**|
    |**Siti non attendibili**|**Disabilitato**|
    |**MyComputer**|**Enabled**|
    |**LocalIntranet**|**Enabled**|
    |**TrustedSites**|**Enabled**|

     Per impostazione **predefinita, Internet** ha il **valore AuthenticodeRequired** e **UntrustedSites** ha il valore **Disabled**.

### <a name="to-enable-the-inclusion-list-programmatically"></a>Per abilitare l'elenco di inclusione a livello di codice

1. Creare un'Visual Basic o un'applicazione console di Visual C#.

2. Aprire il file *Program.vb o* *Program.cs* per la modifica e aggiungere il codice seguente.

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
 Limitare l'elenco di inclusione in modo che le soluzioni devono essere firmate con certificati Authenticode con identità nota prima che agli utenti venga richiesta una decisione di attendibilità.

### <a name="to-restrict-the-inclusion-list"></a>Per limitare l'elenco di inclusione

1. Aprire l'editor del Registro di sistema:

    1. Fare clic sul pulsante **Start** e quindi scegliere **Esegui**.

    2. Nella casella **Apri** digitare **regedt32.exe** e quindi fare clic su **OK.**

2. Trovare la chiave del Registro di sistema seguente:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se la chiave non esiste, crearla.

3. Aggiungere le sottochiavi seguenti come **Valore** stringa , se non esistono già, con i valori associati.

    |Sottochiave Valore stringa|Valore|
    |-------------------------|-----------|
    |**Siti non attendibili**|**Disabilitato**|
    |**Internet**|**AuthenticodeRequired**|
    |**MyComputer**|**AuthenticodeRequired**|
    |**LocalIntranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     Per impostazione **predefinita, Internet** ha il **valore AuthenticodeRequired** e **UntrustedSites** ha il valore **Disabled**.

### <a name="to-restrict-the-inclusion-list-programmatically"></a>Per limitare l'elenco di inclusione a livello di codice

1. Creare un'Visual Basic o un'applicazione console di Visual C#.

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

## <a name="disable-the-inclusion-list"></a>Disabilitare l'elenco di inclusione
 È possibile disabilitare l'elenco di inclusione in modo che gli utenti finali possano installare solo soluzioni firmate con un certificato attendibile e noto.

### <a name="to-disable-the-inclusion-list"></a>Per disabilitare l'elenco di inclusione

1. Aprire l'editor del Registro di sistema:

    1. Fare clic sul pulsante **Start** e quindi scegliere **Esegui**.

    2. Nella casella **Apri** digitare **regedt32.exe** e quindi fare clic su **OK.**

2. Creare la chiave del Registro di sistema seguente, se non esiste già:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

3. Aggiungere le sottochiavi seguenti come **Valore** stringa , se non esistono già, con i valori associati.

    |Sottochiave Valore stringa|Valore|
    |-------------------------|-----------|
    |**Siti non attendibili**|**Disabilitato**|
    |**Internet**|**Disabilitato**|
    |**MyComputer**|**Disabilitato**|
    |**LocalIntranet**|**Disabilitato**|
    |**TrustedSites**|**Disabilitato**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>Per disabilitare l'elenco di inclusione a livello di codice

1. Creare un'Visual Basic o un'applicazione console di Visual C#.

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
- [Considerare attendibili Office soluzioni tramite elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
