---
title: Registrazione dei modelli di progetto e di elemento | Microsoft Docs
description: Informazioni su Visual Studio informazioni di registrazione per i tipi di progetto per determinare cosa visualizzare nelle finestre di dialogo Aggiungi nuovo progetto e Aggiungi nuovo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b60022c6adf65d0b0d60d32b4ad7ae72067726d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905631"
---
# <a name="registering-project-and-item-templates"></a>Registrazione di modelli di progetto e di elementi
I tipi di progetto devono registrare le directory in cui si trovano i modelli di progetto e di elemento di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]usa le informazioni di registrazione associate ai tipi  di progetto per determinare cosa visualizzare nelle finestre di dialogo Aggiungi nuovo progetto **e** Aggiungi nuovo elemento.

 Per altre informazioni sui modelli, vedere [Aggiunta di modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Voci del Registro di sistema per i progetti
 Gli esempi seguenti illustrano le voci del Registro di sistema HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ < *versione>.* Le tabelle che accompagnano illustrano gli elementi usati negli esempi.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Nome|Tipo|Descrizione|
|----------|----------|-----------------|
|@|REG_SZ|Nome predefinito dei progetti di questo tipo.|
|DisplayName|REG_SZ|ID risorsa del nome da recuperare dalla DLL satellite registrata in Pacchetti.|
|Pacchetto|REG_SZ|ID di classe del pacchetto registrato in Pacchetti.|
|ProjectTemplatesDir|REG_SZ|Percorso predefinito dei file del modello di progetto. I file del modello di progetto vengono visualizzati dal **modello Nuovo** progetto.|

### <a name="registering-item-templates"></a>Registrazione di modelli di elemento
 È necessario registrare la directory in cui archiviare i modelli di elemento.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Nome | Tipo | Descrizione |
|--------------------------|-----------| - |
| @ | REG_SZ | ID risorsa per i modelli Aggiungi elemento. |
| TemplatesDir | REG_SZ | Percorso degli elementi di progetto visualizzati nella finestra di dialogo per la **procedura guidata Aggiungi nuovo** elemento. |
| TemplatesLocalizedSubDir | REG_SZ | ID risorsa di una stringa che indica la sottodirectory di TemplatesDir che contiene modelli localizzati. Poiché carica la risorsa stringa dalle DLL satellite, se presenti, ogni DLL satellite può contenere un nome di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sottodirectory localizzato diverso. |
| SortPriority | REG_DWORD | Impostare SortPriority per determinare l'ordine di visualizzazione dei modelli nella **finestra di** dialogo Aggiungi nuovo elemento . I valori SortPriority più grandi vengono visualizzati in precedenza nell'elenco dei modelli. |

### <a name="registering-file-filters"></a>Registrazione dei filtri di file
 Facoltativamente, è possibile registrare i filtri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che vengono utilizzati quando viene richiesto di specificare i nomi di file. Ad esempio, il [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtro per la finestra di dialogo Apri **file** è:

 **File di Visual C# \* (con estensione cs, \* resx, \* settings, \* xsd, \* wsdl); \* . cs, \* resx, \* settings, \* xsd, \* wsdl)**

 Per supportare la registrazione di più filtri, ogni filtro viene registrato nella propria sottochiave in HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ < *Version*>\Projects \\ { \<*ProjectGUID*> }\Filters \\ < *Subkey*>. Il nome della sottochiave è arbitrario. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignora il nome della sottochiave e usa solo i relativi valori.

 È possibile controllare i contesti in cui viene usato un filtro impostando i flag, illustrati nella tabella seguente. Se per un filtro non è impostato alcun flag, verrà  elencato dopo i filtri comuni nella finestra di dialogo  Aggiungi elemento esistente e nella finestra di dialogo Apri **file** , ma non verrà usato nella finestra di dialogo Trova nei file .

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
|CommonFindFilesFilter|REG_DWORD|Rende il filtro uno dei filtri comuni nella finestra **di dialogo** Trova nei file . I filtri comuni sono elencati nell'elenco dei filtri prima dei filtri non contrassegnati come comuni.|
|CommonOpenFilesFilter|REG_DWORD|Rende il filtro uno dei filtri comuni nella finestra **di dialogo Apri** file . I filtri comuni sono elencati nell'elenco dei filtri prima dei filtri non contrassegnati come comuni.|
|FindInFilesFilter|REG_DWORD|Elenca il filtro dopo i filtri comuni nella **finestra di dialogo** Trova nei file .|
|NotOpenFileFilter|REG_DWORD|Indica che il filtro non viene usato nella finestra **di dialogo Apri** file.|
|NotAddExistingItemFilter|REG_DWORD|Indica che il filtro non viene usato nella finestra **di dialogo Aggiungi elemento** esistente.|
|SortPriority|REG_DWORD|Impostare SortPriority per determinare l'ordine di visualizzazione dei filtri. I valori SortPriority più grandi vengono visualizzati in precedenza nell'elenco dei filtri.|

## <a name="directory-structure"></a>Struttura di directory
 I pacchetti VSPackage possono inserire file modello e cartelle in qualsiasi posizione su un disco locale o remoto, purché il percorso sia registrato tramite l'ambiente di sviluppo integrato (IDE). Tuttavia, per semplificare l'organizzazione, è consigliabile usare la struttura di directory seguente nel percorso di installazione del prodotto.

 \Templates

 \Projects (contiene i modelli di progetto)

 \Applicazioni

 \Components

 \ ...

 \ProjectItems (contiene gli elementi di progetto)

 \Class

 \Form

 \Pagina Web

 \HelperFiles (contiene i file usati negli elementi di progetto a più file)

 \WizardFiles

## <a name="see-also"></a>Vedere anche

- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [Applicazioni localizzate](../../ide/globalizing-and-localizing-applications.md)
- [CATID per gli oggetti che vengono in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
