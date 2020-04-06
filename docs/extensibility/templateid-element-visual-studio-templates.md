---
title: Elemento TemplateID (modelli di Visual Studio) . Documenti Microsoft
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8eb5abac9c837b3022354d6da743ac8f21d5e41d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699062"
---
# <a name="templateid-element-visual-studio-templates"></a>Elemento TemplateID (modelli di Visual Studio)
Specifica un identificatore per un modello di elemento categorizzato in un gruppo di modelli di elemento in base all'elemento [TemplateGroupID.](../extensibility/templategroupid-element-visual-studio-templates.md)

 \<VSTemplate \<> Template \<>Data>

## <a name="syntax"></a>Sintassi

```
<TemplateID> ... </TemplateID>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 No.

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 Oggetto `string` che rappresenta un identificatore per un modello di elemento `TemplateGroupID` categorizzato in un gruppo di modelli di elemento in base all'elemento.

## <a name="remarks"></a>Osservazioni
 `TemplateID` è un elemento facoltativo.

 Se un file .vstemplate `TemplateID` omette l'elemento, l'elemento [Name](../extensibility/name-element-visual-studio-templates.md) viene utilizzato come identificatore per il modello.

 Il valore `TemplateID` dell'elemento viene utilizzato insieme alla registrazione del sistema del progetto (HKEY_LOCAL_MACHINE\\, SOFTWARE , Microsoft , VisualStudio , 11.0 , Projects ) per filtrare i modelli visualizzati nella finestra di dialogo **Aggiungi nuovo elemento** .

## <a name="see-also"></a>Vedere anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
