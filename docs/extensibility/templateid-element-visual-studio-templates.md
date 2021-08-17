---
title: Elemento TemplateID (modelli Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento TemplateID e su come specifica un identificatore per un modello di elemento categorizzato in un gruppo di modelli di elemento in base all'elemento TemplateGroupID.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aa94da28cf02916b0961da722785c4f51d14d171ca61b69630f1a6c027491468
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388175"
---
# <a name="templateid-element-visual-studio-templates"></a>Elemento TemplateID (modelli di Visual Studio)
Specifica un identificatore per un modello di elemento categorizzato in un gruppo di modelli di elemento [dall'elemento TemplateGroupID.](../extensibility/templategroupid-element-visual-studio-templates.md)

 \<VSTemplate> \<TemplateData>
 \<TemplateID>

## <a name="syntax"></a>Sintassi

```
<TemplateID> ... </TemplateID>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 Oggetto `string` che rappresenta un identificatore per un modello di elemento categorizzato in un gruppo di modelli di elemento in base all'elemento. `TemplateGroupID`

## <a name="remarks"></a>Commenti
 `TemplateID` è un elemento facoltativo.

 Se un file con estensione vstemplate omette `TemplateID` l'elemento , [l'elemento Name](../extensibility/name-element-visual-studio-templates.md) viene usato come identificatore per il modello.

 Il valore dell'elemento viene usato insieme alla registrazione del sistema del progetto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects) per filtrare i modelli visualizzati nella finestra di dialogo `TemplateID` \\ Aggiungi nuovo elemento. 

## <a name="see-also"></a>Vedi anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
