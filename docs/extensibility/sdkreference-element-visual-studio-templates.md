---
title: Elemento SDKReference (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cf1b3bed942894e20132ecd7b06c1884caa9a93
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720083"
---
# <a name="sdkreference-element-visual-studio-templates"></a>Elemento SDKReference (modelli di Visual Studio)
Specifica che il modello di elemento usa un riferimento all'SDK.

## <a name="syntax"></a>Sintassi

```xml
<VSTemplate>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>SDKname</SDKReference>
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
|[Reference](../extensibility/reference-element-visual-studio-templates.md)|Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

## <a name="remarks"></a>Note
 Questo testo indica il riferimento all'SDK da aggiungere a un progetto quando viene creata un'istanza del modello di elemento.

```xml
<VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
    <TemplateData> . . . </TemplateData>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>Microsoft Visual C++ Runtime Package, Version=11.0.0.0</SDKReference>
...
```

## <a name="see-also"></a>Vedere anche
- [Elemento References (modelli di Visual Studio)](../extensibility/references-element-visual-studio-templates.md)
- [Elemento Reference (modelli di Visual Studio)](../extensibility/reference-element-visual-studio-templates.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)