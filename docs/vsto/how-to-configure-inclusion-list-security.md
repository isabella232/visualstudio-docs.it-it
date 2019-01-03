---
title: 'Procedura: Configurare la sicurezza di elenco di inclusione'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 026cdef278f87ec4367dd88a8530a35425452b75
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895577"
---
# <a name="how-to-configure-inclusion-list-security"></a>Procedura: Configurare la sicurezza di elenco di inclusione
  Se si dispone delle autorizzazioni di amministratore, è possibile configurare il [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] richiesta di attendibilità per controllare se gli utenti finali è data la possibilità di installare le soluzioni Office mediante il salvataggio di una decisione di attendibilità per l'elenco di inclusione. Per informazioni sugli elenchi di inclusione, vedere [soluzioni di Office Trust usando gli elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Per le soluzioni in ognuna delle cinque aree, è possibile impostare le opzioni seguenti:  
  
-   Abilitare il [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave dei messaggi di richiesta di attendibilità e l'elenco di inclusione. È possibile consentire agli utenti finali di concedere l'attendibilità alle soluzioni Office firmate con un certificato.  
  
-   Limitare il [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave dei messaggi di richiesta di attendibilità e l'elenco di inclusione. È possibile consentire agli utenti finali di installare le soluzioni Office firmate con un certificato che identifica il server di pubblicazione, ma che non è attendibile.  
  
-   Disabilitare il [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave dei messaggi di richiesta di attendibilità e l'elenco di inclusione. È possibile impedire agli utenti finali di installazione di qualsiasi soluzione Office che non è firmato con un certificato attendibile in modo esplicito.  
  
## <a name="enable-the-inclusion-list"></a>Abilitare l'elenco di inclusione  
 Quando si desidera che gli utenti finali devono essere presentati con l'opzione di installazione ed esecuzione di qualsiasi soluzione Office che provengono da tale area, abilitare l'elenco di inclusione per una zona.  
  
### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Per abilitare l'elenco di inclusione con l'editor del Registro di sistema  
  
1.  Aprire l'editor del Registro di sistema:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aperto** , digitare **regedt32.exe**, quindi fare clic su **OK**.  
  
2.  Trovare la chiave del Registro di sistema seguente:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
     Se la chiave non esiste, crearla.  
  
3.  Aggiungere le seguenti sottochiavi come **valore stringa**, se non esistono già, con i valori associati.  
  
    |Sottochiave del valore stringa|Value|  
    |-------------------------|-----------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**Siti non attendibili**|**Disabilitato**|  
    |**Risorse del computer**|**Enabled**|  
    |**Intranet locale**|**Enabled**|  
    |**Siti attendibili**|**Enabled**|  
  
     Per impostazione predefinita **Internet** ha il valore **AuthenticodeRequired** e **siti non attendibili** ha il valore **disabilitato**.  
  
### <a name="to-enable-the-inclusion-list-programmatically"></a>Per abilitare l'elenco di inclusione a livello di codice  
  
1.  Creare un'applicazione console Visual Basic o Visual c#.  
  
2.  Aprire il *Program. vb* oppure *Program.cs* file per la modifica e aggiungere il codice seguente.  
  
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
  
3.  Compilare ed eseguire l'applicazione.  
  
## <a name="restrict-the-inclusion-list"></a>Limitare l'elenco di inclusione  
 Limitare l'elenco di inclusione in modo che le soluzioni devono essere firmate con i certificati Authenticode con identità nota prima che vengono richiesto agli utenti di prendere una decisione di attendibilità.  
  
### <a name="to-restrict-the-inclusion-list"></a>Per limitare l'elenco di inclusione  
  
1.  Aprire l'editor del Registro di sistema:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aperto** , digitare **regedt32.exe**, quindi fare clic su **OK**.  
  
2.  Trovare la chiave del Registro di sistema seguente:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
     Se la chiave non esiste, crearla.  
  
3.  Aggiungere le seguenti sottochiavi come **valore stringa**, se non esistono già, con i valori associati.  
  
    |Sottochiave del valore stringa|Valore|  
    |-------------------------|-----------|  
    |**Siti non attendibili**|**Disabilitato**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**Risorse del computer**|**AuthenticodeRequired**|  
    |**Intranet locale**|**AuthenticodeRequired**|  
    |**Siti attendibili**|**AuthenticodeRequired**|  
  
     Per impostazione predefinita **Internet** ha il valore **AuthenticodeRequired** e **siti non attendibili** ha il valore **disabilitato**.  
  
### <a name="to-restrict-the-inclusion-list-programmatically"></a>Per limitare l'elenco di inclusione a livello di codice  
  
1.  Creare un'applicazione console Visual Basic o Visual c#.  
  
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
  
## <a name="disable-the-inclusion-list"></a>Disabilitare l'elenco di inclusione  
 È possibile disabilitare l'elenco di inclusione in modo che gli utenti finali possono installare solo le soluzioni che sono firmate con un certificato attendibile e noto.  
  
### <a name="to-disable-the-inclusion-list"></a>Per disabilitare l'elenco di inclusione  
  
1.  Aprire l'editor del Registro di sistema:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aperto** , digitare **regedt32.exe**, quindi fare clic su **OK**.  
  
2.  Se questo non esiste già, creare la chiave del Registro di sistema seguente:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  Aggiungere le seguenti sottochiavi come **valore stringa**, se non esistono già, con i valori associati.  
  
    |Sottochiave del valore stringa|Valore|  
    |-------------------------|-----------|  
    |**Siti non attendibili**|**Disabilitato**|  
    |**Internet**|**Disabilitato**|  
    |**Risorse del computer**|**Disabilitato**|  
    |**Intranet locale**|**Disabilitato**|  
    |**Siti attendibili**|**Disabilitato**|  
  
### <a name="to-disable-the-inclusion-list-programmatically"></a>Per disabilitare l'elenco di inclusione a livello di codice  
  
1.  Creare un'applicazione console Visual Basic o Visual c#.  
  
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
 [Trust di soluzioni Office mediante elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)  
