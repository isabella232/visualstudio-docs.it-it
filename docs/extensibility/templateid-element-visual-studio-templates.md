---
title: Elemento TemplateID (modelli di Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento TemplateID e su come specifica un identificatore per un modello di elemento categorizzato in un gruppo di modelli di elemento tramite l'elemento TemplateGroupID.
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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 26a0b3ef90eab7cef51e5ca65032f2f4f68acd42
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895323"
---
# <a name="templateid-element-visual-studio-templates"></a>Elemento TemplateID (modelli di Visual Studio)
Specifica un identificatore per un modello di elemento categorizzato in un gruppo di modelli di elemento dall'elemento [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) .

 \<VSTemplate> \<TemplateData>
 \<TemplateID>

## <a name="syntax"></a>Sintassi

```
<TemplateID> ... </TemplateID>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuna.

### <a name="child-elements"></a>Elementi figlio
 Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 Oggetto `string` che rappresenta un identificatore per un modello di elemento categorizzato in un gruppo di modelli di elemento dall' `TemplateGroupID` elemento.

## <a name="remarks"></a>Commenti
 `TemplateID` è un elemento facoltativo.

 Se un file con estensione vstemplate omette l' `TemplateID` elemento, l'elemento [Name](../extensibility/name-element-visual-studio-templates.md) viene utilizzato come identificatore per il modello.

 Il valore dell' `TemplateID` elemento viene utilizzato insieme alla registrazione del sistema del progetto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\ ) per filtrare i modelli visualizzati nella finestra di dialogo **Aggiungi nuovo elemento** .

## <a name="see-also"></a>Vedi anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
