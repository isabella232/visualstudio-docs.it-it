---
title: Registrazione di modelli di progetti e di elementi | Microsoft Docs
description: Scopri in che modo Visual Studio usa le informazioni di registrazione per i tipi di progetto per determinare gli elementi da visualizzare nelle finestre di dialogo Aggiungi nuovo progetto e Aggiungi nuovo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: d6f4abe3a8632f4fe9208922aee1ccd92da3dab5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062694"
---
# <a name="registering-project-and-item-templates"></a>Registrazione di modelli di progetto e di elementi
I tipi di progetto devono registrare le directory in cui si trovano i modelli di progetto e di elemento di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Usa le informazioni di registrazione associate ai tipi di progetto per determinare gli elementi da visualizzare nelle finestre di dialogo **Aggiungi nuovo progetto** e **Aggiungi nuovo elemento** .

 Per ulteriori informazioni sui modelli, vedere [aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Voci del registro di sistema per i progetti
 Negli esempi seguenti vengono illustrate le voci del registro di sistema in HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ < *versione*>. Le tabelle associate spiegano gli elementi utilizzati negli esempi.

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
|DisplayName|REG_SZ|ID risorsa del nome da recuperare dalla DLL satellite registrata nei pacchetti.|
|Pacchetto|REG_SZ|ID classe del pacchetto registrato in pacchetti.|
|ProjectTemplatesDir|REG_SZ|Percorso predefinito dei file del modello di progetto. I file del modello di progetto vengono visualizzati dal nuovo modello di **progetto** .|

### <a name="registering-item-templates"></a>Registrazione di modelli di elemento
 È necessario registrare la directory in cui vengono archiviati i modelli di elemento.

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
| TemplatesDir | REG_SZ | Percorso degli elementi del progetto visualizzati nella finestra di dialogo per la procedura guidata **Aggiungi nuovo elemento** . |
| TemplatesLocalizedSubDir | REG_SZ | ID risorsa di una stringa che denomina la sottodirectory di TemplatesDir che include i modelli localizzati. Poiché [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica la risorsa di stringa da dll satellite, se sono presenti, ogni DLL satellite può contenere un nome di sottodirectory localizzato diverso. |
| SortPriority | REG_DWORD | Impostare SortPriority per regolare l'ordine di visualizzazione dei modelli nella finestra di dialogo **Aggiungi nuovo elemento** . I valori SortPriority più grandi vengono visualizzati in precedenza nell'elenco dei modelli. |

### <a name="registering-file-filters"></a>Registrazione dei filtri di file
 Facoltativamente, è possibile registrare i filtri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzati da quando viene richiesto di specificare i nomi dei file. Ad esempio, il [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtro per la finestra di dialogo **Apri file** è:

 **File di Visual C# ( \* . cs, \* . resx, \* . Settings, \* . xsd, \* . WSDL); \* . CS, \* . resx, \* . Settings, \* . xsd, \* . WSDL)**

 Per supportare la registrazione di più filtri, ogni filtro viene registrato nella relativa sottochiave in HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ < *versione*> \\ \<*ProjectGUID*> sottochiave \Filters \projects {} \\ < >. Il nome della sottochiave è arbitrario; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ignora il nome della sottochiave e usa solo i relativi valori.

 È possibile controllare i contesti in cui viene utilizzato un filtro impostando i flag, illustrati nella tabella seguente. Se per un filtro non è impostato alcun flag, questo verrà elencato dopo i filtri comuni nella finestra di dialogo **Aggiungi elemento esistente** e nella finestra di dialogo **Apri file** , ma non verrà utilizzato nella finestra di dialogo **Cerca nei file** .

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
|CommonFindFilesFilter|REG_DWORD|Consente di filtrare uno dei filtri comuni nella finestra di dialogo **Cerca nei file** . I filtri comuni sono elencati nell'elenco di filtri prima che i filtri non siano contrassegnati come comuni.|
|CommonOpenFilesFilter|REG_DWORD|Consente di filtrare uno dei filtri comuni nella finestra di dialogo **Apri file** . I filtri comuni sono elencati nell'elenco di filtri prima che i filtri non siano contrassegnati come comuni.|
|FindInFilesFilter|REG_DWORD|Elenca il filtro dopo i filtri comuni nella finestra di dialogo **Cerca nei file** .|
|NotOpenFileFilter|REG_DWORD|Indica che il filtro non viene utilizzato nella finestra di dialogo **Apri file** .|
|NotAddExistingItemFilter|REG_DWORD|Indica che il filtro non viene utilizzato nella finestra di dialogo **Aggiungi elemento esistente** .|
|SortPriority|REG_DWORD|Impostare SortPriority per regolare l'ordine di visualizzazione dei filtri. I valori SortPriority più grandi vengono visualizzati in precedenza nell'elenco dei filtri.|

## <a name="directory-structure"></a>Struttura di directory
 I pacchetti VSPackage possono inserire i file di modello e le cartelle ovunque in un disco locale o remoto, purché il percorso venga registrato tramite il Integrated Development Environment (IDE). Tuttavia, per semplificare l'organizzazione, è consigliabile usare la seguente struttura di directory nel percorso di installazione del prodotto.

 \Modelli

 \Projects (contiene i modelli di progetto)

 \Registri applicazioni

 \Components

 \ ...

 \ProjectItems (contiene gli elementi del progetto)

 \Class

 \Form

 Pagina \Web

 \HelperFiles (contiene i file usati negli elementi del progetto con più file)

 \WizardFiles

## <a name="see-also"></a>Vedi anche

- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [Applicazioni localizzate](../../ide/globalizing-and-localizing-applications.md)
- [CATID per gli oggetti che vengono in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
