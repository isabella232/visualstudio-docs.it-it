---
title: Elemento CustomDataSignature (modelli di Visual Studio) Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec8bae34da0f007bac65f26c4e442c1d03e56d08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739438"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>Elemento CustomDataSignature (modelli di Visual Studio)
Specifica la firma di testo per individuare i dati personalizzati.

 \<VSTemplate \<> TemplateData> \<> CustomDataSignature

## <a name="syntax"></a>Sintassi

```
<CustomDataSignature>"string"</CustomDataSignature>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Categorizza il modello e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o Aggiungi **nuovo elemento.**|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo è una stringa con la firma di testo necessaria per individuare i dati personalizzati.

## <a name="remarks"></a>Osservazioni
 `CustomDataSignature` è un elemento facoltativo.

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento sullo schema dei modelli di Visual StudioVisual Studio Template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
