---
title: Elemento SDKReference (modelli Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento SDKReference e su come specifica che il modello di elemento usa un riferimento SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5ea070cf466782a1da09e1ba48d08a6965fd041a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634492"
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
 Nessuno.

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Riferimento](../extensibility/reference-element-visual-studio-templates.md)|Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

## <a name="remarks"></a>Commenti
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

## <a name="see-also"></a>Vedi anche
- [Elemento References (modelli di Visual Studio)](../extensibility/references-element-visual-studio-templates.md)
- [Elemento Reference (modelli di Visual Studio)](../extensibility/reference-element-visual-studio-templates.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
