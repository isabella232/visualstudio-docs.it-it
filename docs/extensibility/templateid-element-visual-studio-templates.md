---
title: Elemento TemplateID (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0e404921d1ed74db2a1f23117242f49a07206c2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718731"
---
# <a name="templateid-element-visual-studio-templates"></a>Elemento TemplateID (modelli di Visual Studio)
Specifica un identificatore per un modello di elemento categorizzato in un gruppo di modelli di elemento dall'elemento [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) .

 \<VSTemplate > \<TemplateData > \<TemplateID >

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
 @No__t_0 che rappresenta un identificatore per un modello di elemento categorizzato in un gruppo di modelli di elemento dall'elemento `TemplateGroupID`.

## <a name="remarks"></a>Note
 `TemplateID` è un elemento facoltativo.

 Se un file con estensione vstemplate omette l'elemento `TemplateID`, l'elemento [Name](../extensibility/name-element-visual-studio-templates.md) viene usato come identificatore per il modello.

 Il valore dell'elemento `TemplateID` viene utilizzato insieme alla registrazione del sistema di progetto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects \\) per filtrare i modelli visualizzati nella finestra di dialogo **Aggiungi nuovo elemento** .

## <a name="see-also"></a>Vedere anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)