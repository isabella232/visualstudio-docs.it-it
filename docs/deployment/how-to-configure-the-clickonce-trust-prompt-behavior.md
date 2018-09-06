---
title: 'Procedura: configurare il comportamento di richiesta di attendibilità di ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 103fcd8b47e423aaa8d66c3df96afe3598818de2
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/05/2018
ms.locfileid: "43774807"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Procedura: configurare il comportamento dei messaggi di richiesta di attendibilità di ClickOnce
È possibile configurare la richiesta di attendibilità ClickOnce per controllare se gli utenti finali disponibile l'opzione di installazione di applicazioni ClickOnce, ad esempio applicazioni Windows Forms, le applicazioni Windows Presentation Foundation, le applicazioni console, browser WPF le applicazioni e soluzioni Office. Per configurare la richiesta di attendibilità, impostando le chiavi del Registro di sistema nel computer di ogni utente finale.  
  
 Nella tabella seguente mostra le opzioni di configurazione che possono essere applicate a ognuna delle cinque aree (Internet, siti non attendibili, Computer1, LocalIntranet e siti attendibili).  
  
|Opzione|Valore dell'impostazione del Registro di sistema|Descrizione|  
|------------|----------------------------|-----------------|  
|Abilitare la richiesta di attendibilità.|`Enabled`|La richiesta di attendibilità di ClickOnce è visualizzato in modo che gli utenti finali possono concedere l'attendibilità delle applicazioni ClickOnce.|  
|Limitare la richiesta di attendibilità.|`AuthenticodeRequired`|La richiesta di attendibilità di ClickOnce viene visualizzata solo se le applicazioni ClickOnce sono firmate con un certificato che identifica il server di pubblicazione.|  
|Disabilita la richiesta di attendibilità.|`Disabled`|La richiesta di attendibilità di ClickOnce non viene visualizzata per le applicazioni ClickOnce che non sono firmate con un certificato attendibile in modo esplicito.|  
  
 La tabella seguente illustra il comportamento predefinito per ogni zona. Fa riferimento la colonna di applicazioni per applicazioni Windows Forms, le applicazioni Windows Presentation Foundation, le applicazioni browser WPF e applicazioni console.  
  
|Zona|Applicazioni|soluzioni Office|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 È possibile eseguire l'override di queste impostazioni abilitando, limitare o disabilitare la richiesta di attendibilità di ClickOnce.  
  
## <a name="enable-the-clickonce-trust-prompt"></a>Abilitare la richiesta di attendibilità di ClickOnce  
 Quando si desidera che gli utenti finali devono essere presentati con l'opzione di installazione ed esecuzione di qualsiasi applicazione ClickOnce che viene fornito da tale area, attivare la richiesta di attendibilità per una zona.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per abilitare la richiesta di attendibilità di ClickOnce con l'editor del Registro di sistema  
  
1.  Aprire l'editor del Registro di sistema:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aperto** , digitare `regedit`, quindi fare clic su **OK**.  
  
2.  Trovare la chiave del Registro di sistema seguente:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
     Se la chiave non esiste, crearla.  
  
3.  Aggiungere le seguenti sottochiavi come **valore stringa**, se non esistono già, con i valori associati illustrati nella tabella seguente.  
  
    |Sottochiave del valore stringa|Valore|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Per le soluzioni Office `Internet` ha il valore predefinito `AuthenticodeRequired` e `UntrustedSites` ha valore `Disabled`. Per tutti gli altri, `Internet` ha il valore predefinito `Enabled`.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Per abilitare a livello di codice la richiesta di attendibilità di ClickOnce  
  
1.  Creare un'applicazione console Visual Basic o Visual c# in Visual Studio.  
  
2.  Aprire il *Program. vb* oppure *Program.cs* file per la modifica e aggiungere il codice seguente.  
  
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
  
3.  Compilare ed eseguire l'applicazione.  
  
## <a name="restrict-the-clickonce-trust-prompt"></a>Limitare la richiesta di attendibilità di ClickOnce  
 Limitare la richiesta di attendibilità in modo che le soluzioni devono essere firmate con i certificati Authenticode con identità nota prima che vengono richiesto agli utenti di prendere una decisione di attendibilità.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per limitare la richiesta di attendibilità di ClickOnce tramite l'editor del Registro di sistema  
  
1.  Aprire l'editor del Registro di sistema:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aperto** , digitare `regedit`, quindi fare clic su **OK**.  
  
2.  Trovare la chiave del Registro di sistema seguente:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel** 
  
     Se la chiave non esiste, crearla.  
  
3.  Aggiungere le seguenti sottochiavi come **valore stringa**, se non esistono già, con i valori associati illustrati nella tabella seguente.  
  
    |Sottochiave del valore stringa|Valore|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Per limitare a livello di codice la richiesta di attendibilità di ClickOnce  
  
1.  Creare un'applicazione console Visual Basic o Visual c# in Visual Studio.  
  
2.  Aprire il *Program. vb* oppure *Program.cs* file per la modifica e aggiungere il codice seguente.  
  
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
  
3.  Compilare ed eseguire l'applicazione.  
  
## <a name="disable-the-clickonce-trust-prompt"></a>Disabilita la richiesta di attendibilità di ClickOnce  
 È possibile disabilitare la richiesta di attendibilità in modo che gli utenti finali non viene forniti l'opzione per installare le soluzioni che non sono già considerati attendibili nel loro criteri di sicurezza.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per disabilitare la richiesta di attendibilità di ClickOnce utilizzando l'editor del Registro di sistema  
  
1.  Aprire l'editor del Registro di sistema:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aperto** , digitare `regedit`, quindi fare clic su **OK**.  
  
2.  Trovare la chiave del Registro di sistema seguente:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
     Se la chiave non esiste, crearla.  
  
3.  Aggiungere le seguenti sottochiavi come **valore stringa**, se non esistono già, con i valori associati illustrati nella tabella seguente.  
  
    |Sottochiave del valore stringa|Valore|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Per disabilitare a livello di codice la richiesta di attendibilità di ClickOnce  
  
1.  Creare un'applicazione console Visual Basic o Visual c# in Visual Studio.  
  
2.  Aprire il *Program. vb* oppure *Program.cs* file per la modifica e aggiungere il codice seguente.  
  
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
  
3.  Compilare ed eseguire l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)   
 [Procedura: abilitare le impostazioni di sicurezza ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Procedura: impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Procedura: impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Procedura: eseguire il Debug di un'applicazione ClickOnce con autorizzazioni limitate](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Procedura: aggiungere un autore attendibile a un computer client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Procedura: firmare manifesti dell'applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
