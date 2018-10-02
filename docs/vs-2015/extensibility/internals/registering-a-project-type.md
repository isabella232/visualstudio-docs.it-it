---
title: Registrazione di un tipo di progetto | Microsoft Docs
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
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 336658e0a216f7fc24435715bf978ce5badefe5c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532900"
---
# <a name="registering-a-project-type"></a>Registrazione di un tipo di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [registrazione di un tipo di progetto](https://docs.microsoft.com/visualstudio/extensibility/internals/registering-a-project-type).  
  
Quando si crea un nuovo tipo di progetto, è necessario creare voci del Registro di sistema che consentono a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] riconoscere e usare il tipo di progetto. Queste voci del Registro di sistema in genere create usando un file di script (con estensione RGS) del Registro di sistema.  
  
 Nell'esempio seguente, le istruzioni dal Registro di sistema forniscono i percorsi predefiniti e i dati dove applicabile, seguita da una tabella che contiene le voci dello script del Registro di sistema per ogni istruzione. Le tabelle forniscono le voci di script e informazioni aggiuntive sulle istruzioni.  
  
> [!NOTE]
>  Le seguenti informazioni del Registro di sistema deve essere un esempio del tipo e ai fini delle voci negli script del Registro di sistema che si scriverà la registrazione del tipo di progetto. Le voci effettive e sul loro utilizzo può variare in base ai requisiti specifici del tipo di progetto. È consigliabile esaminare gli esempi disponibili per trovarne uno che rispecchia maggiormente il tipo di progetto che si sviluppa ed esaminare lo script del Registro di sistema per tale esempio.  
  
 Negli esempi seguenti sono da HKEY_CLASSES_ROOT.  
  
## <a name="example"></a>Esempio  
  
```  
\.figp  
   @="FigPrjFile"  
   "Content Type"="text/plain"  
\.figp\ShellNew  
   "NullFile"=""  
\FigPrjFile  
   @="Figure Project File"  
\DefaultIcon  
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"  
\shell\open  
   @="&Open in Visual Studio"  
\shell\open\command  
   @="devenv.exe \"%1\""  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|Nome e una descrizione dei file del tipo di progetto con l'estensione .figp.|  
|`Content Type`|REG_SZ|`Text/plain`|Tipo di contenuto per i file di progetto.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Icona predefinita utilizzata per il progetto di questo tipo. L'istruzione % di modulo % viene completata nel Registro di sistema nel percorso predefinito del tipo di progetto DLL.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Applicazione predefinita in cui questo tipo di progetto verrà aperto.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Comando predefinito che verrà eseguita quando viene aperto un progetto di questo tipo.|  
  
 Negli esempi seguenti sono da HKEY_LOCAL_MACHINE e si trovano nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].  
  
## <a name="example"></a>Esempio  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
   "CompanyName"="Microsoft"  
   "ProductName"="Figure Project Sample"  
   "ProductVersion"="9.0"  
   "MinEdition"="professional"  
   "ID"=dword:00000001  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL  
   "DllName"="FigPrjUI.dll"  
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation  
   "FigProjects"=""  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents  
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"  
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@` (Impostazione predefinita)|REG_SZ|`FigPrj Project VSPackage`|Nome localizzabili di questo oggetto registrato VSPackage (tipo di progetto).|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Percorso del tipo di progetto DLL. IDE Carica questa DLL e lo passa CLSID VSPackage `DllGetClassObject` per ottenere <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> per costruire il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> oggetto.|  
|`CompanyName`|REG_SZ|`Microsoft`|Nome della società che ha sviluppato il tipo di progetto.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Nome per il tipo di progetto.|  
|`ProductVersion`|REG_SZ|`9.0`|Numero di versione del tipo di progetto di rilascio.|  
|`MinEdition`|REG_SZ|`professional`|Edizione del pacchetto VSPackage in fase di registrazione.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Chiave per il progetto VSPackage di caricamento del pacchetto. La chiave viene convalidata quando viene caricato un progetto dopo l'avvio dell'ambiente.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nome del file della DLL che contiene risorse localizzate per il tipo di progetto satellite.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Percorso della DLL satellite.|  
|`FigProjectsEvents`|REG_SZ|Vedere l'informativa per valore.|Determina la stringa di testo restituita per questo evento di automazione.|  
|`FigProjectItemsEvents`|REG_SZ|Vedere l'informativa per valore.|Determina la stringa di testo restituita per questo evento di automazione.|  
  
 Tutti gli esempi seguenti si trovano nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Esempio  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
   @="#4"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000000  
   "FindInFilesFilter"=dword:00000000  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2  
      (Folder 2 contains settings for Find in Files filters.)  
   @="#5"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000001  
   "FindInFilesFilter"=dword:00000001  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|Nome predefinito di progetti di questo tipo.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|ID risorsa del nome da recuperare dalla DLL satellite registrato in pacchetti.|  
