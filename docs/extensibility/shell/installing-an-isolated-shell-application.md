---
title: Installazione di un'applicazione Shell isolata | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: "40"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6672ed634ad8c8056ae372c9d1d9a3fa44b56243
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="installing-an-isolated-shell-application"></a>Installazione di un'applicazione Shell isolata
Per installare un'applicazione Shell è necessario eseguire i passaggi seguenti.  
  
-   Preparare la soluzione.  
  
-   Creare un pacchetto Windows Installer (MSI) per l'applicazione.  
  
-   Creare un programma di avvio del programma di installazione.  
  
 Tutto il codice di esempio in questo documento viene fornito dal [Shell di esempio di distribuzione](http://go.microsoft.com/fwlink/?LinkId=262245), che è possibile scaricare da nel sito Web MSDN Code Gallery. L'esempio mostra i risultati dell'esecuzione di ognuno di questi passaggi.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire le procedure descritte in questo argomento, è necessario installare gli strumenti seguenti nel computer in uso.  
  
-   Visual Studio SDK  
  
-   Il [il set di strumenti di Windows Installer XML](http://go.microsoft.com/fwlink/?LinkId=82720) versione 3.6  
  
 L'esempio è necessario anche Microsoft Visualization e SDK di modellazione, che richiedono che non tutte le shell.  
  
## <a name="preparing-your-solution"></a>Preparazione della soluzione  
 Per impostazione predefinita, la compilazione di modelli della Shell per pacchetti VSIX, ma questo comportamento è destinato principalmente a scopo di debug. Quando si distribuisce un'applicazione Shell, è necessario utilizzare i pacchetti MSI per consentire per l'accesso del Registro di sistema e i riavvii durante l'installazione. Per preparare l'applicazione per la distribuzione MSI, eseguire la procedura seguente.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Per preparare un'applicazione Shell per la distribuzione MSI  
  
1.  Modifica di ogni file con estensione vsixmanifest nella soluzione.  
  
     Nel `Identifier` elemento, aggiungere un `InstalledByMSI` elemento e un `SystemComponent` elemento, quindi impostare i valori su `true`.  
  
     Questi elementi impediscono che il programma di installazione VSIX sta tentando di installare i componenti e l'utente da disinstallarli tramite il **estensioni e aggiornamenti** la finestra di dialogo.  
  
2.  Per ogni progetto che contiene un manifesto VSIX, modificare le attività di compilazione per il contenuto nel percorso da cui verrà installato il file MSI di output. Includere il manifesto VSIX nell'output di compilazione, ma non creare un file con estensione VSIX.  
  
## <a name="creating-an-msi-for-your-shell"></a>Creazione di un file MSI per la Shell  
 Per compilare il pacchetto MSI, è consigliabile utilizzare il [il set di strumenti di Windows Installer XML](http://go.microsoft.com/fwlink/?LinkId=82720) perché fornisce maggiore flessibilità rispetto a un progetto di installazione standard.  
  
 Nel file Product.wxs impostare blocchi di rilevamento e il layout dei componenti della Shell.  
  
 Quindi creare le voci del Registro di sistema sia nel file con estensione reg per la soluzione ApplicationRegistry.wxs.  
  
### <a name="detection-blocks"></a>Blocchi di rilevamento  
 Un blocco di rilevamento è costituito da un `Property` elemento che specifica un prerequisito per rilevare e un `Condition` elemento che specifica un messaggio da restituire se il prerequisito non è presente nel computer. Ad esempio, l'applicazione Shell richiederà Microsoft Visual Studio Shell ridistribuibili e il blocco di rilevamento sarà simile il markup seguente.  
  
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
  
### <a name="layout-of-shell-components"></a>Layout dei componenti della Shell  
 È necessario aggiungere gli elementi per identificare la struttura di directory di destinazione e i componenti da installare.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Per impostare il layout dei componenti della Shell  
  
1.  Creare una gerarchia di `Directory` gli elementi per rappresentare tutte le directory da creare nel file system nel computer di destinazione, come illustrato nell'esempio seguente.  
  
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
  
     Queste directory a cui fa riferimento `Id` quando vengono specificati i file che devono essere installati.  
  
2.  Identificare i componenti che richiedono la Shell e l'applicazione Shell, come illustrato nell'esempio seguente.  
  
    > [!NOTE]
    >  Alcuni elementi possono fare riferimento alle definizioni di altri file con estensione wxs.  
  
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
  
    1.  Il `ComponentRef` elemento fa riferimento a un altro file con estensione wxs che identifica i file che richiede il componente corrente. Ad esempio, GeneralProfile presenta la seguente definizione in HelpAbout.wxs.  
  
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
  
         Il `DirectoryRef` elemento specifica in cui questi file vengono inviati nel computer dell'utente. Il `Directory` elemento specifica che verrà installato in una sottodirectory, mentre ogni `File` elemento rappresenta un file che viene compilato o che esiste come parte della soluzione e identifica in tale file è disponibile quando viene creato il file con estensione MSI.  
  
    2.  Il `ComponentGroupRef` elemento fa riferimento a un gruppo di altri componenti (o i componenti e i gruppi di componenti). Ad esempio, `ComponentGroupRef` in ApplicationGroup viene definito come segue in Application.wxs.  
  
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
    >  Le dipendenze per le applicazioni Shell (Isolated) sono necessari: DebuggerProxy, MasterPkgDef, risorse (in particolare il file .winprf), applicazione e PkgDefs.  
  
### <a name="registry-entries"></a>Voci del Registro di sistema  
 Il modello di progetto Shell (Isolated) include un *ProjectName*file con estensione reg per le chiavi del Registro di sistema nell'installazione di tipo merge. Queste voci del Registro di sistema devono far parte del file MSI per scopi di pulizia sia l'installazione. È inoltre necessario creare i blocchi del Registro di sistema corrispondenti in ApplicationRegistry.wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Per integrare le voci del Registro di sistema in MSI  
  
1.  Nel **Shell Customization** cartella, aprire *ProjectName*. reg.  
  
2.  Sostituire tutte le istanze del token di $ $RootFolder con il percorso della directory di installazione di destinazione.  
  
3.  Aggiungere eventuali altre voci del Registro di sistema richieste dall'applicazione.  
  
4.  Aprire ApplicationRegistry.wxs.  
  
5.  Per ogni voce del Registro di sistema in *ProjectName*reg, aggiungere un blocco del Registro di sistema corrispondenti, come negli esempi seguenti.  
  
    |*NomeProgetto*Reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "Oggetto DTE PhotoStudio"|\<RegistryKey Id = 'DteClsidRegKey' radice 'HKCR' chiave = =' $(VAR. DteClsidRegKey)' azione = 'createAndRemoveOnUninstall' ><br /><br /> \<Tipo RegistryValue = 'stringa' nome =' @' valore =' $(VAR. Oggetto ShortProductName) DTE' / ><br /><br /> \</ RegistryKey >|  
    |[HKEY_CLASSES_ROOT\CLSID\\\LocalServer32 {bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "$RootFolder$\PhotoStudio.exe"|\<RegistryKey Id = 'DteLocSrv32RegKey' radice 'HKCR' chiave = =' $(VAR. \LocalServer32 DteClsidRegKey)' azione = 'createAndRemoveOnUninstall' ><br /><br /> \<Tipo RegistryValue = 'stringa' nome =' @' valore ='[INSTALLDIR] $(VAR. .Exe ShortProductName)' / ><br /><br /> \</ RegistryKey >|  
  
     In questo esempio, Var.DteClsidRegKey risolve la chiave del Registro di sistema nella riga superiore. Risolve Var.ShortProductName `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Creazione di un programma di avvio del programma di installazione  
 MSI completato verrà installato solo se tutti i prerequisiti vengono installati prima di tutto. Per semplificare l'esperienza utente finale, creare un programma di installazione che raccoglie e installa tutti i prerequisiti prima di installare l'applicazione. Per garantire una corretta installazione, eseguire queste azioni:  
  
-   Applicare l'installazione dall'amministratore.  
  
-   Rilevare se è installata Visual Studio Shell (Isolated).  
  
-   Eseguire uno o entrambi Shell i programmi di installazione nell'ordine.  
  
-   Gestire le richieste di riavvio.  
  
-   Eseguire il file MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Applicazione di installazione dall'amministratore  
 Questa procedura è necessaria per abilitare il programma di installazione di accedere alle directory necessarie, ad esempio il file \Programmi\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Per imporre l'installazione dall'amministratore  
  
1.  Aprire il menu di scelta rapida per il progetto di installazione e quindi scegliere **proprietà**.  
  
2.  In **File di configurazione del Linker/proprietà/manifesto**, impostare **il livello di esecuzione controllo dell'account utente** a **requireAdministrator**.  
  
     Questa proprietà consente di inserire l'attributo che richiede il programma da eseguire come amministratore nel file manifesto incorporato.  
  
### <a name="detecting-shell-installations"></a>Rilevamento di installazioni di Shell  
 Per determinare se è necessario installare Visual Studio Shell (Isolated), determinare innanzitutto se è già installato controllando il valore del Registro di sistema di HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
>  Questi valori vengono inoltre letti dal blocco in Product.wxs rilevamento Shell.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder specifica il percorso in cui è stata installata Visual Studio Shell e possono essere cercati i file non esiste.  
  
 Per un esempio di come rilevare un'installazione di Shell, vedere il `GetProductDirFromReg` funzione di Utilities.cpp nell'esempio di distribuzione della Shell.  
  
 Se una o entrambe delle shell di Visual Studio che richiede il pacchetto non è installato nel computer, è necessario aggiungere all'elenco dei componenti da installare. Per un esempio, vedere il `ComponentsPage::OnInitDialog` funzione di ComponentsPage.cpp nell'esempio di distribuzione della Shell.  
  
### <a name="running-the-shell-installers"></a>Esegue i programmi di installazione della Shell  
 Per eseguire i programmi di installazione di Shell, chiamare i componenti ridistribuibili di Visual Studio Shell utilizzando gli argomenti della riga di comando appropriati. Come minimo, è necessario utilizzare gli argomenti della riga di comando **/q /norestart** e verificare che il codice restituito determinare le azioni da intraprendere successivamente. Nell'esempio seguente viene eseguita la Shell (Isolated) redistributable.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Esegue i programmi di installazione di Shell Language Pack  
 Se si trova invece che la shell o la shell sono state installate e solo necessario un language pack, è possibile installare i language pack come illustrato nell'esempio seguente.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Valori restituiti sulla decifrazione  
 In alcuni sistemi operativi, l'installazione di Visual Studio Shell (Isolated) richiede il riavvio. Questa condizione può essere determinata mediante il codice restituito della chiamata a `ExecCmd`.  
  
|Valore restituito|Descrizione|  
|------------------|-----------------|  
|ERROR_SUCCESS|Installazione completata. È ora possibile installare l'applicazione.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Installazione completata. È possibile installare l'applicazione dopo il riavvio del computer.|  
|3015|È in corso l'installazione. Per continuare l'installazione, è necessario un riavvio del computer.|  
  
### <a name="handling-restarts"></a>Gestione riavvio  
 Quando è stato eseguito il programma di installazione di Shell utilizzando il **/norestart** argomento, è specificato che non riavviare il computer o richiedere il riavvio del computer. Tuttavia, potrebbe essere necessario un riavvio e, è necessario assicurarsi che il programma di installazione continuerà dopo il riavvio del computer.  
  
 Per gestire correttamente i riavvii, assicurarsi che un solo programma di installazione viene impostato per riprendere e che il processo di ripristino verrà gestito correttamente.  
  
 Se viene restituito ERROR_SUCCESS_REBOOT_REQUIRED o 3015, il codice necessario riavviare il computer prima di continua l'installazione.  
  
 Per gestire i riavvii, eseguire queste azioni:  
  
-   Impostare il Registro di sistema per riprendere l'installazione di avvio di Windows.  
  
-   Eseguire un riavvio del doppio del programma di avvio automatico.  
  
-   Eliminare la chiave di ResumeData installer Shell.  
  
-   Riavvio di Windows.  
  
-   Reimpostare il percorso iniziale del file MSI.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Impostazione del Registro di sistema a riprendere l'installazione all'avvio di Windows  
 La chiave del Registro di sistema HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ viene eseguita all'avvio del sistema con autorizzazioni amministrative e quindi verrà cancellata. HKEY_CURRENT_USER contiene una chiave simile, ma viene eseguito come utente normale e non è appropriato per le installazioni. È possibile riprendere l'installazione inserendo un valore stringa nella chiave RunOnce che chiama il programma di installazione. Tuttavia, si consiglia di chiamare il programma di installazione utilizzando un **/riavviare** o un parametro simile per notificare all'applicazione che sta riprendendo anziché iniziare. È anche possibile includere parametri per indicare in cui ti trovi nel processo di installazione, è particolarmente utile nelle installazioni che potrebbero richiedere più riavvii.  
  
 Nell'esempio seguente mostra un valore di chiave del Registro di sistema RunOnce per la ripresa di un'installazione.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Riavvio di Double l'installazione del programma di avvio automatico  
 Se il programma di installazione viene utilizzato direttamente dal RunOnce, sarà in grado di caricare completamente il desktop. Per rendere disponibile l'interfaccia utente completa, è necessario creare un'altra esecuzione del programma di installazione e terminare l'istanza RunOnce.  
  
 È necessario eseguire nuovamente il programma di installazione in modo che ottiene le autorizzazioni corrette, è necessario fornire informazioni sufficienti per sapere dove è stato arrestato prima del riavvio, come illustrato nell'esempio seguente.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>L'eliminazione della chiave di ResumeData Shell programma di installazione  
 Il programma di installazione di Shell imposta la chiave del Registro di sistema HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData con i dati per riprendere l'installazione dopo il riavvio. Poiché l'applicazione, non il programma di installazione Shell, viene ripresa, eliminare tale chiave del Registro di sistema, come illustrato nell'esempio seguente.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Il riavvio di Windows  
 Dopo aver impostato le chiavi del Registro di sistema, è possibile riavviare Windows. L'esempio seguente richiama i comandi di riavvio per diversi sistemi operativi Windows.  
  
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
  
### <a name="resetting-the-start-path-of-msi"></a>Reimpostare il percorso iniziale di MSI  
 Prima del riavvio, la directory corrente sia il percorso del programma di installazione, ma dopo il riavvio, il percorso diventa directory system32. Il programma di installazione deve reimpostare la directory corrente prima di ogni chiamata MSI, come illustrato nell'esempio seguente.  
  
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
  
### <a name="running-the-application-msi"></a>Esecuzione dell'applicazione MSI  
 Dopo l'installazione di Visual Studio Shell restituisce ERROR_SUCCESS, è possibile eseguire il file MSI per l'applicazione. Perché il programma di installazione fornisce l'interfaccia utente, è possibile avviare il file MSI in modalità non interattiva (**/q**) e con la registrazione (**/L**), come illustrato nell'esempio seguente.  
  
```cpp  
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
 [Procedura dettagliata: Creazione di un'applicazione shell isolata di base](walkthrough-creating-a-basic-isolated-shell-application.md)