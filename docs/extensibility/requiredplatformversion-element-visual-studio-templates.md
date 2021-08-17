---
description: Specifica la versione minima del sistema operativo necessaria per il corretto funzionamento del modello di progetto.
title: Elemento RequiredPlatformVersion (modelli di Visual Studio)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9f5f72045fdfca073fbc740698c2eefe57a1a932f32751f9fe278e17c280fad9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388531"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Elemento RequiredPlatformVersion (Visual Studio modelli)

Specifica la versione minima del sistema operativo necessaria per il corretto funzionamento del modello di progetto. Questo elemento viene usato per i modelli di progetto che creano [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app.

 Il `RequiredPlatformVersion` valore viene confrontato direttamente con la versione del sistema operativo. Se è superiore alla versione del sistema operativo, il modello non viene visualizzato nella finestra di `RequiredPlatformVersion` **dialogo Project** nuova versione. Per specificare un modello per [!INCLUDE[win8](../debugger/includes/win8_md.md)] o versione successiva, `RequiredPlatformVersion` impostare su 6.2.0. Per specificare un modello per [!INCLUDE[win81](../debugger/includes/win81_md.md)] o versione successiva, `RequiredPlatformVersion` impostare su 6.3.0.

 I modelli che `RequiredPlatformVersion` specificano =8 sono compatibili con i modelli dei clienti [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] precedenti.

 VsTemplate TemplateData ..... TargetPlatformName RequiredPlatformVersion

## <a name="syntax"></a>Sintassi

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nessuno.

### <a name="attributes"></a>Attributi

 Nessuno.

### <a name="child-elements"></a>Elementi figlio

 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Specifica la piattaforma a cui è destinato il modello di progetto.|

## <a name="text-value"></a>Valore di testo

 È necessario specificare un valore di testo.

## <a name="remarks"></a>Commenti

 Questo testo specifica la versione minima del sistema operativo richiesta dal modello.

## <a name="example"></a>Esempio

 Questo esempio specifica che il modello di progetto è destinato a [!INCLUDE[win8](../debugger/includes/win8_md.md)] o versioni successive.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedi anche

- [Elemento TargetPlatformName (Visual Studio modelli)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Visual Studio riferimento allo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
