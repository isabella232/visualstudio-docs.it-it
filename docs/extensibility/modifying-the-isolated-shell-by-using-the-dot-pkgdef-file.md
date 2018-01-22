---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file
title: Modifica la Shell isolata tramite il. File pkgdef | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: addeeaa294a81acce6558feb5257fee1344532f8
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2018
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>Modifica la Shell isolata tramite il. File pkgdef
Il file. pkgdef supporta le impostazioni che è possibile utilizzare per personalizzare un'applicazione shell isolata. Specifica valori che vengono creati quando un'applicazione è installata in un computer e di cui viene fatto riferimento dalla shell di Visual Studio quando avvia l'applicazione. Le impostazioni sono organizzate nel file in base alle chiavi del Registro di sistema applicabili.  
  
> [!WARNING]
>  Si noti che quando si avvia Visual Studio non vengono analizzati i file. pkgdef che non sono dichiarati i file con estensione vsixmanifest del pacchetto VSPackage.  
  
 Il file. pkgdef contiene sezioni che sono ognuna identificate da una chiave, ovvero `[$RootKey$]` o `[$RootKey$\` *sottochiave*`]`, dove $ $RootKey è la chiave radice per l'applicazione.  
  
 Ogni sezione contiene le coppie nome/valore con il seguente formato: `"` *ValueName*`"=`*valore*.  
  
 I valori sono una stringa racchiusa tra virgolette o un numero intero a 32 bit che è rappresentato come un valore dword. I valori sono i seguenti vincoli:  
  
-   Tutti i valori dword sono in formato esadecimale, ad esempio `dword:00000001`.  
  
     Per i valori booleani, 1 rappresenta il valore true e 0 rappresenta false.  
  
-   Tutte le stringhe GUID sono nel formato del Registro di sistema, ad esempio, `"{00000000-0000-0000-0000-000000000000}"`.  
  
-   Tutti gli identificatori di risorsa localizzabile hanno il formato "@*resourceID*" o "#*resourceID*", dove *resourceID* è l'identificatore di risorsa nel pacchetto di interfaccia utente dell'applicazione, ad esempio, `"@102"`. Il pacchetto di applicazione dell'interfaccia utente è il pacchetto a cui fa riferimento in base alle impostazioni AppLocalizationPackage.  
  
 Ad esempio,  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 È possibile aggiungere commenti al file. pkgdef. Un commento a riga singola con due barre come i primi due caratteri.  
  
 Per un elenco di stringhe di sostituzione, vedere [sostituzione utilizzare stringhe. Pkgdef e. File Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
 Nelle sezioni seguenti vengono descritti i valori del Registro di sistema che influiscono sul comportamento della shell di Visual Studio in modalità isolata. È inoltre possibile definire i valori del Registro di sistema aggiuntive per l'applicazione in questo file.  
  
> [!NOTE]
>  Se un'impostazione non viene specificata nel file. pkgdef, quindi viene creata alcuna voce corrispondente nel Registro di sistema.  
  
## <a name="settings"></a>Impostazioni  
 Nella tabella seguente vengono descritti i valori definiti in [$$RootKey].  
  
|nome|Tipo|Valore|  
|----------|----------|-----------|  
|AddinsAllowed|dword|True se i componenti aggiuntivi possono essere caricati; in caso contrario, false.<br /><br /> Il valore predefinito è true.|  
|AllowsDroppedFilesOnMainWindow|dword|True se la finestra principale può accettare file rilasciati; in caso contrario, false. I file trascinati nella finestra principale vengono aperte usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> metodo. Ciò equivale all'apertura di un documento tramite il **aprire** comando il **File** menu nell'applicazione.<br /><br /> Il valore predefinito è true.|  
|AppIcon|stringa|Il percorso completo dell'icona di programma. Questa icona viene visualizzata nella barra del titolo a sinistra del nome dell'applicazione.<br /><br /> Il valore predefinito è "$ $RootFolder\\*solutionName*ico", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|AppLocalizationPackage|stringa|Il GUID del pacchetto VSPackage che contiene l'assembly satellite di interfaccia utente per l'applicazione. Questo pacchetto VSPackage include una versione compilata del file con estensione vsct e può includere altre stringhe localizzate. Set di funzionalità e i gruppi di comandi di menu possono essere abilitati o disabilitati modificando le impostazioni nel file vsct del progetto dell'interfaccia utente.<br /><br /> Il valore predefinito è "{*vsUiPackageGuid*}", dove *vsUiPackageGuid* è il GUID assegnato al pacchetto di interfaccia utente dell'applicazione.|  
|AppName|stringa|Nome dell'applicazione. Il nome viene visualizzato nella barra del titolo della finestra dell'applicazione.<br /><br /> Il valore predefinito è il nome del file di soluzione dell'applicazione.|  
|CommandLineLogo|stringa|Il testo dell'intestazione quando l'applicazione viene eseguita in una finestra della console. Questa impostazione influisce solo sulle applicazioni che supportano operazioni di compilazione da riga di comando.<br /><br /> Il valore predefinito è "*companyName * * solutionName* versione 1.0.", dove *companyName* è il nome della società fornito durante l'installazione di Windows, e *solutionName*è il nome del file di soluzione dell'applicazione.|  
|DefaultDebugEngine|stringa|Il GUID dell'oggetto default motore da utilizzare per l'applicazione di debug.<br /><br /> Nota: Un GUID vuoto (tutti zeri) indica che l'applicazione non specifica un motore di debug predefinito. In questo modo il debugger selezionare il motore di debug da usare.<br /><br /> Il valore predefinito è "{00000000-0000-0000-0000-000000000000}".|  
|DefaultHomePage|stringa|L'URL di pagina iniziale predefinito per la finestra del Web browser interna.<br /><br /> Se il **Home page** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. Per ulteriori informazioni, vedere [Web Browser, ambiente, finestra di dialogo Opzioni](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> Il valore predefinito è l'URL della società fornita durante l'installazione di Windows.|  
|DefaultProjectsLocation|stringa|Il percorso completo della cartella di progetti predefinita. Ad esempio,<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> Se il **percorso progetti di Visual Studio** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. <br /><br /> Il valore predefinito è "$ $MyDocuments\\*solutionName*", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|DefaultSearchPage|stringa|L'URL di pagina di ricerca predefinito per la finestra del browser Web interna.<br /><br /> Se il **pagina ricerca** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. Per ulteriori informazioni, vedere [Web Browser, ambiente, finestra di dialogo Opzioni](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> Il valore predefinito è "http://search.live.com".|  
|DefaultUserFilesFolderRoot|stringa|Il nome della cartella utente relativo all'utente corrente cartella documenti del.<br /><br /> Il valore predefinito è il nome del file di soluzione dell'applicazione.|  
|DisableOutputWindow|dword|Indica se la shell isolata deve considerare la finestra di output come disabilitato.<br /><br /> Se questo valore è impostato su true, Visual Studio non verrà visualizzato l'output di manager di compilazione soluzioni nel **Output** finestra e nasconde il **Mostra finestra di Output a inizio compilazione** casella di controllo di  **Progetti e soluzioni** categoria di **opzioni** la finestra di dialogo.<br /><br /> Il valore predefinito è false.|  
|HideMiscellaneousFilesByDefault|dword|True per nascondere il **file esterni** cartella per impostazione predefinita in **Esplora**; in caso contrario, false.<br /><br /> Se il **Mostra file esterni in Esplora soluzioni** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. Per ulteriori informazioni, vedere [documenti, ambiente, finestra di dialogo Opzioni](../ide/reference/documents-environment-options-dialog-box.md).<br /><br /> Il valore predefinito è false.|  
|HideSolutionConcept|dword|True per creare progetti di tutti i progetti in modalità autonoma e per nascondere la soluzione e i comandi relativi alle soluzioni per i progetti autonomi per impostazione predefinita. in caso contrario, false.<br /><br /> Se il **Mostra sempre soluzione** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione.<br /><br /> Il valore predefinito è false.|  
|NewProjDlgInstalledTemplatesHdr|stringa|Il nome per l'intestazione di modelli di Visual Studio nstalled nel **modelli** nell'elenco di **nuovo progetto** la finestra di dialogo. Si tratta di una stringa o un identificatore di risorsa localizzabile che viene caricato dal pacchetto di interfaccia utente dell'applicazione.<br /><br /> Il valore predefinito è "*solutionName* modelli installati", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|NewProjDlgSlnTreeNodeTitle|stringa|Il nome per il **soluzioni di Visual Studio** nodo il **tipi di progetto** ad albero nel **nuovo progetto** la finestra di dialogo. Si tratta di una stringa o un identificatore di risorsa localizzabile che viene caricato dal pacchetto di interfaccia utente dell'applicazione.<br /><br /> Il valore predefinito è "*solutionName* modelli installati", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|SolutionFileCreatorIdentifier|stringa|L'identificatore di applicazione, viene visualizzato come la seconda riga nei file di soluzione che vengono generati dall'applicazione. Questa riga indica l'applicazione che ha creato il file. Per convenzione, questo valore include sia il nome dell'applicazione e il numero di versione dell'applicazione. Ad esempio,<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> Il programma VSLauncher.exe, vale a dire il programma predefinito per l'apertura di un file di soluzione di Visual Studio, utilizza la seconda riga per determinare la versione di Visual Studio in cui aprire il file della soluzione. L'applicazione richiede il proprio utilità di avvio per gestire i file di soluzione associata. L'utilità di avvio è anche possibile utilizzare questa seconda riga nel file di soluzione per determinare in quale versione dell'applicazione per aprire la soluzione.<br /><br /> Nota: Il programma di Visual Studio VSLauncher.exe non gestisce i file con estensione sln creati da un'applicazione shell isolata.<br /><br /> Il valore predefinito è "*solutionName* File della soluzione, versione del formato 10,00", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|SolutionFileExt|stringa|Estensione di file di soluzione per l'applicazione. Si consiglia di scegliere un'estensione di file univoco (not.sln).<br /><br /> Il valore predefinito è "*solutionName*_sln", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|SplashScreenBitmap|stringa|Il percorso completo del file bitmap per la schermata iniziale per l'applicazione.<br /><br /> Il valore predefinito è "$RootFolder$\Splash.bmp".|  
|ThisVersionDTECLSID|stringa|Identificatore di classe (CLSID) dell'oggetto di automazione per l'applicazione.<br /><br /> L'oggetto di automazione di applicazioni è l'oggetto di livello superiore per l'applicazione nel modello di automazione di Visual Studio shell e implementa il <xref:EnvDTE._DTE?displayProperty=fullName> interfaccia.<br /><br /> Se l'oggetto di automazione di applicazioni è registrato correttamente con la chiave del Registro di sistema HKEY_CLASSES_ROOT\CLSID, quindi è possibile utilizzare il [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) funzione per creare direttamente un'istanza dell'applicazione.<br /><br /> Shell di Visual Studio Usa questo CLSID per registrare l'oggetto di automazione di applicazioni in esecuzione oggetto tabella (tabella ROT) utilizzando il flag ACTIVEOBJECT_WEAK. Consente di utilizzare il [GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)per recuperare un puntatore a un'istanza dell'applicazione in esecuzione. Inoltre, se si definisce un ProgID per l'oggetto di automazione di applicazioni, quindi la shell di Visual Studio registra anche ogni istanza dell'applicazione nella tabella ROT usando un moniker di elemento del form *progID*:*processID* , dove *progID* è il valore ProgID dell'oggetto di automazione dell'applicazione, e *processID* è l'identificatore di processo per l'istanza dell'applicazione. Ad esempio, se si crea un moniker come segue:<br /><br /> `CreateItemMoniker(L"!",`  *instanceString* `, &instanceMoniker)`<br /><br /> dove `instanceString` è il *progID*:*processID* stringa. si potrebbe usare `instanceMoniker` con la funzione GetObject imputrescibili per ottenere l'istanza.<br /><br /> Se l'impostazione ThisVersionDTECLSID viene omesso, l'applicazione non è esposta tramite il modello COM (Component Object). In questo caso, non è possibile creare un'istanza dell'applicazione chiamando il [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) funzione e non può essere registrato nella tabella ROT.<br /><br /> Ogni versione di un pacchetto VSPackage deve avere un CLSID differente.<br /><br /> Il valore predefinito è il GUID generato da Visual Studio per l'oggetto di automazione dell'applicazione.|  
|ThisVersionSolutionCLSID|stringa|Il CLSID dell'oggetto soluzione per l'applicazione.<br /><br /> L'oggetto di automazione soluzione contiene informazioni sulla soluzione corrente aperta in un'istanza dell'applicazione e implementa il <xref:EnvDTE._Solution?displayProperty=fullName> interfaccia.<br /><br /> Se l'oggetto di automazione di soluzione è registrato correttamente con la chiave del Registro di sistema HKEY_CLASSES_ROOT\CLSID, quindi è possibile utilizzare il [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) funzione per creare direttamente un oggetto della soluzione per l'applicazione.<br /><br /> La shell di Visual Studio Usa questo CLSID per registrare l'oggetto di automazione di soluzione nella tabella ROT utilizzando il flag ACTIVEOBJECT_WEAK.<br /><br /> Se questa impostazione viene omessa, quindi la classe di soluzione non è registrata con il modello COM (Component Object) e non può essere creato un oggetto di soluzione chiamando il [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) funzione e non può essere registrato la tabella ROT.<br /><br /> Il valore predefinito è un GUID generato da Visual Studio per l'oggetto della soluzione dell'applicazione.|  
|UserFilesSubFolderName|stringa|Il nome della sottocartella nella cartella documenti dell'utente in cui l'applicazione crea le sottocartelle e file utente.<br /><br /> Il valore predefinito è il nome del file di soluzione dell'applicazione.|  
|UserOptsFileExt|stringa|L'estensione per i file di opzioni utente di soluzione per l'applicazione.<br /><br /> Il valore predefinito è il nome del file di soluzione dell'applicazione.|  
  
## <a name="binding-path-settings"></a>Impostazioni del percorso di associazione  
 Il [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}] chiave contiene l'elenco delle directory in cui la shell verifica la presenza di assembly. Queste directory vengono aggiunti all'elenco delle directory in cui la shell le ricerche degli assembly privati per l'applicazione.  
  
 Per impostazione predefinita, le voci di alcun percorso di associazione non vengono aggiunti al file. pkgdef. Tuttavia, le seguenti sottodirectory della directory di installazione di Visual Studio vengono aggiunti automaticamente il percorso di associazione all'elenco all'applicazione nel Registro di sistema.  
  
-   Common7\IDE\  
  
-   Common7\IDE\\\PrivateAssemblies  
  
-   Common7\IDE\\\PublicAssemblies  
  
 Per aggiungere una directory per il percorso di associazione, aggiungere una voce nel formato "*nomedirectory*"="", dove *nomedirectory* è un percorso assoluto. Ad esempio,  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>Impostazioni del profilo  
 Nella tabella seguente vengono descritti i valori definiti per ogni pacchetto associati in [$RootKey$ \Profile].  
  
|nome|Tipo|Valore|  
|----------|----------|-----------|  
|AutoSaveFile|stringa|La directory in cui l'applicazione archivia i file di salvataggio automatico.<br /><br /> Il valore predefinito è "$RootFolder$\Profiles\CurrentSettings.vssettings".|  
  
## <a name="package-satellite-dll-settings"></a>Impostazioni di DLL Satellite del pacchetto  
 Nella tabella seguente vengono descritti i valori definiti in [$RootKey$ \Packages\\{*vsPackageGuid*} \SatelliteDll] per il satellite DLL in ogni pacchetto associati, in cui *vsPackageGuid* è il GUID del pacchetto associato.  
  
|nome|Tipo|Valore|  
|----------|----------|-----------|  
|NomeDLL|stringa|Il nome del file della DLL.<br /><br /> Il valore predefinito è "*solutionName*ui.dll", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|Path|stringa|La directory che contiene la DLL satellite.<br /><br /> Il valore predefinito è "$PackageFolder$".|  
  
## <a name="package-menu-item-settings"></a>Impostazioni di voce di Menu pacchetto  
 La chiave del Registro di sistema [$RootKey$ \Menus] definisce i file di risorse dell'interfaccia utente per l'applicazione.  
  
 Valori di voci di menu hanno il formato "{*vsUiPackageGuid*}"=" *resourceId*, *versionNumber*", dove *vsUiPackageGuid* è il GUID del il pacchetto dell'interfaccia utente dell'applicazione, *resourceId* è l'identificatore di risorsa della risorsa che contiene gli elementi dell'interfaccia utente, CTMENU e *versionNumber* è un numero di versione virtuale per il CTMENU risorsa. Per ulteriori informazioni, vedere [Assembly di interoperabilità la registrazione di gestori di comandi](../extensibility/internals/registering-interop-assembly-command-handlers.md).  
  
 Per impostazione predefinita, viene creata una voce di menu nel file. pkgdef per il pacchetto di applicazione dell'interfaccia utente.  
  
 Per ogni pacchetto che fornisce le voci di menu e che viene distribuito come parte dell'applicazione, aggiungere una voce di menu per il pacchetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione Shell isolata](../extensibility/customizing-the-isolated-shell.md)   
 [. File Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)