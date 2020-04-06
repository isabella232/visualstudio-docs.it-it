---
title: Registrazione dei modelli di progetto e di elemento Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b64504c39b1fc3c4a82530b265cfd0e96832b4f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705818"
---
# <a name="registering-project-and-item-templates"></a>Registrazione di modelli di progetto e di elementi
I tipi di progetto devono registrare le directory in cui si trovano i relativi modelli di progetto e di elemento di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilizza le informazioni di registrazione associate ai tipi di progetto per determinare gli elementi da visualizzare nelle finestre di dialogo **Aggiungi nuovo progetto** e Aggiungi nuovo **elemento.**

 Per ulteriori informazioni sui modelli, vedere Aggiunta di modelli di [progetto e di elemento](../../extensibility/internals/adding-project-and-project-item-templates.md)di progetto .

## <a name="registry-entries-for-projects"></a>Voci del Registro di sistema per i progettiRegistry Entries for Projects
 Negli esempi seguenti vengono illustrate le voci del\\<Registro di sistema *>* HKEY_LOCAL_MACHINE. Le tabelle di accompagnamento spiegano gli elementi utilizzati negli esempi.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Nome|Type|Descrizione|
|----------|----------|-----------------|
|@|REG_SZ|Nome predefinito dei progetti di questo tipo.|
|DisplayName|REG_SZ|ID risorsa del nome da recuperare dalla DLL satellite registrata in Pacchetti.|
|Pacchetto|REG_SZ|ID di classe del pacchetto registrato in Pacchetti.|
|ProjectTemplatesDir|REG_SZ|Percorso predefinito dei file modello di progetto. I file del modello di progetto vengono visualizzati dal modello **Nuovo progetto.**|

### <a name="registering-item-templates"></a>Registrazione di modelli di elemento
 È necessario registrare la directory in cui vengono archiviati i modelli di elemento.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Nome | Type | Descrizione |
|--------------------------|-----------| - |
| @ | REG_SZ | ID risorsa per i modelli Aggiungi elemento. |
| ModelliDir | REG_SZ | Percorso degli elementi di progetto visualizzati nella finestra di dialogo per la procedura guidata **Aggiungi nuovo elemento.** |
| ModelliLocalizedSubDir | REG_SZ | ID risorsa di una stringa che denomina la sottodirectory di TemplatesDir che contiene i modelli localizzati. Poiché [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica la risorsa stringa dalle DLL satellite, se disponibili, ogni DLL satellite può contenere un nome di sottodirectory localizzato diverso. |
| SortPriority (Priorità ordinamento) | REG_DWORD | Impostare SortPriority per controllare l'ordine in cui i modelli vengono visualizzati nella finestra di dialogo **Aggiungi nuovo elemento.** I valori SortPriority più grandi vengono visualizzati in precedenza nell'elenco dei modelli. |

### <a name="registering-file-filters"></a>Registrazione dei filtri di file
 Facoltativamente, è possibile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registrare i filtri che vengono utilizzati quando vengono richiesti i nomi di file. Ad esempio, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] il filtro per la finestra di dialogo **Apri file** è:

 **File di Visual\*C,\*ovvero cs,\*resx,\*\*settings, xsd, wsdl; \*.cs,\*.resx,\*.settings,\*\*.xsd, .wsdl)**

 Per supportare la registrazione di più filtri, ogni filtro viene registrato nella\\<relativa sottochiave in HKEY_LOCAL_MACHINE , Software , Microsoft*VisualStudio Version*> , Projects\\,\<*ProjectGUID*> ,\\<*Filters Subkey*>. Il nome della sottochiave è arbitrario. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignora il nome della sottochiave e ne utilizza solo i valori.

 È possibile controllare i contesti in cui viene utilizzato un filtro impostando i flag, illustrati nella tabella seguente. Se per un filtro non è impostato alcun flag, verrà elencato dopo i filtri comuni nella finestra di dialogo **Aggiungi elemento esistente** e nella finestra di dialogo Apri **file,** ma non verrà utilizzato nella finestra di dialogo **Trova nei file.**

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

|Nome|Type|Descrizione|
|----------|----------|-----------------|
|CommonFindFilesFilter|REG_DWORD|Rende il filtro uno dei filtri comuni nella finestra di dialogo **Trova nei file.** I filtri comuni sono elencati nell'elenco dei filtri prima dei filtri non contrassegnati come comuni.|
|CommonOpenFilesFilter (Filtro CommonOpenFilesFilter)|REG_DWORD|Rende il filtro uno dei filtri comuni nella finestra di dialogo **Apri file.** I filtri comuni sono elencati nell'elenco dei filtri prima dei filtri non contrassegnati come comuni.|
|Filtro FindInFiles|REG_DWORD|Elenca il filtro dopo i filtri comuni nella finestra di dialogo **Trova nei file.**|
|NonOpenFileFilter (Filtro file Non OpenFileFilter)|REG_DWORD|Indica che il filtro non viene utilizzato nella finestra di dialogo **Apri file.**|
|NotAddExistingItemFilter (Filtro per elemento non AddExistingItemFilter)|REG_DWORD|Indica che il filtro non viene utilizzato nella finestra di dialogo **Aggiungi elemento esistente.**|
|SortPriority (Priorità ordinamento)|REG_DWORD|Impostare SortPriority per controllare l'ordine di visualizzazione dei filtri. I valori SortPriority più grandi vengono visualizzati in precedenza nell'elenco dei filtri.|

## <a name="directory-structure"></a>Struttura di directory
 VSPackage possono inserire file di modello e cartelle in qualsiasi punto su un disco locale o remoto, purché il percorso viene registrato tramite l'ambiente di sviluppo integrato (IDE). Tuttavia, per semplificare l'organizzazione, si consiglia la seguente struttura di directory nel percorso di installazione del prodotto.

 -Modelli

 -Progetti (contiene i modelli di progetto)

 - Applicazioni

 - Componenti

 \ ...

 ProjectItems (contiene gli elementi del progetto)

 Classe Classe

 - Modulo

 Pagina Web

 (contiene i file utilizzati negli elementi di progetto su più file)

 File Wizard

## <a name="see-also"></a>Vedere anche

- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [Applicazioni localizzate](../../ide/globalizing-and-localizing-applications.md)
- [CATID per gli oggetti che vengono in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
