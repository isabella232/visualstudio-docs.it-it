---
title: Modifica della Shell isolata tramite il. File pkgdef | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f70036f91eb52d85054465e6eea9f82672d851f6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528792"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>Modifica della Shell isolata tramite il. File pkgdef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [modificando l'isolato Shell tramite l'utilizzo di. File pkgdef](https://docs.microsoft.com/visualstudio/extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file).  
  
Il file con estensione pkgdef supporta le impostazioni che è possibile usare per personalizzare un'applicazione shell isolata. Specifica i valori che vengono creati quando un'applicazione è installata in un computer e che viene fatto riferimento dalla shell di Visual Studio quando avvia l'applicazione. Le impostazioni sono organizzate nel file di base alle chiavi del Registro di sistema applicabili.  
  
> [!WARNING]
>  Si noti che quando si avvia Visual Studio non vengono analizzati i file con estensione pkgdef che non sono dichiarati i file con estensione vsixmanifest del pacchetto VSPackage.  
  
 Il file con estensione pkgdef contiene sezioni che sono tutti identificate da una chiave, ovvero `[$RootKey$]` oppure `[$RootKey$\` *sottochiave*`]`, dove $ $RootKey è la chiave radice per l'applicazione.  
  
 Ogni sezione contiene coppie nome/valore che hanno il formato seguente: `"` *ValueName*`"=`*valore*.  
  
 I valori sono una stringa racchiusa tra virgolette o un numero intero a 32 bit che è rappresentato come un valore dword. I valori sono i seguenti vincoli:  
  
-   Tutti i valori dword sono in formato esadecimale, ad esempio `dword:00000001`.  
  
     Per i valori booleani, 1 indica true e 0 rappresenta false.  
  
-   Tutte le stringhe GUID sono nel formato del Registro di sistema, ad esempio, `"{00000000-0000-0000-0000-000000000000}"`.  
  
-   Tutti gli identificatori di risorsa localizzabile hanno il formato "@*resourceID*" o "&*resourceID*", dove *resourceID* è l'identificatore di risorsa nel pacchetto dell'interfaccia utente dell'applicazione, ad esempio, `"@102"`. Il pacchetto dell'interfaccia utente dell'applicazione è il pacchetto cui viene fatto riferimento in base alle impostazioni AppLocalizationPackage.  
  
 Ad esempio,  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 È possibile aggiungere commenti al file pkgdef. Un commento a riga singola dispone di due barre come i primi due caratteri.  
  
 Per un elenco di stringhe di sostituzione, vedere [le stringhe di sostituzione usate in. Pkgdef e. File Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
 Le sezioni seguenti descrivono i valori del Registro di sistema che influiscono sul comportamento della shell di Visual Studio in modalità isolata. È anche possibile definire i valori del Registro di sistema aggiuntive per l'applicazione in questo file.  
  
> [!NOTE]
>  Se un'impostazione non viene specificata nel file con estensione pkgdef, viene immessa alcuna voce corrispondente nel Registro di sistema.  
  
## <a name="settings"></a>Impostazioni  
 Nella tabella seguente vengono descritti i valori definiti in [$RootKey$].  
  
|nome|Tipo|Valore|  
|----------|----------|-----------|  
|AddinsAllowed|dword|True se è possano caricare componenti aggiuntivi; in caso contrario, false.<br /><br /> Il valore predefinito è true.|  
|AllowsDroppedFilesOnMainWindow|dword|True se la finestra principale può accettare file rilasciati; in caso contrario, false. I file rilasciati nella finestra principale vengono aperti utilizzando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> (metodo). Ciò equivale all'apertura di un documento tramite il **aperto** comando le **File** menu nell'applicazione.<br /><br /> Il valore predefinito è true.|  
|AppIcon|stringa|Il percorso completo dell'icona del programma. Questa icona viene visualizzata nella barra del titolo a sinistra del nome dell'applicazione.<br /><br /> Il valore predefinito è "$ $RootFolder\\*solutionName*ico", dove *solutionName* è il nome del file della soluzione dell'applicazione.|  
|AppLocalizationPackage|stringa|Il GUID del pacchetto VSPackage che contiene l'assembly satellite di interfaccia utente per l'applicazione. Questo pacchetto di Visual Studio include una versione compilata del file con estensione vsct e può includere altre stringhe localizzate. Set di funzionalità e i gruppi di comandi di menu possono essere attivati o disabilitati modificando le impostazioni nel file con estensione vsct progetto dell'interfaccia utente.<br /><br /> Il valore predefinito è "{*vsUiPackageGuid*}", dove *vsUiPackageGuid* è il GUID assegnato al pacchetto dell'interfaccia utente dell'applicazione.|  
|NomeApp|stringa|Nome dell'applicazione. Il nome viene visualizzato nella barra del titolo della finestra dell'applicazione.<br /><br /> Il valore predefinito è il nome del file della soluzione dell'applicazione.|  
|CommandLineLogo|stringa|Il testo dell'intestazione quando viene eseguita l'applicazione in una finestra della console. Questa impostazione influisce solo sulle applicazioni che supportano operazioni di compilazione da riga di comando.<br /><br /> Il valore predefinito è "*companyName * * solutionName* versione 1.0.", dove *companyName* è il nome della società fornito durante l'installazione di Windows, e *solutionName*è il nome del file della soluzione dell'applicazione.|  
|DefaultDebugEngine|stringa|Il GUID del valore predefinito di debug motore da usare per l'applicazione.<br /><br /> Nota: Un GUID vuoto (tutti zeri) indica che l'applicazione non specifica un motore di debug predefinito. In questo modo il debugger selezionare il motore di debug da usare.<br /><br /> Il valore predefinito è "{00000000-0000-0000-0000-000000000000}".|  
|DefaultHomePage|stringa|URL della home page predefinita per la finestra del Web browser interna.<br /><br /> Se il **homepage** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. Per altre informazioni, vedere [Web Browser, ambiente, finestra di dialogo Opzioni](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> Il valore predefinito è l'URL della società fornita durante l'installazione di Windows.|  
|DefaultProjectsLocation|stringa|Il percorso completo della cartella di progetti predefinita. Ad esempio,<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> Se il **percorso progetti di Visual Studio** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. Per altre informazioni, vedere [NIB: generale, progetti e soluzioni, finestra di dialogo Opzioni](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> Il valore predefinito è "$ $MyDocuments\\*solutionName*", dove *solutionName* è il nome del file della soluzione dell'applicazione.|  
|DefaultSearchPage|stringa|L'URL di pagina di ricerca predefinito per la finestra del Web browser interna.<br /><br /> Se il **pagina di ricerca** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. Per altre informazioni, vedere [Web Browser, ambiente, finestra di dialogo Opzioni](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> Il valore predefinito è "http://search.live.com".|  
|DefaultUserFilesFolderRoot|stringa|Cartella documenti del nome della cartella, utente relativo all'utente corrente.<br /><br /> Il valore predefinito è il nome del file della soluzione dell'applicazione.|  
|DisableOutputWindow|dword|Indica se la shell isolata deve considerare la finestra di output come disabilitato.<br /><br /> Se questo valore è impostato su true, Visual Studio non viene visualizzato l'output di gestione di compilazione soluzioni nel **Output** finestra e nasconde il **Mostra finestra di Output a inizio compilazione** casella di controllo di  **Progetti e soluzioni** categoria la **opzioni** nella finestra di dialogo.<br /><br /> Il valore predefinito è false.|  
|HideMiscellaneousFilesByDefault|dword|True per nascondere il **file esterni** per impostazione predefinita nella cartella **Esplora soluzioni**; in caso contrario, false.<br /><br /> Se il **Mostra file esterni in Esplora soluzioni** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. Per altre informazioni, vedere [documenti, ambiente, finestra di dialogo Opzioni](../ide/reference/documents-environment-options-dialog-box.md).<br /><br /> Il valore predefinito è false.|  
|HideSolutionConcept|dword|True per creare progetti di tutti i progetti di esempio autonomi e nascondere la soluzione e i comandi correlati alla soluzione per progetti autonomi per impostazione predefinita. in caso contrario, false.<br /><br /> Se il **Mostra sempre soluzione** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. Per altre informazioni, vedere [NIB: generale, progetti e soluzioni, finestra di dialogo Opzioni](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> Il valore predefinito è false.|  
|NewProjDlgInstalledTemplatesHdr|stringa|Il nome per l'intestazione di modelli di installare Visual Studio nel **modelli** nell'elenco il **nuovo progetto** nella finestra di dialogo. Questa è una stringa o un identificatore di risorsa localizzabile che viene caricato dal pacchetto dell'interfaccia utente dell'applicazione.<br /><br /> Il valore predefinito è "*solutionName* modelli installati", dove *NomeSoluzione* è il nome del file della soluzione dell'applicazione.|  
|NewProjDlgSlnTreeNodeTitle|stringa|Il nome per il **soluzioni di Visual Studio** nodo il **tipi di progetto** ad albero nel **nuovo progetto** nella finestra di dialogo. Questa è una stringa o un identificatore di risorsa localizzabile che viene caricato dal pacchetto dell'interfaccia utente dell'applicazione.<br /><br /> Il valore predefinito è "*solutionName* modelli installati", dove *NomeSoluzione* è il nome del file della soluzione dell'applicazione.|  
|SolutionFileCreatorIdentifier|stringa|L'identificatore dell'applicazione, che viene visualizzato come la seconda riga nei file di soluzione che vengono generati dall'applicazione. Questa riga indica l'applicazione che ha creato il file. Per convenzione, questo valore include sia il nome dell'applicazione e il numero di versione dell'applicazione. Ad esempio,<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> Il programma VSLauncher.exe, ovvero il programma predefinito per l'apertura di un file di soluzione Visual Studio, Usa la seconda riga per determinare la versione di Visual Studio in cui aprire il file della soluzione. L'applicazione richiede la propria utilità di avvio per gestire i file di soluzione associato. L'utilità di avvio è anche possibile usare questa seconda riga nel file di soluzione per determinare in quale versione dell'applicazione per aprire la soluzione.<br /><br /> Nota: Il programma Visual Studio VSLauncher.exe non gestisce i file con estensione sln creati da un'applicazione shell isolata.<br /><br /> Il valore predefinito è "*solutionName* File di soluzione, versione del formato 10,00", dove *NomeSoluzione* è il nome del file della soluzione dell'applicazione.|  
|SolutionFileExt|stringa|L'estensione di nome file di soluzione per l'applicazione. È consigliabile scegliere un'estensione nome file univoco (not.sln).<br /><br /> Il valore predefinito è "*solutionName*_sln", dove *NomeSoluzione* è il nome del file della soluzione dell'applicazione.|  
|SplashScreenBitmap|stringa|Il percorso completo del file bitmap per la schermata iniziale per l'applicazione.<br /><br /> Il valore predefinito è "$RootFolder$\Splash.bmp".|  
|ThisVersionDTECLSID|stringa|L'identificatore di classe (CLSID) dell'oggetto di automazione per l'applicazione.<br /><br /> L'oggetto di automazione dell'applicazione è l'oggetto di primo livello per l'applicazione nel modello di automazione di Visual Studio shell e implementa la <xref:EnvDTE._DTE?displayProperty=fullName> interfaccia.<br /><br /> Se l'oggetto di automazione dell'applicazione è registrato correttamente con la chiave del Registro di sistema HKEY_CLASSES_ROOT\CLSID., quindi è possibile usare la [CComPtrBase:: CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6) funzione per creare direttamente un'istanza dell'applicazione.<br /><br /> La shell di Visual Studio Usa questo CLSID per registrare l'oggetto di automazione dell'applicazione nell'oggetto tabella in esecuzione (ROT) usando il flag ACTIVEOBJECT_WEAK. Consente di utilizzare il [GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)funzione per recuperare un puntatore a un'istanza in esecuzione dell'applicazione. Inoltre, se si definisce un ProgID per l'oggetto di automazione dell'applicazione, quindi la shell di Visual Studio registra anche ogni istanza dell'applicazione nella ROT usando un moniker dell'elemento del form *progID*:*processID* , dove *progID* è il valore ProgID dell'oggetto di automazione dell'applicazione, e *IDprocesso* è l'identificatore di processo per l'istanza dell'applicazione. Ad esempio, se si crea un moniker, come indicato di seguito:<br /><br /> `CreateItemMoniker(L"!",`  *instanceString* `, &instanceMoniker)`<br /><br /> in cui `instanceString` è il *progID*:*IDprocesso* stringa. si potrebbe usare `instanceMoniker` con la funzione GetObject imputrescibili per ottenere l'istanza.<br /><br /> Se l'impostazione ThisVersionDTECLSID viene omesso, quindi l'applicazione non viene esposto tramite il modello COM (Component Object). In questo caso, non è possibile creare un'istanza dell'applicazione chiamando il [CComPtrBase:: CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6) funzionare e non può essere registrato nella tabella ROT.<br /><br /> Ogni versione di un pacchetto VSPackage deve avere un CLSID diversi.<br /><br /> Il valore predefinito è il GUID generato da Visual Studio per l'oggetto di automazione dell'applicazione.|  
|ThisVersionSolutionCLSID|stringa|Il CLSID dell'oggetto soluzione per l'applicazione.<br /><br /> L'oggetto di automazione della soluzione contiene informazioni sulla soluzione aperta in un'istanza dell'applicazione e implementa la <xref:EnvDTE._Solution?displayProperty=fullName> interfaccia.<br /><br /> Se l'oggetto di automazione della soluzione è registrato correttamente con la chiave del Registro di sistema HKEY_CLASSES_ROOT\CLSID., quindi è possibile usare la [CComPtrBase:: CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6) funzione per creare direttamente un oggetto della soluzione per l'applicazione.<br /><br /> La shell di Visual Studio Usa questo CLSID per registrare l'oggetto di automazione della soluzione nella ROT usando il flag ACTIVEOBJECT_WEAK.<br /><br /> Se questa impostazione viene omessa, quindi la classe di soluzione non è registrata con il modello COM (Component Object) e un oggetto della soluzione non è possibile creare chiamando il [CComPtrBase:: CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6) funzionare e non può essere registrato la tabella ROT.<br /><br /> Il valore predefinito è un GUID generato da Visual Studio per l'oggetto della soluzione dell'applicazione.|  
|UserFilesSubFolderName|stringa|Il nome della sottocartella nella cartella documenti dell'utente in cui l'applicazione crea sottocartelle e i file dell'utente.<br /><br /> Il valore predefinito è il nome del file della soluzione dell'applicazione.|  
|UserOptsFileExt|stringa|L'estensione per i file di opzioni utente di soluzione per l'applicazione.<br /><br /> Il valore predefinito è il nome del file della soluzione dell'applicazione.|  
  
## <a name="binding-path-settings"></a>Impostazioni del percorso di associazione  
 Il [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}] chiave contiene l'elenco delle directory in cui la shell verifica per gli assembly. Queste directory vengono aggiunti all'elenco delle directory in cui la shell verifica la presenza di assembly privati per l'applicazione.  
  
 Per impostazione predefinita, nessuna voce di percorso di associazione vengono aggiunti al file pkgdef. Tuttavia, le seguenti sottodirectory della directory di installazione di Visual Studio vengono aggiunti automaticamente all'elenco di percorso di associazione dell'applicazione nel Registro di sistema.  
  
-   Common7\IDE\  
  
-   Common7\IDE\\\PrivateAssemblies  
  
-   Common7\IDE\\\PublicAssemblies  
  
 Per aggiungere una directory nel percorso di associazione, aggiungere una voce nel formato "*nomedirectory*"="", dove *nomedirectory* è un percorso assoluto. Ad esempio,  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>Impostazioni del profilo  
 Nella tabella seguente vengono descritti i valori definiti per ogni pacchetto associato con [$RootKey$ \Profile].  
  
|nome|Tipo|Valore|  
|----------|----------|-----------|  
|AutoSaveFile|stringa|La directory in cui l'applicazione vengono archiviati i file di salvataggio automatico.<br /><br /> Il valore predefinito è "$RootFolder$\Profiles\CurrentSettings.vssettings".|  
  
## <a name="package-satellite-dll-settings"></a>Impostazioni di DLL Satellite del pacchetto  
 Nella tabella seguente vengono descritti i valori definiti in [$RootKey$ \Packages\\{*vsPackageGuid*} \SatelliteDll] per la DLL di ogni pacchetto associato, satellite dove *vsPackageGuid* è il GUID del pacchetto associato.  
  
|nome|Tipo|Valore|  
|----------|----------|-----------|  
|DllName|stringa|Il nome di file della DLL.<br /><br /> Il valore predefinito è "*solutionName*ui.dll", dove *NomeSoluzione* è il nome del file della soluzione dell'applicazione.|  
|Path|stringa|La directory che contiene la DLL satellite.<br /><br /> Il valore predefinito è "$PackageFolder$".|  
  
## <a name="package-menu-item-settings"></a>Impostazioni elemento Menu del pacchetto  
 La chiave del Registro di sistema [$RootKey$ \Menus] definisce i file di risorse dell'interfaccia utente per l'applicazione.  
  
 Valori di voci di menu hanno il formato "{*vsUiPackageGuid*}"=" *resourceId*, *versionNumber*", dove *vsUiPackageGuid* è il GUID del il pacchetto dell'interfaccia utente dell'applicazione, *resourceId* è l'identificatore di risorsa della risorsa CTMENU che contiene gli elementi dell'interfaccia utente, e *versionNumber* è un numero di versione virtuale per il CTMENU risorsa. Per altre informazioni, vedere [Assembly di interoperabilità la registrazione di gestori di comandi](../extensibility/internals/registering-interop-assembly-command-handlers.md).  
  
 Per impostazione predefinita, viene creata una voce di menu nel file con estensione pkgdef per il pacchetto dell'interfaccia utente dell'applicazione.  
  
 Per ogni pacchetto che fornisce le voci di menu e che viene distribuito come parte dell'applicazione, aggiungere una voce di menu per il pacchetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione della Shell isolata](../extensibility/customizing-the-isolated-shell.md)   
 [File con estensione Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)

