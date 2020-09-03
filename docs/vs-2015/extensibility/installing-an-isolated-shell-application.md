---
title: Installazione di un'applicazione shell isolata | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0adc81cfe9ea4462940c31a02c6429be89709565
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75944259"
---
# <a name="installing-an-isolated-shell-application"></a>Installazione di un'applicazione di shell isolata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per installare un'app shell è necessario eseguire i passaggi seguenti.  
  
- Preparare la soluzione.  
  
- Creare un pacchetto di Windows Installer (MSI) per l'applicazione.  
  
- Creare un programma di avvio automatico dell'installazione.  
  
  Tutto il codice di esempio di questo documento deriva dall' [esempio di distribuzione della shell](https://code.msdn.microsoft.com/Sample-setup-program-for-81ca73f7), che è possibile scaricare dalla raccolta di codice sul sito Web MSDN. Nell'esempio vengono illustrati i risultati dell'esecuzione di ognuno di questi passaggi.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire le procedure descritte in questo argomento, è necessario che nel computer siano installati gli strumenti seguenti.  
  
- Visual Studio SDK  
  
- Il [set di strumenti XML Windows Installer](https://documentation.help/WiX-Toolset/index.html/) versione 3,6  
  
  L'esempio richiede anche l'SDK di visualizzazione e modellazione di Microsoft, che non è necessario per tutte le shell.  
  
## <a name="preparing-your-solution"></a>Preparazione della soluzione  
 Per impostazione predefinita, i modelli di shell vengono compilati in pacchetti VSIX, ma questo comportamento è destinato principalmente a scopi di debug. Quando si distribuisce un'applicazione shell, è necessario usare i pacchetti MSI per consentire l'accesso al registro di sistema e per i riavvii durante l'installazione. Per preparare l'applicazione per la distribuzione MSI, seguire questa procedura.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Per preparare un'applicazione shell per la distribuzione MSI  
  
1. Modificare ogni file con estensione vsixmanifest nella soluzione.  
  
     Nell' `Identifier` elemento aggiungere un `InstalledByMSI` elemento e un `SystemComponent` elemento e quindi impostarne i valori su `true` .  
  
     Questi elementi impediscono al programma di installazione VSIX di provare a installare i componenti e all'utente di disinstallarli usando la finestra di dialogo **estensioni e aggiornamenti** .  
  
2. Per ogni progetto che contiene un manifesto VSIX, modificare le attività di compilazione per restituire il contenuto al percorso da cui viene installato il file MSI. Includere il manifesto VSIX nell'output di compilazione, ma non compilare un file con estensione VSIX.  
  
## <a name="creating-an-msi-for-your-shell"></a>Creazione di un file MSI per la shell  
 Per compilare il pacchetto MSI, è consigliabile usare il set di [strumenti Windows Installer XML](https://documentation.help/WiX-Toolset/index.html) perché offre una maggiore flessibilità rispetto a un progetto di installazione standard.  
  
 Nel file Product. wxs impostare i blocchi di rilevamento e il layout dei componenti della shell.  
  
 Quindi, creare le voci del registro di sistema, entrambe nel file. reg per la soluzione e in ApplicationRegistry. wxs.  
  
### <a name="detection-blocks"></a>Blocchi di rilevamento  
 Un blocco di rilevamento è costituito da un `Property` elemento che specifica un prerequisito da rilevare e da un `Condition` elemento che specifica un messaggio da restituire se il prerequisito non è presente nel computer. Ad esempio, l'applicazione shell richiederà il ridistribuibile di Microsoft Visual Studio Shell e il blocco di rilevamento sarà simile al markup seguente.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>Layout dei componenti della shell  
 È necessario aggiungere elementi per identificare la struttura di directory di destinazione e i componenti da installare.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Per impostare il layout dei componenti della shell  
  
1. Creare una gerarchia di `Directory` elementi per rappresentare tutte le directory da creare nel file System nel computer di destinazione, come illustrato nell'esempio seguente.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     A queste directory viene fatto riferimento `Id` quando si specificano i file che devono essere installati.  
  
2. Identificare i componenti richiesti dalla shell e dall'applicazione shell, come illustrato nell'esempio riportato di seguito.  
  
    > [!NOTE]
    > Alcuni elementi possono fare riferimento a definizioni in altri file con estensione wxs.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1. L' `ComponentRef` elemento fa riferimento a un altro file con estensione wxs che identifica i file necessari per il componente corrente. Ad esempio, GeneralProfile presenta la definizione seguente in HelpAbout. wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         L' `DirectoryRef` elemento specifica la posizione in cui i file vengono inseriti nel computer dell'utente. L' `Directory` elemento specifica che verrà installato in una sottodirectory e ogni `File` elemento rappresenta un file compilato o esistente come parte della soluzione e identifica la posizione in cui è possibile trovare il file quando viene creato il file MSI.  
  
    2. L' `ComponentGroupRef` elemento fa riferimento a un gruppo di altri componenti (o componenti e gruppi di componenti). Ad esempio, `ComponentGroupRef` in ApplicationGroup viene definito come segue in Application. wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    > Le dipendenze necessarie per le applicazioni shell (isolated) sono: DebuggerProxy, MasterPkgDef, Resources (in particolare il file con estensione winprf), Application e PkgDefs.  
  
### <a name="registry-entries"></a>Voci del Registro di sistema  
 Il modello di progetto Shell (isolated) include un file *NomeProgetto*. reg per le chiavi del registro di sistema da unire all'installazione. Queste voci del registro di sistema devono far parte dell'identità del servizio gestito per scopi di installazione e pulizia. È inoltre necessario creare blocchi del registro di sistema corrispondenti in ApplicationRegistry. wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Per integrare le voci del registro di sistema nel file MSI  
  
1. Nella cartella **personalizzazione della shell** aprire *NomeProgetto*. reg.  
  
2. Sostituire tutte le istanze del token $RootFolder $ con il percorso della directory di installazione di destinazione.  
  
3. Aggiungere qualsiasi altra voce del registro di sistema richiesta dall'applicazione.  
  
4. Aprire ApplicationRegistry. wxs.  
  
5. Per ogni voce del registro di sistema in *NomeProgetto*. reg, aggiungere un blocco del registro di sistema corrispondente, come illustrato negli esempi seguenti.  
  
    |*NomeProgetto*. reg|ApplicationRegisty. wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT \CLSID \\ {bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @ = "PhotoStudio DTE Object"|\<RegistryKey Id='DteClsidRegKey' Root='HKCR' Key='$(var.DteClsidRegKey)' Action='createAndRemoveOnUninstall'><br /><br /> \<RegistryValue Type='string' Name='@' Value='$(var.ShortProductName) DTE Object' /><br /><br /> \</RegistryKey>|  
    |[HKEY_CLASSES_ROOT \CLSID \\ {bb431796-a179-4df7-b65d-c0df6bda7cc6}\LocalServer32]<br /><br /> @ = "$RootFolder $\PhotoStudio.exe"|\<RegistryKey Id='DteLocSrv32RegKey' Root='HKCR' Key='$(var.DteClsidRegKey)\LocalServer32' Action='createAndRemoveOnUninstall'><br /><br /> \<RegistryValue Type='string' Name='@' Value='[INSTALLDIR]$(var.ShortProductName).exe' /><br /><br /> \</RegistryKey>|  
  
     In questo esempio var. DteClsidRegKey viene risolto nella chiave del registro di sistema nella riga superiore. Var. ShortProductName viene risolto in `PhotoStudio` .  
  
## <a name="creating-a-setup-bootstrapper"></a>Creazione di un programma di avvio automatico dell'installazione  
 L'MSI completato verrà installato solo se tutti i prerequisiti vengono installati per primi. Per semplificare l'esperienza dell'utente finale, creare un programma di installazione che raccoglie e installa tutti i prerequisiti prima di installare l'applicazione. Per garantire una corretta installazione, eseguire le operazioni seguenti:  
  
- Applicare l'installazione in base all'amministratore.  
  
- Rilevare se è installato Visual Studio Shell (isolated).  
  
- Eseguire uno o entrambi i programmi di installazione della shell nell'ordine.  
  
- Gestire le richieste di riavvio.  
  
- Eseguire il file MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Applicazione dell'installazione da amministratore  
 Questa procedura è necessaria per consentire al programma di installazione di accedere alle directory necessarie, ad esempio \Program Files \\ .  
  
##### <a name="to-enforce-installation-by-administrator"></a>Per applicare l'installazione in base all'amministratore  
  
1. Aprire il menu di scelta rapida per il progetto di installazione, quindi scegliere **Proprietà**.  
  
2. In **proprietà di configurazione/linker/file manifesto**impostare il **livello di esecuzione UAC** su **requireAdministrator**.  
  
     Questa proprietà inserisce l'attributo che richiede che il programma venga eseguito come amministratore nel file manifesto incorporato.  
  
### <a name="detecting-shell-installations"></a>Rilevamento delle installazioni della shell  
 Per determinare se è necessario installare Visual Studio Shell (isolated), determinare prima di tutto se è già installato controllando il valore del registro di sistema di HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
> Questi valori vengono letti anche dal blocco di rilevamento della shell in Product. wxs.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder specifica il percorso in cui è stata installata la shell di Visual Studio ed è possibile verificare la presenza di file.  
  
 Per un esempio di come rilevare l'installazione di una shell, vedere la `GetProductDirFromReg` funzione di Utilities. cpp nell'esempio relativo alla distribuzione della shell.  
  
 Se una o entrambe le shell di Visual Studio richieste dal pacchetto non sono installate nel computer, è necessario aggiungerle all'elenco dei componenti da installare. Per un esempio, vedere la `ComponentsPage::OnInitDialog` funzione di ComponentsPage. cpp nell'esempio relativo alla distribuzione della shell.  
  
### <a name="running-the-shell-installers"></a>Esecuzione dei programmi di installazione della shell  
 Per eseguire i programmi di installazione della shell, chiamare i ridistribuibili della shell di Visual Studio usando i corretti argomenti della riga di comando. Come minimo, è necessario usare gli argomenti della riga di comando **/norestart/q** e controllare il codice restituito per determinare le operazioni da eseguire successivamente. Nell'esempio seguente viene eseguita la shell (isolated) Redistributable.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Esecuzione dei programmi di installazione del Language Pack della shell  
 Se invece si scopre che la shell o le shell sono state installate e serve solo un Language Pack, è possibile installare i Language Pack come illustrato nell'esempio seguente.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Decifrazione dei valori restituiti  
 In alcuni sistemi operativi, l'installazione di Visual Studio Shell (isolated) richiederà un riavvio. Questa condizione può essere determinata dal codice restituito della chiamata a `ExecCmd` .  
  
|Valore restituito|Descrizione|  
|------------------|-----------------|  
|ERROR_SUCCESS|Installazione completata. È ora possibile installare l'applicazione.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Installazione completata. È possibile installare l'applicazione dopo il riavvio del computer.|  
|3015|L'installazione è in corso. Per continuare l'installazione, è necessario riavviare il computer.|  
  
### <a name="handling-restarts"></a>Gestione dei riavvii  
 Quando è stato eseguito il programma di installazione della shell utilizzando l'argomento **/norestart** , è stato specificato che non avrebbe riavviato il computer o richiesto il riavvio del computer. Tuttavia, potrebbe essere necessario un riavvio ed è necessario verificare che il programma di installazione continui dopo il riavvio del computer.  
  
 Per gestire correttamente i riavvii, verificare che sia stato impostato un solo programma di installazione da riprendere e che il processo di ripresa venga gestito correttamente.  
  
 Se viene restituito ERROR_SUCCESS_REBOOT_REQUIRED o 3015, il codice deve riavviare il computer prima che l'installazione continui.  
  
 Per gestire i riavvii, eseguire le azioni seguenti:  
  
- Impostare il registro di sistema per riprendere l'installazione all'avvio di Windows.  
  
- Eseguire un doppio riavvio del programma di avvio automatico.  
  
- Eliminare la chiave ResumeData del programma di installazione della shell.  
  
- Riavviare Windows.  
  
- Reimposta il percorso di avvio dell'identità del servizio gestito.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Impostazione del registro di sistema per riprendere l'installazione all'avvio di Windows  
 La chiave del registro di sistema HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ viene eseguita all'avvio del sistema con autorizzazioni amministrative e viene quindi cancellata. HKEY_CURRENT_USER contiene una chiave simile, ma viene eseguita come utente normale e non è appropriata per le installazioni. È possibile riprendere l'installazione inserendo un valore stringa nella chiave RunOnce che chiama il programma di installazione. Tuttavia, si consiglia di chiamare il programma di installazione usando un **/Restart** o un parametro simile per notificare all'applicazione che è in corso la ripresa anziché l'avvio. È anche possibile includere parametri per indicare la posizione del processo di installazione, che risulta particolarmente utile nelle installazioni che possono richiedere più riavvii.  
  
 Nell'esempio seguente viene illustrato un valore della chiave del registro di sistema RunOnce per riprendere un'installazione.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Installazione del doppio riavvio del programma di avvio automatico  
 Se il programma di installazione viene usato direttamente da RunOnce, il desktop non sarà in grado di caricarlo completamente. Per rendere disponibile l'interfaccia utente completa, è necessario creare un'altra esecuzione del programma di installazione e terminare l'istanza di RunOnce.  
  
 È necessario eseguire di nuovo il programma di installazione in modo che ottenga le autorizzazioni corrette ed è necessario fornire informazioni sufficienti per individuare il punto in cui è stato interrotto prima del riavvio, come illustrato nell'esempio riportato di seguito.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Eliminazione della chiave ResumeData del programma di installazione della shell  
 Il programma di installazione della shell imposta la chiave del registro di sistema HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData con dati per riprendere l'installazione dopo il riavvio. Poiché l'applicazione, non il programma di installazione della shell, sta riprendendo, eliminare la chiave del registro di sistema, come illustrato nell'esempio seguente.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Riavvio di Windows  
 Dopo aver impostato le chiavi del registro di sistema necessarie, è possibile riavviare Windows. Nell'esempio seguente vengono richiamati i comandi di riavvio per diversi sistemi operativi Windows.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>Reimpostazione del percorso iniziale di MSI  
 Prima del riavvio, la directory corrente è il percorso del programma di installazione ma, dopo il riavvio, il percorso diventa la directory system32. Il programma di installazione deve reimpostare la directory corrente prima di ogni chiamata MSI, come illustrato nell'esempio seguente.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>Esecuzione del file MSI dell'applicazione  
 Quando il programma di installazione della shell di Visual Studio restituisce ERROR_SUCCESS, è possibile eseguire il file MSI per l'applicazione. Poiché il programma di installazione fornisce l'interfaccia utente, avviare l'identità del servizio gestito in modalità non interattiva (**/q**) e con registrazione (**/l**), come illustrato nell'esempio seguente.  
  
```cpp#  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
