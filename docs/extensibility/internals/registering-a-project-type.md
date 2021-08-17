---
title: Registrazione di un Project di | Microsoft Docs
description: Informazioni sulla creazione di voci del Registro di sistema che Visual Studio riconoscere e usare il nuovo tipo di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8b3966b807f87fd6767727e66b6f5b035cfc1510
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042166"
---
# <a name="registering-a-project-type"></a>Registrazione di un tipo di progetto
Quando si crea un nuovo tipo di progetto, è necessario creare voci del Registro di sistema che consentono di riconoscere e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usare il tipo di progetto. Queste voci del Registro di sistema vengono in genere create usando un file di script del Registro di sistema (con estensione rgs).

 Nell'esempio seguente le istruzioni del Registro di sistema forniscono percorsi e dati predefiniti, se applicabile, seguiti da una tabella contenente voci dello script del Registro di sistema per ogni istruzione. Le tabelle forniscono le voci di script e informazioni aggiuntive sulle istruzioni .

> [!NOTE]
> Le informazioni del Registro di sistema seguenti sono destinate a essere un esempio del tipo e degli scopi delle voci negli script del Registro di sistema che verranno scritti per registrare il tipo di progetto. Le voci effettive e il relativo utilizzo possono variare in base ai requisiti specifici del tipo di progetto. Esaminare gli esempi disponibili per trovarne uno simile al tipo di progetto che si sta sviluppando e quindi esaminare lo script del Registro di sistema per tale esempio.

 Gli esempi seguenti sono di HKEY_CLASSES_ROOT.

## <a name="example-1"></a>Esempio 1

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

|Nome|Tipo|Dati|Descrizione|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|Nome e descrizione dei file del tipo di progetto con estensione figp.|
|`Content Type`|REG_SZ|`Text/plain`|Tipo di contenuto per i file di progetto.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Icona predefinita usata per il progetto di questo tipo. L'istruzione %MODULE% viene completata nel Registro di sistema nel percorso predefinito della DLL del tipo di progetto.|
|`@`|REG_SZ|`&Open in Visual Studio`|Applicazione predefinita in cui verrà aperto questo tipo di progetto.|
|`@`|REG_SZ|`devenv.exe "%1"`|Comando predefinito che verrà eseguito quando viene aperto un progetto di questo tipo.|

 Gli esempi seguenti sono HKEY_LOCAL_MACHINE e si trovano nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].

## <a name="example-2"></a>Esempio 2

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

|Nome|Tipo|Dati|Descrizione|
|----------|----------|----------|-----------------|
|`@` (impostazione predefinita)|REG_SZ|`FigPrj Project VSPackage`|Nome localizzabile di questo VSPackage registrato (tipo di progetto).|
|`InprocServer32`|REG_SZ|`%MODULE%`|Percorso della DLL del tipo di progetto. L'IDE carica questa DLL e passa il CLSID VSPackage a `DllGetClassObject` per ottenere per costruire <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> l'oggetto.|
|`CompanyName`|REG_SZ|`Microsoft`|Nome della società che ha sviluppato il tipo di progetto.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Nome per il tipo di progetto.|
|`ProductVersion`|REG_SZ|`9.0`|Numero di versione della versione del tipo di progetto.|
|`MinEdition`|REG_SZ|`professional`|Edizione del pacchetto VSPackage da registrare.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Chiave di caricamento del pacchetto per il progetto VSPackage. La chiave viene convalidata quando un progetto viene caricato dopo l'avvio dell'ambiente.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nome file della DLL satellite che contiene le risorse localizzate per il tipo di progetto.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Percorso della DLL satellite.|
|`FigProjectsEvents`|REG_SZ|Vedere l'istruzione per value.|Determina la stringa di testo restituita per questo evento di automazione.|
|`FigProjectItemsEvents`|REG_SZ|Vedere l'istruzione per value.|Determina la stringa di testo restituita per questo evento di automazione.|

 Tutti gli esempi seguenti si trovano nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-3"></a>Esempio 3

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

|Nome|Tipo|Dati|Descrizione|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|Nome predefinito dei progetti di questo tipo.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|ID risorsa del nome da recuperare dalla DLL satellite registrata in Pacchetti.|
|`Package`|REG_SZ|`%CLSID_Package%`|ID di classe del pacchetto VSPackage registrato in Pacchetti.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Percorso predefinito dei Project modello. Si tratta dei file visualizzati dal modello New Project.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Percorso predefinito dei file Project modello di elemento. Questi sono i file visualizzati dal modello Aggiungi nuovo elemento.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Consente all'IDE di implementare la **finestra di** dialogo Apri.|
|`PossibleProjectExtensions`|REG_SZ|`figp`|Usato dall'IDE per determinare se il progetto aperto viene gestito da questo tipo di progetto (factory del progetto). Il formato per più voci è un elenco delimitato da punti e virgola. Ad esempio, "vdproj;vdp".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|Usato dall'IDE come estensione di file predefinita per l'operazione Salva con nome.|
|`Filter Settings`|REG_DWORD|Nella tabella seguente sono riportate diverse istruzioni e commenti.|Queste impostazioni vengono usate per impostare i vari filtri per la visualizzazione dei file nelle finestre di dialogo dell'interfaccia utente.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|ID risorsa per i modelli Aggiungi elemento.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Percorso degli elementi di progetto visualizzati nella finestra di dialogo per il **modello Aggiungi nuovo** elemento.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Determina l'ordinamento nel nodo della struttura ad albero dei file visualizzati nella finestra **di** dialogo Aggiungi nuovo elemento .|

 La tabella seguente illustra le opzioni filtri disponibili nel segmento di codice precedente.