|`Package`|REG_SZ|`%CLSID_Package%`|ID classe del pacchetto VSPackage è registrato in pacchetti.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Percorso predefinito dei file di modello di progetto. Questi sono i file visualizzati dal modello nuovo progetto.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Percorso predefinito dei file di modello di elemento di progetto. Questi sono i file visualizzati dal modello Aggiungi nuovo elemento.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Abilita l'IDE implementare il **aperto** nella finestra di dialogo.|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|Usato dall'IDE per determinare se il progetto in fase di apertura è gestito da questo tipo di progetto (factory del progetto). Il formato per più di una voce è un elenco delimitato da punto e virgola. Ad esempio "vdproj; vdp".|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|Utilizzare dall'IDE come l'estensione predefinita per l'operazione Salva con nome.|  
|`Filter Settings`|REG_DWORD|Diversi, vedere le istruzioni e i commenti nella tabella seguente.|Queste impostazioni vengono usate per impostare i vari filtri per visualizzare i file nelle finestre di dialogo dell'interfaccia utente.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|ID risorsa per i modelli di elemento aggiunta.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Percorso degli elementi di progetto visualizzato nella finestra di dialogo per la **Aggiungi nuovo elemento** modello.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Determina l'ordine di ordinamento nel nodo della struttura dei file visualizzati nei **Aggiungi nuovo elemento** nella finestra di dialogo.|  
  
 Nella tabella seguente illustra le opzioni di filtri disponibili nel segmento di codice precedente.  
  
|Opzione di filtro|Descrizione|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Indica che il filtro è uno dei filtri comuni nel **Cerca nei file** nella finestra di dialogo. I filtri comuni sono elencati nell'elenco di filtri prima dei filtri non è contrassegnato come comuni.|  
|`CommonOpenFilesFilter`|Indica che il filtro è uno dei filtri comuni nel **Apri File** nella finestra di dialogo. I filtri comuni sono elencati nell'elenco di filtri prima dei filtri non è contrassegnato come comuni.|  
|`FindInFilesFilter`|Indica che il filtro sarà uno dei filtri nel **Cerca nei file** dialogo casella e saranno elencati dopo i filtri comuni.|  
|`NotOpenFileFilter`|Indica che il filtro non verrà essere utilizzato nel **Apri File** nella finestra di dialogo.|  
|`NotAddExistingItemFilter`|Indica che il filtro non verrà essere utilizzato in Aggiungi **elemento esistente** nella finestra di dialogo.|  
  
 Per impostazione predefinita, se un filtro non dispone di uno o più di questi flag impostati, viene utilizzato il filtro nel **Aggiungi elemento esistente** finestra di dialogo e i **Apri File** finestra di dialogo dopo che sono elencati i filtri comuni. Il filtro non viene usato nel **Cerca nei file** nella finestra di dialogo.  
  
 Tutti gli esempi seguenti si trovano nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Esempio  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID risorsa per nuovi modelli di progetto.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Percorso per i progetti del tipo di progetto registrato predefinito.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Set di ordinamento dei progetti viene visualizzato nella finestra di dialogo Creazione guidata nuovi progetti.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica che i progetti di questo tipo vengono visualizzati solo nella finestra di dialogo Nuovo progetto.|  
  
 Tutti gli esempi seguenti si trovano nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Esempio  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|nessuno|Valore predefinito che indica che le voci seguenti sono per le voci di progetti di file esterni.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valore di ID risorsa per i file di modello di aggiungere nuovi elementi.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Percorso predefinito degli elementi che verrà visualizzato nei **Aggiungi nuovo elemento** nella finestra di dialogo.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Stabilisce l'ordinamento per la visualizzazione nel nodo della struttura ad albero di **Aggiungi nuovo elemento** nella finestra di dialogo.|  
  
 Nell'esempio seguente si trova nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].  
  
