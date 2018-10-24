---
title: Installazione di un'applicazione Shell isolata | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7722132a81c63902450edd85ef90bde94ad94744
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880510"
---
# <a name="installing-an-isolated-shell-application"></a>Installazione di un'applicazione Shell isolata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per installare un'app di Shell è necessario eseguire i passaggi seguenti.  
  
- Preparare la soluzione.  
  
- Creare un pacchetto Windows Installer (MSI) per l'applicazione.  
  
- Creare un programma di avvio del programma di installazione.  
  
  Tutto il codice di esempio in questo documento provengono dal [Shell di esempio di distribuzione](http://go.microsoft.com/fwlink/?LinkId=262245), che è possibile scaricare dalla raccolta di codice del sito Web MSDN. L'esempio mostra i risultati dell'esecuzione di ognuno di questi passaggi.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire le procedure descritte in questo argomento, gli strumenti seguenti devono essere installati nel computer.  
  
- Visual Studio SDK  
  
- Il [set di strumenti di Windows Installer XML](http://go.microsoft.com/fwlink/?LinkId=82720) versione 3.6  
  
  L'esempio richiede anche il Microsoft Visualization and Modeling SDK, che richiedono la shell non tutte.  
  
## <a name="preparing-your-solution"></a>Preparazione della soluzione  
 Per impostazione predefinita, i modelli di Shell di compilazione di pacchetti VSIX, ma questo comportamento è destinato principalmente a scopo di debug. Quando si distribuisce un'applicazione Shell, è necessario utilizzare i pacchetti MSI per consentire l'accesso del Registro di sistema e per i riavvii durante l'installazione. Per preparare l'applicazione per la distribuzione di file MSI, eseguire la procedura seguente.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Per preparare un'applicazione di Shell per la distribuzione di identità del servizio gestito  
  
1.  Modificare ogni file con estensione vsixmanifest nella soluzione.  
  
     Nel `Identifier` elemento, aggiungere un' `InstalledByMSI` elemento e un `SystemComponent` elemento, quindi impostare i relativi valori su `true`.  
  
     Questi elementi impediscono che il programma di installazione VSIX sta tentando di installare i componenti e l'utente da disinstallarli tramite la **estensioni e aggiornamenti** nella finestra di dialogo.  
  
2.  Per ogni progetto che contiene un manifesto VSIX, modificare le attività di compilazione per il contenuto nella posizione da cui si installerà l'identità del servizio gestito di output. Includere il manifesto VSIX nell'output di compilazione, ma non creare un file con estensione VSIX.  
  
## <a name="creating-an-msi-for-your-shell"></a>Creazione di un file MSI per la Shell  
 Per compilare il pacchetto MSI, è consigliabile usare la [set di strumenti di Windows Installer XML](http://go.microsoft.com/fwlink/?LinkId=82720) perché offre maggiore flessibilità rispetto a un progetto di installazione standard.  
  
 Nel file Product.wxs, impostare blocchi di rilevamento e il layout dei componenti della Shell.  
  
 Creare quindi le voci del Registro di sistema, nel file con estensione reg per la soluzione sia in ApplicationRegistry.wxs.  
  
### <a name="detection-blocks"></a>Blocchi di rilevamento  
 Un blocco di rilevamento è costituito da un `Property` elemento che specifica un prerequisito per il rilevamento e un `Condition` elemento che specifica un messaggio da restituire se il prerequisito non è presente nel computer. Ad esempio, l'applicazione di Shell richiederà Microsoft Visual Studio Shell redistributable e il blocco di rilevamento sarà simile al markup seguente.  
  
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
  
1.  Creare una gerarchia di `Directory` elementi per rappresentare tutte le directory da creare nel file system nel computer di destinazione, come illustrato nell'esempio seguente.  
  
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
  
     Queste directory a cui fa riferimento `Id` quando sono stati specificati file da installare.  
  
2.  Identificare i componenti che richiedono la Shell e l'applicazione di Shell, come illustrato nell'esempio seguente.  
  
    > [!NOTE]
    >  Alcuni elementi potrebbero fare riferimento alle definizioni in altri file con estensione wxs.  
  
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
  
    1.  Il `ComponentRef` elemento fa riferimento a un altro file con estensione wxs che identifica i file richiesti dal componente corrente. Ad esempio, GeneralProfile presenta la seguente definizione in HelpAbout.wxs.  
  
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
  
         Il `DirectoryRef` elemento specifica in cui questi file Vai nel computer dell'utente. Il `Directory` elemento specifica che verrà installato in una sottodirectory, mentre ogni `File` elemento rappresenta un file che viene compilato o che esiste come parte della soluzione e identifica in cui tale file è disponibile quando viene creato il file MSI.  
  
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
    >  Le dipendenze per le applicazioni di Shell (Isolated) sono necessari: DebuggerProxy, MasterPkgDef, risorse (in particolare il file .winprf), applicazione e PkgDefs.  
  
### <a name="registry-entries"></a>Voci del Registro di sistema  
 Il modello di progetto Shell (Isolated) include un' *ProjectName*file con estensione reg per le chiavi del Registro di sistema nell'installazione di tipo merge. Queste voci del Registro di sistema devono far parte del servizio gestito per scopi di pulizia sia l'installazione. È anche necessario creare i blocchi del Registro di sistema corrispondenti in ApplicationRegistry.wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Integrare le voci del Registro di sistema in MSI  
  
1.  Nel **personalizzazione della Shell** cartella, aprire *ProjectName*. reg.  
  
2.  Sostituire tutte le istanze del token $ $RootFolder con il percorso della directory di installazione di destinazione.  
  
3.  Aggiungere eventuali altre voci del Registro di sistema richieste dall'applicazione.  
  
4.  Aprire ApplicationRegistry.wxs.  
  
5.  Per ogni voce del Registro di sistema *ProjectName*. reg, aggiungere un blocco del Registro di sistema corrispondenti, come negli esempi seguenti.  
  
    |*ProjectName*Reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "Oggetto DTE PhotoStudio"|\<Id RegistryKey = radice 'DteClsidRegKey' = la chiave 'HKCR' =' $(VAR. DteClsidRegKey)' azione = 'createAndRemoveOnUninstall' ><br /><br /> \<Tipo RegistryValue = 'stringa' nome =' @' valore =' $(VAR. Oggetto ShortProductName) DTE' / ><br /><br /> \</ RegistryKey >|  
    |[HKEY_CLASSES_ROOT\CLSID\\\LocalServer32 {bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "$RootFolder$\PhotoStudio.exe"|\<Id RegistryKey = radice 'DteLocSrv32RegKey' = la chiave 'HKCR' =' $(VAR. \LocalServer32 DteClsidRegKey)' azione = 'createAndRemoveOnUninstall' ><br /><br /> \<Tipo RegistryValue = 'stringa' nome =' @' valore ='[INSTALLDIR] $(VAR. .Exe ShortProductName) "/ ><br /><br /> \</ RegistryKey >|  
  
     In questo esempio Var.DteClsidRegKey risolve la chiave del Registro di sistema nella riga superiore. Viene risolto Var.ShortProductName `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Creazione di un programma di installazione bootstrap  
 Identità del servizio gestito completato verrà installato solo se tutti i prerequisiti sono installati prima di tutto. Per semplificare l'esperienza dell'utente finale, creare un programma di installazione che raccoglie e installa tutti i prerequisiti prima di installare l'applicazione. Per garantire una corretta installazione, eseguire queste operazioni:  
  
-   Imporre l'installazione dall'amministratore.  
  
-   Verificare se è installata Visual Studio Shell (Isolated).  
  
-   Eseguire uno o entrambi Shell i programmi di installazione nell'ordine.  
  
-   Gestire le richieste di riavvio.  
  
-   Eseguire il file MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>L'applicazione di installazione dall'amministratore  
 Questa procedura è necessaria per abilitare il programma di installazione di accesso richiesto alle directory, ad esempio file \Programmi\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Per imporre l'installazione dall'amministratore  
  
1.  Aprire il menu di scelta rapida per il progetto di installazione e quindi scegliere **proprietà**.  
  
2.  Sotto **File di configurazione del Linker/proprietà/manifesto**, impostare **livello di esecuzione controllo dell'account utente** al **requireAdministrator**.  
  
     Questa proprietà inserisce l'attributo che richiede il programma da eseguire come amministratore nel file manifesto incorporato.  
  
### <a name="detecting-shell-installations"></a>Rilevamento di installazioni di Shell  
 Per determinare se deve essere installata Visual Studio Shell (Isolated), determinare innanzitutto se è già installato controllando il valore del Registro di sistema di HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
>  Questi valori vengono inoltre letti dal blocco di rilevamento della Shell in Product.wxs.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder specifica la posizione in cui è stata installata Visual Studio Shell e possono essere cercati i file non esiste.  
  
 Per un esempio di come rilevare un'installazione di Shell, vedere il `GetProductDirFromReg` funzione Utilities.cpp nell'esempio di distribuzione della Shell.  
  
 Se una o entrambe di Visual Studio Shell che richiede il pacchetto non è installato nel computer, è necessario aggiungerli all'elenco di componenti da installare. Per un esempio, vedere il `ComponentsPage::OnInitDialog` funzione ComponentsPage.cpp nell'esempio di distribuzione della Shell.  
  
### <a name="running-the-shell-installers"></a>Esegue i programmi di installazione della Shell  
 Per eseguire i programmi di installazione di Shell, chiamare i componenti ridistribuibili di Visual Studio Shell utilizzando gli argomenti della riga di comando appropriati. Come minimo, è necessario usare gli argomenti della riga di comando **/q /norestart** e controllare il codice restituito determinare che cosa deve essere eseguita successivamente. L'esempio seguente esegue la Shell (Isolated) redistributable.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Esegue i programmi di installazione di Shell Language Pack  
 Se si trova invece che la shell o la shell sono state installate e semplicemente necessario un linguaggio di tipo pack, è possibile installare i language pack come illustrato nell'esempio seguente.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Valori restituiti per decifrare  
 In alcuni sistemi operativi, l'installazione di Visual Studio Shell (Isolated) richiede il riavvio. Questa condizione può essere determinata mediante il codice restituito della chiamata a `ExecCmd`.  
  
|Valore restituito|Descrizione|  
|------------------|-----------------|  
|ERROR_SUCCESS|Installazione completata. È ora possibile installare l'applicazione.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Installazione completata. È possibile installare l'applicazione dopo che il computer è stato riavviato.|  
|3015|È in corso l'installazione. È necessario riavviare il computer per continuare l'installazione.|  
  
### <a name="handling-restarts"></a>Gestione riavvio  
 Quando è stato eseguito il programma di installazione di Shell usando il **/norestart** argomento, è specificato che non sarebbe riavviare il computer o richiedere il riavvio del computer. Tuttavia, potrebbe essere necessario un riavvio e assicurarsi che il programma di installazione continuerà dopo il riavvio del computer.  
  
 Per gestire correttamente i riavvii, assicurarsi che un solo programma di installazione viene impostato per riprendere e che il processo di ripristino verrà gestito correttamente.  
  
 Se viene restituito ERROR_SUCCESS_REBOOT_REQUIRED o 3015, il codice deve riavviare il computer prima di proseguirà con l'installazione.  
  
 Per gestire i riavvii, eseguire queste operazioni:  
  
-   Impostare il Registro di sistema per riprendere l'installazione all'avvio di Windows.  
  
-   Eseguire un riavvio del doppio del programma di avvio automatico.  
  
-   Eliminare la chiave di ResumeData Shell programma di installazione.  
  
-   Riavviare Windows.  
  
-   Reimpostare il percorso di avvio del servizio gestito.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Impostazione del registro per riprendere il programma di installazione all'avvio di Windows  
 La chiave del Registro di sistema HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ viene eseguita all'avvio del sistema con autorizzazioni amministrative e quindi verrà cancellata. HKEY_CURRENT_USER contiene una chiave simile, ma viene eseguito come utente normale e non è appropriato per le installazioni. È possibile riprendere l'installazione, inserendo un valore stringa nella chiave RunOnce che chiama il programma di installazione. Tuttavia, si consiglia di chiamare il programma di installazione tramite un **riavviata** o parametro simile per notificare all'applicazione che sta riprendendo anziché iniziare. È anche possibile includere parametri per indicare dove si è nel processo di installazione, è particolarmente utile nelle installazioni dei componenti che potrebbero richiedere più riavvii.  
  
 Nell'esempio seguente mostra un valore di chiave del Registro di sistema RunOnce per la ripresa di un'installazione.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Installazione di Double il riavvio del programma di avvio automatico  
 Se il programma di installazione viene utilizzato direttamente dal RunOnce, il desktop sarà in grado di caricare completamente. Per rendere disponibile l'interfaccia utente completa, è necessario creare un'altra esecuzione del programma di installazione e terminare l'istanza RunOnce.  
  
 È necessario eseguire nuovamente il programma di installazione in modo che ottiene le autorizzazioni corrette, è necessario specificare informazioni sufficienti per sapere in cui è stata interrotta prima del riavvio, come illustrato nell'esempio seguente.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Eliminazione della chiave di ResumeData Shell programma di installazione  
 Il programma di installazione di Shell imposta la chiave del Registro di sistema HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData con i dati per riprendere l'installazione dopo il riavvio. Poiché l'applicazione, non il programma di installazione Shell, viene ripresa, eliminare tale chiave del Registro di sistema, come illustrato nell'esempio seguente.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Il riavvio di Windows  
 Dopo aver impostato le chiavi del Registro di sistema, è possibile riavviare Windows. Nell'esempio seguente richiama i comandi di riavvio per diversi sistemi operativi Windows.  
  
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
  
### <a name="resetting-the-start-path-of-msi"></a>Reimpostare il percorso di avvio del servizio gestito  
 Prima del riavvio, la directory corrente è il percorso del programma di installazione, ma, dopo il riavvio, il percorso diventa directory system32. Il programma di installazione deve reimpostare la directory corrente prima di ogni chiamata di identità del servizio gestito, come illustrato nell'esempio seguente.  
  
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
  
### <a name="running-the-application-msi"></a>Esecuzione dell'applicazione identità del servizio gestito  
 Dopo che il programma di installazione di Visual Studio Shell viene restituito ERROR_SUCCESS, è possibile eseguire il file MSI dell'applicazione. Poiché il programma di installazione fornisce l'interfaccia utente, iniziare l'identità del servizio gestito in modalità non interattiva (**/q**) e con la registrazione (**/L**), come illustrato nell'esempio seguente.  
  
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