|Opzione di filtro|Descrizione|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Indica che il filtro è uno dei filtri comuni nella finestra **di** dialogo Trova nei file . I filtri comuni sono elencati nell'elenco dei filtri prima dei filtri non contrassegnati come comuni.|
|`CommonOpenFilesFilter`|Indica che il filtro è uno dei filtri comuni nella finestra **di dialogo Apri** file. I filtri comuni sono elencati nell'elenco dei filtri prima dei filtri non contrassegnati come comuni.|
|`FindInFilesFilter`|Indica che il filtro sarà uno dei  filtri nella finestra di dialogo Cerca nei file e verrà elencato dopo i filtri comuni.|
|`NotOpenFileFilter`|Indica che il filtro non verrà utilizzato nella finestra **di dialogo Apri** file.|
|`NotAddExistingItemFilter`|Indica che il filtro non verrà utilizzato nella finestra di dialogo **Aggiungi elemento** esistente .|

 Per impostazione predefinita, se per un filtro non è impostato uno  o più di questi flag, il filtro viene utilizzato nella finestra di dialogo Aggiungi elemento esistente e nella finestra di dialogo Apri **file** dopo l'elenco dei filtri comuni. Il filtro non viene utilizzato nella **finestra di dialogo Trova** nei file .

 Tutti gli esempi seguenti si trovano nel Registro di sistema sotto la chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-4"></a>Esempio 4

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Nome|Tipo|Dati|Descrizione|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID risorsa per i nuovi Project personalizzati.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Percorso predefinito per i progetti del tipo di progetto registrato.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Imposta l'ordinamento dei progetti visualizzati nella finestra di dialogo Creazione guidata nuovi progetti.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica che i progetti di questo tipo vengono visualizzati solo nella finestra di dialogo Project nuovo progetto.|

 Tutti gli esempi seguenti si trovano nel Registro di sistema sotto la chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-5"></a>Esempio 5

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Nome|Tipo|Dati|Descrizione|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|Nessuno|Valore predefinito che indica che le voci seguenti sono relative alle voci di progetto File esterni.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valore dell'ID risorsa per i file modello aggiungi nuovi elementi.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Percorso predefinito degli elementi che verranno visualizzati nella finestra **di dialogo** Aggiungi nuovo elemento .|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Stabilisce l'ordinamento per la visualizzazione nel nodo della struttura ad albero della **finestra di dialogo** Aggiungi nuovo elemento .|

 L'esempio seguente si trova nel Registro di sistema sotto la chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].

## <a name="example-6"></a>Esempio 6

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 La voce di menu punta l'IDE alla risorsa usata per recuperare le informazioni di menu. Dopo che questi dati sono stati uniti nel database dei menu, la stessa chiave verrà aggiunta nella sezione MenusMerged del Registro di sistema. Il pacchetto VSPackage non deve modificare nulla direttamente nella sezione MenusMerged. Nel campo Dati della tabella seguente sono presenti tre campi delimitati da virgole. Il primo campo identifica un percorso completo di un file di risorse di menu:

- Se il primo campo viene omesso, la risorsa di menu viene caricata dalla DLL satellite identificata dal GUID del pacchetto VSPackage.

  Il secondo campo identifica un ID risorsa di menu di tipo CTMENU:

- Se viene specificato l'ID risorsa e il percorso del file viene fornito dal primo parametro, viene caricata una risorsa di menu dal percorso completo del file.

- Se viene specificato l'ID risorsa, ma il percorso del file non lo è, la risorsa di menu viene caricata dalla DLL satellite.

- Se viene specificato il percorso completo del file e l'ID risorsa viene omesso, si prevede che il file da caricare sia un file CTO.

  L'ultimo campo identifica il numero di versione per la risorsa CTMENU. È possibile unire nuovamente il menu modificando il numero di versione.

|Nome|Tipo|Dati|Descrizione|
|----------|----------|----------|-----------------|
|%CLSID_Package%|REG_SZ|`,1000,1`|Risorsa per recuperare le informazioni di menu.|

 Tutti gli esempi seguenti si trovano nel Registro di sistema sotto la chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Nome|Tipo|Dati|Descrizione|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Valore dell'ID risorsa per i Project nuovi Project figure.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Percorso predefinito della directory Nuovi progetti. Gli elementi in questa directory verranno visualizzati nella finestra **di dialogo Project procedura** guidata.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Stabilisce l'ordine in cui i progetti verranno visualizzati nel nodo della struttura ad albero della finestra **di dialogo Project** nuova finestra di dialogo.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica che i progetti di questo tipo vengono visualizzati solo nella finestra **di dialogo Project** nuova versione.|

 L'esempio seguente si trova nel Registro di sistema sotto la chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Nome|Tipo|Dati|Descrizione|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|ID di classe del pacchetto VSPackage registrato.|
|`UseInterface`|REG_DWORD|`1`|1 indica che l'interfaccia utente verrà usata per interagire con questo progetto. 0 indica che non è presente alcuna interfaccia utente.|

 I file con estensione vsz che controllano i nuovi tipi di progetto contengono spesso una RELATIVE_PATH voce. Questo percorso è relativo al percorso specificato nella voce \ProductDir del tipo di progetto nella chiave di installazione seguente:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup

 Ad esempio, i modelli Enterprise Frameworks aggiungono le voci del Registro di sistema seguenti:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Programmi\Microsoft Visual Studio\EnterpriseFrameworks\

 Ciò significa che se si include una voce PROJECT_TYPE=EF nel file con estensione vsz, l'ambiente trova i file con estensione vsz nella directory ProductDir specificata in precedenza.

## <a name="see-also"></a>Vedi anche
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)
- [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