## <a name="example"></a>Esempio  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 La voce di menu punta l'IDE per la risorsa usata per recuperare le informazioni di menu. Quando questi dati sono stati uniti al database di menu, la stessa chiave verrà aggiunto nella sezione MenusMerged del Registro di sistema. Il pacchetto VSPackage deve modificare qualsiasi elemento nella sezione MenusMerged direttamente. Nel campo dati nella tabella seguente, sono presenti tre virgole-campi delimitati da. Il primo campo definisce un percorso completo di un file di risorse di menu:  
  
-   Se il primo campo è omesso, la risorsa di menu verrà caricata dal identificata dal GUID VSPackage DLL satellite.  
  
 Il secondo campo che identifica un ID di risorsa di menu di scelta del tipo CTMENU:  
  
-   Se viene specificato l'ID di risorsa e il percorso del file viene fornito dal primo parametro, una risorsa di menu verrà caricata dal percorso di file completo.  
  
-   Se è specificato l'ID di risorsa, ma non è il percorso del file, la risorsa di menu verrà caricata della DLL satellite.  
  
-   Se viene fornito il percorso completo e l'ID risorsa omesso, il file da caricare è previsto che un file CTO.  
  
 L'ultimo campo identifica il numero di versione per la risorsa CTMENU. È possibile unire nuovamente il menu modificando il numero di versione.  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|% CLSID_Package %|REG_SZ|`,1000,1`|La risorsa per recuperare le informazioni di menu.|  
  
 Tutti gli esempi seguenti si trovano nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Valore di ID risorsa per i modelli di progetto di nuovo progetto di figure.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Percorso predefinito della directory di nuovi progetti. Gli elementi in questa directory verranno visualizzati nei **Creazione guidata nuovo progetto** nella finestra di dialogo.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Consente di stabilire l'ordine in cui verranno visualizzati nel nodo della struttura dei progetti di **nuovo progetto** nella finestra di dialogo.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica che i progetti di questo tipo vengono visualizzati solo nel **nuovo progetto** nella finestra di dialogo.|  
  
 Nell'esempio seguente si trova nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|ID classe del pacchetto VSPackage registrato.|  
|`UseInterface`|REG_DWORD|`1`|1 indica che l'interfaccia utente verrà utilizzato per interagire con questo progetto. 0 indica che non è disponibile alcuna interfaccia dell'interfaccia utente.|  
  
 File VSZ sono che consentono di controllare nuovi tipi di progetto spesso contengono una voce RELATIVE_PATH. Questo percorso è relativo al percorso specificato nella voce \ProductDir del tipo di progetto nella chiave del programma di installazione seguente:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Ad esempio, i modelli di progetto di Enterprise Framework aggiungono le voci del Registro di sistema seguenti:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 Che significa che se si include un PROJECT_TYPE = movimento di Entity Framework nel file VSZ, trova l'ambiente di vsz i file nella directory ProductDir specificata in precedenza.  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

