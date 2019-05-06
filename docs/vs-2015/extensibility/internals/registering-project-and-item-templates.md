---
title: La registrazione di Project and Item Templates | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a06e7a292d960e675ad4b0de97499557542fef1c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965565"
---
# <a name="registering-project-and-item-templates"></a>Registrazione di modelli di progetto e di elementi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tipi di progetto devono registrare le directory in cui si trovano i relativi modelli di progetto ed elemento di progetto. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Usa le informazioni di registrazione associate ai tipi di progetto per determinare gli elementi da visualizzare nel **Aggiungi nuovo progetto** e **Aggiungi nuovo elemento** finestre di dialogo.  
  
 Per altre informazioni sui modelli, vedere [aggiunta di progetto e modelli di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="registry-entries-for-projects"></a>Voci del Registro di sistema per i progetti  
 Gli esempi seguenti illustrano le voci del Registro di sistema nella HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*versione*>. Le tabelle di accompagnamento illustrano gli elementi utilizzati negli esempi.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Nome|Tipo|Descrizione|  
|----------|----------|-----------------|  
|@|REG_SZ|Nome predefinito di progetti di questo tipo.|  
|DisplayName|REG_SZ|ID risorsa del nome da recuperare dalla DLL satellite registrato in pacchetti.|  
|Pacchetto|REG_SZ|ID classe del pacchetto di registrazione in pacchetti.|  
|ProjectTemplatesDir|REG_SZ|Percorso predefinito dei file di modello di progetto. I file di modello di progetto vengono visualizzati per il **nuovo progetto** modello.|  
  
### <a name="registering-item-templates"></a>La registrazione di modelli di elemento  
 È necessario registrare la directory in cui vengono archiviati i modelli di elemento.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|Nome|Tipo|Descrizione|  
|----------|----------|-----------------|  
|@|REG_SZ|ID risorsa per i modelli di elemento aggiunta.|  
|TemplatesDir|REG_SZ|Percorso degli elementi di progetto visualizzato nella finestra di dialogo per la **Aggiungi nuovo elemento** procedura guidata.|  
|TemplatesLocalizedSubDir|REG_SZ|ID risorsa della stringa che denomina la sottodirectory della TemplatesDir che contiene i modelli localizzati. Poiché [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] carica la risorsa stringa dalla DLL satellite nelle varie se disponibili, ogni DLL satellite può contenere un nome di sottodirectory localizzate diverse.|  
|SortPriority|REG_DWORD|Impostare SortPriority per regolare l'ordine in cui i modelli vengono visualizzati nei **Aggiungi nuovo elemento** nella finestra di dialogo. I valori maggiori SortPriority vengono visualizzati in precedenza nell'elenco dei modelli.|  
  
### <a name="registering-file-filters"></a>La registrazione di filtri file  
 Facoltativamente, è possibile registrare i filtri che [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utilizza quando richiesto, specificare i nomi file. Ad esempio, il [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Filtra per il **Apri File** è la finestra di dialogo:  
  
 **File Visual C# (\*cs,\*resx,\*Settings,\*XSD,\*WSDL);\*. cs,\*, RESX\*Settings,\*XSD,\*. WSDL)**  
  
 Per supportare la registrazione di più filtri, ogni filtro è registrato nella propria sottochiave in HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*versione*> \Projects\\{ \< *ProjectGUID*>} \Filters\\<*sottochiave*>. Il nome della sottochiave è arbitrario. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ignora il nome della sottochiave e utilizza solo i relativi valori.  
  
 È possibile controllare i contesti in cui viene utilizzato un filtro impostando flag, illustrato nella tabella seguente. Se un filtro non ha nessun flag impostato, verrà elencata dopo i filtri nelle attività comuni la **Aggiungi elemento esistente** finestra di dialogo e il **Apri File** la finestra di dialogo, ma non verrà utilizzato nel **Cerca nei file**  nella finestra di dialogo.  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|Nome|Tipo|Descrizione|  
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|Rende il filtro per uno dei filtri comuni nella **Cerca nei file** nella finestra di dialogo. Filtri comuni sono elencati nell'elenco di filtri prima i filtri non è contrassegnato come comuni.|  
|CommonOpenFilesFilter|REG_DWORD|Rende il filtro per uno dei filtri comuni nella **Apri File** nella finestra di dialogo. Filtri comuni sono elencati nell'elenco di filtri prima i filtri non è contrassegnato come comuni.|  
|FindInFilesFilter|REG_DWORD|Elenca il filtro dopo i filtri nelle attività comuni di **Cerca nei file** nella finestra di dialogo.|  
|NotOpenFileFilter|REG_DWORD|Indica che il filtro non viene utilizzato nel **Apri File** nella finestra di dialogo.|  
|NotAddExistingItemFilter|REG_DWORD|Indica che il filtro non viene utilizzato nel **Aggiungi elemento esistente** nella finestra di dialogo.|  
|SortPriority|REG_DWORD|Impostare SortPriority per regolare l'ordine in cui vengono visualizzati i filtri. I valori maggiori SortPriority vengono visualizzati in precedenza nell'elenco di filtri.|  
  
## <a name="directory-structure"></a>Struttura di directory  
 Pacchetti VSPackage possono inserire le cartelle e file di modello in qualsiasi punto su un disco locale o remoto, purché la posizione è registrata tramite l'ambiente di sviluppo integrato (IDE). Tuttavia, per facilitare l'organizzazione, è consigliabile la seguente struttura di directory nel percorso di installazione del prodotto.  
  
 \Templates  
  
 \Projects (contiene i modelli di progetto)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (contiene gli elementi del progetto)  
  
 \CLASSE  
  
 \Form  
  
 \Web pagina  
  
 \HelperFiles (contiene i file usati negli elementi di progetto a più file)  
  
 \WizardFiles  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di progetto e modelli di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [Applicazioni localizzate](../../ide/localizing-applications.md)   
 [CATID per gli oggetti che vengono in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
